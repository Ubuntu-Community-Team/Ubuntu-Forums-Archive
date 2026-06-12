---
title: "MySQL doesn't start"
date: 2007-03-21
forum: Server Platforms
---

### Post by pabloles on 2007-03-21
Hello!

I install mysql server on my ubuntu deskop:

```
# apt-get install mysql-server
```

everything install ok, mysql start, i change root password and i restart sql server:

```
# /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld  [ ok ]
 * Starting MySQL database server mysqld   [fail]
#
```

If i run some script (/etc/mysql/debian-start):

```
# /etc/mysql/debian-start
Checking for corrupt, not cleanly closed and upgrade needing tables.
# /usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

#
```

I use 'find' command to find socket like mysql.sock and mysqld.sock but this found nothing....

If you can, please help me :)
Thank you

edit: 

```
# mysqld
mysqld got signal 4;
This could be because you hit a bug. It is also possible that this binary
or one of the libraries it was linked against is corrupt, improperly built,
or misconfigured. This error can also be caused by malfunctioning hardware.
We will try our best to scrape up some info that will hopefully help diagnose
the problem, but since we have already crashed, something is definitely wrong
and this may fail.

key_buffer_size=0
read_buffer_size=131072
max_used_connections=0
max_connections=100
threads_connected=0
It is possible that mysqld could use up to 
key_buffer_size + (read_buffer_size + sort_buffer_size)*max_connections = 217599 K
bytes of memory
Hope that's ok; if not, decrease some variables in the equation.

# 
```

---

### Post by outZider on 2007-03-31
I'm going to assume you're running 64 bit Ubuntu.

This is Bug 66702 for Ubuntu AMD64 -- seems to have cropped up recently. You'll have to add the edgy-proposed repository and install mysql-server and mysql-server-5.0. In a few days, it should hit edgy-updates.

[https://launchpad.net/ubuntu/edgy/+source/mysql-dfsg-5.0/+bug/66702](https://launchpad.net/ubuntu/edgy/+source/mysql-dfsg-5.0/+bug/66702)

---

### Post by norwyn on 2007-04-01
I've got the same problem and I'm on a intel p4.
I have tried to reinstall mysql and php, but without success.
Any ideas?

SOLVED: 
I just had to change my ip to localhost in /etc/mysql/my.cnf .
Then it worked.

---

