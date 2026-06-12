---
title: "apache not compiling wont use APR util with bundled APR"
date: 2007-05-25
forum: Server Platforms
---

### Post by madubuntuer on 2007-05-25
using apache 2.2-4 on dapper. It wont let me configure the binary.
Configuring Apache Portable Runtime Utility library...

checking for APR-util... yes
configure: error: Cannot use an external APR-util with the bundled APR
root@ubuntu:/home/s/binary/httpd-2.2.4#
root@ubuntu:/home/s/binary/httpd-2.2.4#   

tried both gcc3.4 and 4.0

I seemed to have fixed that by install the APR but now i get different eror

awk -f /home/s/binary/httpd-2.2.4/build/make_exports.awk `cat export_files` > exports.c
/usr/local/apr/build-1/libtool --silent --mode=compile gcc-4.0 -g -O2 -pthread    -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE    -I/home/s/binary/httpd-2.2.4/srclib/pcre -I. -I/home/s/binary/httpd-2.2.4/os/unix -I/home/s/binary/httpd-2.2.4/server/mpm/prefork -I/home/s/binary/httpd-2.2.4/modules/http -I/home/s/binary/httpd-2.2.4/modules/filters -I/home/s/binary/httpd-2.2.4/modules/proxy -I/home/s/binary/httpd-2.2.4/include -I/home/s/binary/httpd-2.2.4/modules/generators -I/home/s/binary/httpd-2.2.4/modules/mappers -I/home/s/binary/httpd-2.2.4/modules/database -I/usr/local/apr/include/apr-1 -I/usr/local/apache2/include -I/home/s/binary/httpd-2.2.4/modules/proxy/../generators -I/home/s/binary/httpd-2.2.4/modules/ssl -I/home/s/binary/httpd-2.2.4/modules/dav/main  -prefer-non-pic -static -c exports.c && touch exports.lo
libtool: compile: unable to infer tagged configuration
libtool: compile: specify a tag with `--tag'
make[2]: *** [exports.lo] Error 1
make[2]: Leaving directory `/home/s/binary/httpd-2.2.4/server'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/s/binary/httpd-2.2.4/server'
make: *** [all-recursive] Error 1
root@ubuntu:/home/s/binary/httpd-2.2.4# make && make install

---

### Post by marslert on 2007-08-07
Hi madubuntuer,

U can try this.

[PHP]# ./configure --prefix=/usr/local/apache2 --enable-so --with-included-apr[/PHP]

from [laffers.net]("http://laffers.net/howtos/howto-install-apache")

---

