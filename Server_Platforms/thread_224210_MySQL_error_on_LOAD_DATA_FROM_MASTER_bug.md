---
title: "MySQL error on LOAD DATA FROM MASTER: bug?"
date: 2006-07-27
forum: Server Platforms
---

### Post by heisters on 2006-07-27
Hi all, I just upgraded my servers to Dapper, which includes MySQL 5.0. When I did that, I started getting errors when trying to execute LOAD DATA FROM MASTER on a slave:
```

[FONT="Courier New"]$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 7580 to server version: 5.0.22-Debian_0ubuntu6.06-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> load data from master;
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql> show warnings;
+-------+------+-------------------------------------------------------------+
| Level | Code | Message                                                     |
+-------+------+-------------------------------------------------------------+
| Error | 1007 | Can't create database 'information_schema'; database exists | 
+-------+------+-------------------------------------------------------------+
1 row in set (0.00 sec)

mysql>[/FONT]

```

So I did a little looking around and found a [bug report]("http://bugs.mysql.com/bug.php?id=18607") that seems to fit my problem precisely. However, it's supposed to be fixed in 5.0.22, and as you can see from the transcript above, I am running 5.0.22.

Well, no problem the thread linked above has a workaround, so I just added replicate-ignore-db=information_schema to my.cnf. When I do that LOAD DATA FROM MASTER doesn't drop any errors, but suddenly I start getting lots of "mysql_result error: cannot jump to row 0" errors (sorry, that was from memory) on trying to connect to the database. So I removed the replicate-ignore-db line, but the errors persisted, so I had to drop the database and manually restore it from a mysqldump of the master.

I have a couple questions. 1) is this the same bug as MySQL #18607, or is this a new one introduced by the Ubuntu revision? Where should I report it? 2) does anyone know of a workaround I can use to get replication working for the time being?

Thanks!

[EDITED for formatting]. Also, FYI, the master is also running 5.0.22-0ubuntu6.06

---

### Post by heisters on 2006-08-02
Anyone have any ideas? I'm loathe to report this to MySQL as a bug, since they say it's fixed in the version I have. Seems it must be specific to either Ubuntu or me.

---

### Post by heisters on 2006-08-09
I went ahead and [reported]("https://launchpad.net/distros/ubuntu/+source/mysql-dfsg-5.0/+bug/55682") the bug. In the meantime, I found that starting and stopping the slave allows me to get updates on demand, rather than constantly.

---

