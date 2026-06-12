---
title: "Apache. Problem loading mysql objects"
date: 2007-03-24
forum: Server Platforms
---

### Post by prodsacnetworking on 2007-03-24
Hi,

I have a couple of ubuntu servers that I use lamp by compiling it.

My main web server is a trustix with LAMP packages.

I have a web site that I'm unable to use on the ubuntu ones because everything that needs MySQL connection don't work... I have nothing in any logs.

Don't work:
[http://www2.fermieresmandeville.com/projets.php](http://www2.fermieresmandeville.com/projets.php)

Works:
[http://www.fermieresmandeville.com/projets.php](http://www.fermieresmandeville.com/projets.php)

Do you have any ideas what module I would need to install in the complilation process??

thanks

---

### Post by conjur3r on 2007-03-24
When you manually compile things in, the important connection you need to make is to tell PHP to support MySQL by giving it the **--with-mysql** parameter.  Without this, your php applications will not have the basic mechanisms to interface with the database.

[http://php.net/mysql](http://php.net/mysql)

---

### Post by prodsacnetworking on 2007-03-24
my compile command::

'./configure' '--prefix=/usr/local/apache2_php5/php' '--with-apxs2=/usr/local/apache2_php5/bin/apxs' '--with-zlib' '--with-mysql' '--with-gd' '--with-jpeg-dir' '--with-openssl' '--with-curl' '--with-exif' '--with-mysqli' '--with-mhash' '--with-php-mbstring'

---

### Post by conjur3r on 2007-03-25
Is there a section on MySQL in your phpinfo?

The only other thing I can think of is that the php config/make/make install process put the shared object somewhere else that hasn't been configured by php.ini.  This is defined by something like extensions_dir.

Also, the reason why you are not getting any php errors is most likely because display_errors has been switched off in your php.ini file.  Take a look at it in /etc/php5/apache2/php.ini

---

### Post by prodsacnetworking on 2007-03-25
ok. thanks.

so I get: 

httpd: PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/share/php/exif.so' - /usr/share/php/exif.so: cannot open shared object file: No such file or directory in Unknown on line 0
Mar 25 09:07:33 smith httpd: PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/share/php/gd.so' - /usr/share/php/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0
Mar 25 09:07:33 smith httpd: PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/share/php/mysqli.so' - /usr/share/php/mysqli.so: cannot open shared object file: No such file or directory in Unknown on line 0
Mar 25 09:07:33 smith httpd: PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/share/php/mhash.so' - /usr/share/php/mhash.so: cannot open shared object file: No such file or directory in Unknown on line 0
Mar 25 09:07:33 smith httpd: PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/share/php/curl.so' - /usr/share/php/curl.so: cannot open shared object file: No such file or directory in Unknown on line 0

He seems not to be able to copy the modules in the goos repertoires... 

ls /usr/local/apache2_php5/php/include/php/ext/
date  dom  gd  hash  iconv  libxml  pcre  pdo  session  sqlite  standard  xml

I'm gonna try reinstall it with:
'./configure' '--prefix=/usr/local/apache2_php5/php' '--with-apxs2=/usr/local/apache2_php5/bin/apxs' '--with-zlib' '--with-mysql' '--with-gd' '--with-jpeg-dir' '--with-openssl' '--with-curl' '--with-exif' '--with-mysqli=/usr/bin/mysql_config' '--with-mhash' '--with-php-mbstring'

---

