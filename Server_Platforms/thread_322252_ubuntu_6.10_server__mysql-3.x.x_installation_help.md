---
title: "ubuntu 6.10 server  mysql-3.x.x installation help"
date: 2006-12-20
forum: Server Platforms
---

### Post by badilcan on 2006-12-20
Hi all. I installed a  ubuntu server 6.10 edgy eft at
core2duo .
I tried to install
Mysql-3.23.58 

tar xzfv mysql-3.23.58
cd mysql-3.23.58

./configure
--prefix=/usr/local/mysql
but I got this message

configure: error: This is a linux system and Linuxthreads was not found.On linux linuxthreads should be used.Please install Linuxthreads ( or a new glibc ) and try again.

after that I tried that for amd64


CC=gcc \
CFLAGS="-O3 -fno-omit-frame-pointer" \
CXX=gcc \
CXXFLAGS="-O3 -fno-omit-frame-pointer -felide-constructors \
-fno-exceptions -fno-rtti" \
./configure --prefix=/usr/local/mysql \
"--with-comment=Official MySQL binary" \
--with-extra-charsets=complex

but result is same
Please help.....

---

