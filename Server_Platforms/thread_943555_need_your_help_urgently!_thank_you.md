---
title: "need your help urgently! thank you"
date: 2008-10-10
forum: Server Platforms
---

### Post by Grace.zhang on 2008-10-10
I used JDBC connector to connect Java to MySQL and it worked well. After I installed PHP5 and Apache2, PHP can connect MySQL. However, the JDBC connector to MySQL doesn't work any more. Here's the error info:

Exception in thread "main" com.mysql.jdbc.CommunicationsException: Communications link failure due to underlying exception: 

** BEGIN NESTED EXCEPTION ** 

java.net.SocketException
MESSAGE: java.net.ConnectException: Connection refused

STACKTRACE:

java.net.SocketException: java.net.ConnectException: Connection refused
	at com.mysql.jdbc.StandardSocketFactory.connect(StandardSocketFactory.java:156)
	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:284)
	at com.mysql.jdbc.Connection.createNewIO(Connection.java:2555)
	at com.mysql.jdbc.Connection.<init>(Connection.java:1485)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:266)
	at java.sql.DriverManager.getConnection(DriverManager.java:582)
	at java.sql.DriverManager.getConnection(DriverManager.java:207)
	at com.dao.test.DaoMySQL.<init>(DaoMySQL.java:21)
	at com.dao.test.DaoMySQL.main(DaoMySQL.java:67)


** END NESTED EXCEPTION **



Last packet sent to the server was 15 ms ago.
	at com.mysql.jdbc.Connection.createNewIO(Connection.java:2621)
	at com.mysql.jdbc.Connection.<init>(Connection.java:1485)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:266)
	at java.sql.DriverManager.getConnection(DriverManager.java:582)
	at java.sql.DriverManager.getConnection(DriverManager.java:207)
	at com.dao.test.DaoMySQL.<init>(DaoMySQL.java:21)
	at com.dao.test.DaoMySQL.main(DaoMySQL.java:67)

Is there any conflict after I installed Apache2 or there're some error in configure? 

Thanks for your time.

---

### Post by lykwydchykyn on 2008-10-10
Did you make any changes to the MySQL configuration to get apache and php working? 

Can you post /etc/mysql/my.cnf

---

### Post by koenn on 2008-10-10
I'd guess that your ptoblem is this
java.net.SocketException: java.net.ConnectException: Connection refused

which might mean that either your server refuses the connection (eg wrong tcp port ? wrong address & there's noone there ?) or mysql refuses the connection (bad username/password ? ...)

but i'm not a programmer or a dba, so i could be completely wrong.
Maybe the programmers forum could be of assistance


EDIT: ah, someone else's already looking in to it ...

---

### Post by Grace.zhang on 2008-10-10
> **lykwydchykyn said:**
> Did you make any changes to the MySQL configuration to get apache and php working? 

Can you post /etc/mysql/my.cnf

I guess that's the error lying, here's my my.cnf:

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
# [http://dev.mysql.com/doc/mysql/en/server-system-variables.html](http://dev.mysql.com/doc/mysql/en/server-system-variables.html)

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
 bind-address		= 10.40.5.62
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log		= /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
#
# Here you can see queries with especially long duration
#log_slow_queries	= /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
#server-id		= 1
log_bin			= /var/log/mysql/mysql-bin.log
# WARNING: Using expire_logs_days without bin_log crashes the server! See README.Debian!
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
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
#
!includedir /etc/mysql/conf.d/
set-variable = lower_case_table_names=1

---

