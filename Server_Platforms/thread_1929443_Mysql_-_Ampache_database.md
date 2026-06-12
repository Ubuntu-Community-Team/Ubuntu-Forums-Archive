---
title: "Mysql - Ampache database"
date: 2012-02-22
forum: Server Platforms
---

### Post by kamelie1706 on 2012-02-22
Hi,

yesterday I have installed ampache server together with mysql. It was working fine but this morning when reboot the connection to mysql server is not possible.

When I check the status I got 
```
sudo service mysql status 
mysql respawn/post-start, (post-start) process 17759

```Then I have tried to restart the mysql server using "sudo service mysql restart" and I get now
```
sudo service mysql status 
mysql start/running
```When I look at the process running
```
ps -ef | grep mysql
cyril    13413 13410  0 08:41 ?        00:00:00 /usr/sbin/mysqld --defaults-file=/home/cyril/.local/share/akonadi/mysql.conf --datadir=/home/cyril/.local/share/akonadi/db_data/ --socket=/home/cyril/.local/share/akonadi/socket-htpc/mysql.socket
cyril    18252 13244  0 08:57 ?        00:00:02 /usr/bin/mysql-admin
cyril    19233 14283  0 09:06 pts/1    00:00:00 grep --color=auto mysql
```'/var/run/mysqld/mysqld.sock' does not exists.

Somehow it seems that my server is a local instance specific to "akonadi" ... where can I found other databases managed by mysql?

Thanks

---

### Post by kamelie1706 on 2012-02-22
In /var/log/mysql/error.log I can find

```
120222  8:54:46 [Note] Plugin 'FEDERATED' is disabled.
120222  8:54:46  InnoDB: Initializing buffer pool, size = 8.0M
120222  8:54:46  InnoDB: Completed initialization of buffer pool
120222  8:54:46  InnoDB: Started; log sequence number 0 44233
120222  8:54:46 [ERROR] Can't start server : Bind on unix socket: Permission denied
120222  8:54:46 [ERROR] Do you already have another mysqld server running on socket: /var/run/mysqld/mysqld.sock ?
120222  8:54:46 [ERROR] Aborting

120222  8:54:46  InnoDB: Starting shutdown...
120222  8:54:51  InnoDB: Shutdown completed; log sequence number 0 44233
120222  8:54:51 [Note] /usr/sbin/mysqld: Shutdown complete

```

'/var/run/mysqld/' is empty ....

---

### Post by kamelie1706 on 2012-02-22
I am looking at the permission of the directory that the socket file should be created 

```
120222  8:54:46 [ERROR] Can't start server : Bind on unix socket: Permission denied 120222  8:54:46 [ERROR] Do you already have another mysqld server running on socket: /var/run/mysqld/mysqld.sock ?
```

I get the following
```
drwxr-xr-x  2 mysql      root         40 2012-02-22 17:37 mysqld/

```

I guess the mysqld service as to be launch under root or mysql user.

Am I going to the right direction?

---

### Post by kamelie1706 on 2012-02-22
Nothing special in /etc/mysql /my.cnf
```
#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user        = mysql
socket        = /var/run/mysqld/mysqld.sock
port        = 3306
basedir        = /usr
datadir        = /var/lib/mysql
tmpdir        = /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address        = 127.0.0.1
```

:confused:

---

### Post by kamelie1706 on 2012-02-22
Found the answer there
[http://my.opera.com/djfake/blog/2011/11/05/ubuntu-11-10-mysql-problem-after-upgrade](http://my.opera.com/djfake/blog/2011/11/05/ubuntu-11-10-mysql-problem-after-upgrade)

Those 2 lines were originally causing problem ... do not remenber why 
 /{,var/}run/mysqld/mysqld.pid w,  /{,var/}run/mysqld/mysqld.sock w,
[FONT=Verdana]
in [/FONT] [U]/etc/apparmor.d/usr.sbin.mysqld


[/U]

---

