---
title: "Can't connect to wordpress from internet"
date: 2008-09-15
forum: Server Platforms
---

### Post by locrian on 2008-09-15
Ubuntu server 8.04
Php 5
Most recent wordpress

1)  If I connect to the server locally from another computer(meaning behind my router), everything comes up fine
2)  From anywhere else over the internet, we get an error saying no site found
3)  If I put an index.html in the directory, an exterior computer finds it and it displays correctly

I'm not sure how to troubleshoot this.  Since I can connect to the wordpress page from other computers in the house and everything comes up fine, does that mean php is running correctly?  Since I can connect to an .html file from anywhere, doesn't that mean the server is seeing the internet correctly?

By the way I can connect to webmin and ssh from anywhere fine.

Thanks for any help!

---

### Post by lazyart on 2008-09-16
Have you forwarded port 80 to the server?

---

### Post by TigerWolf on 2008-09-16
Try to create a file called phpinfo.php and access this from the internet.

```
<?php phpinfo(); ?>
```

---

### Post by locrian on 2008-09-16
> **lazyart said:**
> Have you forwarded port 80 to the server?

Yes, and I know it is working because otherwise people wouldn't be able to view .html pages that I place in my web directory.

---

### Post by locrian on 2008-09-16
> **TigerWolf said:**
> Try to create a file called phpinfo.php and access this from the internet.

```
<?php phpinfo(); ?>
```

Okay I will try that.  However part of the problem I'm having is that everything works from my house.  I'll have to go somewhere else entirely to do your test.

And that's one thing I really want help with - why is it this server works perfectly from another computer in the house (behind the same router) but no one else (outside) can see the .php page?  I feel if I understood that I could solve the problem.  Is there a way I can test this without leaving my home every time (because that's annoying)?

---

### Post by locrian on 2008-09-16
Here is what the test php page says:

--------------------

PHP Version 5.2.4-2ubuntu5.3

System 	Linux hserver 2.6.24-19-server #1 SMP Sat Jul 12 00:40:01 UTC 2008 i686
Build Date 	Jul 23 2008 06:28:41
Server API 	Apache 2.0 Handler
Virtual Directory Support 	disabled
Configuration File (php.ini) Path 	/etc/php5/apache2
Loaded Configuration File 	/etc/php5/apache2/php.ini
Scan this dir for additional .ini files 	/etc/php5/apache2/conf.d
additional .ini files parsed 	/etc/php5/apache2/conf.d/gd.ini, /etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini
PHP API 	20041225
PHP Extension 	20060613
Zend Extension 	220060519
Debug Build 	no
Thread Safety 	disabled
Zend Memory Manager 	enabled
IPv6 Support 	enabled
Registered PHP Streams 	zip, php, file, data, http, ftp, compress.bzip2, compress.zlib, https, ftps
Registered Stream Socket Transports 	tcp, udp, unix, udg, ssl, sslv3, sslv2, tls
Registered Stream Filters 	string.rot13, string.toupper, string.tolower, string.strip_tags, convert.*, consumed, convert.iconv.*, bzip2.*, zlib.*

Suhosin logo This server is protected with the Suhosin Patch 0.9.6.2
Copyright (c) 2006 Hardened-PHP Project

Zend logo This program makes use of the Zend Scripting Language Engine:
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies

-------------------------

Along with more I'd be happy to paste here if its useful.  I notice that virtual directory support is disabled, so I'll do some research on whether that's important.

Thank you for reading!

---

