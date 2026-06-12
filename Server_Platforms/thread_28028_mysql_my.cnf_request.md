---
title: "mysql my.cnf request"
date: 2005-04-18
forum: Server Platforms
---

### Post by jdodson on 2005-04-18
i know this seems like an odd request, but can someone paste the contents of the /etc/mysql/my.cnf file to this thread.

i did not create a backup before i edited the file(slapping my hand as i speak).  anyways, if anyone could post the contents of that file, i would appreciate it.

---

### Post by alastair on 2005-04-18
Here you go - the only thing of mine is the "datadir" setting :

```
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "/var/lib/mysql/my.cnf" to set server-specific options or
# - "~/.my.cnf" to set user-specific options.
#
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
 
# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
[client]
#password       = my_password
port            = 3306
socket          = /var/run/mysqld/mysqld.sock
 
# Here is entries for some specific programs
# The following values assume you have at least 32M ram
 
# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0
 
[mysqld]
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
# Both location gets rotated by the cronjob.
#log            = /var/log/mysql.log
log             = /var/log/mysql/mysql.log
basedir         = /usr
datadir         = /home/data
tmpdir          = /tmp
language        = /usr/share/mysql/english
skip-external-locking
#
# The skip-networking option will no longer be set via debconf menu.
# You have to manually change it if you want networking i.e. the server
# listening on port 3306. The default is "disable" - for security reasons.
skip-networking
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 128K
#
# Query Cache Configuration
#
query_cache_limit       = 1048576
query_cache_size        = 26214400
query_cache_type        = 1
#
# Here you can see queries with especially long duration
#log-slow-queries       = /var/log/mysql/mysql-slow.log
#
# The following can be used as easy to replay backup logs or for replication
#server-id              = 1
#log-bin                = /var/log/mysql/mysql-bin.log
#binlog-do-db           = include_database_name
#binlog-ignore-db       = include_database_name
#
# Read the manual if you want to enable InnoDB!
skip-innodb
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# If you want to enable SSL support (recommended) read the manual or my
# HOWTO in /usr/share/doc/mysql-server/SSL-MINI-HOWTO.txt
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem
 
 
 
[mysqldump]
quick
quote-names
max_allowed_packet      = 16M
 
[mysql]
#no-auto-rehash # faster start of mysql but no tab completition
 
[isamchk]
key_buffer              = 16M
```

---

### Post by jdodson on 2005-04-18
thanks.  somehow the mysqld process would not start or restart.  a simple reboot and all is well.

i thought i borked the conf, but i guess i did not.  

thanks anyways!

---

