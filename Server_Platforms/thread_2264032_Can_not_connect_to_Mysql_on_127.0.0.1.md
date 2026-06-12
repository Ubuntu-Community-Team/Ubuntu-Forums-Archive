---
title: "Can not connect to Mysql on 127.0.0.1"
date: 2015-02-04
forum: Server Platforms
---

### Post by jonas17 on 2015-02-04
Hello,

I am quite new with linux ubuntu and mysql. I am unable to give a java plugin access to the mysql which I believe uses 127.0.0.1 ip
I am able to connect to mysql via ssh with:
mysql -u root -p
or
mysql -h localhost -u root

But if I use mysql -h 127.0.0.1 -u root -p
ERROR 2003 (HY000): Can't connect to MySQL server on '127.0.0.1' (111)

my.cnf ([http://pastebin.com/SibeY1tP](http://pastebin.com/SibeY1tP))

Any ideas?

And if I do "service mysql stop" it outputs "mysql stop/waiting" and am still able to log in to mysql, is it supposed to be like that? Is it possibly stuck/frozen and my previous attempts to fix this issue were a failure?

Found this in mysql logs spammed:
InnoDB: Check that you do not already have another mysqld process
InnoDB: Unable to lock .ibdata1, error: 11

---

### Post by jonas17 on 2015-02-05
reinstalled mysql, reconfigurated it and it seems to be fixed

---

