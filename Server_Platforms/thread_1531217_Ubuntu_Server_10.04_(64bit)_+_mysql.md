---
title: "Ubuntu Server 10.04 (64bit) + mysql"
date: 2010-07-14
forum: Server Platforms
---

### Post by Illusion80 on 2010-07-14
Hi all,

I have a problem with mysql 5.1 on my Ubuntu server 10.04. (64 bit) 

1. I can't restart mysql with the following commands:

/etc/init.d/mysql restart (hangs)
service mysql restart (hangs)

2. the startupjob/deamon from mysql is disabled but mysql is up and running 

mysql     1084  4.9  4.7 559528 98696 ?        Ssl  21:19   2:10 /usr/sbin/mysqld
root     11137  0.0  0.0   7624   908 pts/1    S+   22:03   0:00 grep mysql


3. I've found out some strange behaviour:

mysql -u username -p password

The program 'mysql' can be found in the following packages:
 * mysql-client-core-5.1
 * mysql-client-5.0
 * mysql-cluster-client-5.1

apt-get install mysql-client-core-5.1

Reading package lists... Done
Building dependency tree
Reading state information... Done
mysql-client-core-5.1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


dpkg-reconfigure mysql-client-core-5.1 - nothing happens
and same problem appears to be

Anybody has an idea?

---

### Post by cariboo on 2010-07-14
Can you kill mysql by pid?

To find the pid, in a terminal type:

```
ps ax | grep mysql
```

---

### Post by Illusion80 on 2010-07-14
Yes, I can, but I need to reboot the whole server to get mysql up and running again. The restart commands just hangs and that's it.

---

### Post by ptn107 on 2010-07-14
Install the *mysql-client* package?  Also my *mysqld* locks up when I try to start/stop it.  If I make a change I'll just kill it with *killall* and it's fine.

---

