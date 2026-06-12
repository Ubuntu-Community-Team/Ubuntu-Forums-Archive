---
title: "[SOLVED] MySQL --- HELP Needed rather urgently"
date: 2008-04-20
forum: Server Platforms
---

### Post by aceth on 2008-04-20
hey there,
i restarted my ubuntu (gutsy) server today as i moved it downstairs closer to the AP when i turn it on everything seems to be working fine except the mysql server ... i run ...


```
 
sudo /etc/init.d/mysql start

```
and i get the
> 
Starting MySQL database server mysqld [ [COLOR="Red"]FAIL[/COLOR] ]


then i ran ...
```
tail -f /var/log/syslog
```

and then got .... 
> 

Apr 20 20:48:38 hades mysqld[8576]: InnoDB: Some operating system error numbers are described at
Apr 20 20:48:38 hades mysqld[8576]: InnoDB: [http://dev.mysql.com/doc/refman/5.0/en/operating-system-error-codes.html](http://dev.mysql.com/doc/refman/5.0/en/operating-system-error-codes.html)
Apr 20 20:48:38 hades mysqld[8576]: InnoDB: File operation call: 'read'.
Apr 20 20:48:38 hades mysqld[8576]: InnoDB: Cannot continue operation.
Apr 20 20:48:38 hades mysqld_safe[8582]: ended
Apr 20 20:48:53 hades /etc/init.d/mysql[8717]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Apr 20 20:48:53 hades /etc/init.d/mysql[8717]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Apr 20 20:48:53 hades /etc/init.d/mysql[8717]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Apr 20 20:48:53 hades /etc/init.d/mysql[8717]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Apr 20 20:48:53 hades /etc/init.d/mysql[8717]: 


any ideas what i could do to fix it ? 
Thanks

---

### Post by Rinzwind on 2008-04-20
- Check the bind-address in my.conf

- Check with```

ps aux | grep mysqld

``` whether the daemon actually isn't running.

- Anything inside?
/var/log/mysql.err
/var/log/myslq.log

- did you edit /etc/network/interfaces?
You can get this error if you did something wrong with 'lo' in /etc/network/interfaces.

- Try
```
netstat -tulnp | grep 3306
```
to see if anything is running here.
Should be something like this:```
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      5547/mysqld   
```


and 1 more!

- Check if  '/var/run/mysqld/mysqld.sock'  exists.
a ```

ls -l /var/run/mysqld/
``` should return this:
-rw-rw---- 1 mysql mysql 5 2008-04-20 19:37 mysqld.pid
srwxrwxrwx 1 mysql mysql 0 2008-04-20 19:37 mysqld.sock

---

### Post by aceth on 2008-04-20
Contents of the my.cnf ....
> #
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
bind-address		= 127.0.0.1
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





```
ps aux | grep mysqld
```

produces ...

> ace       9467  0.0  0.2   1760   528 pts/0    R+   22:38   0:00 grep mysqld



Nope theres nothing in ...
/var/log/mysql.err
/var/log/myslq.log


/etc/network/interfaces containts (lo bit) ....
> 
auto lo
iface lo inet loopback




```
netstat -tulnp | grep 3306
```

doesnt produce anything (even with sudo)

Nothing in ..
/var/run/mysqld/mysqld.sock

????

---

### Post by aceth on 2008-04-20
ok the mysql server seems to be running ok now all i did was delete ...


```

sudo rm /var/lib/mysql/ib*

```


and restart the mysql server by 

```

sudo /etc/init.d/mysql start

``` 

and hey presto it worked :)
thanks for all the help i was given ;D

---

