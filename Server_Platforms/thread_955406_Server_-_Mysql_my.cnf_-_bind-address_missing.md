---
title: "Server - Mysql my.cnf - bind-address missing"
date: 2008-10-22
forum: Server Platforms
---

### Post by madman045 on 2008-10-22
Hi,

I am quite new to Ubuntu and I am following this guide

[http://www.howtoforge.com/the-perfect-spamsnake-ubuntu-8.04-p3](http://www.howtoforge.com/the-perfect-spamsnake-ubuntu-8.04-p3)

However I have hit a problem, when I edit the my.cnf for mysql, the bind-address line is no where to be found, so i cannot comment out the localhost part

vi /etc/mysql/my.cnf

This is the result

[IMG]http://img.photobucket.com/albums/v54/madman045/Work%20Related/mysqlconfigfile.jpg[/IMG]

Anyone tell me where I can find this line to comment it out as mysql is listening on localhost

Thanks

---

### Post by Nostalos on 2008-10-22
What exactly are you trying to accomplish?   If the bind-address is missing then it should already be listening on all addresses and not just localhost.

---

### Post by Iowan on 2008-10-22
I did the CD LAMP install - the */etc/mysql/my.cnf* file has a section:```
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
language        = /usr/share/mysql/english
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 127.0.0.1
#
# * Fine Tuning

```

---

