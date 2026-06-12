---
title: "mySql socket problem"
date: 2006-08-23
forum: Server Platforms
---

### Post by Marcboy on 2006-08-23
As far as i know i haven't changed anything to cause this but suddenly my mySql server refuses to start. When i try to start it up i get this...

```
Starting MySQL database server: mysqld.
.
.
.
.
.
.
.
.
.
.
.
.
.
...failed or took more than 6s.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

It has worked fine for ages and suddenly this has happened. Anyone know why or how to fix it?

Thanks, Marcus!

---

### Post by henrrrik on 2006-08-23
What do the logs say?

---

### Post by Marcboy on 2006-08-23
which logs?

edit: 

syslog display....
```
Aug 23 17:56:23 localhost /etc/init.d/mysql[27440]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Aug 23 17:56:23 localhost /etc/init.d/mysql[27440]: ^G/usr/bin/mysqladmin: connect to server at '127.0.0.1' failed
Aug 23 17:56:23 localhost /etc/init.d/mysql[27440]: error: 'Lost connection to MySQL server during query'
Aug 23 17:56:23 localhost /etc/init.d/mysql[27440]: 
Aug 23 17:56:23 localhost kernel: [17206750.892000] evbug.c: Event. Dev: isa0061/input0, Type: 18, Code: 2, Value: 400
Aug 23 17:56:23 localhost kernel: [17206750.992000] evbug.c: Event. Dev: isa0061/input0, Type: 18, Code: 2, Value: 0
Aug 23 17:56:23 localhost kernel: [17206750.992000] evbug.c: Event. Dev: isa0061/input0, Type: 18, Code: 1, Value: 0
Aug 23 17:56:23 localhost /etc/init.d/mysql[27445]: /etc/mysql/debian-log-rotate.conf is obsolete, see /usr/share/doc/mysql-server-5.0/NEWS.Debian.gz

```

Edit 2:

i tried to run mysqld and was presented with this...

```
$ sudo mysqld
060823 18:29:46  InnoDB: Started; log sequence number 0 43912
060823 18:29:46 [Note] Recovering after a crash using /var/log/mysql/mysql-bin
060823 18:29:46 [Note] Starting crash recovery...
060823 18:29:46 [Note] Crash recovery finished.
060823 18:29:46 [ERROR] Fatal error: Can't open and lock privilege tables: Incorrect file format 'host'
```

---

### Post by Marcboy on 2006-08-24
Anyone able to help with this? I've tried everything i can think of and nothing seems to work. I really don't feel like re-installing ubuntu.

---

### Post by lamego on 2006-08-24
Your database files have been corrupted.
You will need to reinstall mysql after purging the current database.
```
sudo aptitude purge mysql-server
mkdir ~/mysql_bak
sudo mv /var/lib/mysql/* ~/mysql_bak
sudo aptitude install mysql-server
```

---

### Post by Marcboy on 2006-08-24
Yeah thats pretty much what i tried last. It worked ^_^ Thanks for the help! Not too sure how it happened

---

