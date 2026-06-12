---
title: "Mysql Error"
date: 2011-12-30
forum: Server Platforms
---

### Post by maverickaddicted on 2011-12-30
Hello,

I am getting these error message when trying to access a simple script

Could not connect to database...Lost connection to MySQL server at 'reading initial communication packet', system error: 111

---

### Post by rubylaser on 2011-12-30
The error message is telling you the problem :)  Your script can't connect to the database.  You either provided the wrong username/password, haven't setup MySQL up to allow your host, or if you're making the query from a different machine, comment out the bind_address in your /etc/mysql/my.cnf file.  Have you tried to connect with the same credentials with the mysqlclient?
```
mysql -u <user> -p -h <ip_address_of_mysql_host>
```

---

### Post by maverickaddicted on 2011-12-31
I am trying to access the script from the client machine. The script is located at server. The username, password and hostname are correct. Now here is the new twist, if I use localhost as hostname, the script works perfectly. However, if I use "openserver" as hostname, then that previous error shows up.

---

### Post by rubylaser on 2011-12-31
That means, you need to allow that remote computer to connect.  If it has a static ip, you can allow it like this from the mysql console. 

```
GRANT ALL PRIVILEGES ON *.* TO 'user'@'remote_ip_address' IDENTIFIED BY 'Password' WITH GRANT OPTION;
FLUSH PRIVILEGES;
exit;
```

Does the openserver hostname resolve properly from your remote host?

---

### Post by SeijiSensei on 2011-12-31
> **maverickaddicted said:**
> I am trying to access the script from the client machine. The script is located at server. The username, password and hostname are correct. Now here is the new twist, if I use localhost as hostname, the script works perfectly. However, if I use "openserver" as hostname, then that previous error shows up.

Along with rubylaser's suggestions, another possibility is that the MySQL server is bound to the localhost interface.  (For security reasons, that's the default in Ubuntu.) Take a look at the my.cnf file and see what "bind-address" is set to.

---

### Post by maverickaddicted on 2012-01-02
> **rubylaser said:**
> That means, you need to allow that remote computer to connect.  If it has a static ip, you can allow it like this from the mysql console. 

```
GRANT ALL PRIVILEGES ON *.* TO 'user'@'remote_ip_address' IDENTIFIED BY 'Password' WITH GRANT OPTION;
FLUSH PRIVILEGES;
exit;
```

Does the openserver hostname resolve properly from your remote host?

I am trying to access server from LAN, therefore I do not have any specific IP of remote computer.

---

### Post by maverickaddicted on 2012-01-02
My my.cnf file is - 

```

serveradmin@openserver:~$ cat /etc/mysql/my.cnf 
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
bind-address            = 192.168.1.5
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

```

I have manually set the bind address to 192.168.1.5, previously it was 127.0.0.1.

---

### Post by maverickaddicted on 2012-01-04
What to do next?

---

### Post by rubylaser on 2012-01-04
Just comment out the bind-address for now and restart mysql.  Then try to connect from the remote box with the root account.  If that works, try with your regular user.  If that fails, you're down to a user privileges problem, and you'll need to allow the user access to the database as I showed before.

---

### Post by maverickaddicted on 2012-01-04
> **rubylaser said:**
> Just comment out the bind-address for now and restart mysql.  Then try to connect from the remote box with the root account.  If that works, try with your regular user.  If that fails, you're down to a user privileges problem, and you'll need to allow the user access to the database as I showed before.

Thank You very much, commenting the bind-address line solved my issue.

---

### Post by rubylaser on 2012-01-04
No problem, glad you got it working.

---

