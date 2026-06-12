---
title: "How to insert values in mysql user table?"
date: 2016-04-16
forum: Server Platforms
---

### Post by shamsat on 2016-04-16
I installed ubuntu 16.04 beta2, mysql server only accept connections for root from root@localhost and reject from root@127.0.0.1 and [email]root@me.exmaple.com[/email] after search i found to add the other hosts to mysql user table this is my mysql user table:
> 
mysql> select host, user from user;
+-----------+------------------+
| host      | user             |
+-----------+------------------+
| localhost | debian-sys-maint |
| localhost | mysql.sys        |
| localhost | root             |
| localhost | roundcube        |
| localhost | test             |
+-----------+------------------+
5 rows in set (0.00 sec)

I want to insert  these hosts to user root in user table,when i run this insert command getting error and asking values for other columns as well which are non null:
> 
mysql> INSERT INTO user (host,user) VALUES ("example", "root");
ERROR 1364 (HY000): Field 'ssl_cipher' doesn't have a default value

How i can run a command that insert these two values and all other columns get their default values.

---

### Post by howefield on 2016-04-16
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2016-04-16
I'm no mysql expert but I believe you are going the wrong way if you only want to set user permissions. You don't do it by inserting into tables directly.
Check this tutorial for example for creating mysql users and assigning permissions:[https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql)

---

