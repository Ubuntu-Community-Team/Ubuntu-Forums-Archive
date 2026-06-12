---
title: "MySQL won't start, no errors"
date: 2010-01-15
forum: Server Platforms
---

### Post by Dooley on 2010-01-15
My mysql server won't start on my machine.

It simply fails with no errors.

```

sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                                                                             [ OK ] 
 * Starting MySQL database server mysqld                                                                                             [fail] 

```

When I run cat /var/log/mysql.err the file is empty, thinking this might be a permissions issue I tried chowning to a mysql user.

Here's the current permissions.

```
ls -alh /var/log/mysql*
\-rw-r----- 1 mysql adm    0 2009-09-30 11:08 /var/log/mysql.err
-rw-r----- 1 mysql adm    0 2010-01-15 09:07 /var/log/mysql.log
-rw-r----- 1 mysql adm   20 2009-11-25 07:35 /var/log/mysql.log.1.gz
-rw-r----- 1 mysql adm   20 2009-11-24 07:59 /var/log/mysql.log.2.gz
-rw-r----- 1 mysql adm   20 2009-11-23 07:56 /var/log/mysql.log.3.gz
-rw-r----- 1 mysql adm   20 2009-11-22 07:54 /var/log/mysql.log.4.gz
-rw-r----- 1 mysql adm   20 2009-11-21 07:47 /var/log/mysql.log.5.gz
-rw-r----- 1 mysql adm   20 2009-11-20 07:43 /var/log/mysql.log.6.gz
-rw-r----- 1 mysql adm   20 2009-11-19 07:35 /var/log/mysql.log.7.gz

/var/log/mysql:
total 8.0K
drwxrwsrwx  2 mysql adm  4.0K 2009-09-30 11:08 .
drwxr-xr-x 16 root  root 4.0K 2010-01-15 10:24 ..
```

Still having the same issue, mysql server is still failing and /var/log/mysql.err is still empty. 

Does anyone know where else I should look to diagnose my problem?

Thanks,

Dooley

---

### Post by Dooley on 2010-01-15
A bit more info I tried simply executing mysqld as root

```
sudo mysqld
100115 10:39:43  InnoDB: Started; log sequence number 0 43655
100115 10:39:44 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
100115 10:39:44 [ERROR] Do you already have another mysqld server running on port: 3306 ?
100115 10:39:44 [ERROR] Aborting

100115 10:39:44  InnoDB: Starting shutdown...
100115 10:39:45  InnoDB: Shutdown completed; log sequence number 0 43655
100115 10:39:46 [Note] mysqld: Shutdown complete
```


But when I run 
```
sudo netstat -an | grep 3306
``` 
it doesn't return anything.

Oh and when I try a different port

```
sudo mysqld -P 3305
[sudo] password for shane: 
100115 10:45:49  InnoDB: Started; log sequence number 0 43655
100115 10:45:49 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
100115 10:45:49 [ERROR] Do you already have another mysqld server running on port: 3305 ?
100115 10:45:49 [ERROR] Aborting

100115 10:45:49  InnoDB: Starting shutdown...
100115 10:45:51  InnoDB: Shutdown completed; log sequence number 0 43655
100115 10:45:51 [Note] mysqld: Shutdown complete

```

and

```
sudo mysqld -P 9999
100115 10:47:13  InnoDB: Started; log sequence number 0 43655
100115 10:47:13 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
100115 10:47:13 [ERROR] Do you already have another mysqld server running on port: 9999 ?
100115 10:47:13 [ERROR] Aborting

100115 10:47:13  InnoDB: Starting shutdown...
100115 10:47:15  InnoDB: Shutdown completed; log sequence number 0 43655
100115 10:47:15 [Note] mysqld: Shutdown complete
```

I'm now very confused.

---

### Post by wojox on 2010-01-15
What happens when you run:

```
mysql -u root -p <enter>
```

---

### Post by Dooley on 2010-01-15
Hi wojox,

I tried what you suggested but the server definitely wasn't running.

Turns out it was a bad bind-address in my /etc/mysql/my.cnf

With only 

```
bind-address 127.0.0.1 
```

It works fine now. 

:) 

Thanks wojox.

---

