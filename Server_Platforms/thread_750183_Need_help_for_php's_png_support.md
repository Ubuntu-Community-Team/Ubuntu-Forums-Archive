---
title: "Need help for php's png support"
date: 2008-04-09
forum: Server Platforms
---

### Post by roamer.roamer on 2008-04-09
hi all.
These days I tried to build a lamp server from source files.My php program must use the png functions. I compiled my php with gd support.I cannot get my php to support png and just didn't know how to solve it.
Here is what I did.
packages
jpegsrc.v6b.tar.gz
libpng-1.2.26.tar.gz
gd-2.0.36RC1.tar.gz
php-5.2.4.tar.gz
I installed jpeg with the following configuration.
./configure --prefix=/usr/local/gdlib/jpeg --enable-shared --enable-static
I installed png with the following configuration.
./configure --prefix=/usr/local/gdlib/png
I installed gd with the following configuration.
./configure --prefix=/usr/local/gdlib/gd --with-png=/usr/local/gdlib/png --with-jpeg=/usr/local/gdlib/jpeg
I installed php with the following configuration.
./configure --prefix=/usr/local/php --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql=/usr/local/mysql --with-config-file-path=/usr/local/php --with-mysqli=/usr/local/mysql/bin/mysql_config --enable-mbstring --enable-sockets --enable-soap --enable-libxml --enable-session --with-gd=/usr/local/gdlib/gd --with-jpeg-dir=/usr/local/gdlib/jpeg --with-png-dir=/usr/local/gdlib/png

There were no errors during the install process.I ran the phpinfo function and found that the gd didn't support png and jpeg.
GD Support enabled
GD Version 2.0 or higher
GIF Read Support enabled
GIF Create Support enabled
WBMP Support enabled 
what's wrong?who can help me?
Thanks a lot.

---

### Post by Dr Small on 2008-04-09
I never could get Php's GD functions to work for me either. I ended up going to Xampp with it already enabled.

---

