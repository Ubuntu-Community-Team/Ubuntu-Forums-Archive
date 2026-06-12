---
title: "Problem with MySQL and debian-sys-maint"
date: 2009-04-30
forum: Server Platforms
---

### Post by Mamsaac on 2009-04-30
The other day it solved by just restarting the user's password (or at least it seemed like it had fixed). Today it's different.

So, here's the output:

```
USER@HOST:~$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                                            [fail] 
 * Starting MySQL database server mysqld                                                            [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
USER@HOST:~$ 

```

The good: mysql is running... I can access all databases and do whatever I want with them.

The bad: I need to restart it but I can't. Also, it's not ok to have this kind of errors.

So, I tried changing the password for debian-sys-maint. 

```
mysql> grant all privileges on *.* to 'debian-sys-maint'@'localhost' identified by 'PASSWORD' with grant option;

```
And it worked (yay for me). Still, this is the second time I have to do this.

Any possible reasons it's been necessary to do this? I've been even feeling someone could be changing it, but I seriously doubt so (I've checked SSH access and executed queries, but nothing).

Thanks in advance for all the help.

---

