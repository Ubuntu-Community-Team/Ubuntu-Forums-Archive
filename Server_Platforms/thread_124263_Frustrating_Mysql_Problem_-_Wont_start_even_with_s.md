---
title: "Frustrating Mysql Problem - Wont start even with sudo and 777 perm"
date: 2006-02-01
forum: Server Platforms
---

### Post by mpa on 2006-02-01
Ive just installed kubuntu and now trying to get mysql to work so I can get my drupal-ed site up and running again. So far, mysql has been very very stubborn.

```
sudo /etc/init.d/mysql start
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

```

ls -l /var/run/

<snip>
drwxr-xr-x  2 mysql     root       48 2006-02-01 10:00 mysqld/
```

It would work though if I set it to run as root 

```
#sudo mysqld --user=root

060201 10:05:55  InnoDB: Started
mysqld: ready for connections.
Version: '4.0.24_Debian-10ubuntu2'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Source distribution

```

Yes, I've googled around, also searching in the forum for this problem. Most of the solution consists of chmoding /var/lib/run/ to 777. I tried that and get the same problem. In fact, I tried telling mysql to put the socket in /tmp which also has 777 permission and it still says it is unable to create the socket. :confused:

---

### Post by mpa on 2006-02-01
Okay, after deleting the old /var/run/mysqld and /var/lib/mysql and then purge+reinstall the mysql-* package, then reinitialize the master database. I managed to get it to work. :-|

---

### Post by LordHunter317 on 2006-02-01
Don't ever chmod anything to 777 as part of a solution.  It won't help a thing, and you jsut wrecked your security.

I'm glad you got it working though.

---

