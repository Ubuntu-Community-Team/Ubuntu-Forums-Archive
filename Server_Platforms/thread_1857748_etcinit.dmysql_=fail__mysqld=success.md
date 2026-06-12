---
title: "/etc/init.d/mysql =fail  mysqld=success"
date: 2011-10-10
forum: Server Platforms
---

### Post by lolinternet on 2011-10-10
Hello, 

When I run /etc/init.d/mysql start sql doesnt run 
```


root@cloneubuntu:/var/log/mysql# date
Mon Oct 10 19:32:56 PDT 2011
root@cloneubuntu:/var/log/mysql# /etc/init.d/mysql start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
start: Job is already running: mysql
root@cloneubuntu:/var/log/mysql# cat /var/log/mysql/error.log

root@cloneubuntu:/var/log/mysql# ps ax | grep sql
 4797 pts/0    S+     0:00 grep --color=auto sql
root@cloneubuntu:/var/log/mysql# cat /etc/mysql/my.cnf
[client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock


[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0

[mysqld]


user            = mysql
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
skip-external-locking
bind-address            = 0.0.0.0
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 192K
thread_cache_size       = 8
myisam-recover         = BACKUP
query_cache_limit       = 1M
query_cache_size        = 16M

log_error                = /var/log/mysql/error.log

expire_logs_days        = 10
max_binlog_size         = 100M



[mysqldump]
quick
quote-names
max_allowed_packet      = 16M

[mysql]

[isamchk]
key_buffer              = 16M

!includedir /etc/mysql/conf.d/

root@cloneubuntu:/var/log/mysql#

```
However when i run mysqld alone, it works
```

root@cloneubuntu:/var/log/mysql# date
Mon Oct 10 19:34:21 PDT 2011
root@cloneubuntu:/var/log/mysql# mysqld &
[1] 4815
root@cloneubuntu:/var/log/mysql# cat /var/log/mysql/error.log

111010 19:34:30 [Note] Plugin 'FEDERATED' is disabled.
111010 19:34:30  InnoDB: Started; log sequence number 0 44233
111010 19:34:30 [Note] Event Scheduler: Loaded 0 events
111010 19:34:30 [Note] mysqld: ready for connections.
Version: '5.1.41-3ubuntu12.10'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
root@cloneubuntu:/var/log/mysql# ps ax | grep sql
 4815 pts/0    Sl     0:00 mysqld
 4830 pts/0    S+     0:00 grep --color=auto sql
root@cloneubuntu:/var/log/mysql# mysql -u root
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.1.41-3ubuntu12.10 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>

```I cannot reinstall mysql, I have a feeling it's an issue with the init.d script or somethign along those lines.

Please help :S

---

### Post by Vegan on 2011-10-10
Batter backup as it appears you have some system problems

Best is to make 2 copies in case the unthinkable happens

---

### Post by pdtpatrick on 2011-10-11
> sudo service mysql stop 

or if it running as mysqld then

> sudo service mysqld stop 

> sudo apt-get --purge mysql 

then reinstall:

> sudo apt-get install mysql-server-5.1

... now prior to starting the server, open another terminal and become root. Then run:

> tail -f syslog.log

now back to the other terminal, run:

> sudo service mysql start 

Check out the error you are getting and proceed from there.

---

### Post by jazzon on 2011-10-11
post redacted because i was totally wrong and didnt want to confuse the issue

---

### Post by karlson on 2011-10-11
> **lolinternet said:**
> Hello, 

When I run /etc/init.d/mysql start sql doesnt run 
```


root@cloneubuntu:/var/log/mysql# date
Mon Oct 10 19:32:56 PDT 2011
root@cloneubuntu:/var/log/mysql# /etc/init.d/mysql start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start


```


First off /etc/init.d/mysql is going the way of the dinosaurs you should do:
```

sudo /usr/sbin/service mysql start

```

You should also check to see if there are any lock files or pid files created by mysql in /var/run.  I don't have the service script in front of me to check by that may be what is reporting the issue.

I'd do this first before trying to whack my installation:
```

$ sudo /usr/sbin/service mysql stop
$ ps -fu mysql
$ ps -ef | grep mysql | grep -v grep

```
at this point you should see no mysql processes running.  If you do terminate with extreme prejudice.
```

$ sudo /bin/rm /var/run/*mysql* /var/run/mysqld/mysqld.sock
$ sudo /usr/sbin/service mysql start

```

It is quite likely that you have messed up the permissions on the files by running mysqld as root(don't do this again. :)), so you could expect additional problems after doing the steps above.

---

