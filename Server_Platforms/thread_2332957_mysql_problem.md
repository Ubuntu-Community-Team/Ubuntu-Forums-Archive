---
title: "mysql problem"
date: 2016-08-05
forum: Server Platforms
---

### Post by Vegan on 2016-08-05
i have some storage mounted in /sql and i copied the default files

the my.cnf does not seem to have anything expected

change or add

datadir=/var/lib/mysql
socket=/var/lib/mysql/mysql.sock

to

datadir=/sql
socket=/sql/mysql.sock

where are these hiding?

---

### Post by darkod on 2016-08-05
If you are trying to set only custom datadir, do only that. Why copying mysql program files?

In case you really want to do that, I haven't tried it before. But google should help you, there are tons of tutorials about mysql...

---

### Post by Vegan on 2016-08-05
I only copied the data files, to a large chunk of storage

i tried to edit the my.cnf but no options as expected

so are they somewhere else? adding causes errors

---

### Post by darkod on 2016-08-05
mysql.sock would not be part of the database files. That's the socket running mysql.

PS. [http://stackoverflow.com/questions/1795176/how-to-change-mysql-data-directory](http://stackoverflow.com/questions/1795176/how-to-change-mysql-data-directory)
[http://askubuntu.com/questions/137424/moving-mysql-datadir](http://askubuntu.com/questions/137424/moving-mysql-datadir)

---

### Post by Vegan on 2016-08-05
I used a slightly different copy 

sudo cp -rap /var/lib/mysq /sql

I also did a chown

all that is in my my.cnf is a pair of includes

!includedir /etc/mysql/conf.d/
!includedir /etc/mysql/mysql.conf.d/

I added

[mysqld]
datadir=/sql
tmpdir=/sql

---

### Post by darkod on 2016-08-05
Maybe it changed with the latest versions. Look at the includes and their content.

---

### Post by Vegan on 2016-08-05
found this

  GNU nano 2.5.3              File: mysqld.cnf

user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
lc-messages-dir = /usr/share/mysql
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 127.0.0.1
#
# * Fine Tuning
#
key_buffer_size         = 16M
max_allowed_packet      = 16M
thread_stack            = 192K


in mysqld.cnf

maybe i need to only change the data dir?

wonder why Oracle made so many changes when the old way worked fine

---

