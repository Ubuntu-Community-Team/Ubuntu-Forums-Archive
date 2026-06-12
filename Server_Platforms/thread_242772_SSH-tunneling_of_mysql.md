---
title: "SSH-tunneling of mysql"
date: 2006-08-24
forum: Server Platforms
---

### Post by patjoh on 2006-08-24
Hello
I'm trying to use a remote mysql-server and tried to set up a SSH-tunnel with this command: ssh -L 3306:localhost:3306 mysqlserver

The problem is that php tries to use some sock-file:
```
Warning: mysql_query() [function.mysql-query]: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) in /home/user1/common/php/conn.php on line 13
``` 

I have tried the SSL-tunneling in Windows and it works great, so I guess I have missed some important config-file.

I use Dapper with php5, mysql5 and apache2.

Any ideas how I can solve this?

Cheers
Patrik

---

