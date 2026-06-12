---
title: "MySQL won't start (now)"
date: 2010-05-20
forum: Server Platforms
---

### Post by Ashocka on 2010-05-20
Hi,

I had MySQL running (latest 5.x) on Ubuntu Desktop 9.10 (64).

I think there are two possible things that have caused this problem. 1) adding a Apache/PHP module or dropping a database from within Webmin.

EG

```
gdeering@ubuntu:~$ sudo /etc/init.d/mysql start >/dev/null 2>&1 &
[1] 10292
gdeering@ubuntu:~$ mysqladmin create nklr
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

[1]+ Stopped sudo /etc/init.d/mysql start > /dev/null 2>&1
gdeering@ubuntu:~$

```
I have reinstalled it... but still same problem.

Solutions / Help appreciated.

Geoff

---

### Post by Ashocka on 2010-05-20
I've solved this by doing a uninstall purge and reinstall

---

