---
title: "MySQL eating all of my Memory"
date: 2016-07-09
forum: Server Platforms
---

### Post by Tactical Fart on 2016-07-09
Hey guys, here again with another issue.

I have a Ubuntu 16.04 running on a vps with 1GB of RAM. It has the basic LAMP stack and is hosing WordPress.

The issue I'm having is that the MySQL daemon (mysqld) is eating my memory alive. After a clean boot, I would have about 300-350 MB remaining. Also available memory would drop by about 4 -20 MB with each page request. Then, when I kill mysqld, my RAM would jump from about 1-3MB (not a typo) to 700MB of available memory. Eventually so much memory get's used that I can't ssh into it, run "free -m -h", top, or even run a basic command from the web console (courtesy of the hoster). Eventually the server would start giving out 500 errors. 

Here is my mysqld.conf if it helps. I followed [this tutorial]("https://opensourcehacker.com/2011/03/31/reducing-mysql-memory-usage-on-ubuntu-debian-linux/") to try and get a little extra memory out of it, but that obviously didn't help. Also I am not using swap because the vps is using an SSD, which is discouraged in [this article.]("https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04")
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

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

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
lc-messages-dir	= /usr/share/mysql
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 127.0.0.1
#
# * Fine Tuning
#
key_buffer_size		= 8M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size       = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover-options  = BACKUP
max_connections         = 30
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit	= 512K
query_cache_size        = 8M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file        = /var/log/mysql/mysql.log
#general_log             = 1
#
# Error log - should be very few entries.
#
log_error = /var/log/mysql/error.log
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
max_binlog_size   = 100M
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

```

Any tips or advise would be appreciated. I wasn't planning on many visitors anyway so I thought 1GB of RAM would be sufficient.

---

### Post by Graham_Willis on 2016-07-09
You said that MySQL is eating up more and more memory with every request, have you made sure that these requests end (uncommenting log_slow_queries may be useful)?
Second thing, I'd try to start troubleshooting with limiting the size of cache-related values. Also, take a look at this:

[URL="https://www.percona.com/blog/2014/01/24/mysql-server-memory-usage-2/"]https://www.percona.com/blog/2014/01/24/mysql-server-memory-usage-2/
[/URL]
Besides that, could you provide us with some samples of the output of **free -m **(some shortly after reboot + start of MySQL and some after memory started to significantly fill up)?

---

### Post by Tactical Fart on 2016-07-09
I did what you suggested. The intel is below.

Data from using "free -m". Swap is excluded because it is not being used due to this being an SSD server.
```

(Taken Right after a reboot)
              total        used        free      shared  buff/cache   available
Mem:            992         179         598           9         214         655

(Taken about 45-50 minutes later)
              total        used        free      shared  buff/cache   available
Mem:            992         756          68          19         167          67


```

Logs from /var/log/mysql/mysql-slow.log
```
Time                 Id Command    Argument
# Time: 2016-07-09T15:57:46.121200Z
# User@Host: wordpressuser[wordpressuser] @ localhost []  Id:     3
# Query_time: 0.010397  Lock_time: 0.008340 Rows_sent: 134  Rows_examined: 144
use wordpress;
SET timestamp=1468079866;
SELECT option_name, option_value FROM wp_options WHERE autoload = 'yes';
# Time: 2016-07-09T15:57:46.417984Z
# User@Host: wordpressuser[wordpressuser] @ localhost []  Id:     3
# Query_time: 0.000859  Lock_time: 0.000768 Rows_sent: 0  Rows_examined: 0
SET timestamp=1468079866;
DELETE FROM wp_statistics_useronline WHERE timestamp < '1468061836';
# Time: 2016-07-09T15:58:59.050021Z
# User@Host: wordpressuser[wordpressuser] @ localhost []  Id:     4
# Query_time: 0.002471  Lock_time: 0.000911 Rows_sent: 134  Rows_examined: 144
SET timestamp=1468079939;
SELECT option_name, option_value FROM wp_options WHERE autoload = 'yes';
# Time: 2016-07-09T15:58:59.098316Z
# User@Host: wordpressuser[wordpressuser] @ localhost []  Id:     4
# Query_time: 0.000502  Lock_time: 0.000336 Rows_sent: 0  Rows_examined: 0
SET timestamp=1468079939;
DELETE FROM wp_statistics_useronline WHERE timestamp < '1468061909';
# Time: 2016-07-09T17:00:44.068475Z
# User@Host: wordpressuser[wordpressuser] @ localhost []  Id:     5
# Query_time: 0.001693  Lock_time: 0.000583 Rows_sent: 134  Rows_examined: 144
SET timestamp=1468083644;
SELECT option_name, option_value FROM wp_options WHERE autoload = 'yes';
# Time: 2016-07-09T17:00:44.089869Z
# User@Host: wordpressuser[wordpressuser] @ localhost []  Id:     5
# Query_time: 0.000371  Lock_time: 0.000266 Rows_sent: 0  Rows_examined: 0
SET timestamp=1468083644;
DELETE FROM wp_statistics_useronline WHERE timestamp < '1468065614';
```

---

### Post by Graham_Willis on 2016-07-10
[quote="Tactical Fart"]I did what you suggested.[/quote]

1. Have you also zeroed all the cache-related values?
2. What is in error logs (**/var/log/mysql/error.log**)?
3. Can you provide us with the output of **ps auwx** taken shortly after reboot and start of mysql service and taken after the memory started to fill up (if not **ps auwx | grep -i mysql **will still be useful)?  
4. The same with **lsof | wc -l **.
5. The same with **lsof -p *pid_of_mysql*** **| wc -l **.
6. The same with **sysctl -a | grep -i file** .
7. Please try to log in to mysql as admin, **mysql -u** ***admin* -p **(***admin ***is probably root, but I can't be sure), and then issue

```

RESET QUERY CACHE;
FLUSH QUERY CACHE;

```

Tell us if it has any positive effects.

7. **echo 3 > /proc/sys/vm/drop_caches** and again, tell us if it brings any positive effects.
8. Create a database with two columns being able to hold long VARCHARs.
 Paste the following into **script.sh **:

```

#!/bin/sh
echo use *my_database*;
echo INSERT INTO *table* \(*column1*, *column2*\) VALUES \(\'xxxx\'\), \(\'xxxx\'\)';'

```

What is in italic, you replace as necessary. Replace xxxx with very long strings. Then of course **chmod 700 script.sh** .

Then **cut off your machine from the Internet** (or do something similar, so only you'd be able to access databases) , restart mysql daemon, check if memory is filled up. If yes, then reboot, if it isn't then continue immediately with this:

**free -m**
[B]i=0; while [ "$i" -le 1024 ]; do echo -n '.'; ./script.sh | mysql -u *admin* -p*password*; : $((i+=1)); done
free -m

[/B]Check if you observe behaviour similar to that when queries are made to WordPress databases, experiment with that by increasing the value 1024 and so on. Please provide us with the information what you got from these tests.

---

### Post by nerdtron on 2016-07-11
I have  VPS too with the same specs. Based from my experience, mysql really does like to consume as much memory at it can get. Mostly used for caching requests. And yes, adding more swap will help alleviate the problem, but not much of a life server for a busy server?
1 CPU and 1 GB ram is not very much for a full blown LAMP Wordpress stack. 
Have you tried these mysql tune-ups? [https://www.linode.com/docs/databases/mysql/tuning-your-mysql-database](https://www.linode.com/docs/databases/mysql/tuning-your-mysql-database)

More to point is how much traffic or request does your server receive every minute? You can only do so much on tuning for small server, but if the workload is high, you have no choice but to increase the server specs.

---

### Post by Tactical Fart on 2016-07-11
Sorry for the late reply. I got really busy yesterday and today. Here are my findings.

Output of /var/log/mysql/error.log
```
2016-07-12T01:54:52.430326Z 0 [Note] Giving 2 client threads a chance to die gracefully
2016-07-12T01:54:52.431316Z 0 [Note] Shutting down slave threads
2016-07-12T01:54:54.432033Z 0 [Note] Forcefully disconnecting 2 remaining clients
2016-07-12T01:54:54.432789Z 0 [Warning] /usr/sbin/mysqld: Forcing close of thread 4  user: 'root'

2016-07-12T01:54:54.434316Z 0 [Warning] /usr/sbin/mysqld: Forcing close of thread 5  user: 'root'

2016-07-12T01:54:54.440972Z 0 [Note] Event Scheduler: Purging the queue. 0 events
2016-07-12T01:54:54.448042Z 0 [Note] Binlog end
2016-07-12T01:54:54.468963Z 0 [Note] Shutting down plugin 'ngram'
2016-07-12T01:54:54.469072Z 0 [Note] Shutting down plugin 'ARCHIVE'
2016-07-12T01:54:54.469115Z 0 [Note] Shutting down plugin 'partition'
2016-07-12T01:54:54.469141Z 0 [Note] Shutting down plugin 'BLACKHOLE'
2016-07-12T01:54:54.469685Z 0 [Note] Shutting down plugin 'INNODB_SYS_VIRTUAL'
2016-07-12T01:54:54.470436Z 0 [Note] Shutting down plugin 'INNODB_SYS_DATAFILES'
2016-07-12T01:54:54.470479Z 0 [Note] Shutting down plugin 'INNODB_SYS_TABLESPACES'
2016-07-12T01:54:54.470504Z 0 [Note] Shutting down plugin 'INNODB_SYS_FOREIGN_COLS'
2016-07-12T01:54:54.470529Z 0 [Note] Shutting down plugin 'INNODB_SYS_FOREIGN'
2016-07-12T01:54:54.470553Z 0 [Note] Shutting down plugin 'INNODB_SYS_FIELDS'
2016-07-12T01:54:54.470574Z 0 [Note] Shutting down plugin 'INNODB_SYS_COLUMNS'
2016-07-12T01:54:54.470597Z 0 [Note] Shutting down plugin 'INNODB_SYS_INDEXES'
2016-07-12T01:54:54.470618Z 0 [Note] Shutting down plugin 'INNODB_SYS_TABLESTATS'
2016-07-12T01:54:54.470639Z 0 [Note] Shutting down plugin 'INNODB_SYS_TABLES'
2016-07-12T01:54:54.470659Z 0 [Note] Shutting down plugin 'INNODB_FT_INDEX_TABLE'
2016-07-12T01:54:54.470679Z 0 [Note] Shutting down plugin 'INNODB_FT_INDEX_CACHE'
2016-07-12T01:54:54.470703Z 0 [Note] Shutting down plugin 'INNODB_FT_CONFIG'
2016-07-12T01:54:54.470725Z 0 [Note] Shutting down plugin 'INNODB_FT_BEING_DELETED'
2016-07-12T01:54:54.470744Z 0 [Note] Shutting down plugin 'INNODB_FT_DELETED'
2016-07-12T01:54:54.470818Z 0 [Note] Shutting down plugin 'INNODB_FT_DEFAULT_STOPWORD'
2016-07-12T01:54:54.470843Z 0 [Note] Shutting down plugin 'INNODB_METRICS'
2016-07-12T01:54:54.470862Z 0 [Note] Shutting down plugin 'INNODB_TEMP_TABLE_INFO'
2016-07-12T01:54:54.470883Z 0 [Note] Shutting down plugin 'INNODB_BUFFER_POOL_STATS'
2016-07-12T01:54:54.470903Z 0 [Note] Shutting down plugin 'INNODB_BUFFER_PAGE_LRU'
2016-07-12T01:54:54.470927Z 0 [Note] Shutting down plugin 'INNODB_BUFFER_PAGE'
2016-07-12T01:54:54.470948Z 0 [Note] Shutting down plugin 'INNODB_CMP_PER_INDEX_RESET'
2016-07-12T01:54:54.470968Z 0 [Note] Shutting down plugin 'INNODB_CMP_PER_INDEX'
2016-07-12T01:54:54.470989Z 0 [Note] Shutting down plugin 'INNODB_CMPMEM_RESET'
2016-07-12T01:54:54.471037Z 0 [Note] Shutting down plugin 'INNODB_CMPMEM'
2016-07-12T01:54:54.471061Z 0 [Note] Shutting down plugin 'INNODB_CMP_RESET'
2016-07-12T01:54:54.471085Z 0 [Note] Shutting down plugin 'INNODB_CMP'
2016-07-12T01:54:54.471104Z 0 [Note] Shutting down plugin 'INNODB_LOCK_WAITS'
2016-07-12T01:54:54.471125Z 0 [Note] Shutting down plugin 'INNODB_LOCKS'
2016-07-12T01:54:54.471164Z 0 [Note] Shutting down plugin 'INNODB_TRX'
2016-07-12T01:54:54.471191Z 0 [Note] Shutting down plugin 'InnoDB'
2016-07-12T01:54:54.473904Z 0 [Note] InnoDB: FTS optimize thread exiting.
2016-07-12T01:54:54.474716Z 0 [Note] InnoDB: Starting shutdown...
2016-07-12T01:54:54.576597Z 0 [Note] InnoDB: Dumping buffer pool(s) to /var/lib/mysql/ib_buffer_pool
2016-07-12T01:54:54.578280Z 0 [Note] InnoDB: Buffer pool(s) dump completed at 160711 21:54:54
2016-07-12T01:54:56.335997Z 0 [Note] InnoDB: Shutdown completed; log sequence number 8356134
2016-07-12T01:54:56.337247Z 0 [Note] InnoDB: Removed temporary tablespace data file: "ibtmp1"
2016-07-12T01:54:56.337315Z 0 [Note] Shutting down plugin 'MEMORY'
2016-07-12T01:54:56.337605Z 0 [Note] Shutting down plugin 'PERFORMANCE_SCHEMA'
2016-07-12T01:54:56.338004Z 0 [Note] Shutting down plugin 'MRG_MYISAM'
2016-07-12T01:54:56.338045Z 0 [Note] Shutting down plugin 'MyISAM'
2016-07-12T01:54:56.338538Z 0 [Note] Shutting down plugin 'CSV'
2016-07-12T01:54:56.338577Z 0 [Note] Shutting down plugin 'sha256_password'
2016-07-12T01:54:56.338596Z 0 [Note] Shutting down plugin 'mysql_native_password'
2016-07-12T01:54:56.340637Z 0 [Note] Shutting down plugin 'binlog'
2016-07-12T01:54:56.342518Z 0 [Note] /usr/sbin/mysqld: Shutdown complete

2016-07-12T01:54:56.510037Z 0 [Warning] Changed limits: max_open_files: 1024 (requested 5000)
2016-07-12T01:54:56.510657Z 0 [Warning] Changed limits: table_open_cache: 499 (requested 2000)
2016-07-12T01:54:56.775485Z 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
2016-07-12T01:54:56.777963Z 0 [Note] /usr/sbin/mysqld (mysqld 5.7.12-0ubuntu1.1-log) starting as process 20942 ...
2016-07-12T01:54:56.796112Z 0 [Note] InnoDB: PUNCH HOLE support available
2016-07-12T01:54:56.796228Z 0 [Note] InnoDB: Mutexes and rw_locks use GCC atomic builtins
2016-07-12T01:54:56.796255Z 0 [Note] InnoDB: Uses event mutexes
2016-07-12T01:54:56.796304Z 0 [Note] InnoDB: GCC builtin __atomic_thread_fence() is used for memory barrier
2016-07-12T01:54:56.796328Z 0 [Note] InnoDB: Compressed tables use zlib 1.2.8
2016-07-12T01:54:56.796347Z 0 [Note] InnoDB: Using Linux native AIO
2016-07-12T01:54:56.797312Z 0 [Note] InnoDB: Number of pools: 1
2016-07-12T01:54:56.797898Z 0 [Note] InnoDB: Using CPU crc32 instructions
2016-07-12T01:54:56.832446Z 0 [Note] InnoDB: Initializing buffer pool, total size = 128M, instances = 1, chunk size = 128M
2016-07-12T01:54:56.857405Z 0 [Note] InnoDB: Completed initialization of buffer pool
2016-07-12T01:54:56.862670Z 0 [Note] InnoDB: If the mysqld execution user is authorized, page cleaner thread priority can be changed. See the man page of setpriority().
2016-07-12T01:54:56.898346Z 0 [Note] InnoDB: Highest supported file format is Barracuda.
2016-07-12T01:54:57.001823Z 0 [Note] InnoDB: Creating shared tablespace for temporary tables
2016-07-12T01:54:57.002213Z 0 [Note] InnoDB: Setting file './ibtmp1' size to 12 MB. Physically writing the file full; Please wait ...
2016-07-12T01:54:57.093278Z 0 [Note] InnoDB: File './ibtmp1' size is now 12 MB.
2016-07-12T01:54:57.095656Z 0 [Note] InnoDB: 96 redo rollback segment(s) found. 96 redo rollback segment(s) are active.
2016-07-12T01:54:57.095698Z 0 [Note] InnoDB: 32 non-redo rollback segment(s) are active.
2016-07-12T01:54:57.106828Z 0 [Note] InnoDB: 5.7.12 started; log sequence number 8356134
2016-07-12T01:54:57.109530Z 0 [Note] Plugin 'FEDERATED' is disabled.
2016-07-12T01:54:57.111759Z 0 [Note] InnoDB: Loading buffer pool(s) from /var/lib/mysql/ib_buffer_pool
2016-07-12T01:54:57.147749Z 0 [Warning] Failed to set up SSL because of the following SSL library error: SSL context is not usable without certificate and private key
2016-07-12T01:54:57.147839Z 0 [Note] Server hostname (bind-address): '127.0.0.1'; port: 3306
2016-07-12T01:54:57.147983Z 0 [Note]   - '127.0.0.1' resolves to '127.0.0.1';
2016-07-12T01:54:57.148120Z 0 [Note] Server socket created on IP: '127.0.0.1'.
2016-07-12T01:54:57.171000Z 0 [Note] InnoDB: Buffer pool(s) load completed at 160711 21:54:57
2016-07-12T01:54:57.265511Z 0 [Note] Event Scheduler: Loaded 0 events
2016-07-12T01:54:57.266323Z 0 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.7.12-0ubuntu1.1-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
2016-07-12T01:54:57.498925Z 2 [Note] Access denied for user 'root'@'localhost' (using password: NO)

```
```
After Restart
#ps auwx | grep -i mysql
mysql     1244  1.0 14.9 1759596 151896 ?      Ssl  09:09   0:00 /usr/sbin/mysqld
root      1586  0.0  0.0  14512   924 pts/0    S+   09:10   0:00 grep -i mysql

#lsof | wc -l 
4488

#lsof -p pid_of_mysql | wc -l
fs.file-max = 99816
fs.file-nr = 864	0	99816
sysctl: reading key "net.ipv6.conf.all.stable_secret"
sysctl: reading key "net.ipv6.conf.default.stable_secret"
sysctl: reading key "net.ipv6.conf.eth0.stable_secret"
sysctl: reading key "net.ipv6.conf.eth1.stable_secret"
sysctl: reading key "net.ipv6.conf.lo.stable_secret"

#sysctl -a | grep -i file
82


After memory is used up

#ps auwx | grep -i mysql
mysql     1244  0.0 75.8 1760396 771408 ?      Ssl  09:09   0:17 /usr/sbin/mysqld
root      2404  0.0  0.0  14512   944 pts/0    S+   16:08   0:00 grep -i mysql

#lsof | wc -l 
4892

#lsof -p pid_of_mysql | wc -l
fs.file-max = 99816
fs.file-nr = 864	0	99816
sysctl: reading key "net.ipv6.conf.all.stable_secret"
sysctl: reading key "net.ipv6.conf.default.stable_secret"
sysctl: reading key "net.ipv6.conf.eth0.stable_secret"
sysctl: reading key "net.ipv6.conf.eth1.stable_secret"
sysctl: reading key "net.ipv6.conf.lo.stable_secret"

#sysctl -a | grep -i file
85
```

I tried ```
RESET QUERY CACHE;
FLUSH QUERY CACHE;
and 
echo 3 > /proc/sys/vm/drop_caches

```, but saw no change at all. (I ran the commands in the appropriate environments, mysql for the first two and shell for the last)

I had to make some modifications to the script you provided and used it. I verified that the table was populated (with 1024 records), but the memory remaining was not changed by much. In fact, it seems to slowly get used up in a way that seems like time is the only factor. Output below.
```
Before script
              total        used        free      shared  buff/cache   available
Mem:           992M        172M        723M        692K         96M        693M

After script
              total        used        free      shared  buff/cache   available
Mem:           992M        183M        698M        692K        110M        675M

```

I'm going to try what nerdtron suggested and follow that article. I'll report back with my findings on that.

---

### Post by Graham_Willis on 2016-07-11
Please provide us with the output of 

[B]lsof | wc -l
lsof -p pid_of_mysql | wc -l
sysctl -a | grep -i file

[/B]both immediately after the start of the server + mysql daemon and after the memory started to fill up. The point's that it's possible that mysql may open some (or many) files and be not able to close them properly later. Also, did you try to zero the cache? It'll probably result in performance degradation to some extent, but it should help you find the root cause of the problem. You can observe yourself how websites are working with cache disabled to check if doing this (just temporarily) is acceptable. 

Does VPS that you use host only a single WordPress? What kind of queries are mostly directed to MySQL server, are they inserts/selects?
BTW, can you turn off plugins (if you have them) in WordPress, if not all, then as many as possible and check if this is of any help? Have you checked if you don't have spam entries in the database?

@nerdtron - you may be right that RAM memory in the server concerned is insufficient, but it should be possible to disable using the cache entirely as well as limit its size. Also, if cache is the reason, why flushing/resetting it doesn't result in free memory increase? I think that the original poster should first of all establish what the root cause of these problems with memory actually is, it doesn't make sense to tune up mysql earlier in my opinion.

---

### Post by Tactical Fart on 2016-07-12
The output of the commands you are requesting are in my previous post, in the second code block. I have the results for just after a restart and after the server has been running for a while (about 30-40 minutes). Also I did try to zero out the cache. I accessed MySQL's configuration file and looked for any settings that reference cache and set it to zero (assuming that is what you meant, I also did the RESET QUERY CACHE; FLUSH QUERY CACHE; commands.)

Also, the vps is just an (almost) vanilla Ubuntu 16.04 server. I had to manually set up Apache, MySQL, PHP, etc. I could have just as easily gone with Drupal or Joomla, or what ever, so WordPress is not my only option. I can literally do just about anything with this server (specs willing of course).

As an experiment I restarted the vps and immediately disabled Apache. I'm going to see if it fills up regardless of whether it is getting queries or not.

Update: after about 5 minutes it went from 632MB free to 381MB free. In less than an hour, I''l probably be at about <1MB to about 15MB.

Update 2: Confirmed. MySQL is eating up memory regardless of the fact that WordPress is not interacting with it. Perhaps I should just go with SQLite, since there's a plugin for that.

---

### Post by Graham_Willis on 2016-07-30
[quote="Tactical Fart"]
The output of the commands you are requesting are in my previous post,  in the second code block. I have the results for just after a restart  and after the server has been running for a while (about 30-40 minutes).
[/quote]

Yes, I missed the fact that it's possible to pull down the code, sorry.

I confirmed to some extent that a problem is there. That is, I basically applied the script I presented in my earlier post just having changed inserts with selects (I had created large records in the database queried). All cache-related (not only these ones that you see in config file by default, but everything what is seen after you issue **show variables;** as mysql administrator) variables that can be set to 0 set to 0 and after running this script, mysql fills up memory anyway (both machine's memory and mysql memory jumped up; it doesn't always happen though, but frequently - I have perfomed many tests) However, after I issued the command "**echo 1 > /proc/sys/vm/drop_caches" **I could see that the machine's memory freed up. But the amount of memory occupied by mysql was the same as after running the script, it wasn't freed. Now, I don't know, there are also buffer-related variables so perhaps it is something about this.

But what you're saying, that mysql fills up the memory even if there are no queries sounds really strange. Suggests a memory le: ak in an idle application... weird. 
Can you turn on logging on queries (I believe it can be done by going to **/etc/mysql/my.cnf**, then uncommenting general_log_file, general_log and restarting mysql) and check if there are no queries indeed?

**Update:** I let my virtual machine to go idle for almost an hour, mysql running and there was nothing of the kind you mentioned. That is, the amount of memory taken by mysql process remained the same throughout the whole time frame of the machine running. And a process filling up "on its own when it is idle" is **an indication that somebody is doing something nasty**. Are you sure that queries to mysql server from the outside were disabled? Also, I would really turn off apache and turn on logging of all queries and also tried to show what's going on using **show processlist; **from mysql console. Also, check what's the output of **netstat -an. **Aren't some undesired IP addresses visible? Also, try to cut off all the external traffic with firewall and check if the problem still shows up. If it still does, try killing processes. Finally, scan the disk immediately after reboot  and after the memory's filled up, it can also provide some valuable suggestions.

It is also recommended that you check that you're actually using what you think that you're using (check MD5 of your Ubuntu Installation medium, think if it isn't possible if somebody changed your configuration etc.).

Switching to SQLite might be a solution to your problem, but it also might not be (even if it currently doesn't show up), you should really make sure that your box is secured properly.

---

### Post by SeijiSensei on 2016-07-30
> **Graham_Willis said:**
> Are you sure that queries to mysql server from the outside were disabled?

In Ubuntu, mysqld is bound only to the localhost interface by default.  The OP would have had to change the "bind-address" directive in my.cnf to open the server to remote connections.

OP, I don't know how flexible your VM provider is, but if you have the ability to spin up another server, I'd try cloning your current server onto one with 2 GB and see if that works better.  I run a 2 GB CentOS 6 server with LAMP, two instances of PostgreSQL, sendmail, and the Sphinx search daemon and never run into memory problems. The server hosts a few WordPress blogs as well as conventional websites.

---

### Post by Graham_Willis on 2016-07-30
[quote="SeijiSensei"]In Ubuntu, mysqld is bound only to the localhost interface by default.   The OP would have had to change the "bind-address" directive in my.cnf  to open the server to remote connections.[/quote]

So perhaps somebody did this favour for him. I know, in my.cnf file he showed this bind is unchanged, but perhaps this file should not be trusted - worth checking if modifying values there has in fact an effect on mysql variables.

I'll repeat: extending the amount of RAM available is by no means a solution to these problems at this point. Even averagely decent software shouldn't eats up memory when it's supposed to do nothing (some services can perform some actions in the background,  but never-queried mysql daemon filling up memory on its own doesn't make any sense). I performed tests on a VM which has < 1 GB RAM and nothing of the kind (that is, when mysql was no queried at all) the OP mentioned occured. It's really important that he identifies what exactly is causing this weird behaviour, otherwise these problems will come back to chase him when it's least desired.

---

