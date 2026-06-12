---
title: "Unable to start MySQL"
date: 2009-08-30
forum: Server Platforms
---

### Post by Milambar on 2009-08-30
Ubuntu spontaenously rebooted last night, and since then, I've been unable to persuade mysql to start or restart.

/etc/init.d/mysql start  just returns FAILED
/etc/init.d/mysql restart also returns FAILED

/var/log/mysql.err is an empty file
/var/log/mysql.log is an empty file
cat /var/log/syslog | grep mysql gives:
> 
Aug 30 12:06:18 masterroot /etc/init.d/mysql[6881]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Aug 30 12:06:18 masterroot /etc/init.d/mysql[6881]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Aug 30 12:06:18 masterroot /etc/init.d/mysql[6881]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Aug 30 12:06:18 masterroot /etc/init.d/mysql[6881]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

Its kind of obvious that /var/run/mysqld/mysqld.sock doesn't exist since mysql isn't running. Seems like a catch 22 situation. mysql won't start, because /var/run/mysqld/mysqld.sock doesn't exist, but /var/run/mysqld/mysqld.sock doesnt exist because mysql server isnt running.

Anyway

How do I fix this, plesae?

---

### Post by DaithiF on 2009-08-30
just to check, are you running:
```
**sudo** /etc/init.d/mysql start
```

---

### Post by Milambar on 2009-08-30
> **DaithiF said:**
> just to check, are you running:
```
**sudo** /etc/init.d/mysql start
```

As you can see from my initial post, yes I am. Here is the exact, verbatim output from the shell:

> 
root@masterroot:/etc/mysql# /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                                                                                                                  [fail]
root@masterroot:/etc/mysql# /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                                                                                                                  [ OK ]
 * Starting MySQL database server mysqld                                                                                                                                  [fail]



---

### Post by DaithiF on 2009-08-30
Those log messages in syslog are only from the init process, there should be something logged by mysqld also to indicate the error -- should have been picked up by your grep I know, but maybe your syslog rolled over, I don't know but worth having a further look.

also worth trying
```
sudo /usr/bin/mysqld_safe &

```
to start mysqld in safe mode and see what that does.

---

### Post by Milambar on 2009-08-30
> **DaithiF said:**
> Those log messages in syslog are only from the init process, there should be something logged by mysqld also to indicate the error -- should have been picked up by your grep I know, but maybe your syslog rolled over, I don't know but worth having a further look.

also worth trying
```
sudo /usr/bin/mysqld_safe &

```
to start mysqld in safe mode and see what that does.

Okay, thank you. No joy on that either though. Heres what happened:
> 
root@masterroot:/home/milambar/sqldumps# /usr/bin/mysqld_safe &
[1] 5685
root@masterroot:/home/milambar/sqldumps# nohup: ignoring input and redirecting stderr to stdout
Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[5721]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[5731]: ended

[1]+  Done                    /usr/bin/mysqld_safe


The messages logged in syslog:
> 
Aug 30 13:13:12 masterroot mysqld_safe[5936]: started
Aug 30 13:13:13 masterroot mysqld_safe[5946]: ended


---

