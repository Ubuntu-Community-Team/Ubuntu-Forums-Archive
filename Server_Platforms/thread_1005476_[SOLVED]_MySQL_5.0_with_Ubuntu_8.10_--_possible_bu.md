---
title: "[SOLVED] MySQL 5.0 with Ubuntu 8.10 -- possible bug?"
date: 2008-12-08
forum: Server Platforms
---

### Post by Arnitak on 2008-12-08
Hi, I've got a problem with the MySQL Configuration. I got a router which connects itself to the internet and shares with 3 pc's. Each one has a 192.x.x.x address. I configured my MySQL server to be bound on 192.168.1.100 as this is my server. I use the box for development. The trouble is, that with no firewall, no nothing, with the network wide open I get the error:

ERROR 1130 (00000): Host '192.168.1.101' is not allowed to connect to this MySQL server

The configuration file is ok, the firewall is wide open, no trouble at all on this part. What am I doing wrong?

---

### Post by lykwydchykyn on 2008-12-08
can you post your /etc/mysql/my.cnf?  That might provide some clues.
Also /var/log/mysql.err and /var/log/mysql.log from the server.

---

### Post by Arnitak on 2008-12-08
> **lykwydchykyn said:**
> can you post your /etc/mysql/my.cnf?  That might provide some clues.
Also /var/log/mysql.err and /var/log/mysql.log from the server.

mysql.err and mysql.log are completly empty.

This is the my.cnf

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
bind-address		= 192.168.1.100
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover		= BACKUP
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
# * Federated
#
# The FEDERATED storage engine is disabled since 5.0.67 by default in the .cnf files
# shipped with MySQL distributions (my-huge.cnf, my-medium.cnf, and so forth).
#
skip-federated
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
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/
```

---

### Post by cdenley on 2008-12-08
That is the error you get if you have not granted the user to connect from that computer to that database. This lets you connect to a database from anywhere, which I don't recommend.
```

grant all on <mydb>.* to '<myuser>'@'%' identified by '<mypassword>';

```
By default, root can only connect locally, which is the way it should be.

---

### Post by Arnitak on 2008-12-08
> **cdenley said:**
> That is the error you get if you have not granted the user to connect from that computer to that database. This lets you connect to a database from anywhere, which I don't recommend.
```

grant all on <mydb>.* to '<myuser>'@'%' identified by '<mypassword>';

```
By default, root can only connect locally, which is the way it should be.

Thanks, it worked, if I change my mind, how can I revoke the privileges?

---

### Post by cdenley on 2008-12-08
> **Arnitak said:**
> Thanks, it worked, if I change my mind, how can I revoke the privileges?

[http://dev.mysql.com/doc/refman/5.1/en/revoke.html](http://dev.mysql.com/doc/refman/5.1/en/revoke.html)

---

### Post by Arnitak on 2008-12-08
> **cdenley said:**
> [http://dev.mysql.com/doc/refman/5.1/en/revoke.html](http://dev.mysql.com/doc/refman/5.1/en/revoke.html)

Actually, I think I did something wrong. I wrote : 

revoke all on mysql.* from 'root'@'%'; 

However, I still CAN connect from other hosts ... however when I access the user information, it tells me I cannot retrieve it :(

---

### Post by cdenley on 2008-12-08
> **Arnitak said:**
> Actually, I think I did something wrong. I wrote : 

revoke all on mysql.* from 'root'@'%'; 

However, I still CAN connect from other hosts ... however when I access the user information, it tells me I cannot retrieve it :(

Try this
```

REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'root'@'%';

```

---

### Post by Arnitak on 2008-12-08
> **cdenley said:**
> Try this
```

REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'root'@'%';

```

Nope, I can still connect from a remote host, plus I cannot access the user panel.

---

### Post by cdenley on 2008-12-08
```

DROP USER 'root'@'%';

```
user panel?

---

### Post by Arnitak on 2008-12-08
> **cdenley said:**
> ```

DROP USER 'root'@'%';

```
user panel?

Well, the user panel is in the GUI I use to connect from my other PC. But if I drop the user root, how could I log in as administrator?

---

### Post by cdenley on 2008-12-08
> **Arnitak said:**
> Well, the user panel is in the GUI I use to connect from my other PC. But if I drop the user root, how could I log in as administrator?

That would drop the user 'root'@'%'. The user 'root'@'localhost' would still work. At least it did for me.

---

### Post by Arnitak on 2008-12-08
> **cdenley said:**
> That would drop the user 'root'@'%'. The user 'root'@'localhost' would still work. At least it did for me.

Thanks, it worked!

---

