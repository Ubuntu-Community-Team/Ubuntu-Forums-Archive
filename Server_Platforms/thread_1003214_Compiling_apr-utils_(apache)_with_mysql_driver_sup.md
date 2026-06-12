---
title: "Compiling apr-utils (apache) with mysql driver support"
date: 2008-12-05
forum: Server Platforms
---

### Post by PC_Nerd on 2008-12-05
Hi,

I'm trying to compile apr-utils with mysql driver so I can use mod_dbd for apache authentication.  I've compile mysql from source, apr, apr-utils and apache ( then php).  No success.  From looking back I dont think that it found my mysql directory properly.

I've kept a log of the ./configure options i made etc - so Ill attach that at the end.

Can I just add that where I specify --with-mysql for the apr-utils, I've tried both the --prefix directory for compiling mysql, as well as the raw source code directory ( which is/root/downloads/<whatever the download was named>

with the current --with-mysql option, It finds/can use mysql.h however it cannot use/find mysql_r ( which is the safe threads i beleive).


I understand that this is an apache compilation issue and shoudl probably go onto the apache forums - however theyve been down for a few days so I appreciate any suggestions you can make.

I've included the php configuration incase it may have written over anything etc.  The only other thing I think I shoudl mention is that im installing everythign to /usr/local/server/<component> eg: /usr/local/server/apache2||mysql etc.


Thanks,
Jack


* The first few lines are the sites that I used to get the information I need ( plus other stuff regarding server configuration etc etc etc).  It might provide any additional information that I've missed or need etc. Thanks
```


http://spiralbound.net/2005/04/29/apache-mysql-and-php-howto-from-source
http://ubuntuforums.org/archive/index.php/t-757353.html
http://www.usefuljaja.com/2007/4/ubuntu-setup-page-1
http://lists.netfilter.org/pipermail/netfilter/2001-November/027724.html
http://dev.mysql.com/doc/refman/5.0/en/installing-binary.html
https://help.ubuntu.com/community/phpMyAdmin

Download sources.

aptitude install libncurses-dev ( mysql dependency)

(mysql)
./configure --prefix=/usr/local/server/mysql
make
make install
(mysql setup for running)
groupadd mysql
useradd -g mysql mysql
cd /usr/local

apache apr/apr-utils ( with mysql support for dbd)


(in srclib/apr)
./configure --prefix=/usr/local/server/apache2
make
make install


(in srclib/apr-util)
./configure --pref-c=/usr/local/server/apache2 --with-apr=/usr/local/server/apache2 --with-mysql=/usr/local/server/mysql
make
make install


dependency: zlib1g-dev (mod_defalte), libssl-dev (mod_ssl)

(httpd)
./configure --prefix=/usr/local/server/apache2 --with-included-apr --with-apr-utils=/usr/local/server/apache2 --enable-mods-shared=all --enable-module=so --enable-rewrite --enable-ssl
make
make install

(php)
dependency: libxml2-dev, libjpeg-dev (accept dependancy change), libpng-dev (accept the dependency change),

./configure –with-apxs2=/usr/local/server/apache2/bin/apxs –with-mysqli=/usr/local/server/mysql/bin –enable-debug=no –enable-track-vars=yes –enable-bcmath=yes –enable-memory-limit=yes –enable-ftp –with-gd –with-jpeg-dir=/usr/local –with-png-dir=/usr/local –with-zlib-dir=/usr 
make
make test (send test report)
make install




```

---

### Post by PC_Nerd on 2008-12-06
Bump - any suggestions ?

Thanks

---

