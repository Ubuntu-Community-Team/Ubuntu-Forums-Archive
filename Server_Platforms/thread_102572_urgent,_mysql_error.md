---
title: "urgent, mysql error"
date: 2005-12-12
forum: Server Platforms
---

### Post by akurashy on 2005-12-12
I'm getting this error

david@akulinux:~$ sudo /etc/init.d/mysql start
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
david@akulinux:~$ sudo cat /var/run/mysqld/mysqld.sock
cat: /var/run/mysqld/mysqld.sock: No such file or directory


can anyone really help me? I already tried reinstalling, i tried all! i'm really desperated, i'm kinda behind on some projects, and well i'm lost, i hope a mysql savvy is around here =/

help asap :(

---

### Post by xinman on 2005-12-12
I'm having the same problem, I already tried to reinstall twice now.  Anybody with some help?

---

### Post by xinman on 2005-12-12
Found a fix, go into synaptic and uninstall mysql-server and install mysql-server4.1  that worked for me

---

