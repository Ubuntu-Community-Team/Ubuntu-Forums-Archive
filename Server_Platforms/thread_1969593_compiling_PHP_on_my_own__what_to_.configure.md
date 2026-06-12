---
title: "compiling PHP on my own / what to ./configure?"
date: 2012-04-30
forum: Server Platforms
---

### Post by A2llex on 2012-04-30
hi, i'm gonna to compile PHP on my own, but i don't know yet what are all those parameters for.

Please do you know any source where would i read about that? or about configuring web server? or could you write about that here? thx.


./configure \
      --enable-bcmath \
      --enable-calendar \
      --enable-dba \
      --enable-exif \
      --enable-ftp \
      --enable-mbstring \
      --enable-shmop \
      --enable-sigchild \
      --enable-soap \
      --enable-sockets \
      --enable-sysvmsg \
      --enable-wddx \
      --enable-zip \
      --with-apxs2=/usr/local/apache2/bin/apxs \
      --with-bz2 \
      --with-config-file-path=/usr/local/apache2/conf \
      --with-curl \
      --with-gd \
      --with-gettext \
      --with-mcrypt \
      --with-openssl \
      --with-xmlrpc \
      --with-zlib

---

### Post by CharlesA on 2012-04-30
Why not use the copy of PHP5 (and apache2) in the repos?

As for compiling stuff yourself, see here: [http://hulan.info/item/compile-apache-with-ssl-php-5-and-mysql-on-linux](http://hulan.info/item/compile-apache-with-ssl-php-5-and-mysql-on-linux)

---

### Post by A2llex on 2012-04-30
> **CharlesA said:**
> Why not use the copy of PHP5 (and apache2) in the repos?

As for compiling stuff yourself, see here: [http://hulan.info/item/compile-apache-with-ssl-php-5-and-mysql-on-linux](http://hulan.info/item/compile-apache-with-ssl-php-5-and-mysql-on-linux)


cuz there is old version, and even i have an option what to configure..

---

### Post by CharlesA on 2012-04-30
> **A2llex said:**
> cuz there is old version, and even i have an option what to configure..
Then read the docs here:
[http://php.net/releases/index.php](http://php.net/releases/index.php)

I just checked my Precise install and I have php 5.3.10:

```
php5 5.3.10-1ubuntu3 
```

EDIT: If you want the latest version, use a PPA:
[http://askubuntu.com/questions/109404/how-do-i-install-php-5-4-0](http://askubuntu.com/questions/109404/how-do-i-install-php-5-4-0)

---

### Post by A2llex on 2012-04-30
> **CharlesA said:**
> Then read the docs here:
[http://php.net/releases/index.php](http://php.net/releases/index.php)

I just checked my Precise install and I have php 5.3.10:

```
php5 5.3.10-1ubuntu3 
```EDIT: If you want the latest version, use a PPA:
[http://askubuntu.com/questions/109404/how-do-i-install-php-5-4-0](http://askubuntu.com/questions/109404/how-do-i-install-php-5-4-0)

yep, i know that ppa, but i don't very like unofficial repos. 
further, i want to use only the latest versions of software.

and in that ondrey's ppa there's not suhosin patch included :( so even so i hafto recompile php then...

Pity that precise doesn't support latest 5.4* version - do you think, will they update sometimes?

---

### Post by CharlesA on 2012-04-30
If you want to be running the latest version of software, you might be better off with a distro such as Debian Sid. Maybe want to try a rolling release distro too.

I don't know if Precise will be getting the 5.4 version of php.

---

