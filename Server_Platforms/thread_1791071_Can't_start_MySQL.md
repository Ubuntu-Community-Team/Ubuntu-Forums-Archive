---
title: "Can't start MySQL"
date: 2011-06-26
forum: Server Platforms
---

### Post by karlarneg on 2011-06-26
Helllo. I have trouble with MySQL server on my Ubuntu 11.04.
Below is what I get in Terminal

Thanks for all help!
-----------------------------------------------------------------
root@linux:/home/karl# /etc/init.d/mysql start 
 Rather than invoking init scripts through /etc/init.d, use the 
 service(8) 
 utility, e.g. service mysql start 
 Since the script you are attempting to invoke has been converted to an 
 Upstart job, you may also use the start(8) utility, e.g. start mysql 
 
Warning: Fake initctl called, doing nothing. 
 ------------------------------------------------------------------- 
 root@linux:/home/karl# service mysql start 
 
Warning: Fake initctl called, doing nothing. 
 root@linux:/home/karl# 
 ----------------------------------------------------------------- 
 root@linux:/home/karl# start mysql 
 
Warning: Fake initctl called, doing nothing. 
 root@linux:/home/karl# 
 ------------------------------------------------------------------------ 
 root@linux:/home/karl# mysql -u root 
 ERROR 2002 (HY000): Can't connect to local MySQL server through socket 
 '/var/run/mysqld/mysqld.sock' (2) 
 root@linux:/home/karl# mysql -u root -p 
 Enter password: 
 ERROR 2002 (HY000): Can't connect to local MySQL server through socket 
 '/var/run/mysqld/mysqld.sock' (2) 
 root@linux:/home/karl#

---

### Post by TeoBigusGeekus on 2011-06-26
Try [this]("http://sites.google.com/site/ubuntu4us/artigos/solucao-de-problemas-e-erros/starting-services-ubuntu/fake-start-stop-daemon").

---

### Post by howefield on 2011-06-26
Thread moved to "*Server Platforms*"

---

### Post by olexiyb on 2011-06-26
Try this

[http://korbinus.geotruc.net/blog/?tag=initctl](http://korbinus.geotruc.net/blog/?tag=initctl)

---

