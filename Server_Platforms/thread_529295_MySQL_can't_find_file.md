---
title: "MySQL can't find file"
date: 2007-08-19
forum: Server Platforms
---

### Post by antisho on 2007-08-19
I'm having trouble with MySQL... it seems to be broken. Running mysql gives
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```
Running service mysql start gives
```
 * Starting MySQL database server mysqld                                 [fail] 
```
Running mysql_install_db gives
```
Installing MySQL system tables...
ERROR: 1062  Duplicate entry '%-test-' for key 1
070819  1:36:26 [ERROR] Aborting

070819  1:36:26 [Note] /usr/sbin/mysqld: Shutdown complete

Installation of system tables failed!

Examine the logs in /var/lib/mysql/mysql for more information.
You can try to start the mysqld daemon with:
/usr/sbin/mysqld --skip-grant &
and use the command line tool
/usr/bin/mysql to connect to the mysql
database and look at the grant tables:

shell> /usr/bin/mysql -u root mysql
mysql> show tables

Try 'mysqld --help' if you have problems with paths. Using --log
gives you a log in /var/lib/mysql/mysql that may be helpful.

The latest information about MySQL is available on the web at
http://www.mysql.com
Please consult the MySQL manual section: 'Problems running mysql_install_db',
and the manual section that describes problems on your OS.
Another information source is the MySQL email archive.
Please check all of the above before mailing us!
And if you do mail us, you MUST use the /usr/bin/mysqlbug script!
```
Running mysqld_safe gives simply
```
Starting mysqld daemon with databases from /var/lib/mysql/mysql
mysqld_safe[13095]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[13101]: ended
```
And running mysqld gives
```
070819  1:25:29 [Warning] One can only use the --user switch if running as root
070819  1:25:29  InnoDB: Database was not shut down normally!
InnoDB: Starting crash recovery.
InnoDB: Reading tablespace information from the .ibd files...
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/db.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/db.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/db.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/host.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/host.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/host.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/user.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/user.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/user.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/func.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/func.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/func.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/tables_priv.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/tables_priv.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/tables_priv.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/columns_priv.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/columns_priv.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/columns_priv.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/help_topic.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/help_topic.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/help_topic.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/help_category.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/help_category.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/help_category.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/help_relation.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/help_relation.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/help_relation.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/help_keyword.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/help_keyword.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/help_keyword.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/time_zone_name.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/time_zone_name.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/time_zone_name.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/time_zone.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/time_zone.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/time_zone.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/time_zone_transition.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/time_zone_transition.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/time_zone_transition.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/time_zone_transition_type.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/time_zone_transition_type.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/time_zone_transition_type.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/time_zone_leap_second.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/time_zone_leap_second.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/time_zone_leap_second.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/proc.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/proc.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/proc.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/procs_priv.frm
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/procs_priv.MYI
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./mysql/procs_priv.MYD
InnoDB: File operation call: 'stat'.
InnoDB: Error: os_file_readdir_next_file() returned -1 in
InnoDB: directory ./mysql
InnoDB: Crash recovery may have failed for some .ibd files!
InnoDB: Restoring possible half-written data pages from the doublewrite
InnoDB: buffer...
070819  1:25:29  InnoDB: Starting log scan based on checkpoint at
InnoDB: log sequence number 0 36808.
InnoDB: Doing recovery: scanned up to log sequence number 0 43655
070819  1:25:29  InnoDB: Starting an apply batch of log records to the database...
InnoDB: Progress in percents: 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96 97 98 99 
InnoDB: Apply batch completed
070819  1:25:30  InnoDB: Started; log sequence number 0 43655
070819  1:25:30 [ERROR] mysqld: Can't find file: './mysql/host.frm' (errno: 13)
070819  1:25:30 [ERROR] mysqld: Can't find file: './mysql/host.frm' (errno: 13)
070819  1:25:30 [ERROR] Fatal error: Can't open and lock privilege tables: Can't find file: './mysql/host.frm' (errno: 13)
```
Any help would be appreciated!

---

### Post by antisho on 2007-08-19
Also, there's no sign of a mysqld.sock anywhere in my system.

---

### Post by killerdragon on 2007-08-19
> InnoDB: Reading tablespace information from the .ibd files...
070819  1:25:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.

That tells me that the permissions got screwed up for the file its trying to access...or you deleted the mysql user.

If you don't have anything important on the mysql server, I would reinstall it.

---

### Post by antisho on 2007-08-19
I've tried removing all the MySQL packages and reinstalling. It tells me it can't finish configuring, so it doesn't completely install.

---

### Post by don durito on 2007-08-21
i have got the same problem here after updateting my appache through the repos.

running mysql gives me:
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```
any help would realy be appreachiated

---

### Post by antisho on 2007-08-23
I actually gave up on MySQL and moved to PostgreSQL... which is (hopefully) working fine now. :)

---

