---
title: "No user table mysql fresh lamp install"
date: 2009-11-22
forum: Server Platforms
---

### Post by Synnapse on 2009-11-22
Hello, I installed LAMP on a clean ubuntu jaunty server and when I try to login to mysql I get wrong password error, when I run with --skip-grant-tables and check out the users table, its empty apart from 'debian-sys-maint'... anyone know how to add a root user?

Ubuntu 9.04 / Jaunty
Installed lamp using tasksel

I'm new to linux so please explain well.

```

mysql> use mysql
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> UPDATE user SET Password=PASSWORD('blabla') WHERE user='root';
Query OK, 0 rows affected (0.00 sec)
Rows matched: 0  Changed: 0  Warnings: 0

mysql> select user from user
    -> ;
+------------------+
| user             |
+------------------+
| debian-sys-maint |
+------------------+
1 row in set (0.00 sec)

```

---

### Post by Synnapse on 2009-11-22
Did a 
dpkg-reconfigure mysql-server-5.0
Still no dice. no root user in table.

---

### Post by Synnapse on 2009-11-22
solved by manually adding root user to the user table.

---

### Post by norby on 2009-12-08
Hi there,

I'm going through the same problem but I can find a way of adding the user manually ? how did you manage to add it ?

The only way I can get to access mysql is by starting the mysqld with --skip-grant-tables. Using this option it doesn't allow me to add any users.

Cheers,

---

### Post by gerv on 2010-03-17
Adding the root user manually:

mysql> INSERT INTO user VALUES ('localhost','root',password('newpassword'),'Y','Y ','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y', 'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','' ,'','','',0,0,0,0);
mysql> INSERT INTO user VALUES ('127.0.0.1','root',password('newpassword'),'Y','Y ','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y', 'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','' ,'','','',0,0,0,0);

(That's according to [http://forums.mysql.com/read.php?10,277700,280261](http://forums.mysql.com/read.php?10,277700,280261) ).

---

