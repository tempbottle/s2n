#
# Copyright 2014 Amazon.com, Inc. or its affiliates. All Rights Reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License").
# You may not use this file except in compliance with the License.
# A copy of the License is located at
#
#  http://aws.amazon.com/apache2.0
#
# or in the "license" file accompanying this file. This file is distributed
# on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either
# express or implied. See the License for the specific language governing
# permissions and limitations under the License.
#

SRCS=$(wildcard *.c)
OBJS=$(SRCS:.c=.o)

all: libtests2n.so libtests2n.dylib

include ../../s2n.mk

CFLAGS += -I../../ -I../../api/ -I../../libcrypto-root/include/
LDFLAGS += -L../../lib/ -lcrypto -lpthread -ls2n

libtests2n.so: ${OBJS}
	gcc ${CFLAGS} -shared ${LDFLAGS} -o libtests2n.so ${OBJS}

libtests2n.dylib: ${OBJS}
	test ! -f /usr/lib/libSystem.dylib || libtool ${LDFLAGS} -dynamic -o libtests2n.dylib ${OBJS}
