---
title: "server 12.04 can't connect to MySQL"
date: 2013-02-04
forum: Server Platforms
---

### Post by bart.a on 2013-02-04
Hi..

Before my main board started smoking my (very simple) file server (Ubuntu 12.04 also) with MySQL support was running just fine.. I used it as a file server for a couple of workstations and had MySQL server running for a few simple databases.. I used to connect to the databases with LibreOffice Base via the java connector and that all worked fine.. BUT..

Now I re installed all of the above on my new hardware and everything works. I can see, manage and do everything with the databases via phpmyadmin (from a workstation).
But I cannot get the connection between LibreOffice and MySQL and I can't find what I'm doing wrong..

It gives me the same error over and over: SQL-status: 08S01 Communications link failure.

I tried disabling the firewall on both machines, no success.
The cause could be that I installed "mysql_secure_installation" after my install but I don't know how to undo it.. Re-installing did not even remove my databases so that's an issue..

Can anyone please help me? I'm lost.. Thanks..

---

### Post by volkswagner on 2013-02-04
Your user needs to have access from the LAN.

Check your user database to see where the user in question is allowed to connect from.  You may need to modify the host field for the user or add the user again with the specific host.

```
mysql -u root -p
```
```
mysql> use mysql;
```
```
mysql> select host, user from user;
```

If you only have localhost configured this could be the problem.  This is assuming you are trying to connect to mysql from a remote machine (LibreOffice is not running on the server).

---

### Post by Cheesemill on 2013-02-04
Also by default MySQL doesn't allow external connections.

To enable connections from other machines you need to edit /etc/mysql/my.conf and comment out the bind-address line so it looks like...
```
#bind-address = 127.0.0.1
```

Restart mysql and you should be good to go.

---

### Post by bart.a on 2013-02-04
Thanks for your reply Volkswagner and Cheesemill..

my /etc/mysql/my.cnf file did not have the bind-address commented out.. but I believe it was in my first 100 tries.. I changed it now. I'll test it tomorrow morning..
edit: I tested it, no success, still the same error.. It just doesn't seem to connect..

I looked at my mysql users all users have access to the databases from there own (static) IP-address and from the range all address are in, so that shouldn't be the problem..

Output:
```

mysql> SELECT host, user FROM user;

+--------------+------------------+
| host         | user             |
+--------------+------------------+
| 127.0.0.1    | root             |
| 192.168.1.%  | usr1             |
| 192.168.1.%  | usr2             |
| 192.168.1.%  | usr3             |
| 192.168.1.71 | usr2             |
| 192.168.1.72 | usr1             |
| ::1          | root             |
| fileServer   |                  |
| fileServer   | root             |
| localhost    |                  |
| localhost    | usr1             |
| localhost    | debian-sys-maint |
| localhost    | phpmyadmin       |
| localhost    | root             |
| localhost    | usr3             |
+--------------+------------------+

```

I also exported the CLASSPATH by putting it in my .bashrc file
```

CLASSPATH=$CLASSPATH:/usr/share/java/mysql-connector-java.jar
export CLASSPATH

```

---

### Post by bart.a on 2013-02-05
Hi..

I think I have problems with my MySQL connections because I installed "mysql_secure_installation" after my install.. Re-installing did not even remove my databases so that's an issue..

I would like to undo the "mysql_secure_installation" so I can test if my connections can be made.. But I don't know how to do that..

Can anyone please help me? I'm lost.. Thanks..

---

### Post by spynappels on 2013-02-05
Hi Bart,

I don't think that the mysql_secure_installation has anything to do with this, it is just a script which carries out 4 different functions:
[LIST=1]
[*]Set a root password for mysql
[*]Remove anonymous users
[*]Limit root login to localhost only
[*]Remove the test database
[/LIST]

So to answer your question in another thread, you don't "uninstall" it as such, although you can undo each of the above actions individually. However, I'm really not convinced that these are the casue of your problems.

Have you checked your firewall rules?

---

### Post by spynappels on 2013-02-05
Hi Bart,

I answered this question in your other thread, but to summarise, the mysql_secure_installation script is not installed, it carries out 4 specific functions which can be undone individually if required. However, I don't think this is causing your issues. 

I'll try and help out in the other thread.

Regards,
Stefan

---

### Post by howefield on 2013-02-05
Threads merged.

---

### Post by bart.a on 2013-02-05
Hi spynappels thanks for your reply..

> **spynappels said:**
> 
Have you checked your firewall rules?


ufw allows all relevant ip-addresses for apache and port 3306.. 

Just to be sure I tried it again.. I disabled ufw, stopped windows firewall completely and stopped virus scanner..
But still the same error..

Have you got another suggestion? I really don't know what to do next

---

### Post by spynappels on 2013-02-05
Ok, let's go back to the beginning. After you re-installed, you did not run the mysql_secure_install script again,  because there are still anonymous users. Are these anonymous connections required? If not, I'd get rid of them. Have you also set a password for root and all other users?

Are user1 etc running on Ubuntu as well? If they are, I'd check if you can access the MySQL DB from a cli mysql client on that user's machine. This will check whether access to the db works from other hosts for specific users.

From user1's machine, do the following:
```
mysql -u user1 -h 192.168.1.xx -p
```
where the IP address is that of the server.

If this works correctly, the issue is more likely to be with the Java connector.

---

### Post by Cheesemill on 2013-02-05
Can you check if mysql is actually listening for connections on port 3306...
```
netstat -anp | grep -i mysql
```

---

### Post by The Cog on 2013-02-05
I don't think that will show anything unless run with sudo because listing process names is privileged. Can I suggest this command:
```
netstat -lnt
```
and look for port 3306. It should be listening on 0.0.0.0, not 127.0.0.1.

After changing mysql.conf, you need to restart the mysql service for the change to take effect.

---

### Post by bart.a on 2013-02-05
Unfortunately I need to connect from a windows machine, I could test it from an ubuntu machine though, but I don't have it here now.. 

Output for netstat -anp | grep -i mysql

```

tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      7695/mysqld
unix  2      [ ACC ]     STREAM     LISTENING     19040    7695/mysqld         /var/run/mysqld/mysqld.sock

```

Output for netstat -lnt

```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:1105            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp6       0      0 :::1105                 :::*                    LISTEN

```

I have tried connecting via LibreOffice directly using the openoffice mysql-connector but that doesn't connect either..

---

### Post by Cheesemill on 2013-02-05
> **bart.a said:**
> ```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
[COLOR=Red] tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN[/COLOR]
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:1105            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp6       0      0 :::1105                 :::*                    LISTEN

```
 
This line seems to say that mysql is only listening on localhost.

Can you post the contents of your /etc/mysql/my.cnf please.

---

### Post by bart.a on 2013-02-05
Output /etc/mysql/my.cnf

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
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
lc-messages-dir = /usr/share/mysql
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
# bind-address          = 127.0.0.1
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
#
# Error logging goes to syslog due to /etc/mysql/conf.d/mysqld_safe_syslog.cnf.
#
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

```

---

### Post by bart.a on 2013-02-05
PROBLEM SOLVED!!

Thanks guys for all your efforts and pointing me in the right direction! I really appreciate it!

The bind-address in my.cnf was just commented out..
I removed the comment and set the bind-address to the servers (static) IP-address..

Now I can connect to the dbases from LibreOffice out of every workstation like before..

Thanks again for your efforts!!

---

### Post by Cheesemill on 2013-02-05
How strange.

The default behaviour if bind-address is commented out is to listen on ***all*** available interfaces.

This is why I suggested it as a solution in my first post.

---

### Post by spynappels on 2013-02-05
Binding mysqld to the 192.168.1.x address may have some unexpected consequences....

Anything requiring a localhost connection, like phpmyadmin or the debian syst maintenance user will not be able to connect unless they use the Unix socket.

You could change the bind-address to 0.0.0.0 to listen on all interfaces.

---

### Post by bart.a on 2013-02-05
I tried it and phpmyadmin and libreoffice both connect just fine with the bind-address set to either the servers IP-address or 0.0.0.0

So the best option would be to set the bind-address to 0.0.0.0 , right?

---

### Post by spynappels on 2013-02-05
> **bart.a said:**
> I tried it and phpmyadmin and libreoffice both connect just fine with the bind-address set to either the servers IP-address or 0.0.0.0

So the best option would be to set the bind-address to 0.0.0.0 , right?

It will definitely mean that mysql will be listening on all interfaces, yes.

---

