---
title: "Upgrading to Ubuntu server 22.04 from 20.04 makes no  LAMP applications are working"
date: 2022-06-04
forum: Server Platforms
---

### Post by deepakdeshp on 2022-06-04
I installed LAMP applications on my Ubuntu 20.04 server, I upgraded the server to 22.04 and none of them work.
The error is internal server error 500
I can login to mysql apache2 is also running.


```
 uma@ubuntu:/var/log/apache2$ tail error.log[Sat Jun 04 12:10:14.541485 2022] [mpm_prefork:notice] [pid 3722] AH00163: Apache/2.4.52 (Ubuntu) mpm-itk/2.4.7-04 configured -- resuming normal operations
[Sat Jun 04 12:10:14.541585 2022] [core:notice] [pid 3722] AH00094: Command line: '/usr/sbin/apache2'
[Sat Jun 04 13:54:24.645152 2022] [php:warn] [pid 6030] [client 192.168.1.7:54152] PHP Warning:  require_once(/var/www/html/includes/defines.php): Failed to open stream: No such file or directory in /var/www/html/index.php on line 37
[Sat Jun 04 13:54:24.686853 2022] [php:error] [pid 6030] [client 192.168.1.7:54152] PHP Fatal error:  Uncaught Error: Failed opening required '/var/www/html/includes/defines.php' (include_path='.:/usr/share/php') in /var/www/html/index.php:37\nStack trace:\n#0 {main}\n  thrown in /var/www/html/index.php on line 37
[Sat Jun 04 13:54:36.636038 2022] [php:warn] [pid 6033] [client 192.168.1.7:54154] PHP Warning:  require_once(/var/www/html/includes/defines.php): Failed to open stream: No such file or directory in /var/www/html/index.php on line 37
[Sat Jun 04 13:54:36.636117 2022] [php:error] [pid 6033] [client 192.168.1.7:54154] PHP Fatal error:  Uncaught Error: Failed opening required '/var/www/html/includes/defines.php' (include_path='.:/usr/share/php') in /var/www/html/index.php:37\nStack trace:\n#0 {main}\n  thrown in /var/www/html/index.php on line 37
[Sat Jun 04 13:57:31.765105 2022] [php:error] [pid 6181] [client 192.168.1.7:54158] PHP Fatal error:  Type of xml_format_exception::$line must be int (as in class Exception) in /var/www/html/moodle/lib/xmlize.php on line 0
[Sat Jun 04 14:04:18.560854 2022] [php:error] [pid 6535] [client 192.168.1.7:54160] PHP Fatal error:  Type of xml_format_exception::$line must be int (as in class Exception) in /var/www/html/moodle/lib/xmlize.php on line 0
[Sat Jun 04 14:04:23.374302 2022] [php:error] [pid 6538] [client 192.168.1.7:54162] PHP Fatal error:  Type of xml_format_exception::$line must be int (as in class Exception) in /var/www/html/moodle/lib/xmlize.php on line 0
[Sat Jun 04 14:04:26.271004 2022] [php:error] [pid 6539] [client 192.168.1.7:54164] PHP Fatal error:  Type of xml_format_exception::$line must be int (as in class Exception) in /var/www/html/moodle/lib/xmlize.php on line 0
uma@ubuntu:/var/log/apache2$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 21
Server version: 8.0.29-0ubuntu0.22.04.2 (Ubuntu)


Copyright (c) 2000, 2022, Oracle and/or its affiliates.


Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.


Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.


mysql> 


  
```
 Line 37 in /var/www/html/index.php is as follows
require_once JPATH_BASE . '/includes/defines.php';

If any other information is required , please let me know,

---

### Post by TheFu on 2022-06-04
Whenever a system is upgraded, the versions of almost every program changed.  The Release notes spell out the differences and it is expected that webapps will need to be reworked for the new versions of the software stack.

Basically, it is working as expected. There isn't any magical tool that will look through your webapp and magically migrated deprecated code. Sorry.

---

### Post by deepakdeshp on 2022-06-04
There has to be something not very big cause like may be php version upgrade causes the problem. Just the /var/www/html/index.php page also doesnt work in the browser. Surely that has to work in 22.04? When it starts working I guess all the LAMP applications like phpmyadmin,phpbb will work

---

### Post by #&amp;thj^% on 2022-06-04
The diff is in PHP 8.1 22.04 vs. php 7.4 20.04
Another poster had problems with PHP here : [https://ubuntuforums.org/showthread.php?t=2475324&p=14098712#post14098712](https://ubuntuforums.org/showthread.php?t=2475324&p=14098712#post14098712)

---

### Post by deepakdeshp on 2022-06-04
@1fallen That looks to be the problem . The different php versions. 
I am looking at a way to force the php version in 22.04 to version 7.4.3 and test.

---

### Post by #&amp;thj^% on 2022-06-04
There is plenty of options for that, But do Note: I've not tried with a lesser version PHP, and I use the PPA for PHP described in the other link.
Example:
```
apt search php 7.4
Sorting... Done
Full Text Search... Done
libapache2-mod-php7.4/jammy 8.1.2-1ubuntu2 i386
  Transitional package

libphp7.4-embed/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  HTML-embedded scripting language (Embedded SAPI library)

php-sabre-dav/jammy,jammy 1.8.12-10 all
  WebDAV Framework for PHP

php-symfony-polyfill-php74/jammy,jammy 1.24.0-1ubuntu2 all
  Symfony polyfill backporting some PHP 7.4+ features to lower PHP versions

php7.4/jammy,jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 all
  server-side, HTML-embedded scripting language (metapackage)

php7.4-amqp/jammy 1.11.0-4+ubuntu22.04.1+deb.sury.org+1 amd64
  AMQP extension for PHP

php7.4-apcu/jammy 5.1.21+4.0.11-7+ubuntu22.04.1+deb.sury.org+1 amd64
  APC User Cache for PHP

php7.4-apcu-bc/jammy 1.0.5-18+ubuntu22.04.1+deb.sury.org+1 amd64
  APCu Backwards Compatibility Module

php7.4-ast/jammy 1.0.16-4+ubuntu22.04.1+deb.sury.org+1 amd64
  AST extension for PHP 7

php7.4-bcmath/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  Bcmath module for PHP

php7.4-bz2/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  bzip2 module for PHP

php7.4-cgi/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  server-side, HTML-embedded scripting language (CGI binary)

php7.4-cli/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  command-line interpreter for the PHP scripting language

php7.4-common/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  documentation, examples and common module for PHP

php7.4-curl/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  CURL module for PHP

php7.4-dba/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  DBA module for PHP

php7.4-decimal/jammy 1.4.0-3+ubuntu22.04.1+deb.sury.org+1 amd64
  Arbitrary precision floating-point decimal for PHP

php7.4-dev/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  Files for PHP7.4 module development

php7.4-ds/jammy 1.4.0-4+ubuntu22.04.1+deb.sury.org+1 amd64
  PHP extension providing efficient data structures for PHP 7

php7.4-enchant/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  Enchant module for PHP

php7.4-facedetect/jammy 1.1.0-29-g0e243c5-2+ubuntu22.04.1+deb.sury.org+1 amd64
  Detect faces with PHP

php7.4-fpm/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  server-side, HTML-embedded scripting language (FPM-CGI binary)

php7.4-gd/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  GD module for PHP

php7.4-gearman/jammy 2.1.0+1.1.2-11+ubuntu22.04.1+deb.sury.org+1 amd64
  PHP wrapper to libgearman

php7.4-geoip/jammy 1.1.1+repack1-5+ubuntu22.04.1+deb.sury.org+1 amd64
  GeoIP module for PHP

php7.4-gmagick/jammy 2.0.6~rc1+1.1.7~rc3-10+ubuntu22.04.1+deb.sury.org+1 amd64
  Provides a wrapper to the GraphicsMagick library

php7.4-gmp/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  GMP module for PHP

php7.4-gnupg/jammy 1.5.1-2+ubuntu22.04.1+deb.sury.org+1 amd64
  PHP wrapper around the gpgme library

php7.4-grpc/jammy 1.45.0+1.33.1-1+ubuntu22.04.1+deb.sury.org+1 amd64
  High performance, open source, general RPC framework for PHP

php7.4-http/jammy 1:3.2.4-1+ubuntu22.04.1+deb.sury.org+1 amd64
  PECL HTTP module for PHP Extended HTTP Support

php7.4-igbinary/jammy 3.2.7+2.0.8-1+ubuntu22.04.1+deb.sury.org+1 amd64
  igbinary PHP serializer

php7.4-imagick/jammy 3.7.0-2+ubuntu22.04.1+deb.sury.org+1 amd64
  Provides a wrapper to the ImageMagick library

php7.4-imap/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  IMAP module for PHP

php7.4-inotify/jammy 3.0.0+0.1.6-3+ubuntu22.04.1+deb.sury.org+1 amd64
  Inotify bindings for PHP

php7.4-interbase/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  Interbase module for PHP

php7.4-intl/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  Internationalisation module for PHP

php7.4-json/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  JSON module for PHP

php7.4-ldap/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  LDAP module for PHP

php7.4-lua/jammy 2.0.7+1.1.0-13+ubuntu22.04.1+deb.sury.org+1 amd64
  PHP Embedded lua interpreter

php7.4-mailparse/jammy 3.1.2+2.1.7~dev20160128-7+ubuntu22.04.1+deb.sury.org+1 amd64
  Email message manipulation for PHP

php7.4-maxminddb/jammy 1.11.0-3+ubuntu22.04.1+deb.sury.org+1 amd64
  Reader for the MaxMind DB file format for PHP

php7.4-mbstring/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  MBSTRING module for PHP

php7.4-mcrypt/jammy 3:1.0.4-8+ubuntu22.04.1+deb.sury.org+1 amd64
  PHP bindings for the libmcrypt library

php7.4-memcache/jammy 8.0+4.0.5.2+3.0.9~20170802.e702b5f9+-7+ubuntu22.04.1+deb.sury.org+1 amd64
  memcache extension module for PHP

php7.4-memcached/jammy 3.2.0+2.2.0-1+ubuntu22.04.1+deb.sury.org+1 amd64
  memcached extension module for PHP, uses libmemcached

php7.4-mongodb/jammy 1.13.0+1.9.2+1.7.5-1+ubuntu22.04.1+deb.sury.org+2 amd64
  MongoDB driver for PHP

php7.4-msgpack/jammy 2.2.0~rc1+2.1.2+0.5.7-6+ubuntu22.04.1+deb.sury.org+1 amd64
  PHP extension for interfacing with MessagePack

php7.4-mysql/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  MySQL module for PHP

php7.4-oauth/jammy 2.0.7+1.2.3-14+ubuntu22.04.1+deb.sury.org+1 amd64
  OAuth 1.0 consumer and provider extension

php7.4-odbc/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  ODBC module for PHP

php7.4-opcache/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  Zend OpCache module for PHP

php7.4-pcov/jammy 1.0.11-4+ubuntu22.04.1+deb.sury.org+1 amd64
  Code coverage driver

php7.4-pgsql/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  PostgreSQL module for PHP

php7.4-phpdbg/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  server-side, HTML-embedded scripting language (PHPDBG binary)

php7.4-pinba/jammy 1.1.2-12+ubuntu22.04.1+deb.sury.org+1 amd64
  Pinba module for PHP

php7.4-propro/jammy 2.1.0+1.0.2+nophp8-14+ubuntu22.04.1+deb.sury.org+1 amd64
  propro module for PHP

php7.4-protobuf/jammy 3.21.1+3.12.4-1+ubuntu22.04.1+deb.sury.org+1 amd64
  Protocol buffers bindings for PHP

php7.4-ps/jammy 1.4.4+1.3.7-6+ubuntu22.04.1+deb.sury.org+1 amd64
  ps module for PHP

php7.4-pspell/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  pspell module for PHP

php7.4-psr/jammy 1.2.0-4+ubuntu22.04.1+deb.sury.org+1 amd64
  PSR interfaces for PHP

php7.4-radius/jammy 1.4.0~b1-22+ubuntu22.04.1+deb.sury.org+1 amd64
  radius client library for PHP

php7.4-raphf/jammy 2.0.1+1.1.2-13+ubuntu22.04.1+deb.sury.org+1 amd64
  raphf module for PHP

php7.4-readline/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  readline module for PHP

php7.4-redis/jammy 5.3.7+4.3.0-1+ubuntu22.04.1+deb.sury.org+1 amd64
  PHP extension for interfacing with Redis

php7.4-rrd/jammy 2.0.3+1.1.3-6+ubuntu22.04.1+deb.sury.org+1 amd64
  PHP bindings to rrd tool system

php7.4-smbclient/jammy 1.0.6-6+ubuntu22.04.1+deb.sury.org+1 amd64
  PHP wrapper for libsmbclient

php7.4-snmp/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  SNMP module for PHP

php7.4-soap/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  SOAP module for PHP

php7.4-solr/jammy 2.5.1+2.4.0-15+ubuntu22.04.1+deb.sury.org+1 amd64
  PHP extension for communicating with Apache Solr server

php7.4-sqlite3/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  SQLite3 module for PHP

php7.4-ssh2/jammy 1.3.1+0.13-6+ubuntu22.04.1+deb.sury.org+1 amd64
  Bindings for the libssh2 library

php7.4-stomp/jammy 2.0.2+1.0.9-15+ubuntu22.04.1+deb.sury.org+1 amd64
  Streaming Text Oriented Messaging Protocol (STOMP) client module for PHP

php7.4-swoole/jammy 4.8.5-2+ubuntu22.04.1+deb.sury.org+1 amd64
  Swoole Coroutine Fiber Async Programming Framework for PHP

php7.4-sybase/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  Sybase module for PHP

php7.4-tideways/jammy 5.0.4-13+ubuntu22.04.1+deb.sury.org+1 amd64
  Tideways PHP Profiler Extension

php7.4-tidy/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  tidy module for PHP

php7.4-uopz/jammy 7.1.1+6.1.2-6+ubuntu22.04.1+deb.sury.org+1 amd64
  UOPZ extension for PHP 7

php7.4-uploadprogress/jammy 2.0.2+1.1.4-7+ubuntu22.04.1+deb.sury.org+1 amd64
  file upload progress tracking extension for PHP

php7.4-uuid/jammy 1.2.0-11+ubuntu22.04.1+deb.sury.org+1 amd64
  PHP UUID extension

php7.4-xdebug/jammy 3.1.4+2.9.8+2.8.1+2.5.5-1+ubuntu22.04.1+deb.sury.org+1 amd64
  Xdebug Module for PHP

php7.4-xhprof/jammy 2.3.5+0.9.4-3+ubuntu22.04.1+deb.sury.org+1 amd64
  Hierarchical Profiler for PHP 5.x

php7.4-xml/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  DOM, SimpleXML, XML, and XSL module for PHP

php7.4-xmlrpc/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  XMLRPC-EPI module for PHP

php7.4-xsl/jammy,jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 all
  XSL module for PHP (dummy)

php7.4-yac/jammy 2.3.1+0.9.2-4+ubuntu22.04.1+deb.sury.org+1 amd64
  YAC (Yet Another Cache) for PHP

php7.4-yaml/jammy 2.2.2+2.1.0+2.0.4+1.3.2-5+ubuntu22.04.1+deb.sury.org+1 amd64
  YAML-1.1 parser and emitter for PHP

php7.4-zip/jammy 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 amd64
  Zip module for PHP

php7.4-zmq/jammy 1.1.3-23+ubuntu22.04.1+deb.sury.org+1 amd64
  ZeroMQ messaging bindings for PHP

php7.4-zstd/jammy 0.11.0-2+ubuntu22.04.1+deb.sury.org+1 amd64
  Zstandard extension for PHP

```
Good Luck, and keep us posted with your test results if you would.

---

### Post by deepakdeshp on 2022-06-04
I did the following, yet no joy

```
 sudo a2dismod php8.1 
sudo a2enmod php7.4
systemctl restart apache2
Still
php -v
PHP 8.1.2 (cli) (built: Apr  7 2022 17:46:26) (NTS)




```
php still doesnt work in 20.2 and the version is still 8.1. What am I missing?

---

### Post by #&amp;thj^% on 2022-06-04
**EDIT: Please be sure to have good back ups of all your Data bases!**

I hope you mean 22.04 and not 20.2 I don't know what that is even. :)
I don't have a clue... and my success comes from the PPA (I haven't had the same problems encountered by Ubuntu versions)I trust him far more than the Ubuntu PHP.
If you decide to follow the other thread link [https://ubuntuforums.org/showthread.php?t=2475324&p=14098712#post14098712](https://ubuntuforums.org/showthread.php?t=2475324&p=14098712#post14098712) I think you'll be happier. ;)
```
apt policy php7.4
php7.4:
  Installed: (none)
  Candidate: 1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1
  Version table:
     1:7.4.29-2+ubuntu22.04.1+deb.sury.org+1 500
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main amd64 Packages
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main i386 Packages
me@me-Standard-PC-Q35-ICH9-2009:~$ apt policy php8.1
php8.1:
  Installed: 8.1.6-1+ubuntu22.04.1+deb.sury.org+1
  Candidate: 8.1.6-1+ubuntu22.04.1+deb.sury.org+1
  Version table:
 *** 8.1.6-1+ubuntu22.04.1+deb.sury.org+1 500
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main amd64 Packages
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main i386 Packages
        100 /var/lib/dpkg/status
     8.1.2-1ubuntu2 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main i386 Packages

```

---

### Post by deepakdeshp on 2022-06-04
I was wrong it is not php version problem that caused the problem. With the Ubuntu 22.04 php8.1 version I installed phpmyadmin and joomla 4. Both the applications work after re installing. The applications were already installed under Ubuntu version 20.04. I have no idea what broke them when I upgraded from 20.04 to 22.04

---

### Post by #&amp;thj^% on 2022-06-04
Good News, thanks for adding your solution as well.
> **deepakdeshp said:**
> The applications were already installed under Ubuntu version 20.04. I have no idea what broke them when I upgraded from 20.04 to 22.04
I think this may be a way of life for the next couple of version upgrades in Ubuntu.

---

### Post by TheFu on 2022-06-04
> **deepakdeshp said:**
> I was wrong it is not php version problem that caused the problem. With the Ubuntu 22.04 php8.1 version I installed phpmyadmin and joomla 4. Both the applications work after re installing. The applications were already installed under Ubuntu version 20.04. I have no idea what broke them when I upgraded from 20.04 to 22.04

The new versions installers will likely perform the needed things for 22.04 that the upgrade doesn't handle.

---

### Post by deepakdeshp on 2022-06-04
@1fallen
I tried the ppa suggested by yoiu but it didnt help too.

---

### Post by mIk3_08 on 2022-06-05
> **deepakdeshp said:**
> The applications were already installed under Ubuntu version 20.04. I have no idea what broke them when I upgraded from 20.04 to 22.04
I prefer to upgraded to 22.04 new release Linux Ubuntu Operating System then install all up again the AMP to the new and fresh environment for you to work so will never need to worry for the EOL and to the new coming Linux Ubuntu Operating System releases because you already have the new one. Regards and Cheers.

---

### Post by #&amp;thj^% on 2022-06-05
> **deepakdeshp said:**
> @1fallen
I tried the ppa suggested by yoiu but it didnt help too.

So just so we all here are clear, is it Solved yet?

---

### Post by LHammonds on 2022-06-06
This is why I never do in-place upgrades.  I create a blank server in a virtual environment and configure it like the server I want to migrate...once running with the desired software and configured similar to old machine, I then copy the data and make sure it can function as a replacement.  During this process, I also document how to install and configure the new software (because there are always changes).

Once I know I can make the system work in the new version, I then make a backup and do it for real.  But not by upgrading in-place.  A fresh install and then restore of the data.

If unfamiliar with how the software was installed and configured, this is a PERFECT time to learn...in a virtual environment with no impact to production AND you can have documentation for the next time you (or someone after you) need to do the same.

LHammonds

---

### Post by #&amp;thj^% on 2022-06-06
> **LHammonds said:**
> This is why I never do in-place upgrades.  I create a blank server in a virtual environment and configure it like the server I want to migrate...once running with the desired software and configured similar to old machine, I then copy the data and make sure it can function as a replacement.  During this process, I also document how to install and configure the new software (because there are always changes).

Once I know I can make the system work in the new version, I then make a backup and do it for real.  But not by upgrading in-place.  A fresh install and then restore of the data.

If unfamiliar with how the software was installed and configured, this is a PERFECT time to learn...in a virtual environment with no impact to production AND you can have documentation for the next time you (or someone after you) need to do the same.

LHammonds
Great Advice! I do the same..

---

