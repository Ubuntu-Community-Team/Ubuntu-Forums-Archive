---
title: "Apache/MySQL using 100% cpu"
date: 2010-05-09
forum: Server Platforms
---

### Post by ravingmad on 2010-05-09
Hi all, I am really at my wits end. I've been reading forums and searching Google for nearly 16 hours now and I am no closer to finding answer to my problem than when I started. I'm feeling very confused and frustrated right now.

My config:
-----------
Ubuntu 9.0.4 (all up to date with security patches)
Apache 2.2.11
MySQL version 5.0.75
PHP Version 5.2.6-3ubuntu4.5

I'm running Ubuntu as a Virtual machine with VMWare on top of a Windows 2008 Server. It has been working perfectly for nearly 9 months. I have one processor and 2GB of Ram assigned to the Virtual machine. Memory usage seldom ever reaches more than 50%, swapfile is hardly used either.

I noticed recently that sites were loading very slow from time to time. Webmin showed me that USER / KERNEL were together using 100% cpu. 

I then started searching for answers to what was causing this and then read about using HTOP. I then installed HTOP and found that the following processes were the culprits

/usr/sbin/mysqld 
/usr/sbin/apache2 -k start 

There are multiple instances of mysqld and apache2 listed in HTOP, I assume this is because I run multiple sites on the box. It does 

however seem limited to only one or two PID's that are repeatedly maxing out the CPU at 100% (every 30 seconds to a minute) sometimes the CPU will stay maxed at 100% for nearly a minute and then free itself again but it is doing this continually. At the point when the CPU maxes out at 100% there will be one instance of mySQLD and one instance of Apache2 right at the top of HTOP and between the two they will be hogging 100% cpu.


All the sites are either Wordpress or Joomla sites and I am quite confident it's one of these sites causing a problem. My issue is that I cannot pin down which PID belongs to which site. So for a start I need some help in figuring that out. Then, once I know which site it is how do I then trace what process / file inside that site is casuing the problem? 

I figured one of my busiest sites (wordpress) might be the culprit and I installed the W3 Total Cache plugin today but that has not helped this 100% cpu problem, so for all I know it might be another WP site on the box or even one of the Joomla sites.

I've noticed that the TIME column on the one MYSQLD instance that maxes out is very long so it seems like Mysql is keeping some connection open or something???

If someone can guide me where to start looking to resolve this it would be most appreciated.

---

### Post by Vegan on 2010-05-09
Sounds like you PHP engine is very busy. A better CPU and more RAM would help a lot.

---

### Post by windependence on 2010-05-10
> **Vegan said:**
> Sounds like you PHP engine is very busy. A better CPU and more RAM would help a lot.
Not a very helpful suggestion. If you notice he is running this in a virtual machine. There should be plenty of resources as VMware will use what is available.

The only thing I would do different is use ESXi instead of VMware Server or at least run Server on top of Unix instead of Windows. Wintel is a huge resource hog.

-Tim

---

### Post by dtfinch on 2010-05-10
If you keep an access log, maybe you can add %P to your log format, which would log the process ids for each access, and then when you see a process using a lot of cpu, you can see what that process was handling at that time.

[http://httpd.apache.org/docs/2.2/mod/mod_log_config.html](http://httpd.apache.org/docs/2.2/mod/mod_log_config.html)

I've never tried it myself though.

---

### Post by ravingmad on 2010-05-10
Thanks guys, I'm still no closer to a solution. I added %P to the log format but I cannot see anything untowards happening, the logs show that apache is serving requests quite normally and I cannot pin down what's spiking the CPU to 100%. I turned Apache into debug log mode to see what's going on and I keep clicking refresh (from webmin) and it's updating quickly which shows Apache is serving the stuff albeit slowly. 

I'm busy right now with the sqlreport script to see if I can optimise MySQL and see if that helps. I've run netstat and there is no massive amount of connections, all traffic coming in appears quite legit and normal. It seems Apache is just going haywire doing something, reboots to the box don't help much it just goes straight back to 100% cpu and pretty much stays there all the time. Eish :(

---

### Post by dragos2 on 2010-05-10
First try to see if you can optimize MySQL, then maybe try memcached ? It seems that mysql alone uses a lot of cpu time.

Maybe try to reinstall mysql, or a newer version.

---

### Post by ravingmad on 2010-05-10
> **dragos2 said:**
> First try to see if you can optimize MySQL, then maybe try memcached ? It seems that mysql alone uses a lot of cpu time.

Maybe try to reinstall mysql, or a newer version.

Thanks Dragos

I tried optimising mySQL with the help of mysqltuner and ended up with the following my.cnf configuration. Makes no difference to performance whatsoever. Can you make any recommendations on the below .cnf file? How do I go about upgrading mySQL to the latest version without losing anything? My current version is 5.13.0really5.0.75-0ubuntu10.3 and according to Synaptics this is the latest version??

[client]
#port		= 3306
#socket		= /var/run/mysqld/mysqld.sock


[mysqld]
user = mysql
pid-file = /var/run/mysqld/mysqld.pid
socket = /var/run/mysqld/mysqld.sock
#port = 3306
basedir	= /usr
datadir = /var/lib/mysql
tmpdir = /tmp
skip-external-locking
bind-address = 127.0.0.1
myisam_sort_buffer_size = 64M
key_buffer = 16M
join_buffer_size = 1M
read_buffer_size = 1M
sort_buffer_size = 2M
table_cache = 1024
max_allowed_packet = 16M
thread_stack = 128K
thread_cache_size = 64
wait_timeout = 1800
connect_timeout = 10
max_allowed_packet = 16M
max_connect_errors = 10
myisam-recover = BACKUP
query_cache_limit = 1M
query_cache_size = 32M
query_cache_type = 1
expire_logs_days = 10
max_binlog_size = 10M
max_connections = 250
tmp_table_size = 64M
max_heap_table_size = 32M
innodb_buffer_pool_size = 278M
skip-federated


[mysqld_safe]
#socket	= /var/run/mysqld/mysqld.sock
#nice = 0
err-log=/var/log/mysqld.log
open_files_limit = 8192

[mysqldump]
quick
quote-names
max_allowed_packet = 16M

[mysql]

[isamchk]
key_buffer		= 16M

[myisamchk]
key_buffer = 64M
sort_buffer = 64M
read_buffer = 16M
write_buffer = 16M

!includedir /etc/mysql/conf.d/

---

### Post by ravingmad on 2010-05-10
Another 8 hours blown on this and still no solution. If there is someone in the Johannesburg area that can help me sort this out please PM me your number, my life is wasting away on this now :(

---

### Post by dragos2 on 2010-05-11
Try to optimize your queries I mean if its possible, your conf seems allright I guess.

Post some $ vmstat 3 please.

---

