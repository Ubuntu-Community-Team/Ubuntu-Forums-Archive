---
title: "mysql database location?"
date: 2011-01-10
forum: Server Platforms
---

### Post by sdowney717 on 2011-01-10
where are the databases located?

how to open up the lan to database queries?

I tried to login from an XP machine to my ubuntu mysql server and cant.
When I explore the network from XP, it shows my ubuntu desktop as part of the workgroup.

---

### Post by chrislynch8 on 2011-01-10
Hi,

Your database is location in /var/lib/mysql/"DB-Name"

What are you using to try and login?

If you have firewalls installed you will need to open up the port for mysql and you may also have to all access via your hosts.allow file 
Rgds

---

### Post by sdowney717 on 2011-01-10
Thanks, I copied the database into that folder

a windows based library program I wrote myself that uses mysql.
hosts.allow file, so I will check that out.

I recall something about that file when I did this before.

---

### Post by chrislynch8 on 2011-01-10
Not sure if copying a database to that folder will work, I think you might need to add the database using proper sql commands.

I have SQLyog here so I access my DB server using 192.168.1.250:3306

In my hosts.allow I have a line mysqld: ALL

Also in you my.conf file make sure that your Mysql instance is listening on the correct LAN interface. By default it may be looking at 127.0.0.1 by default so you will have to change this to listen on the LAN address instance

---

### Post by sdowney717 on 2011-01-10
added ALL: ALL 

> # /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#


stll not connecting yet, and turned off the XP firewall
Will try a reboot


OTHER ISSUE is a database I created with server 5.05
apparently has trouble with server 5.1?

[QUOTE]scott@scott-desktop:~$ mysql -u root -p 
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 44
Server version: 5.1.49-1ubuntu8.1 (Ubuntu)

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.


mysql> use booksgood;
Database changed
mysql> select * from usertable;
ERROR 1017 (HY000): Can't find file: './booksgood/usertable.frm' (errno: 13)
mysql> 

ALL: ALL[/QUOTE]

---

### Post by sdowney717 on 2011-01-10
yes, showing 127.o.o.1 in 
my.cnf

so change it to reflect the client trying to connect or the address of the host?

```
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
# 
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user		= mysql
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 127.0.0.1
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 192K
thread_cache_size       = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover         = BACKUP
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit	= 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file        = /var/log/mysql/mysql.log
#general_log             = 1

log_error                = /var/log/mysql/error.log

# Here you can see queries with especially long duration
#log_slow_queries	= /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id		= 1
#log_bin			= /var/log/mysql/mysql-bin.log
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet	= 16M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/
```

---

### Post by sdowney717 on 2011-01-10
getting closer, now the message is the machine is not authorized
At least it sees the server.

what next?

---

### Post by sdowney717 on 2011-01-10
had to run a grant command
NOW it connects!

GRANT ALL ON *.* TO 'root'@'192.168.1.%' identified by 'MY_PASSWORD';

[http://www.uluga.ubuntuforums.org/showthread.php?t=253153](http://www.uluga.ubuntuforums.org/showthread.php?t=253153)
[http://ubuntuforums.org/archive/index.php/t-253153.html](http://ubuntuforums.org/archive/index.php/t-253153.html)

having a very hard time with the forum server responding

---

### Post by sdowney717 on 2011-01-10
basically had to do 3 things to make it work connecting outside the box the server is running on

modify the hosts.allow file
modify my.cnf file set bind field to the ip address of the host
execute grant statement

GRANT ALL ON *.* TO 'root'@'192.168.1.%' identified by 'MY_PASSWORD';

a couple nice programs are
mysql-query-browser
mysql-admin

---

