---
title: "Compiling PHP 5.3 on Ubuntu 8.04 Server"
date: 2009-11-10
forum: Server Platforms
---

### Post by paralyzah on 2009-11-10
Hi, I've tried for a long time now, but can't seem to get it right. These are the options phpinfo() tells me I've compiled with:

'./configure' '--prefix=/usr' '--with-apxs2=/usr/bin/apxs2' '--with-config-file-path=/etc/php5/apache2' '--with-config-file-scan-dir=/etc/php5/apache2/conf.d' '--mandir=/usr/share/man' '--disable-debug' '--with-regex=php' '--disable-rpath' '--disable-static' '--with-pic' '--with-layout=GNU' '--with-pear=/usr/share/php' '--enable-calendar' '--enable-sysvsem' '--enable-sysvshm' '--enable-sysvmsg' '--enable-bcmath' '--with-bz2' '--enable-ctype' '--with-db4' '--without-gdbm' '--with-iconv' '--enable-exif' '--enable-ftp' '--with-gettext' '--enable-mbstring' '--with-pcre-regex=/usr' '--enable-shmop' '--enable-sockets' '--enable-wddx' '--with-libxml-dir=/usr' '--with-zlib' '--with-kerberos=/usr' '--with-openssl=/usr' '--enable-soap' '--enable-zip' '--with-exec-dir=/usr/lib/php5/libexec' '--without-mm' '--with-curl=shared,/usr' '--with-zlib-dir=/usr' '--with-gd=shared,/usr' '--enable-gd-native-ttf' '--with-gmp=shared,/usr' '--with-jpeg-dir=shared,/usr' '--with-xpm-dir=shared,/usr/X11R6' '--with-png-dir=shared,/usr' '--with-freetype-dir=shared,/usr' '--with-t1lib=shared,/usr' '--with-ldap=shared,/usr' '--with-ldap-sasl=/usr' '--with-mhash=shared,/usr' '--with-mysql=shared,/usr' '--with-mysqli=/usr/bin/mysql_config' '--with-pspell=shared,/usr' '--with-unixODBC=shared,/usr' '--with-xsl=shared,/usr' '--with-snmp=shared,/usr' '--with-sqlite=shared,/usr' '--with-mssql=shared,/usr' '--with-tidy=shared,/usr' '--with-xmlrpc=shared' '--with-pgsql=shared,/usr' '--enable-gd-native-ttf' '--enable-dba=shared' '--with-openssl-dir=shared,/usr' '--enable-gd-jis-conv' '--enable-json' '--with-mcrypt=shared,/usr' '--enable-pcntl' '--with-pdo-mysql' '--with-pdo-odbc=unixODBC,/usr' '--with-pdo-pgsql=shared,/usr' '--with-pdo-sqlite' '--enable-xmlreader' '--with-tsrm-pthreads' '--with-imap' '--with-imap-ssl'

But neither gd, mysql or mcrypt seems to be loaded. All the dependencies seems to be there and I can't recall any errors while compiling. I honestly don't know what more to troubleshoot and I've googled for days without any helping answers so any reply would be greatly appreciated. Thanks!

---

