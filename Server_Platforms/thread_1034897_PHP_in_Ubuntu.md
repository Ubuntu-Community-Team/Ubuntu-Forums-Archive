---
title: "PHP in Ubuntu"
date: 2009-01-09
forum: Server Platforms
---

### Post by bandish on 2009-01-09
Hi all using this forum for first time

can any one help?

My problem is like this : 

below is the steps that i have done to php.ini

steps given below to connect MSSQL with php:

1. Settings related to your php.ini file:

a) search the variable mssql.secure_connection in your php.ini file and put it to on mode if its off
b) remove comment from the dll extention php_mssql.dll (i.e. remove the ; from the front of the extention )

2. Settings related to the dll files.

download a file name ntwdblib.dll from the internet. you can download it from here or can search on internet for that. copy the downloaded dll to the apache/bin directory and for IIS copy it to the php extention directory (if path not known can be found in php.ini for variable extension_dir)

also you need to have your php_mssql.dll in your php extension directory. if its not present please download it and copy it to the default php extension directory.

3. restart all your services (i.e. php and apache or iis) 

After this I am able to connect remote ms-sql server to post and retrive data.

but the problem is after these 3 steps i am not able to open localhost/phpmyadmin

I am using ubuntu 8 as OS
netbeans 6.5 as ide for php
and xampp for linux

i get following error message

1 starting xampp: &#8220;root@bandish-desktop:/home/bandish# /opt/lampp/lampp start
Starting XAMPP for Linux 1.6.8a&#8230;
PHP Warning: PHP Startup: Unable to load dynamic library &#8216;/opt/lampp/lib/php/extensions/no-debug-non-zts-20060613/php_mssql.dll&#8217; - /opt/lampp/lib/php/extensions/no-debug-non-zts-20060613/php_mssql.dll: cannot open shared object file: No such file or directory in Unknown on line 0
XAMPP: Starting Apache with SSL (and PHP5)&#8230;
XAMPP: Starting MySQL&#8230;
XAMPP: Starting ProFTPD&#8230;
XAMPP for Linux started.
&#8221;

2. while opening localhost: &#8221; Existing configuration file (./config.inc.php) is not readable.&#8221;

---

### Post by dgoosens on 2009-01-09
hi,

you followed the Windows instructions...
there are no *.dll files under Linux.

you will find quite some answers here:
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

here:
[http://www.netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html]("http://www.netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html")

just note that the extensions in Linux should have an *.so extenstion (as you can read in the php.ini file)

hope it helps
dGo

---

