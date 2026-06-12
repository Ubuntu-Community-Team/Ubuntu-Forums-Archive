---
title: "ERROR 2002: Can't connect to local MySQL server"
date: 2006-08-20
forum: Server Platforms
---

### Post by psychomonkey on 2006-08-20
Thanks in advance. 

I've looked around the net, but can't seem to find a straight answer. For some reason, MYSQL has started acting up. 

I try to initiate the command **/etc/init.d/mysql start**, but I get the following error:

Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

I've tried doing any **updatedb**, but I cannot locate the file mysqld.sock. Anyone have any suggestions?

---

