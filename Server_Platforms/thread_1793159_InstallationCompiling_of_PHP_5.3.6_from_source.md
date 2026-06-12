---
title: "Installation/Compiling of PHP 5.3.6 from source"
date: 2011-06-29
forum: Server Platforms
---

### Post by beezm on 2011-06-29
Hey guys I've been messing with this problem for at least a few hours now. Searched around quite a bit too... I'm trying to get an nginx/php-fpm/mysql stack setup on Ubuntu Server 10.04 LTS 32 bit version. 

I have pretty much got everything going fine, except PHP extensions. For whatever reason when I compile php it is seeming to not compile any extensions with it ?

I am using the following configure flags:

```
./configure --prefix=/opt/php5 --with-config-file-path=/opt/php5/etc --with-curl --with-pear --with-gd --with-jpeg-dir --with-png-dir --with-zlib --with-mcrypt --with-mhash --with-mysql --with-mysqli --with-pdo-mysql --with-openssl --with-xmlrpc --with-xsl --with-bz2 --with-gettext --with-fpm-user=www-data --with-fpm-group=www-data --enable-fpm --enable-exif --enable-wddx --enable-zip --enable-bcmath --enable-calendar --enable-ftp --enable-mbstring --enable-soap --enable-sockets --enable-sqlite-utf8 --enable-shmop --enable-dba --enable-sysvmsg --enable-sysvsem --enable-sysvshm
```

My understanding is (*or so I thought*) that when the --enable switches are given that tells the compiler to compile those extensions. Well it's not doing that for me. nginx/php-fpm are up and running fine, but without any php extensions !
When I check phpinfo all of the extensions were enabled properly, but I don't have any compiled *.so files to load.
Here is a static copy of phpinfo() from this install, [http://iamstewart.com/dev/phpinfo.html](http://iamstewart.com/dev/phpinfo.html)

Sooo, my next step was attempting to compile them separately, I went into my source/php/ext/mysqli directory and did [FONT="Courier New"]phpize[/FONT] [FONT="Courier New"]./configure --with-mysqli[/FONT] and then [FONT="Courier New"]make[/FONT], and I get a mysqli.so file produced in /modules. This file isn't a valid extension though according to PHP :(

I don't seem to remember having this problem before, any help would be greatly appreciated. I thought it was supposed to compile the modules/extensions when I did make? 

Thanks ahead of time everyone :popcorn:

---

### Post by Bachstelze on 2011-06-29
If phpinfo says the extensions are enabled, it means the extensions are enabled. ;) The reason you don't get any .so files is that the modules are statically built into PHP, but they are there, just try them out.

---

### Post by waffleguy4 on 2011-07-08
Hi,

I'm having problems getting SOAP to work on my installed version of PHP - 5.3.5-1ubuntu7.2.  I am completely lost so I think my next step is to try to upgrade PHP to 5.3.6 from source, like you are saying. However, I do not have much experience in compiling binaries. Could you please outline the commands used to install it?

Thanks!

---

