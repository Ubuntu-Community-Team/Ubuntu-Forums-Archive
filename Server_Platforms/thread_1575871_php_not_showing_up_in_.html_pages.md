---
title: "php not showing up in .html pages"
date: 2010-09-16
forum: Server Platforms
---

### Post by tylerc66 on 2010-09-16
I have some basic PHP ( <?php include("menu.php"); ?> ) on my home page and it is not showing up. This site was copied from my godaddy hosting ( where it worked fine ).  I also tried this on a plain version of debain and ran into the same issue. From what I have read it seems to be some kind of .htaccess, http.conf or php.ini issue. I am new to Ubuntu and would appreciate any help.

I am running Ubuntu server 10.04.1

---

### Post by terazen on 2010-09-16
In your /etc/apache2/mods-enabled/ folder do you have php5 listed?  If not check /etc/apache2/mods-available and enable with "sudo a2enmod modnamehere".  Afterwards restart apache.

What php packages are installed on your server?  Try "dpkg -l | grep -i php5"

---

### Post by tylerc66 on 2010-09-16
PHP5 is already enabled. When I setup the server i selected lamp and it automatically installed all the needed files. 

This is from the phpinfo.php 

PHP Version 5.3.2-1ubuntu4.2


System	Linux sj-webserver01 2.6.32-24-generic-pae #39-Ubuntu SMP Wed Jul 28 07:39:26 UTC 2010 i686
Build Date	May 13 2010 19:49:13
Server API	Apache 2.0 Handler
Virtual Directory Support	disabled
Configuration File (php.ini) Path	/etc/php5/apache2
Loaded Configuration File	/etc/php5/apache2/php.ini
Scan this dir for additional .ini files	/etc/php5/apache2/conf.d
Additional .ini files parsed	/etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini
PHP API	20090626
PHP Extension	20090626
Zend Extension	220090626
Zend Extension Build	API220090626,NTS
PHP Extension Build	API20090626,NTS
Debug Build	no
Thread Safety	disabled
Zend Memory Manager	enabled
Zend Multibyte Support	disabled
IPv6 Support	enabled
Registered PHP Streams	https, ftps, compress.zlib, compress.bzip2, php, file, glob, data, http, ftp, phar, zip
Registered Stream Socket Transports	tcp, udp, unix, udg, ssl, sslv3, sslv2, tls
Registered Stream Filters	zlib.*, bzip2.*, convert.iconv.*, string.rot13, string.toupper, string.tolower, string.strip_tags, convert.*, consumed, dechunk

---

### Post by terazen on 2010-09-16
Anything in the logfiles?  /var/log/apache2/error.log

---

### Post by tylerc66 on 2010-09-16
No

---

### Post by tylerc66 on 2010-09-16
It was the .htaccess file this link was a big help [https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles]("https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles")

---

