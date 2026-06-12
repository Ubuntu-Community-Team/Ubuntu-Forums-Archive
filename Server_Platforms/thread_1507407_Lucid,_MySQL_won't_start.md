---
title: "Lucid, MySQL won't start"
date: 2010-06-11
forum: Server Platforms
---

### Post by Gweniviere on 2010-06-11
I have installed Lucid 4 times now (3 as server, 1 as desktop) and I can not get mysql to run after a reboot. Whenever I try to run it using /etc/init.d/mysql start/restart or start mysql it just hangs there. If I CTRL-C out of the script and try to start it again it says it's already running. A quick ps aux will show that that is not true though.

I am getting no results in /var/log/mysql/error.log to help identify what the problem is. I have restored the original my.conf file and this does not help either.

Here is my current my.cnf 

```
gwen@monster:~$ cat /etc/mysql/my.cnf
[client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock

[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0

[mysqld]

sort_buffer_size        = 512M
key_buffer_size         = 1024M

user            = mysql
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
skip-external-locking
bind-address            = 192.168.1.28
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 192K
thread_cache_size       = 8
myisam-recover         = BACKUP
max_connections        = 100
table_cache            = 64
thread_concurrency     = 4
query_cache_limit       = 1M
query_cache_size        = 16M
general_log_file        = /var/log/mysql/mysql.log
general_log             = 1

log_error                = /var/log/mysql/error.log
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
[isamchk]
key_buffer              = 16M
!includedir /etc/mysql/conf.d/
```

---

### Post by dapperdanny77 on 2010-06-11
hi,


- mysql don't start in any of your installations ?
-  is this a clean installation without any changes?
- /var/log/mysql/error.log  is empty?
- df /var/lib/mysql  shows a value <100% ?


cheers
dapperdan

---

### Post by cdenley on 2010-06-11
I'm not sure if this is related to your problem, but in 10.04, with the default upstart script, mysql would attempt to start after any network adapter (lo) was brought up. This would cause it to attempt and fail to bind to 192.168.1.28 after a reboot. Try commenting out the "bind-address" part then reboot, since that interface is brought up after lo.

---

