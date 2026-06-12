---
title: "php.ini and apache2.conf"
date: 2007-06-26
forum: Server Platforms
---

### Post by Daveyboy on 2007-06-26
I received this prompt when installiing cacti, need help configuring config files, getting this (see attach) when running the poller.php for the program;

Fatal error: Call to undefined function:  mysql_pconnect() in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 373

I installed , apt-get install apache2 php5 libapache2-mod-php5 mysql-server mysql-client php5-mysql, prior to the installation.

---

### Post by Daveyboy on 2007-06-26
It is ubuntu server 6.06

Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006

---

### Post by Wardazo on 2007-06-27
Open /etc/php5/apache2/php.ini

Find the the line that starts with include_path. Edit it to include the new path that's on the blue screen (/usr/share/php/adobe).

 If the line is commented ( ; ), uncomment it.

I've avoided giving you the exact line to cut and paste in case there are multiple include paths (separated by : on *nix systems).

Then restart apache.

---

### Post by Daveyboy on 2007-06-27
edited to this and restarted apache2, but still getting Fatal error: Call to undefined function mysql_pconnect() in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 372

; UNIX: "/path1:/path2"
include_path = ".:/usr/share/php:/usr/share/php/adodb/"

---

### Post by Wardazo on 2007-06-27
> apt-get install apache2 php5 libapache2-mod-php5 mysql-server mysql-client php5-mysql

I know you said that you installed php5-mysql, but are you sure it installed? I think it's worthwhile checking.

The error says it is not recognising mysql_pconnect... which you should have whether you have the adodb abstraction layer or not

Could you try running this in a php script:

```
<?php
if(mysql_connect('localhost',[username],[password])){
echo 'connected';
}
?>
```

.. and see if it produces an error. If it connects then try mysql_pconnect.

---

