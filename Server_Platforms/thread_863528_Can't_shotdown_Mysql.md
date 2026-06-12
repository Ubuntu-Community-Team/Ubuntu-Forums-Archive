---
title: "Can't shotdown Mysql"
date: 2008-07-18
forum: Server Platforms
---

### Post by masoud23 on 2008-07-18
Hi

I have Mysql 5 and Xampp. When I try to start Xampp I get this message:

XAMPP: Another MySQL daemon is already running.

How can i shut Mysql down permanently so it dose not start when i start my computer? 

Ps: i start Mysql first time with mysqld_safe command. Dose it any ting to do with at i can't stop it now?

---

### Post by silverglade00 on 2008-07-18
Try 

```
sudo ps aux | grep mysql
```

then

```
sudo /etc/init.d/mysql_server_from_above stop
```

---

### Post by masoud23 on 2008-07-18
the forst code works but not the second part:

root@masoud-desktop:~# ps aux | grep mysql
root      5015  0.0  0.0   1752   528 ?        S    21:10   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     5055  0.0  1.5 126920 16132 ?        Sl   21:10   0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      5056  0.0  0.0   1680   548 ?        S    21:10   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root      6701  0.0  0.0   2976   768 pts/0    S+   23:24   0:00 grep mysql
root@masoud-desktop:~# sudo /etc/init.d/mysql_server_form_above stop
sudo: /etc/init.d/mysql_server_form_above: command not found
root@masoud-desktop:~#

---

### Post by masoud23 on 2008-07-18
I found someting that worked:

sudo mysqladmin -u root -p shutdown

---

