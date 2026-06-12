---
title: "mysqld.pid file error on Ubuntu 8.04.4 LTS"
date: 2010-02-04
forum: Server Platforms
---

### Post by carvjo on 2010-02-04
Hi I'm a real amateur - so please be gentle with me..

I'm running Ubuntu 8.04.4 LTS to host a moodle server in a school..

moodle is running OK - but I'm having problems with MySql

Any mysql command generates:

unknown variable 'pid-file=/var/run/mysqld/mysqld.pid'

I've taken a look in unknown variable 'pid-file=/var/run/mysqld/ and there is no mysqld.pid file

I have followed these instructions that I found elsewhere:

----------------------------------------------------
If there’s no mysqld.pid inside /var/run/mysqld directory, create mysqld.pid

# cd /var/run/mysqld

# touch mysqld.pid

Assign chown to a mysqld.pid file
# chown -R mysql:mysql mysqld.pid
Why do we assign mysql:mysql to the file?
Because the warning shows –user=mysql

Assign chmod to a mysqld.pid file
# chmod g=rw mysqld.pid
# chmod o= mysqld.pid

It changes permission to a format : -rw-rw----

Assign chown to the directory, /var/run/mysqld. Why? because the owner permission for this directory isn’t mysql.
# chown mysql:mysql /var/run/mysqld

Restart Server
# reboot


--------------------------------------------------------------------

But after reboot the mysqld.pid file is missing again..

I can access mysql via phpmyadmin - but webmin fails with

unknown variable 'pid-file=/var/run/mysqld/mysqld.pid'

Can anyone help with a nice simple to follow recipe how I might solve this..?

Many thanks

John

---

### Post by terazen on 2010-02-04
From the terminal try this command:```
ps -eaf | grep mysqld | grep pid
```

If mysql is running it will say --pid-file=blah in there somewhere.  Whatever blah says is where your pidfile should be.

If mysql isn't running you have another problem.

---

### Post by carvjo on 2010-02-04
aha.. thanks..

--pid-file=/var/lib/mysql/moodle.pid

So I take it I update my my.cnf file with that - and all will be well?

Regards

John

full output of that command

root@moodle:~# ps -eaf | grep mysqld | grep pid
mysql     4434  4409  0 13:19 ?        00:00:15 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/lib/mysql/moodle.pid --skip-external-locking --socket=/var/run/mysqld/mysqld.sock
root@moodle:~# --pid-file=/var/lib/mysql/moodle.pid

---

### Post by terazen on 2010-02-04
Does your my.cnf say something other than /var/run/mysqld/mysqld.pid?  Sure, change it and see if that helps or not.

---

### Post by carvjo on 2010-02-04
Many thanks for your help..

Ok - I edited the my.cnf file

I changed the location of the pid file to:

user        = mysql
pid-file    = /var/lib/mysql/moodle.pid
socket        = /var/run/mysqld/mysqld.sock

After a reboot - mysql starts - but if I try to acces it from my putty console I still get:

 unknown variable 'pid-file=/var/lib/mysql/moodle.pid'

Is there anything else I should do.. (I told you I am an amateur!)

Regards

John

---

### Post by cdenley on 2010-02-04
Post this output.
```

grep "^[^#]" /etc/mysql/my.cnf

```
I suspect you have two pid-file variables, one in the client section and one in the mysqld section. I don't think it belongs in the client section.

---

### Post by carvjo on 2010-02-04
Thank you for your help - here is the output from that command:

root@moodle:~# grep "^[^#]" /etc/mysql/my.cnf
[client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock
[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0
[mysqld]
default-character-set=utf8
default-collation=utf8_general_ci
character-set-server=utf8
collation-server=utf8_general_ci
init-connect='SET NAMES utf8'

[client]
default-character-set=utf8
user            = mysql
pid-file        = /var/lib/mysql/moodle.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
language        = /usr/share/mysql/english
skip-external-locking
bind-address            = 127.0.0.1
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 128K
thread_cache_size       = 8
query_cache_limit       = 1M
query_cache_size        = 16M
expire_logs_days        = 10
max_binlog_size         = 100M
skip-bdb
[mysqldump]
quick
quote-names
max_allowed_packet      = 16M
[mysql]
[isamchk]
key_buffer              = 16M
!includedir /etc/mysql/conf.d/
root@moodle:~#


Does that help?

Thanks again

John

---

### Post by cdenley on 2010-02-04
> **carvjo said:**
> 
```

[client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock
[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0
[mysqld]
default-character-set=utf8
default-collation=utf8_general_ci
character-set-server=utf8
collation-server=utf8_general_ci
init-connect='SET NAMES utf8'

**[COLOR="Red"][client][/COLOR]**
default-character-set=utf8
user            = mysql
[COLOR="Red"]**pid-file        = /var/lib/mysql/moodle.pid**[/COLOR]
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
language        = /usr/share/mysql/english
skip-external-locking
bind-address            = 127.0.0.1
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 128K
thread_cache_size       = 8
query_cache_limit       = 1M
query_cache_size        = 16M
expire_logs_days        = 10
max_binlog_size         = 100M
skip-bdb
[mysqldump]
quick
quote-names
max_allowed_packet      = 16M
[mysql]
[isamchk]
key_buffer              = 16M
!includedir /etc/mysql/conf.d/

```

Yes, that confirms my suspicion. You have a whole 2nd "client" section in my.cnf which appears to have server-specific options set. That looks nothing like a default configuration. Maybe you can try removing the 2nd "[client]", or start from scratch with the default my.cnf.
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

```
By the way, "CODE" tags make it easier to read command output.

---

### Post by carvjo on 2010-02-04
You are a genius - that solved it on my cloned server - so I've applied it to the production machine.. 

Thanks very much.. I owe you..

John

---

