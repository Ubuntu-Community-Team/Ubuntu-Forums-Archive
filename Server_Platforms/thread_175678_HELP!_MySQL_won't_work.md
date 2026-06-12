---
title: "HELP! MySQL won't work"
date: 2006-05-13
forum: Server Platforms
---

### Post by xuyaobo on 2006-05-13
I am a absolute beginner for Linux and MySQL.
I just installed Dapper Drake in my laptop, and then straightly installed mysql-client and mysql-server , but I couldn't create a database or do more in mysql than using commands starting with "\". I got the "Ignoring query to other database" all the time. (c below)

[FONT="Courier New"][COLOR="DimGray"]xuyaobo@dapper:/usr$ sudo mysql -root
Welcome to the MySQL monitor. Commands end with ; or \g.
Your MySQL connection id is 4 to server version: 5.0.21-Debian_3-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> use mysql
Database changed
mysql> show tables;
Ignoring query to other database
mysql> create database gr;
Ignoring query to other database
mysql> \s
--------------
mysql Ver 14.12 Distrib 5.0.21, for pc-linux-gnu (i486) using readline 5.1

Connection id: 4
Current database:
Current user: root@localhost
SSL: Not in use

All updates ignored to this database
Current pager: stdout
Using outfile: ''
Using delimiter: ;
Server version: 5.0.21-Debian_3-log
Protocol version: 10
Connection: Localhost via UNIX socket
Server characterset: latin1
Db characterset: latin1
Client characterset: latin1
Conn. characterset: latin1
UNIX socket: /var/run/mysqld/mysqld.sock
Uptime: 44 min 6 sec

Threads: 1 Questions: 5 Slow queries: 0 Opens: 0 Flush tables: 1 Open tables: 6 Queries per second avg: 0.002
--------------

mysql>[/COLOR][/FONT]

](*,) 
could anyone tell me why and how to solve it?

Thanks.

---

### Post by souki on 2006-05-13
you don't need to sudo
in the following examples, any local account can use root account with no password to grant dbadmin privileges, I think it is the default on ubuntu, not sure.

first, create a databse :
```
 mysqladmin -u root create dbtest
``` if you want to list your databases :
```
mysqlshow -u root
``` 
to connect to a database :
```
mysql -u root dbtest
``` 
from here (mysql client) you can create your tables :
```
CREATE TABLE `TheTable` (
  `IDTheTable` int(11) NOT NULL auto_increment,
  `Label` varchar(64) default NULL,
  PRIMARY KEY  (`IDTheTable`)
) ;

```

---

### Post by xuyaobo on 2006-05-14
Oh, thanks a lot, it works, that's so great.

---

