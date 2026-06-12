---
title: "Can't connect to MySQL server on... (111)"
date: 2005-01-25
forum: Server Platforms
---

### Post by flade on 2005-01-25
Where is error.

I installed MySQL and phpMyAdmin. I think both work just fine, because I use phpMyAdmin to create new databases and other stuff.

I installed MAMBO portal to work with. This portal is working. I can change anything and I get no errors.

But when I try to put my own script to work, It woun't connect to server:

I get this error with bottom code:  Can't connect to MySQL server on '192.168.1.8' (111)

Here is my code to connect to db: 

<?php

$user = "";
$user_pass= "";
$db ="";

$link = mysql_connect("192.168.1.8", $user, $user_pass);
if ( ! $link ){
    die ("ERROR: ". mysql_error());
   }
...
...
...


I created additional user to work with mysql as it is more safer. But with root won't work either.


-----

+ Fladé

---

### Post by albersag on 2005-01-25
Maybe Mysqld is limiting by default access to localhost

try host as 127.0.0.1

---

### Post by flade on 2005-01-25
[QUOTE=albersag]Maybe Mysqld is limiting by default access to localhost

try host as 127.0.0.1[/QUOTE]


Yes, that is correct. It's limited to localhost.



Thank you.



---------
+ Fladé

---

### Post by albersag on 2005-01-25
[QUOTE=flade]Yes, that is correct. It's limited to localhost.



Thank you.



---------
+ Fladé[/QUOTE]
 Its a security tip.

Outbound access to mysql it is always a security risk :)

Not at all :)

---

### Post by parkash on 2005-09-07
Ok..   I have a worse problem...   I can connect (of course) using localhost

mysql -u todo -h localhost -p 

But I can't do 

mysql -u todo -h 127.0.0.1 -p 

It returns:

Warning: mysql_connect(): Can't connect to MySQL server on '127.0.0.1' (111)

It's kinda wierd right?   And I need to do it!!!
 ](*,)

---

### Post by lao_V on 2005-09-08
To be best of my knowledge mysql doesn't recognise localhost and 127.0.0.1 as being the same, even though they are. The best practice is to use localhost from scripts at all times

---

### Post by jklappenbach on 2005-11-05
Hey all, I was running into connection issues on mysql where I could connect using mysql shell, but other applications weren't able to connect (Aqua DataStudio, JBoss).  

I checked out the hosts file which looked something like:

127.0.0.1 localhost localhost.localdomain ...

I thought perhaps mysql isn't parsing this correctly, so I broke out the line to read:

127.0.0.1 localhost
127.0.0.1 localhost.localdomain
127.0.0.1 ...

Sure enough, the connection issues vanished.

Hope this helps!

Julian Klappenbach
Software Developer
Ramp Technology Group

---

### Post by LordHunter317 on 2005-11-06
[quote=jklappenbach]I thought perhaps mysql isn't parsing this correctly, so I broke out the line to read:[/quote]MySQL doesn't read it at all and I'm not sure how that fixed anything.

---

