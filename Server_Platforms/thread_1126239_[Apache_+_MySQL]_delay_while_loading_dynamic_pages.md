---
title: "[Apache + MySQL] delay while loading dynamic pages"
date: 2009-04-15
forum: Server Platforms
---

### Post by cyppher on 2009-04-15
Dear all,

We are having problems serving PHP based CMS pages on Ubuntu Server. Each time a page is requested, a delay of around 6,5 seconds appears. I've benchmarked the server (mysql load, apache ab) but found no problems concerning the performance.

Mostly this delay occurs when serving pages on Wordpress, phpwcms and other regular CMS's.

We're running Ubuntu 8.04 Server with latest Apache,PHP (5.2.6) and MySQL. Checking the error and access-logs didn't show any errors. 

A normal PHP instruction (for example phpinfo() ) is superfast, also phpmyadmin runs superfast. However the delay occuring while serving dynamic pages from Wordpress (or phpwcms, or any other CMS) is really unacceptable.

I actually don't have a clue where to continue searching for the cause of this delay. Did anyone have the same issues here?

Any hints are welcome, thank you in advance!


Mathijs (cyppher)
Edenspiekermann_ 
Berlin Amsterdam

---

### Post by cdenley on 2009-04-15
Could the delay be the mysql server trying to resolve your hostname? Is mysql and apache running on the same server? Post your /etc/hosts file.

---

### Post by cyppher on 2009-04-15
> **cdenley said:**
> Could the delay be the mysql server trying to resolve your hostname? Is mysql and apache running on the same server? Post your /etc/hosts file.

MySQL server and Apache are running on the same Ubuntu server, yes. I've installed and configured Webmin. In Mysql config I've set "skip-name-resolve" (as I read before, to optimize MySQL performance).

```

127.0.0.1	localhost
127.0.0.1	dev.edenspiekermann.com

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```

---

### Post by HighCommander540 on 2009-04-15
How does one enable this "skip-name-resolve"? I would like to get my MySQL server to run as fast as possible.

---

### Post by daboroe on 2009-04-15
@HighCommander540: I beleive it is in teh configuration file for MySQL. I am not 100% sure on this so do not hold me to that.

@cyppher: Have you tried to reconfigure your MySQl and/or your apache server. Maybe reconfiguring it will work and fix your issue. I have not seen this before. What CMS are you using? If it is PHP Nuke or any variety of that that somtimes happens with that CMS and why I stay far from it unless a client wants me to use it and even then I recommend against it for several reasons.

dpkg re-configure apache
dpkg re-configure mysql-server [beleive this is the command for the server]

Hope this helps you out atleaest a little bit. Let me know if it does.

---

### Post by drubin on 2009-04-15
> **cyppher said:**
> 

Mostly this delay occurs when serving pages on Wordpress, phpwcms and other regular CMS's.

How is the load on the machine? This does does like the delay is on the mysql configuration size. Do you have slow logs enabled of the mysql?

Make sure you have these lines
[PHP]log_slow_queries        = /var/log/mysql/mysql-slow.log
long_query_time = 2[/PHP]
 
You db might need some turning and optimization.

---

### Post by cyppher on 2009-05-14
Hi,

**After a month I still haven't been able to solve the slow MySQL performance...**

Server load is not high, almost all resources are unused. 
Logging slow mysql is **enabled**, however there's not much info in there.

In phpmyadmin, in which you can see a detailed status report, it appears that this slow performance is due to some configuration issues. I've followed every guideline in that report, like increasing several types of buffers and caches. Found some guides on the web to optimize MySQL server performance, same increase of caches and so on. 

However, still the same +/- 6 secs delay every time a database is queried. Phpmyadmin still reports that values are too low, which I find very hard to believe when caches are set to 64M...

I just can't come up with a solution. I need your input.
**What else can I try?**

Thanks!

---

### Post by cyppher on 2009-05-14
Ok, here's some extra info:

FILE: **/etc/mysql/my.cnf**:
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
socket = /var/run/mysqld/mysqld.sock
port = 3306
basedir		= /usr
datadir = /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
skip-external-locking
skip-name-resolve
skip-host-cache

#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address = 127.0.0.1
#
# * Fine Tuning
#
key_buffer		= 64M
max_allowed_packet	= 50M
thread_stack		= 512K
thread_cache_size	= 64
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover		= BACKUP
tmp_table_size = 64M
max_heap_table_size = 64M
#max_connections        = 100
table_cache            = 1024
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 50M
query_cache_size        = 50M
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
log_slow_queries	= /var/log/mysql/mysql-slow.log
long_query_time = 2
log-queries-not-using-indexes
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
# * Federated
#
# The FEDERATED storage engine is disabled since 5.0.67 by default in the .cnf files
# shipped with MySQL distributions (my-huge.cnf, my-medium.cnf, and so forth).
#
skip-federated
set-variable = net_buffer_length=50M
set-variable = sort_buffer=50M
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
[B]
phpMyAdmin status report[/B] (after restarting MySQL server and opening a site that uses Wordpress):
> 
Slow_queries: [COLOR="Red"]30[/COLOR]
Innodb_buffer_pool_reads: [COLOR="Red"]16[/COLOR]
Handler_read_rnd: [COLOR="Red"]4[/COLOR]
Handler_read_rnd_next: [COLOR="Red"]3,658[/COLOR]
Created_tmp_disk_tables: [COLOR="Red"]21[/COLOR]
Created_tmp_files: 5
Created_tmp_tables: 82
Key_reads: [COLOR="Red"]22[/COLOR]
Select_full_join: [COLOR="Red"]1[/COLOR]
Opened_tables: [COLOR="Red"]106[/COLOR]


I guess the problem is somewhere in the MySQL configuration. I don't know what to try now.

Edit: a PHP MySQL Benchmark program shows no delay, instead it shows a fast performance... But the CMS-bases sites are still so slow...

Any hints?

---

### Post by drubin on 2009-05-14
The enabling slow queries were to see which queries were taking time and to try and optimize those.

If there is nothing in your slow logs then something is going wrong. because you have it set to 2 seconds slow queries and it takes 6seconds to run.

If you find a query, do an EXPLAIN *sql query* and you will see the rows exacmined vs rows returned. this number should be as close to each other as possible and as low as possible.

Ways to get around this it to read up on mysql indexing? If you tables are indexed but your data sets are just far to large I suggest looking into using sphnix for your indexing and searching.

---

### Post by cyppher on 2009-05-15
> **drubin said:**
> The enabling slow queries were to see which queries were taking time and to try and optimize those.

If there is nothing in your slow logs then something is going wrong. because you have it set to 2 seconds slow queries and it takes 6seconds to run.

If you find a query, do an EXPLAIN *sql query* and you will see the rows exacmined vs rows returned. this number should be as close to each other as possible and as low as possible.

Ways to get around this it to read up on mysql indexing? If you tables are indexed but your data sets are just far to large I suggest looking into using sphnix for your indexing and searching.

Hi, thanks.

I'm actually wondering if **MySQL** is causing the delay. I did some tuning in the configuration (increased several cache values), which didn't solve the delay, but **decreased** the **number** of slow queries in the slow queries logfile. 

Strange thing is that the few queries that are reported in there, show a query time of 0, lock time of 0:

> 
# Query_time: 0  Lock_time: 0  Rows_sent: 1  Rows_examined: 10
 

Reasing why I'm wondering if MySQL is the issue, is that phpMyAdmin (webbased MySQL manager) is **not slow** at all. 
Sometimes, when logged in in phpWcms for instance, there's no delay. Only after a few page-request in that CMS, the delay occurs and measures about 10 - 20 seconds.

I've investigated the Apache logfiles (access / error), but can't find any errors or delaying requests.


Is it possible and easy to backup the databases/tables for the 2 CMS's, **reinstall** Apache en MySQL from **scratch**, by using Webmin?

Or could it be that actually **Webmin** is causing the delay?

Please help me out here, I'm stuck and have insufficient experience and knowlegde to find a solution based on the information I have.

Thank you again!

---

### Post by drubin on 2009-05-15
The reason that querie was logged even though it wasn't slow might because you have "logging enabled for non indexed queries"

It might be an issue with apache/(cms) not closing connections to the DB. if you are runnning the same queries from another application and they aren't slow the bottle neck could be on the page generation time or the page return time (ie network traffic) or diskio.

There are tones and tones of reasons for my mysql would be slow. Have you checked the proccess usage during the page generation and see what is using up resources that would generally show a load..

---

### Post by gregcrn on 2009-05-20
Hi All,

I just checked with stopwatch. It is 6 seconds plus probably 0.4sec. delay on my finger.
I have installed new Ubuntu 8.10 server, new mysql and apache2. 
When I install new Joomla everything in admin panel works fine, but...
When I import joomla from working website ( mysql database about 16MB) I experience 6 seconds delay when I switch between admin functions. 
Delay every time seems to be the same. 
I checked everything and cannot find reason, unfortunately. 
Will post here if only find some hints.

Regards
Greg

P.S. Some forums talk about reverse DNS settings and network issues- that delay occurs when I open website from network and on server in Xorg.

---

### Post by drubin on 2009-05-22
> **gregcrn said:**
> 
P.S. Some forums talk about reverse DNS settings and network issues- that delay occurs when I open website from network and on server in Xorg.

you might have some thing here.. When you connect to mysql which hostname param are you using? an IP or DNS name?  But that would not affect times based on data (when you import the new data it is slugish)

This still leeds me to belive that your mysql queries aren't indexed correctly since small data sets are fine (fresh install) while larger data (imported) isn't.

btw 16mb is tiny so if it is slow with that data set your scaling solution isn't going to be valid should your website grow any bigger.

---

### Post by BjBlaster on 2010-06-13
I don't necessarily think it's a MySQL problem, as I get it with a YaBB perl based forum... exactly 6.5 seconds before it executes the .pl script. Any ideas?

Cheers
Bj

---

