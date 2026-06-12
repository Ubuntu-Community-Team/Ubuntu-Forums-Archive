---
title: "Mysql Can't find messagefile error"
date: 2011-05-22
forum: Server Platforms
---

### Post by pdc124 on 2011-05-22
> ~# mysqld
110522 11:36:12 [ERROR] Can't find messagefile '/usr/share/mysql/english/errmsg.sys'

but ive got 
> # ls -la /usr/share/mysql/english/
total 44
drwxr-xr-x  2 root root  4096 2011-05-21 12:55 .
drwxr-xr-x 26 root root  4096 2011-05-21 12:56 ..
-rw-r--r--  1 root root 36324 2011-02-10 08:54 errmsg.sys
~# 

(this is on my ASUS eee , as i was running out of space on  /dev/sda, I moved all of /usr/share to the other HD.Other things seem to work OK.
> # ls -al /usr/share
lrwxrwxrwx 1 root root 24 2011-04-19 19:22 /usr/share -> /home/.fs-ext/usr/share/
~# 

I've tried purging and reinstalling all of MySQL.
i get this on the re-install
> coop@littleCOOP:~$ sudo dpkg-reconfigure mysql-server-5.1
mysql stop/waiting
110522  8:29:23 [ERROR] Can't find messagefile '/usr/share/mysql/english/errmsg.sys'
"Unable to set password for the MySQL "root" user                          &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; An error occurred while setting the password for the MySQL                &#9474; 
 &#9474; administrative user. This may have happened because the account already   &#9474; 
 &#9474; has a password, or because of a communication problem with the MySQL      &#9474; 
 &#9474; server.                "
ive got this installed
> $ dpkg -l|grep mysql
ii  libdbd-mysql-perl                      4.012-1ubuntu1                                  A Perl5 database interface to the MySQL data
ii  libmysqlclient16                       5.1.41-3ubuntu12.10                             MySQL database client library
ii  mysql-client-5.1                       5.1.41-3ubuntu12.10                             MySQL database client binaries
ii  mysql-client-core-5.1                  5.1.41-3ubuntu12.10                             MySQL database core client binaries
ii  mysql-common                           5.1.41-3ubuntu12.10                             MySQL database common files (e.g. /etc/mysql
ii  mysql-server                           5.1.41-3ubuntu12.10                             MySQL database server (metapackage depending
ii  mysql-server-5.1                       5.1.41-3ubuntu12.10                             MySQL database server binaries
ii  mysql-server-core-5.1                  5.1.41-3ubuntu12.10                             MySQL database core server files
ii  php5-mysql                             5.3.2-1ubuntu4.9                                MySQL module for php5

> 
$ sudo mysqld --skip-grant-tables &
[1] 11106
$ 110522  8:36:02 [ERROR] Can't find messagefile '/usr/share/mysql/english/errmsg.sys'
$ ps -A | grep mysql
[1]+  Exit 1                  sudo mysqld --skip-grant-tables
$ telnet localhost 3306
Trying ::1...
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
$ 
 
and heres the log file in response to mysqld
> 110522 11:55:56 [Note] Plugin 'FEDERATED' is disabled.
110522 11:55:56  InnoDB: Started; log sequence number 0 44233
110522 11:55:56 [ERROR] Aborting

110522 11:55:56  InnoDB: Starting shutdown...
110522 11:55:58  InnoDB: Shutdown completed; log sequence number 0 44233
110522 11:55:58 [Note] 
> # grep ^[a-zA-z\ ] /etc/mysql/my.cnf 
port		= 3306
socket		= /var/run/mysqld/mysqld.sock
socket		= /var/run/mysqld/mysqld.sock
nice		= 0
user		= mysql
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
skip-external-locking
bind-address		= 127.0.0.1
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 192K
thread_cache_size       = 8
myisam-recover         = BACKUP
query_cache_limit	= 1M
query_cache_size        = 16M
log_error                = /var/log/mysql/error.log
expire_logs_days	= 10
max_binlog_size         = 100M
quick
quote-names
max_allowed_packet	= 16M
key_buffer		= 16M
~# 


---

