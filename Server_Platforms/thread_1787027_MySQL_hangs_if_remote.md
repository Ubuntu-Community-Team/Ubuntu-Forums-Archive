---
title: "MySQL hangs if remote"
date: 2011-06-20
forum: Server Platforms
---

### Post by lingenthron on 2011-06-20
I'm having an issue where, when I try to enable remote access to mysql by setting the bind address to my external IP and ensuring skip-networking is not present, on trying to start the service, the console hangs on an empty line.  As far as I know, the service is never started.

All I can do now is disable the remote access and reboot the box, but I need that remote access.

I'm not too experienced with Linux, but the service works just fine when the bind address is 127.0.0.1.  The server is already serving HTTP, so it's not a networking issue.  And the port is forwarded properly.

Using:
Ubuntu Server 11.04
mysql server 5.1

---

### Post by lingenthron on 2011-06-20
Okay, so if I let the box restart or try to start the service in two TTYs at the same time, it starts.  But then I can't connect from anywhere, even localhost, because it says:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'
Which makes sense because that file doesn't exist.  It seems to usually be created by mysql on startup.  Touching to create the file (and opening up permissions/fixing owners, etc) doesn't work.

I've got to get this resolved soon and am banging my head on the wall now because I can't find any resources on the web for this and can't think of any way to fix it.... Help!

---

### Post by ruffEdgz on 2011-06-20
Was curious about your my.cnf file that can be found here:
```

/etc/mysql/my.cnf

```
Can you take the information from that and place it into your next post?

Cheers!

---

### Post by lingenthron on 2011-06-20
Thanks for the reply!  I believe everything is still at default.  Again, the only change I make to this to cause the problem is changing the bindaddress from the loopback to my external ip.  Also, the additional include file path referenced at the bottom does not exist, so this should be the sole config...

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
port        = 3306
socket        = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket        = /var/run/mysqld/mysqld.sock
nice        = 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user        = mysql
socket        = /var/run/mysqld/mysqld.sock
port        = 3306
basedir        = /usr
datadir        = /var/lib/mysql
tmpdir        = /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address        = 127.0.0.1
#
# * Fine Tuning
#
key_buffer        = 16M
max_allowed_packet    = 16M
thread_stack        = 192K
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
query_cache_limit    = 1M
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
#log_slow_queries    = /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id        = 1
#log_bin            = /var/log/mysql/mysql-bin.log
expire_logs_days    = 10
max_binlog_size         = 100M
#binlog_do_db        = include_database_name
#binlog_ignore_db    = include_database_name
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
max_allowed_packet    = 16M

[mysql]
#no-auto-rehash    # faster start of mysql but no tab completition

[isamchk]
key_buffer        = 16M

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/

---

### Post by ruffEdgz on 2011-06-20
I noticed that you still use the default location for error logs, what do those say:
```

/var/log/mysql/error.log

```
Also, is there a reason to why you need to have your 'bind-address' to be your external IP? Localhost works the best and I don't know many who change that part of their configuration file.

Cheers!

---

### Post by lingenthron on 2011-06-21
So, I did find a generic error there with the binding:
> 110621  9:43:47 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
110621  9:43:47 [ERROR] Do you already have another mysqld server running on port: 3306 ?
110621  9:43:47 [ERROR] Aborting

Checking netstat, I have nothing on port 3306 before or after I try to start the server, so I don't know why it can't bind...

I'm changing the bind address because I want to be able to connect to MySQL server remotely and, as I understand it, that's all you have to do other than updating the user host permissions.

Thanks for your help thus far

---

### Post by ruffEdgz on 2011-06-21
So, make sure you turn off your mysql service first before running the commands below to verify that certain 'things' aren't actually causing you this problem:

Lets check if the port 3306 is being used:
```

sudo nmap localhost | grep 3306

```
If nothing shows up, then we know it isn't being used while the mysql service is running
*** If you don't have this, install it 'sudo apt-get install nmap'**

Now lets make sure the mysqld process isn't running:
```

ps aux | grep mysql | grep -v grep

```
If this doesn't return anything, then we can say that another mysqld isn't running at the same exact time.

If you don't get anything from the above code, lets try using a different port for mysql:

[list]
[*]Open up the file /etc/mysql/my.cnf
[*]Find the line 'port            = 3306'
[*]Change it so it says 'port            = 3307'
[*]Save file
[*]Start or restart mysql service
[*]Check logs for any errors
[*]Check nmap or netstat
[*]Report back to this post with your findings
[/list]

Cheers!

---

### Post by lingenthron on 2011-06-21
Okay, so:
When I do not explicitly have it running, both tests you provided returned nothing.
Changing the port had no change.
I tried using my internal IP and it did at least start up. Attempted tp connect via command line from another pc on the network and it couldn't open a named pipe to the host.  So the remote networking still isn't working, even internally.
So far, it will bind to: 0.0.0.0, 127.0.0.1, 192.168.1.100 (static internal IP)

However, running nmap while it's on, I get:
> mysql    12415    0.3    5.2    138436    26300 ?     Ssl 14:25 0:01 /usr/sbin/mysqld
I don't remember setting up SSL for mysql... I do have it running for apache2 though.  Could that be related?

---

### Post by lingenthron on 2011-06-22
Well, now I'm working on writing a C++ wrapper just to overcome this roadbump.  Hate to say it, but it looks like the score is 10 seconds: Windows, 3 Days and custom code: Ubuntu.  Thought it was supposed to be the other way around...

---

