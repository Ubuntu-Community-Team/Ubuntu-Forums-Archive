---
title: "Ubuntu + Apache 2.0 + PHP 5.2.1 - cannot use dynamic extensions (e.g. pdo.so!)"
date: 2007-03-06
forum: Server Platforms
---

### Post by feenster on 2007-03-06
Hi all,
I'm trying to compile **PHP 5.2.1** on my **Ubuntu 6.10** server. I've downloaded the source code from php.net and am running the following configure command on it:
```

./configure --with-apxs2=/usr/bin/apxs2 --with-mysql --with-informix=/opt/informix --enable-shared --enable-pdo=shared --without-sqlite --without-pdo-sqlite --with-pdo-mysql=shared --with-zlib --with-xml --with-pdo-informix=shared,/opt/informix

```

After doing this, then **make**, I copy over the generated **libphp5.so** file into my Apache extensions directory, add **extension=pdo.so** (and lines for the PDO-MySQL/Informix extensions) into my php.ini and restart Apache. I would expect to see PDO, PDO-MySQL and PDO-Informix listed in my **phpinfo()** - but they don't appear. 

So, I tried recompiling PHP but without any of the PDO extensions being shared. This worked, and I could see PDO and PDO-MySQL in **phpinfo()**, but not PDO-Informix.

So, can anyone hazard a guess as to why none of the PDO extensions load when compiled shared? I don't get any related error messages in the Apache or System logs by the way....

Cheers,
  Matt

---

### Post by feenster on 2007-03-07
Sorted! The process was this:

1) Download the PHP 5.2.1 source into a fresh folder
2) Run the following:
```
./configure --with-apxs2=/usr/bin/apxs2 --with-mysql --with-informix=/opt/informix --enable-shared --enable-pdo=shared --without-sqlite --without-pdo-sqlite --with-zlib --with-xml --with-pecl --with-pdo-mysql=shared --with-pdo-informix=shared,/opt/informix --with-config-file-path=/etc/php5/apache2
```
3) Ran "make" and "make install"
4) Altered /etc/php5/apache2/php.ini to this:
```
extension_dir=/usr/local/lib/php/extensions/no-debug-zts-20060613
```
5) Added the following to php.ini:
```
extension=pdo.so
extension=pdo_mysql.so
extension=pdo_informix.so
```
6) Restarted Apache2

And they appear in PHPInfo();!!! This leaves me with another problem unfortunately. *.php files are just displaying as source code in the browser, *except for*:
```
<?php phpinfo(); ?>
```

Any ideas what could be causing this? I've enabled the PHP5 mod using "a2enmod php5", but to no joy. Any thoughts?

Cheers,
  Matt

---

### Post by Parama on 2007-03-23
Hi,

You should map the content-type to the php.so. By adding this to your apache2.conf it should work:

```

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

```

---

