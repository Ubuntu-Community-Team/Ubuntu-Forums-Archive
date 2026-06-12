---
title: "MySQL visible to Windows?"
date: 2008-09-20
forum: Server Platforms
---

### Post by Vegan on 2008-09-20
When I am developing, I was wondering if its possible to make the Linux database usable to a Windows client.

---

### Post by windependence on 2008-09-20
Sure, you would just access the database server by IP address. You will need to enable MySQL to listen on an external port. The default is localhost.

-Tim

---

### Post by koenn on 2008-09-20
You might also need some sort of Database Provider for your windows client application. there's an ODBC driver for mysql
I used it once to get vbscript to work with mysql : 
[http://users.telenet.be/mydotcom/program/bibmon/](http://users.telenet.be/mydotcom/program/bibmon/)

---

### Post by Vegan on 2008-09-20
How do I get MySQL to listen on the network?

---

### Post by koenn on 2008-09-20
you need to edit my.cnf and set the bind address to a real address in stead of loopback.
it's all in the link I posted

---

### Post by promodus on 2008-09-20
Using ODBC & Visio to reverse engineer MySQL:
[http://ubuntuforums.org/showthread.php?t=843827](http://ubuntuforums.org/showthread.php?t=843827)

---

### Post by cariboo on 2008-09-20
You can also use this:

[http://www.mysql.com/products/connector/odbc/](http://www.mysql.com/products/connector/odbc/)

I've used it with access to convert from the proprietory db to mysql

Jim

---

### Post by Vegan on 2008-09-20
I wanted to get various programs to be able to 'see' the SQL engine. I added the listen address.

I can create databases easy enough from the console, I just wanted to be able to use the table on the LAN as well as on localhost.

For example, I have a database of foods, I can select ingredients as I eat them. And use a web page to interface the database. Another page can be used to insert groceries.

Another example, database of cars, as cars come to the lot. etc.

Linux is the host OS, I wanted to be able to run web pages from other hosts etc.

---

### Post by Vegan on 2008-09-21
When I added a line to listen on the LAN 192.168.7.250 which is the machine's IP address, the localhost access for Apache failed.

Thoughts?

---

### Post by koenn on 2008-09-21
> **Vegan said:**
> When I added a line to listen on the LAN 192.168.7.250 which is the machine's IP address, the localhost access for Apache failed.

Thoughts?

where did you add that line ?

---

### Post by Vegan on 2008-09-21
I added the line immediately below the local host line. Commented out to get the phpBB back up.

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
bind-address		= 127.0.0.1
#bind-address		= 192.168.7.250
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
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id		= 1
#log_bin			= /var/log/mysql/mysql-bin.log
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
# The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/

---

### Post by kamaji792 on 2008-09-22
Hi, I've been playing around with MySQL.  To allow me to connect from a windows client I commented out the:

**bind-address = 127.0.0.1**

Just put a '#' caracter at the start of the line.

I was connecting using a java program I had written.

I believe you can only set one bind-address and then MySQL only listens to input from that IP address.

I guess there are security implications to this which I hope I have covered by using a firewall to limit access to MySQL from the local subnet.

All the best.

---

### Post by Vegan on 2008-09-22
My Linux machine, like all of my computers lives behind a firewall. I only wanted SQL access on the LAN. So with SQL more or less an island, I have to use another strategy. Back to the drawing board.

Good thing I have a PHP book or 3.

---

### Post by koenn on 2008-09-22
> **Vegan said:**
> I added the line immediately below the local host line. Commented out to get the phpBB back up.

phpBB, I assume that uses your mysql server as a backend ? If it's running on the same machine as your mysql dbms and uses the localhost address to talk to mysql, that would be the reason phpBB doesn't work when you change the bind address for mssql.

Is that what you meant with "When I added a line to listen on the LAN 192.168.7.250, the localhost access for Apache failed." ? 

> **Vegan said:**
> My Linux machine, like all of my computers lives behind a firewall. I only wanted SQL access on the LAN. So with SQL more or less an island, I have to use another strategy. Back to the drawing board.

Good thing I have a PHP book or 3.
192.168.7.250 is a private address, only visible on your LAN, so perfectly usable for what "LAN only" SQL. The only way anything from outside the LAN can connect to that is if you have a router setup specifically to enable that.

So, it's perfectly reasonable to have mysql listening on 192.168.7.250, configure phpBB to use that address for database access, and let the programs you intend to write do the same.

---
sounds to me you're going to need to read up on basic networking, and client/server architecture, if you're planning to write database frontends

---

### Post by windependence on 2008-09-23
Yes the forum must also be configured to connect to that IP instead of the localhost.

I agree with koenn.

-Tim

---

