---
title: "Quick Ubuntu Server within 24hrs (MySQL,Apache,Mail,PHP,Webmin)"
date: 2006-12-20
forum: Server Platforms
---

### Post by olddocks on 2006-12-20
**Build Your Own Web Server ~ Quick & Easy Do it Yourself Installation ~ All within 24 hours !!!!**

Ubuntu/Debian Linux

- Apache 2 - Linux Web server 
- MySQL 5 - MySQL Database Server 
- PHP4/5 - PHP Scripting Language 
- PhpMyAdmin - Web-based database admin software. 
- Webalizer - Website Traffic Analyzer 
- Mail Server - Postfix (MTA) with Dovecot IMAP/POP3 + Sasl Authentication 
- Squirrelmail - A web based email 
- VSFTP - A fast ftp server to upload files 
- Webmin - A freely available server control panel 
- ClamAV - Antivirus software. 
- A Firewall using IPtables. 

Visit: [http://www.mysql-apache-php.com](http://www.mysql-apache-php.com)

After long hardwork and desperation searching web to prepare for a linux server on my VPS plan, i wrote my tutorial for somebody like me who is new to vps and dedicated server. Just felt that it could be helpful.

Please comment and any advice would be appreciated.

---

### Post by az on 2006-12-20
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by rlozano on 2006-12-20
great post.... ;-)

---

### Post by Brazen on 2006-12-21
this isn't a "Perfect  Linux Web Server" setup.  A webserver should not have MySQL on it.  MySQL should go on a DATABASE server, accessible from the webserver.  A web server should also not have Postfix and dovecot on it, those should go on an EMAIL server.

Split these things up on different servers (use VMWare Server if necessary) and get them to work together and THEN you will have a "Perfect" setup.

---

### Post by olddocks on 2006-12-26
> **Brazen said:**
> this isn't a "Perfect  Linux Web Server" setup.  A webserver should not have MySQL on it.  MySQL should go on a DATABASE server, accessible from the webserver.  A web server should also not have Postfix and dovecot on it, those should go on an EMAIL server.

Split these things up on different servers (use VMWare Server if necessary) and get them to work together and THEN you will have a "Perfect" setup.

thanks brazen for your nice advice. I will work on your advice.

---

### Post by DarrenR114 on 2008-02-11
I know this thread is kind of old, but I just wanted to comment that MySQL is NOT the best database for the job if you value your data. And if your data isn´t worth worrying about, then why bother with it at all?

The better Database for the job is PostgreSQL. It was the better choice back in 2006 when the original post was made. It´s been the better technical choice for over 15 years.

[http://www.postgresql.org/about/](http://www.postgresql.org/about/)

For those of you who think that MySQL is better because it is used by more people, then you may want to think about that when you compare MS-Windows to Linux. Just because a billion flies eat garbage doesn´t mean that it´s the best food for me.

---

