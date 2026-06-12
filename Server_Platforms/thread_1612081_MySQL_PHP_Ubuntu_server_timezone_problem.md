---
title: "MySQL /PHP/ Ubuntu server timezone problem"
date: 2010-11-02
forum: Server Platforms
---

### Post by pdc124 on 2010-11-02
ive got a timesheet MySQL/PHP app running on ubuntu 10.04 LTS

Since the clocks have gone back in the UK , times entered before Sunday have been shifted  back an hour.
the date /time string (yyyy-mm-dd hh:mm:ss) in the DB is OK eg 800-1700 but it is displaying since sunday as 0700-1600. last week the display was correct

this is the server
# date
Tue Nov  2 21:26:05 GMT 2010


when I look at MySQL variables (in phpmyadmin - Ive not found an easy way of listing them from CLI)

time zone = system
and  
system time zone = BST

so mysql thinks the system time zone is BST when it isn't.
Ive restarted the database to see if it picks up the new time , but it hasnt.

Anyone know how to fix this ?

---

### Post by wongo888 on 2010-11-03
Set your system timezone (using sudo):

```
$ sudo dpkg-reconfigure tzdata

Current default time zone: 'Etc/UTC'
Local time is now:      Wed Nov  3 07:54:23 UTC 2010.
Universal Time is now:  Wed Nov  3 07:54:23 UTC 2010.

```

If mysql time_zone is set as SYSTEM then it should pull the tz info from the system. You may want to view your my.cnf file and check that it is not overriding things. In my config file, it also reads additional configs from /etc/mysql/conf.d/

More at: [http://dev.mysql.com/doc/refman/5.1/en/server-system-variables.html#sysvar_time_zone](http://dev.mysql.com/doc/refman/5.1/en/server-system-variables.html#sysvar_time_zone)

You can view time related configs using:

```
# mysqladmin -u root -pYourPassword variables | grep time_zone
# mysqld --verbose --help | grep time_zone

```

---

### Post by Ryan Dwyer on 2010-11-03
Don't forget PHP has its own timezone settings as well. Create a phpinfo script to check what timezone it's using. Configure it in /etc/php5/apache2/php.ini.

---

### Post by pdc124 on 2010-11-03
i ran $ sudo dpkg-reconfigure tzdata and set the TZ to Europe/London

> Current default timezone: 'Europe/London'
Local time is now:      Wed Nov  3 19:49:06 GMT 2010.
Universal Time is now:  Wed Nov  3 19:49:06 UTC 2010.

> ~$ mysqladmin -u root -p variables | grep time_zone
Enter password: 
| system_time_zone                | GMT                         |
| time_zone                       | SYSTEM                      
> 
#:/etc/php5# mysqladmin -u root -p variables | grep time 
Enter password: 
| connect_timeout                 | 5                           |
| datetime_format                 | %Y-%m-%d %H:%i:%s           |
| delayed_insert_timeout          | 300                         |
| flush_time                      | 0                           |
| innodb_lock_wait_timeout        | 50                          |
| innodb_rollback_on_timeout      | OFF                         |
| interactive_timeout             | 28800                       |
| lc_time_names                   | en_US                       |
| long_query_time                 | 10                          |
| ndb_cache_check_time            | 0                           |
| net_read_timeout                | 30                          |
| net_write_timeout               | 60                          |
| slave_net_timeout               | 3600                        |
| slow_launch_time                | 2                           |
| system_time_zone                | GMT                         |
| table_lock_wait_timeout         | 50                          |
| time_format                     | %H:%i:%s                    |
| time_zone                       | SYSTEM                      |
| timed_mutexes                   | OFF                         |
| wait_timeout                    | 28800                       |
*:/etc/php5# 
*:/etc/php5# mysqladmin -u root -p variables | grep time 
Enter password: 
| connect_timeout                 | 5                           |
| datetime_format                 | %Y-%m-%d %H:%i:%s           |
| delayed_insert_timeout          | 300                         |
| flush_time                      | 0                           |
| innodb_lock_wait_timeout        | 50                          |
| innodb_rollback_on_timeout      | OFF                         |
| interactive_timeout             | 28800                       |
| lc_time_names                   | en_US                       |
| long_query_time                 | 10                          |
| ndb_cache_check_time            | 0                           |
| net_read_timeout                | 30                          |
| net_write_timeout               | 60                          |
| slave_net_timeout               | 3600                        |
| slow_launch_time                | 2                           |
| system_time_zone                | GMT                         |
| table_lock_wait_timeout         | 50                          |
| time_format                     | %H:%i:%s                    |
| time_zone                       | SYSTEM                      |
| timed_mutexes                   | OFF                         |
| wait_timeout                    | 28800                       |
root@server:/etc/php5# 



ive restarted mysql and apache. 

Still got the problem - dates before 2010-10-30  are still time-shifted back by 1 hour 

mysqld --verbose --help | grep time_zone 

has no output 

phpinfo has nothing about time /timezones 


> :~# grep -r 'time' /etc/mysql/
/etc/mysql/my.cnf:#long_query_time = 2
root@server:~# 

root@server:~# grep ^[a-z] /etc/mysql/my.cnf
port		= 3306
socket		= /var/run/mysqld/mysqld.sock
socket		= /var/run/mysqld/mysqld.sock
nice		= 0
user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
skip-external-locking
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8
query_cache_limit       = 1M
query_cache_size        = 16M
expire_logs_days	= 10
max_binlog_size         = 100M
skip-bdb
quick
quote-names
max_allowed_packet	= 16M
key_buffer		= 16M
root@server:~# 

root@server:~# grep -r time /etc/mysql/
/etc/mysql/my.cnf:#long_query_time = 2
/etc/mysql/my.cnf~:#long_query_time = 2
root@server:~# 

and scanning the php directory 
> :/etc/php5# grep -r time /etc/php5/  | grep -v ';'
/etc/php5/apache2/php.ini:allow_call_time_pass_reference = On
/etc/php5/apache2/php.ini:magic_quotes_runtime = Off
/etc/php5/apache2/php.ini:default_socket_timeout = 60
/etc/php5/apache2/php.ini:mysql.connect_timeout = 60
/etc/php5/apache2/php.ini:session.cookie_lifetime = 0
/etc/php5/apache2/php.ini:session.gc_maxlifetime = 1440
/etc/php5/cli/php.ini:allow_call_time_pass_reference = On
/etc/php5/cli/php.ini:magic_quotes_runtime = Off
/etc/php5/cli/php.ini:default_socket_timeout = 60
/etc/php5/cli/php.ini:mysql.connect_timeout = 60
/etc/php5/cli/php.ini:session.cookie_lifetime = 0
/etc/php5/cli/php.ini:session.gc_maxlifetime = 1440
root@server:/etc/php5# 

Ive added date.time_zone=Europe/London to php.ini and restarted apache. Still not solved 


and ive still got the problem !

---

### Post by wongo888 on 2010-11-03
It might be a programmatic problem especially if it is a bespoke/custom app. Check if the field is a DATETIME or a TIMESTAMP and ensure that the type is appropriate to the intended result.

[http://stackoverflow.com/questions/1053252/having-timezone-problems-with-php-and-mysql](http://stackoverflow.com/questions/1053252/having-timezone-problems-with-php-and-mysql)

[http://dev.mysql.com/doc/refman/5.1/en/datetime.html](http://dev.mysql.com/doc/refman/5.1/en/datetime.html)

---

### Post by pdc124 on 2010-11-04
the DB field is datatime
in pulling the data it retrieves 

start_time AS start_time_str, end_time AS end_time_str,			unix_timestamp(start_time) AS start_stamp, unix_timestamp(end_time) AS end_stamp,

and then does calculations with start_stamp, end_stamp

with System TZ =GMT MySQL TZ=System and MySQL systemTZ now reports GMT

I've tried setting TZ in php.ini, to UTC but that didnt fix it.

So at the moment I want it to ignore TZ settings and just report the dates/times and entered in the db. I *think* its a PHP/script problem.
 for some real data 

when it was BST 

$data['start_time_str'] - 2010-10-04 08:00:00
$data['start_stamp'] - 12861756008601
8601 date (date('c',$data['start_stamp'])  - 2010-10-04T07:00:00+00:00
TZ date('e',$data['start_stamp']); - UTC 
date(I) date('I',$data['start_stamp']) - 0

data from  GMT
	
	
2010-11-04 06:00:00 
start_stamp 12888504008601 
8601 date :2010-11-04T06:00:00+00:00, 
TZ :UTC 
date (I) :0

I cant see where to identify  whether or not its BST or GMT

---

