---
title: "mysql broke during upgrade (ERROR 2002 (HY000): Can't connect to local ... socket)"
date: 2010-10-20
forum: Server Platforms
---

### Post by Jense on 2010-10-20
Hi,

I recently updated from 8.04 to 10.04 and within the last release-upgrade (9.10 to 10.4) the system hang on setting up mysql. Now I am stuck with a broken mysql-server. When trying to connect I allway get
```

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```
I googled and tried a number of things to get it working:
[LIST]
[*]manually set permission on /var/run/mysqld/mysqld.sock (user and groud: mysql)
[*]remove the file and set permission for the directory
[*]set a symlink on /tmp in the directory
[*]completly remove (remove and autoremove) mysql-server and reinstall
[*]manully choosing a different socket file (mysql -S ~/mysql.sock)
[*] of course I tried rebooting the system, restarting the mysql process, etc..
[/LIST]

I am really stuck by now and I need this database. I have seen varios posts regarding this error, but nothing I tried helped and I haven't seen anything that explains why this happens.
Maybe it's some stupid mistake, so if you can help, thanks a lot.

---

### Post by Jense on 2010-10-20
Just noticed too, that mysql seems not be running, at least 
```

ps -A | grep mysql

```
returns nothing. Trying to start the mysqld out of bin results in the following:
```

/usr/bin# mysqld
101020 12:56:21 [Note] Plugin 'FEDERATED' is disabled.
mysqld: Table 'mysql.plugin' doesn't exist
101020 12:56:21 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
101020 12:56:21  InnoDB: Started; log sequence number 0 300962141
101020 12:56:21 [ERROR] mysqld: unknown option '--skip-bdb'
101020 12:56:21 [ERROR] Aborting

101020 12:56:21  InnoDB: Starting shutdown...
101020 12:56:22  InnoDB: Shutdown completed; log sequence number 0 300962141
101020 12:56:22 [Note] mysqld: Shutdown complete

root@zarafa-plugin:/usr/bin# 

```

---

### Post by Jense on 2010-10-20
So, after lots of searching I got it running again. Cost me nearly a day, so if anybody has problems, here is how I solved it:
[LIST]
[*]purge and reinstall mysql server
[*]chgrp -R mysql /var/lib/mysql/
[*] Check if mysql can run in savemode: /usr/bin: mysqld_safe
[*] Somehow I lost my mysql.conf for upstart. So recreate it and paste exec sudo -u mysql /usr/sbin/mysqld # <- important execute as use mysql
[/LIST]

---

### Post by lgambett on 2011-01-08
> **Jense said:**
> Just noticed too, that mysql seems not be running, at least 
```

ps -A | grep mysql

```
returns nothing. Trying to start the mysqld out of bin results in the following:
```

/usr/bin# mysqld
101020 12:56:21 [Note] Plugin 'FEDERATED' is disabled.
mysqld: Table 'mysql.plugin' doesn't exist
101020 12:56:21 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
101020 12:56:21  InnoDB: Started; log sequence number 0 300962141
101020 12:56:21 [ERROR] mysqld: unknown option '--skip-bdb'
101020 12:56:21 [ERROR] Aborting

101020 12:56:21  InnoDB: Starting shutdown...
101020 12:56:22  InnoDB: Shutdown completed; log sequence number 0 300962141
101020 12:56:22 [Note] mysqld: Shutdown complete

root@zarafa-plugin:/usr/bin# 

```
The interesting part of that error is:

101020 12:56:21 [ERROR] mysqld: unknown option '--skip-bdb'
101020 12:56:21 [ERROR] Aborting

it is sufficient to comment the skip-bdb instruction in my.cnf, et voilà, mysql starts again.

---

### Post by chrislynch8 on 2011-01-10
I see you have it solved but when this happened to me recently, after an upgrade, the username and group for mysql was no mysql it was something else. So mysql was unable to start and I receive alot of errors.

chown -R mysql:mysql /var/lib/mysql resolved the issue.

---

