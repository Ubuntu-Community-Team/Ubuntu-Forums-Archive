---
title: "MYSQl Problems"
date: 2012-01-04
forum: Server Platforms
---

### Post by firedragoneater on 2012-01-04
Hi,
I've been playing around with mysql attempting to get it to work. It won't currently accept a password, I've tried various tutorial on resetting the password, but with no luck. It seems to have all started to happen after I followed this tutorial - [http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html](http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html)

I have changed my.cnf back to it's original settings, but still no luck.

I'd really appreciate any help that you can give.

Many thanks,
Jordan

---

### Post by rubylaser on 2012-01-04
Are you saying that you're unable to log in as root from the MySQL host machine?  Local access should not have been effected by this tutorial.  If the problem is from a remote host, then there are many potential ways that it went awry.

Can you paste in your my.cnf file?
```
cat /etc/mysql/my.cnf
```
Also, your current iptables
```
iptables -L
```

And if you can log in from the local machine, can you connect to the mysql console and run these?
```
mysql -u root -p
```
```
SELECT * FROM `information_schema`.`USER_PRIVILEGES`;
```
```
SELECT * FROM `information_schema`.`SCHEMA_PRIVILEGES`;
```

---

### Post by firedragoneater on 2012-01-05
Hi,
thanks for the reply I cannot login to MYSQL so I cannot get some of the information that you required but I have managed to get some of it.



My.cnf:

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
port            = 3306
socket          = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user            = mysql
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 192.168.1.9
#
# * Fine Tuning
#
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 192K
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
query_cache_limit       = 1M
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
#log_slow_queries       = /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id              = 1
#log_bin                        = /var/log/mysql/mysql-bin.log
expire_logs_days        = 10
max_binlog_size         = 100M
#binlog_do_db           = include_database_name
#binlog_ignore_db       = include_database_name
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
max_allowed_packet      = 16M

[mysql]
#no-auto-rehash # faster start of mysql but no tab completition

[isamchk]
key_buffer              = 16M

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/



iptables:


Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


Thanks for your help,
Jordan

---

### Post by rubylaser on 2012-01-05
Okay, the first thing you'll want to do is to recover your MySQL root user password.  [These directions]("http://www.cyberciti.biz/tips/recover-mysql-root-password.html") are simple and work well for that.  Everything else looks fine.

---

### Post by firedragoneater on 2012-01-05
Hi,
I've tried that and stuck to what they have said to the dot. However, it hasn't worked. It still thinks that my password is incorrect, even after I have just changed it!

It did appear that the password was successfully changed though. It just wouldn't let me login...

---

### Post by rubylaser on 2012-01-05
> **firedragoneater said:**
> Hi,
I've tried that and stuck to what they have said to the dot. However, it hasn't worked. It still thinks that my password is incorrect, even after I have just changed it!

It did appear that the password was successfully changed though. It just wouldn't let me login...

These steps are the best way to do this and I just confirmed that they work from 10.04 LTS - 11.10.  I'm guessing, you're missing something.  Can you try the steps again via SSH, and copy and paste exactly what they have other than just replacing the password?

---

### Post by firedragoneater on 2012-01-08
Hi,
I am using 10.04 LTS and I have tried this twice again, copying and pasting as you said, and still no luck!!

Thanks for your help,
Jordan

---

### Post by rubylaser on 2012-01-08
Well, that's certainly strange.  If you don't have anything in your databases, or if you've backed them up, you could just completely remove MySQL and start over.

```
sudo apt-get --purge remove mysql-server mysql-common mysql-client libmysqlclient15-dev
```

```
sudo apt-get install mysql-server mysql-client
```

---

### Post by firedragoneater on 2012-01-09
Hi,
thanks for the reply, however, it requires a mysql password to purge the Mysql.

Thanks again,
Jordan

---

### Post by catalin.vasilescu on 2012-01-09
**MYSQL optimisation problems**

Hello,
I recently reinstalled a server wich hosts a mysql server with a large database used by an web application.
Installation was a succes,all work fine but the application it takes to much to access the database.
My server it has an intel xeon 4 cores and 12 gb ram. i use ubuntu server 11.04 64bit.
Here is my.cnf :
> 
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
port            = 3306
socket          = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0

[mysqld]
#
# * Basic Settings
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user            = mysql
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
skip-external-locking
skip-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
#bind-address           = 127.0.0.1
#
# * Fine Tuning
#
#key_buffer = 1024M
key_buffer = 384M

max_allowed_packet = 1M
thread_stack            = 192K
thread_cache_size       = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover         = BACKUP
max_connections        = 400

table_cache = 512
#table_cache = 1024
sort_buffer_size = 16M
read_buffer_size = 16M
read_rnd_buffer_size = 32M
myisam_sort_buffer_size = 2G
thread_cache_size = 256
thread_concurrency     = 8
innodb_flush_log_at_trx_commit=1
set-variable=max_allowed_packet=16M
sync_binlog=1
skip-federated
#
# * Query Cache Configuration
#
query_cache_limit       = 512M
query_cache_size = 512M
#
# * Logging and Replication
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file        = /var/log/mysql/mysql.log
#general_log             = 1

log_error                = /var/log/mysql/error.log

# Here you can see queries with especially long duration
#log_slow_queries       = /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id              = 1
#log_bin                        = /var/log/mysql/mysql-bin.log
# Here you can see queries with especially long duration
#log_slow_queries       = /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id              = 1
#log_bin                        = /var/log/mysql/mysql-bin.log
log-bin=mysql-bin
expire_logs_days        = 10
max_binlog_size         = 100M
#binlog_do_db           = include_database_name
#binlog_ignore_db       = include_database_name
#
# * InnoDB
#

innodb_buffer_pool_size = 10G
innodb_additional_mem_pool_size = 50M

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
max_allowed_packet = 16M

[mysql]
no-auto-rehash  # faster start of mysql but no tab completition

[isamchk]
key_buffer = 256M
sort_buffer_size = 256M
read_buffer = 2M
write_buffer = 2M

[myisamchk]
key_buffer = 256M
sort_buffer_size = 256M
read_buffer = 2M
write_buffer = 2M

[mysqlhotcopy]
interactive-timeout

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
!includedir /etc/mysql/conf.d/


I think im missing something but i cant figured out.
Thank you.

---

### Post by SeijiSensei on 2012-01-09
If the problem is that it takes too long to retrieve query results, you probably haven't built the right indexes.  Use the mysql client program to run the queries in the webapp from the command line and see which take excessively long to complete.  

SQL performance problems usually indicate a problem with the database logic more than a problem with the hardware or server software.

I don't use MySQL enough to know if it has an equivalent to PostgreSQL's ANALYZE command, but if so, that might provide some insights.

---

### Post by firedragoneater on 2012-02-26
Hi, I still haven't fixed this. Are there any more suggestions?

---

### Post by rubylaser on 2012-02-26
Try to use MySQL's EXPLAIN command to see what's slowing your query down.  This will be a good way to see if you have all of your foreign keys indexed (assuming it's a normalized database).

---

### Post by firedragoneater on 2012-02-26
I'm locked out of Mysql though. Also, I have changed the password but it reverts straight back to error 1042.

---

### Post by rubylaser on 2012-02-26
The only way to correct that is to reset the root user's password is I mentioned earlier in the thread.  If you're not able to get that to work, maybe you'll need to do a re-install (although, resetting the password works on all versions of Debian / Ubuntu that I've ever tried, so you should be able to get it working).

---

