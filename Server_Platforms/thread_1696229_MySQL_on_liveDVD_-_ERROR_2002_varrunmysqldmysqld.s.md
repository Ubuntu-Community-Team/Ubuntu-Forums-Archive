---
title: "MySQL on liveDVD - ERROR 2002 /var/run/mysqld/mysqld.sock"
date: 2011-02-27
forum: Server Platforms
---

### Post by phillips321 on 2011-02-27
Hi guys,

I'm the lead Dev of GnackTrack and we're having issues with running MySQL on the LiveDVD.

Once installed everything works fine, mysql can be connected to but when using the liveDVD we get the following error:
```
root@root:~# mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

Contents of /etc/mysql/my.cf point to /var/run/mysqld/mysqld.sock but because this is a liveDVD the actual file is located in:
/rofs/var/run/mysqld/mysqld.sock
```
root@root:~# updatedb
root@root:~# locate mysqld.sock
/rofs/var/run/mysqld/mysqld.sock
root@root:~# 
```

Any help on this issue would be greatly appreciated as currently live users are not able to use many of the tools that rely on mysql running
```
root@root:~# cat /etc/mysql/my.cnf 
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
root@root:~# 

```

I

---

### Post by t3r0 on 2011-02-27
Use tcp connection instead of unix socket? Or specify  the correct socket path with the -S option? :confused:

---

### Post by phillips321 on 2011-02-27
sorry how would i set mysql to use tcp? basically connect back to 127.0.0.1?

lots of tools automatically connect back to the DB so i dont think it will be possible to modify the socks option as many use this.

---

### Post by t3r0 on 2011-02-27
```
mysql -h127.0.0.1
```

or if your apps use the mysql cli client directly with out any host or socket option you can alias the mysql command to use the -h or -S param by default..

---

### Post by phillips321 on 2011-02-27
```
root@root:~# mysql -h127.0.0.1
ERROR 2003 (HY000): Can't connect to MySQL server on '127.0.0.1' (111)
root@root:~#
```
```
root@root:~# mysql -S /rofs/var/run/mysqld/mysqld.sock 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/rofs/var/run/mysqld/mysqld.sock' (111)
root@root:~# 

```

No joy for either :-(

---

