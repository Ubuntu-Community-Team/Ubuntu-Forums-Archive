---
title: "PHP won't run code"
date: 2007-06-12
forum: Server Platforms
---

### Post by dameon51 on 2007-06-12
Hey everyone. First post. Some linux experience and linux basics I have, but thats about it. I installed ubuntu server for a LAMP box. The apache portion is working as I can display HTML pages (just testing over a LAN), but the PHP server doesn't seem to be working. When I view the phpinfo.php over the LAN in a browser it runs fine, but any php code in the browser doesn't run. Actually when I go to view source I can SEE the php code in there still! I did a a2enmod and php5 and it says its already enabled. Please help!
This is my html and php code.
```

<html>
<body>

<?php
echo "Hello world";
?>


</body>
</html>
```

---

### Post by Wardazo on 2007-06-12
> When I view the phpinfo.php over the LAN in a browser it runs fine, but any php code in the browser doesn't run.

If you just view a page 'in a browser' you will see php code (i.e. page.php) Php must be processed in the server.

Only once you go via [http://localhost/page.php](http://localhost/page.php) will the dynamic content be processed by php.

Perhaps that's not what you were saying. If not could you clarify the above quote.

---

### Post by dameon51 on 2007-06-12
Sorry, the phpinfo.php will run over the LAN. But my hello world code snippet will not. And when I go to view source I can see the code in there, which I shouldn't be able to do.

---

### Post by EndPerform on 2007-06-12
Where did you put this file, and what is it called?  It seems really odd that phpinfo would work, yet this page will not.

---

### Post by Wardazo on 2007-06-12
What url are you typing for the phpinfo output?

and what are you typing for "a page that doesn't process php"?

Could you pate back the code of the phpinfo file and of the page that doesn't run.

And also the top section of the output form the phpinfo.

sorry... and also the command that you send to install php and apache.

Sorry but I really need a bit more info to try and work out the problem.

---

### Post by jeff00z28 on 2007-06-12
how do u save to the server

---

### Post by dameon51 on 2007-06-12
well for the phpinfo.php its just
[http://192.168.100.170/apache2-default/phpinfo.php](http://192.168.100.170/apache2-default/phpinfo.php)

The code for the page that doesn't run is on my first post in this thread, but here it is again....

```
<html>
<body>

<?php
echo "Hello world";
?>


</body>
</html>
```

To try to access this page i go to
[http://192.168.100.170/apache2-default/](http://192.168.100.170/apache2-default/) 
It runs the index.html fine.... if I put HTML code in there it displays it, but when I go view source from the browser I can see the....
```
<?php
echo "Hello world";
?>

```

Which to me seems that PHP module isn't doing its job....

When I go to the phpinfo.php this is what i get...

System 	Linux ubuntuLAMP 2.6.20-15-server #2 SMP Sun Apr 15 07:41:34 UTC 2007 i686
Build Date 	May 22 2007 18:51:12
Server API 	Apache 2.0 Handler
Virtual Directory Support 	disabled
Configuration File (php.ini) Path 	/etc/php5/apache2/php.ini
Scan this dir for additional .ini files 	/etc/php5/apache2/conf.d
additional .ini files parsed 	/etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini
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

The fact that I can few the phpinfo.php suggests that the php module IS working though.

Ideas? Thanks a million

---

### Post by Wardazo on 2007-06-12
> 
"how do u save to the server"

The default folder is:

/var/www/

You'll need to sudo to write to it. 

(Probably best changing to a different one in you home directory once things are working.)

But lets see if things are working first. Put a php file in the above directory and post back.

---

### Post by Wardazo on 2007-06-12
> To try to access this page i go to
[http://192.168.100.170/apache2-default/](http://192.168.100.170/apache2-default/)
It runs the index.html fine.... i

Does the file with php have a .php extension?

---

### Post by dameon51 on 2007-06-12
BAAAAAAAAAAH! Thanks! index.HTML, should of been index.php!

---

### Post by dienbien001 on 2008-05-06
I have same problem.
I create a file test.php:
```
<?php 
phpinfo(); 
?> 
```
But the output is the same with the source code.
PHP didn't do its job. But I don't know how to solve this problem :(
I installed libapache2-mod-php5, reloaded apache2, installed PHP5, Apache2, enabled mod php5 for apache2.

I've just installed phpmyadmin, and it work perfect.
I don't know why my test.php didn't work?

---

