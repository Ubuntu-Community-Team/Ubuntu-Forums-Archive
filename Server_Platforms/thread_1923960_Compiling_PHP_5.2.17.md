---
title: "Compiling PHP 5.2.17"
date: 2012-02-11
forum: Server Platforms
---

### Post by erickmlr on 2012-02-11
I'm trying to compile PHP 5.2.17 on Ubuntu 11.10 x64 (to use it side-by-side with 5.3), with no success. What I've done:

1. Downloaded source from php.net, unpacked it
2. Run... 

./configure --prefix=/usr/local/php-5.2.17 --with-config-file-path=/usr/local/php-5.2.17/etc --disable-ipv6 --with-zlib --enable-bcmath --with-bz2 --with-curl --enable-exif --enable-ftp --with-gd --with-ttf --enable-gd-native-ttf --with-imap-ssl --enable-mbstring --with-mhash --with-mysql --with-mysqli --enable-pcntl --with-pdo-mysql --with-pdo-sqlite --enable-shmop --enable-soap --enable-sockets --enable-sqlite-utf8 --with-xmlrpc --with-xsl --with-pear --enable-fastcgi --with-openssl --disable-cli --with-jpeg-dir --with-png-dir

and got the result:

configure: error: libjpeg.(a|so) not found.

What I've tried so far:

. install libjpeg-dev (all versions);
. download and build libjpeg, and defined the path on --with-jpeg-dir;
. updatedb, 'locate' for libjpeg.so, and defined on --with-jpeg-dir all the paths found;

On the x32 versions it compiles normally, and on Fedora Core 16 it compiled normally on both architectures.

Any tip or help?

---

### Post by SeijiSensei on 2012-02-12
When you built libjpeg was it installed to /usr/local/lib?  Did you run ldconfig after it was installed?  I would think giving the path explicitly to configure should be enough, but try running ldconfig just in case.

---

### Post by 00trav on 2012-03-01
I just ran into the same problem for both libjpeg and libpng.

I believe the problem is that the .so's for those libraries are no longer in the same place.  I found both in /usr/lib/x86_64-linux-gnu/ (actually found more symlinks pointing libjpeg.so to libjpeg.so.62.0.0 - but there was at least a libjpeg.so to link to)

I was able to fix my problem by just placing symlinks in the /usr/lib folder pointing to each of the libjpeg.so and libpng.so libraries found in the  x86_64-linux-gnu/ directory.

---

### Post by dhiaeddine on 2013-04-15
[http://blog.angeloff.name/post/2012/06/18/ubuntu-12-04-precise-php-5-2/](http://blog.angeloff.name/post/2012/06/18/ubuntu-12-04-precise-php-5-2/)

---

