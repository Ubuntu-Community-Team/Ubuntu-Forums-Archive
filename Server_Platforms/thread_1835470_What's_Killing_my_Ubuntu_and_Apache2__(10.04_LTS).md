---
title: "What's Killing my Ubuntu and Apache2 ?? (10.04 LTS)"
date: 2011-08-29
forum: Server Platforms
---

### Post by ravingmad on 2011-08-29
I am hoping someone could help me or shed some light. I have spent days analyzing this and reading hundreds of forums but I am no closer to solving the problem. Every day around 6am my Apache dies with "child process still did not exit" messages. When this happens I can access nothing on the server not even SSH into the box but it responds to pings. Since I changed my Apache2.conf file a week ago (for the umpteenth time), the server actually recovers after about 60-90 minutes but before I tweaked the apache2.conf it would die and I would have to restart the box completely. I am at my wits end trying to diagnose this one. I have checked virtually every log possible to find what triggers this but I can find nothing obvious, no funny url requests or anything and I am starting to worry if there is a bug in Apache 2.2.14 that someone is exploiting somehow. Is it perhaps a PHP script in a Joomla site that causes this and if so, how the hell do I track it down? Would REALLY appreciate some help on this. I've included as much info as possible below, this issue is driving me mental. #-o

My server config:

Ubuntu 10.04 LTS (Virtual Server using VMWare)
Apache 2.2.14
Mysql - 5.1.41
8GB Ram
Intel Core i7 920 on Physical Hardware (2 x cores assigned to VM Ubuntu)
Virtual Memory 5Gb
Disk Size: 114 Gb, 12.8 Gb used
Server Use: Joomla Web Sites

[B]Apache Loaded Modules:
-------------------------
[/B]```

alias
auth_basic
authn_file
authz_default
authz_groupfile
authz_host
authz_user
cache
cgi
deflate
dir
disk_cache
env
expires
fcgid
headers
include
mem_cache
mime
mod-evasive
mod-security
negotiation
php5
reqtimeout
rewrite
setenvif
ssl
status
unique_id

```

[B]Apache 2 Config
---------------
[/B]```

Timeout 15
KeepAlive Off
MaxKeepAliveRequests 0
KeepAliveTimeout 1
HostNameLookups Off
LogLevel Error

<IfModule mpm_prefork_module>
StartServers 5
MinSpareServers 5
MaxSpareServers 10
    MaxClients  256
MaxRequestsPerChild 1
</IfModule>

```

[B]MySQL Config:
--------------[/B]

```

[mysqld]
user = mysql
socket = /var/run/mysqld/mysqld.sock
basedir	= /usr
datadir = /var/lib/mysql
tmpdir = /tmp
skip-external-locking
bind-address = 127.0.0.1
myisam_sort_buffer_size = 32M
key_buffer = 64M
join_buffer_size = 1M
read_buffer_size = 1M
sort_buffer_size = 16M
table_cache = 1024
max_allowed_packet = 16M
thread_stack = 256K
thread_cache_size = 64
wait_timeout = 1800
connect_timeout = 10
max_allowed_packet = 16M
max_connect_errors = 10
myisam-recover = BACKUP
query_cache_limit = 16M
query_cache_size = 256M
query_cache_type = 1
expire_logs_days = 10
max_binlog_size = 10M
max_connections = 250
tmp_table_size = 64M
max_heap_table_size = 32M
innodb_buffer_pool_size = 278M
# RM
table_cache = 256

[mysqld_safe]
err-log=/var/log/mysqld.log
open_files_limit = 8192

[mysqldump]
quick
quote-names
max_allowed_packet = 16M

[mysql]

[myisamchk]
key_buffer = 32M
sort_buffer = 32M
read_buffer = 16M
write_buffer = 16M

!includedir /etc/mysql/conf.d/

```

[B]PHP Config:
-----------
[/B]
```

engine = On
short_open_tag = On
asp_tags = Off
precision = 14
y2k_compliance = On
output_buffering = 4096
zlib.output_compression = Off
implicit_flush = Off
unserialize_callback_func =
serialize_precision = 100
allow_call_time_pass_reference = Off
safe_mode = Off
safe_mode_gid = Off
safe_mode_include_dir =
safe_mode_exec_dir =
safe_mode_allowed_env_vars = PHP_
safe_mode_protected_env_vars = LD_LIBRARY_PATH
disable_functions =
disable_classes =
expose_php = On
max_execution_time = 120
max_input_time = 60
memory_limit = 512M
error_reporting = E_ALL & ~E_DEPRECATED
display_errors = Off
display_startup_errors = Off
log_errors = On
log_errors_max_len = 1024
ignore_repeated_errors = Off
ignore_repeated_source = Off
report_memleaks = On
track_errors = Off
html_errors = On
error_log = /var/log/apache2/php.log
variables_order = "GPCS"
request_order = "GP"
register_globals = Off
register_long_arrays = Off
register_argc_argv = Off
auto_globals_jit = On
post_max_size = 8M
magic_quotes_gpc = Off
magic_quotes_runtime = Off
magic_quotes_sybase = Off
auto_prepend_file =
auto_append_file =
default_mimetype = "text/html"
doc_root =
user_dir =
enable_dl = Off
file_uploads = On
upload_max_filesize = 10M
max_file_uploads = 20
allow_url_fopen = On
allow_url_include = Off
default_socket_timeout = 60
pdo_mysql.cache_size = 2000
pdo_mysql.default_socket=
define_syslog_variables  = Off
SMTP = localhost
smtp_port = 25
mail.add_x_header = On
sql.safe_mode = Off
odbc.allow_persistent = On
odbc.check_persistent = On
odbc.max_persistent = -1
odbc.max_links = -1
odbc.defaultlrl = 4096
odbc.defaultbinmode = 1
ibase.allow_persistent = 1
ibase.max_persistent = -1
ibase.max_links = -1
ibase.timestampformat = "%Y-%m-%d %H:%M:%S"
ibase.dateformat = "%Y-%m-%d"
ibase.timeformat = "%H:%M:%S"
mysql.allow_local_infile = On
mysql.allow_persistent = On
mysql.cache_size = 2000
mysql.max_persistent = -1
mysql.max_links = -1
mysql.default_port =
mysql.default_socket =
mysql.default_host =
mysql.default_user =
mysql.default_password =
mysql.connect_timeout = 60
mysql.trace_mode = Off
mysqli.max_persistent = -1
mysqli.allow_persistent = On
mysqli.max_links = -1
mysqli.cache_size = 2000
mysqli.default_port = 3306
mysqli.default_socket =
mysqli.default_host =
mysqli.default_user =
mysqli.default_pw =
mysqli.reconnect = Off
mysqlnd.collect_statistics = On
mysqlnd.collect_memory_statistics = Off
pgsql.allow_persistent = On
pgsql.auto_reset_persistent = Off
pgsql.max_persistent = -1
pgsql.max_links = -1
pgsql.ignore_notice = 0
pgsql.log_notice = 0
sybct.allow_persistent = On
sybct.max_persistent = -1
sybct.max_links = -1
sybct.min_server_severity = 10
sybct.min_client_severity = 10
;sybct.timeout=
bcmath.scale = 0
session.save_handler = files
session.use_cookies = 1
session.use_only_cookies = 1
session.name = PHPSESSID
session.auto_start = 0
session.cookie_lifetime = 0
session.cookie_path = /
session.cookie_domain =
session.cookie_httponly =
session.serialize_handler = php
session.gc_probability = 1
session.gc_divisor = 1000
session.gc_maxlifetime = 1440
session.bug_compat_42 = Off
session.bug_compat_warn = Off
session.referer_check =
session.entropy_length = 0
session.entropy_file =
session.cache_limiter = nocache
session.cache_expire = 180
session.use_trans_sid = 0
session.hash_function = 0
session.hash_bits_per_character = 5
url_rewriter.tags = "a=href,area=href,frame=src,input=src,form=fakeentry"
mssql.allow_persistent = On
mssql.max_persistent = -1
mssql.max_links = -1
mssql.min_error_severity = 10
mssql.min_message_severity = 10
mssql.compatability_mode = Off
mssql.secure_connection = Off
tidy.clean_output = Off
soap.wsdl_cache_enabled=1
soap.wsdl_cache_dir="/tmp"
soap.wsdl_cache_ttl=86400
soap.wsdl_cache_limit = 5
ldap.max_links = -1


```


[B]Latest extract from Apache2 error.log (from this morning)
-----------------------------------------------------
[/B]
```

[Mon Aug 29 06:07:10 2011] [error] mod_fcgid: fcgid process manager died, restarting the server
[Mon Aug 29 06:07:20 2011] [error] child process 28121 still did not exit, sending a SIGKILL
[Mon Aug 29 06:07:21 2011] [error] child process 28127 still did not exit, sending a SIGKILL
[Mon Aug 29 06:07:24 2011] [notice] SIGHUP received.  Attempting to restart
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imagick.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Mon Aug 29 06:15:35 2011] [notice] Apache/2.2.14 (Ubuntu) mod_ssl/2.2.14 OpenSSL/0.9.8k mod_fcgid/2.3.4 PHP/5.3.2-1ubuntu4.9 with Suhosin-Patch configured -- resuming normal operations
[Mon Aug 29 06:17:57 2011] [error] [client 66.249.66.12] PHP Warning:  mysql_connect() [<a href='function.mysql-connect'>function.mysql-connect</a>]: Lost connection to MySQL server at 'waiting for initial communication packet', system error: 95 in /var/www/index.php on line 283
[Mon Aug 29 06:18:21 2011] [error] mod_fcgid: fcgid process manager died, restarting the server
[Mon Aug 29 06:18:32 2011] [error] child process 28414 still did not exit, sending a SIGKILL
[Mon Aug 29 06:18:34 2011] [error] child process 28377 still did not exit, sending a SIGKILL
[Mon Aug 29 06:18:35 2011] [error] child process 28418 still did not exit, sending a SIGKILL

------------------------------------------------------------------------------------------------------------------------------
>>>> LOTS OF THESE child process did not exit
------------------------------------------------------------------------------------------------------------------------------

[Mon Aug 29 06:18:36 2011] [notice] SIGHUP received.  Attempting to restart
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imagick.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Mon Aug 29 06:30:15 2011] [notice] Apache/2.2.14 (Ubuntu) mod_ssl/2.2.14 OpenSSL/0.9.8k mod_fcgid/2.3.4 PHP/5.3.2-1ubuntu4.9 with Suhosin-Patch configured -- resuming normal operations
[Mon Aug 29 06:31:10 2011] [error] mod_fcgid: fcgid process manager died, restarting the server
*** glibc detected *** /usr/sbin/apache2: free(): invalid pointer: 0x00007f4fe99a5e98 ***
======= Backtrace: =========
/lib/libc.so.6(+0x775b6)[0x7f4fe969e5b6]
======= Backtrace: =========
/lib/libc.so.6(+0x775b6)[0x7f4fe969e5b6]
/usr/lib/libapr-1.so.0(+0x1d049)[0x7f4fe9be4049]
/usr/sbin/apache2(+0x59cbe)[0x7f4fea4c9cbe]
/lib/libpthread.so.0(+0xf8f0)[0x7f4fe99b98f0]
/lib64/ld-linux-x86-64.so.2(+0x9a1b)[0x7f4fea257a1b]
/lib/librt.so.1(+0x21d6)[0x7f4fe921c1d6]
======= Memory map: ========
7f4fd4000000-7f4fd4021000 rw-p 00000000 00:00 0 
7f4fd4021000-7f4fd8000000 ---p 00000000 00:00 0 
7f4fda614000-7f4fda62a000 r-xp 00000000 fb:00 4718647                    /lib/libgcc_s.so.1
7f4fda62a000-7f4fda829000 ---p 00016000 fb:00 4718647                    /lib/libgcc_s.so.1
7f4fda829000-7f4fda82a000 r--p 00015000 fb:00 4718647                    /lib/libgcc_s.so.1
7f4fda82a000-7f4fda82b000 rw-p 00016000 fb:00 4718647                    /lib/libgcc_s.so.1
7f4fda82b000-7f4fda82c000 ---p 00000000 00:00 0 

------------------------------------------------------------------------------------------------------------------------------
>>>> THIS MEMORY MAP GOES ON AND ON FOR ABOUT 1000 lines of the log (Shortened)
------------------------------------------------------------------------------------------------------------------------------

[Mon Aug 29 06:31:21 2011] [error] child process 28610 still did not exit, sending a SIGKILL
[Mon Aug 29 06:31:26 2011] [notice] SIGHUP received.  Attempting to restart
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imagick.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Mon Aug 29 07:07:31 2011] [notice] Apache/2.2.14 (Ubuntu) mod_ssl/2.2.14 OpenSSL/0.9.8k mod_fcgid/2.3.4 PHP/5.3.2-1ubuntu4.9 with Suhosin-Patch configured -- resuming normal operations
[Mon Aug 29 07:07:39 2011] [error] mod_fcgid: fcgid process manager died, restarting the server
[Mon Aug 29 07:07:48 2011] [error] child process 28905 still did not exit, sending a SIGKILL
[Mon Aug 29 07:07:48 2011] [error] child process 28906 still did not exit, sending a SIGKILL
[Mon Aug 29 07:07:48 2011] [error] child process 28907 still did not exit, sending a SIGKILL
[Mon Aug 29 07:07:48 2011] [error] child process 28908 still did not exit, sending a SIGKILL
[Mon Aug 29 07:07:48 2011] [error] child process 28909 still did not exit, sending a SIGKILL
[Mon Aug 29 07:07:49 2011] [error] could not make child process 28906 exit, attempting to continue anyway
[Mon Aug 29 07:07:49 2011] [error] could not make child process 28908 exit, attempting to continue anyway
[Mon Aug 29 07:07:49 2011] [error] could not make child process 28909 exit, attempting to continue anyway
[Mon Aug 29 07:07:49 2011] [notice] SIGHUP received.  Attempting to restart
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/imagick.ini on line 1 in Unknown on line 0
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Mon Aug 29 07:35:24 2011] [notice] Apache/2.2.14 (Ubuntu) mod_ssl/2.2.14 OpenSSL/0.9.8k mod_fcgid/2.3.4 PHP/5.3.2-1ubuntu4.9 with Suhosin-Patch configured -- resuming normal operations
[Mon Aug 29 07:36:22 2011] [error] [client 62.141.36.214] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.DFind:)
[Mon Aug 29 07:37:13 2011] [error] mod_fcgid: fcgid process manager died, restarting the server
[Mon Aug 29 07:37:30 2011] [error] child process 29337 still did not exit, sending a SIGKILL
[Mon Aug 29 07:37:31 2011] [error] child process 29334 still did not exit, sending a SIGKILL
[Mon Aug 29 07:37:31 2011] [error] child process 29335 still did not exit, sending a SIGKILL


```

---

### Post by Entilza on 2011-08-29
The default cron.daily runs at 6:25 When I read 6 am I thought maybe something there.  But it looks like it's earlier but you may want to check.

Is it every day or sometimes?  Can you script to shutdown your webserver at 6:00am then restart at 6:30am or something?  I know it sounds silly but maybe a different way to 'solve' this issue at least temporarily?

---

### Post by ravingmad on 2011-08-29
Thanks Dinu and Entilza for the replies

Entilza - I have scripted Apache to restart every hour but will consider your option only when all else fails, I really want to know which php script or joomla component may be doing this.

Dinu - thanks for the suggestion, I have scripted the bash file and have it running. I ran into a problem with the date syntax and the syntax of the wget line and eventually got it to work with the following:

```

mydate=$(date +%H_%M_%S)
wget --output-file=/var/log/apachemon/apache_status_$mydate http://localhost/server-status

```

But now I have a problem getting any detailed output from server-status. All I get returned is:

```

Saving to: `server-status.12'

     0K ......                                                100%  381M=0s

2011-08-29 20:45:01 (381 MB/s) - `server-status.12' saved [7051/7051

```

I am running Apache 2.2.14 and there is no extended-status module, on some forum someone mentioned that the "info" module is the extended-status module in Apache 2.2. I have both info and status modules enabled but am not getting any details with server-status ????? and now I am stumped a bit.

---

### Post by ravingmad on 2011-08-29
I managed to finally get it all working with the following bash script:

```

#!/bin/sh

mkdir -p /var/log/apachemon
mydate=$(date +%H_%M)

/usr/sbin/apache2ctl fullstatus > /var/log/apachemon/apache_status_$mydate.log
top -b -n 1 > /var/log/apachemon/top_$mydate.log
netstat -anp > /var/log/apachemon/netstat_$mydate.log
ps -efww > /var/log/apachemon/ps_$mydate.log
free > /var/log/apachemon/free_$mydate.log
w > /var/log/apachemon/w_$mydate.log

```

Will now have to wait and see what I can track down in all the many hundreds of log files tomorrow morning :)

---

### Post by ravingmad on 2011-08-30
Dinu,

I think I tracked down the problem. I have a cron script that runs at 6am that does rss content item feeds into a joomla site. It's about the only culprit I can identify that occurs at the exact time the server dies. Thanks to all the many logs I was able to at least see what the hell is going on.

I have set this same cron to run today during the day at 3 different intervals to see if it happens again. Also the site concerned had it's jos_session database damaged when this happened which also leads me to believe this particular web site is the culprit. Will know later today for sure if the cron job I am running is causing the server crashes. If not then I'll have to wait again until 6am to see if it happens again with this cron now removed from the equation.

Thanks again for your help, that bash script really helps to track down what's going on.

---

### Post by ravingmad on 2011-08-31
I don't want to say I'm out of the woods just yet but it sure does appear that way. This morning at 6am everything kept running smoothly with the particular cron script now changed to a different time. 

I'll see what tomorrow morning brings and if it happens to all continue smoothly again I'll mark this thread as solved. I would not have easily found this offending php script without Dinu's help with the bash script to log everything every minute. So thanks again Dinu that bash script is invaluable at diagnosing problems.

---

### Post by ravingmad on 2011-10-18
Thanks again to Dinu90 for his help with this problem, I have now marked this thread solved as Dinu90's suggestions helped me to track down a Cronjob that was the cause of my Apache/Server dying every morning. 

The particular cronjob was from the 4rss joomla component which checks RSS feeds and posts the articles to a joomla site automatically. I scheduled this cronjob to run at times other than 6am in the morning and it's never happened again. Hope this helps others who may run into similar problems.

---

