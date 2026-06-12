---
title: "PDO install hosing httpd"
date: 2008-09-27
forum: Server Platforms
---

### Post by SMS12095 on 2008-09-27
I'm new to Ubuntu (and Linux in general), and am having trouble with installing PDO.  Here's the deal...

I'm trying to set up a server (Hardy) with SSH, Apache2, PHP 5.2.x, Ruby, ProFtpd, and PostgreSQL 8.3, and want to use PDO.  I set up everything but the PDO, and all works beautifully - very pleased with myself as I've never touched Linux before.  Then I try to set up PDO, and I plummet to earth with a thud.

I run:
pecl install pdo
pecl install pdo_pgsql

I add to php.ini:
extension=pdo.so
extension=pdo_pgsql.so

then restart apache:
/etc/init.d/apache2 force-reload 
/etc/init.d/apache2 restart 

and I get the message
httpd (no pid file) not running

and from that point on I could not browse to my webserver, got...
Firefox can't establish a connection to the server at 192.168.0.100.

Never had that error before until I installed PDO, and I was always able to get a connection before.  So I rebuilt the server from bottom up, documenting every step, and again all was working until I installed PDO and changed the php.ini file

Please help -- I'm baffled

---

