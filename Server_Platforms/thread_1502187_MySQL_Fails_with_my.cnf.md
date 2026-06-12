---
title: "MySQL Fails with my.cnf"
date: 2010-06-05
forum: Server Platforms
---

### Post by Joeb454 on 2010-06-05
I've tried everything now, so I'll ask the people who know best :)

I'm trying to start my MySQL server, and it fails if the /etc/mysql/my.cnf file is there. If it isn't, then it fails - syslog shows me this:
```
Jun  5 11:02:53 myhost /etc/init.d/mysql[21733]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jun  5 11:02:53 myhost /etc/init.d/mysql[21733]: #007/usr/bin/mysqladmin: connect to server at 'localhost' failed
Jun  5 11:02:53 myhost /etc/init.d/mysql[21733]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jun  5 11:02:53 myhost /etc/init.d/mysql[21733]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

The annoying thing is, that if the my.cnf file isn't there, it can create the mysqld.sock file, so I know the permissions are right.

If anybody has any ideas why this is, I'd be very grateful!!

---

### Post by rachaelb on 2010-06-05
what is your my.cnf file? dumb question.... but is your bind address set correctly?

---

### Post by Joeb454 on 2010-06-05
Sorry - forgot to add that :p

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
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
# bind-address		= 127.0.0.1
#
# * Fine Tuning
#
key_buffer		= 32M
max_allowed_packet	= 24M
thread_stack		= 128K
thread_cache_size	= 8
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 5M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log		= /var/log/mysql/mysql.log
#
#
# Error logging goes to syslog. This is a Debian improvement :)
#
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
#expire_logs_days	= 10
#max_binlog_size         = 100M
#binlog_do_db		= forum
#binlog_ignore_db	= include_database_name
#
# * BerkeleyDB
#
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
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
# * NDB Cluster
#
# See /usr/share/doc/mysql-server-*/README.Debian for more information.
#
# The following configuration is read by the NDB Data Nodes (ndbd processes)
# not from the NDB Management Nodes (ndb_mgmd processes).
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1


#
# * IMPORTANT: Additional settings that can override those from this file!
# The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/
```

---

### Post by rachaelb on 2010-06-05
the only differences between that and my file are:

1) the bind address is *not* commented out
2) I have the line: myisam-recover = BACKUP
3) I *don't* have: pid-file    = /var/run/mysqld/mysqld.pid

Hope that helps :)

---

### Post by Joeb454 on 2010-06-05
Still no joy :( I haven't a clue what it could be. I'll try reinstalling and see if that works. Thanks for letting me know the differences though!

---

### Post by rachaelb on 2010-06-05
yikes! good luck!! i'm just completing my second full server migration in the last month... if anyone knows why amavis should be complaining to me, please let me know :)

---

### Post by LG_Auction on 2010-06-09
I installed a fresh 10.04 LAMP and moved a MYSQL database. All was working until yesterday. Now I can not start the server.  I ran the following:

~$ service mysql start 

This is the result:

start: Rejected send message, 1 matched rules; type="method_call", sender=":1.55" (uid=1000 pid=14469 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")) 

Any idea how to start the server?

---

### Post by romy.mathew on 2011-05-07
mysqld_safe --skip-grant-tables --skip-networking &


This might help you to get inside the MySQL Server, I faced the same problem almost 24 hr before and this helped to log inside

---

