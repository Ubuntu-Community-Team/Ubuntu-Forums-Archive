---
title: "Eternal fight with versions and a web application"
date: 2018-08-15
forum: Server Platforms
---

### Post by ligustri on 2018-08-15
Hi,


I do have a web application made in WAMP with these versions:


Apache 2.4.9
----------------------------
PHP 5.5.12 (versions of PEAR and its DB got to have been compatible)
----------------------------
MySQL 5.6.17
----------------------------
Application has also Smarty in it. 


Now, I'm about to improve the application with these:


Ubuntu 14.04.5 LTS
-------------------------------------
Server version: Apache/2.4.7 (Ubuntu)
Server built:   Apr 18 2018 15:36:26
-------------------------------------
PHP 5.5.9-1ubuntu4.25
-------------------------------------
mysql  Ver 14.14 Distrib 5.5.61
-------------------------------------
PEAR Version: 1.9.4
-------------------------------------
DB 1.7.14-2
-------------------------------------


Installation went fine and all configurations went well(for example php.ini), but when I try to open the application in browser, it gives me this error:


The page does not work
localhost can not process this request at this time.
HTTP ERROR 500


What could be wrong? Please help!

---

### Post by spjackson on 2018-08-15
> **ligustri said:**
> 
The page does not work
localhost can not process this request at this time.
HTTP ERROR 500

Does the apache error log file have any messages from the time of the error 500? This file would normally be /var/log/apache2/error.log, but it could be configured to be elsewhere.

---

### Post by ligustri on 2018-08-15
Thanks for answer!

Ok, I found from that error.log that my code is demanding function mysql_set_charset(), which is lacking from PHP -version I've installed ([COLOR=#000000]PHP 5.5.9-1ubuntu4.25). 

[/COLOR]http://php.net/manual/en/function.mysql-set-charset.php ----> solution may be an extension, as I found out with Google: php-mysqlnd. I installed it, but still some error remains touching DB.

[COLOR=#000000]Does DB need an own include_path in php.ini?

[/COLOR]

---

### Post by spjackson on 2018-08-16
> **ligustri said:**
> [COLOR=#000000]
[/COLOR]http://php.net/manual/en/function.mysql-set-charset.php ----> solution may be an extension, as I found out with Google: php-mysqlnd. I installed it, but still some error remains touching DB.

[COLOR=#000000]Does DB need an own include_path in php.ini?
[/COLOR]
If you have installed php & mysql & php's mysql module via Ubuntu packages, any necessary changes to php.ini should have been made. "still some error remains touching DB." is too vague for me to be able to offer any help. Sorry.

---

### Post by ligustri on 2018-08-16
[FONT=arial]The mystery is this in error.log: include_path='/home/y789as9f/[/FONT][FONT=arial]php:.:/usr/sha....
I don't do have such an include_path in my php.ini. The part: [/FONT][FONT=arial]/home/y789as9f/[/FONT][FONT=arial]php is totally weird string. Is it possible, that php is using some other php.ini than it announces in phpinfo()?[/FONT]

---

### Post by ligustri on 2018-08-16
I found a file that manipulates the php.ini's include_path. From there, I removed this string '[COLOR=#000000][FONT=arial]/home/y789as9f/[/FONT][/COLOR][COLOR=#000000][FONT=arial]php' , but it still gives error to error.log.[/FONT][/COLOR]

---

