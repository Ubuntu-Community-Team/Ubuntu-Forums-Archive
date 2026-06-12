---
title: "[SOLVED] mysql datadir permissions issue with Hardy"
date: 2008-09-24
forum: Server Platforms
---

### Post by TomB19 on 2008-09-24
I have a mysql datadir permissions issue

I know about AppArmor and have configured it accordingly.  Thank you to those who left that knowledge in this database.

I have a datadir from a previous install on a huge RAID array.  In the past, I have been able to reinstall, reconfigure, and point mysql to the old datadir.  Everything was fine.

Now, that doesn't work.

```

Sep 23 22:34:17 localhost mysqld_safe[21636]: started
Sep 23 22:34:17 localhost mysqld[21639]: 080923 22:34:17  InnoDB: Started; log sequence number 0 43735
Sep 23 22:34:17 localhost mysqld[21639]: 080923 22:34:17 [ERROR] Fatal error: Can't open and lock privilege tables: Table 'host' is read only
Sep 23 22:34:17 localhost mysqld_safe[21651]: ended

```

The permissions look fine to me.

```

# ls -l
total 716
-rw-rw---- 1 mysql mysql   8820 2008-09-20 15:19 columns_priv.frm
-rw-rw---- 1 mysql mysql  17820 2008-09-20 15:19 columns_priv.MYD
-rw-rw---- 1 mysql mysql   5120 2008-09-20 15:19 columns_priv.MYI
-rw-rw---- 1 mysql mysql   9494 2008-09-20 15:19 db.frm
-rw-rw---- 1 mysql mysql  11826 2008-09-20 15:19 db.MYD
-rw-rw---- 1 mysql mysql   4096 2008-09-20 15:19 db.MYI
-rw-rw---- 1 mysql mysql   8665 2008-09-20 15:19 func.frm
-rw-rw---- 1 mysql mysql      0 2008-09-20 15:19 func.MYD
-rw-rw---- 1 mysql mysql   1024 2008-09-20 15:19 func.MYI
-rw-rw---- 1 mysql mysql   8700 2008-05-10 19:14 help_category.frm
-rw-rw---- 1 mysql mysql   1048 2008-05-10 19:14 help_category.MYD
-rw-rw---- 1 mysql mysql   3072 2008-05-10 19:14 help_category.MYI
-rw-rw---- 1 mysql mysql   8612 2008-05-10 19:14 help_keyword.frm
-rw-rw---- 1 mysql mysql   8228 2008-05-10 19:14 help_keyword.MYD
-rw-rw---- 1 mysql mysql  14336 2008-05-10 19:14 help_keyword.MYI
-rw-rw---- 1 mysql mysql   8630 2008-05-10 19:14 help_relation.frm
-rw-rw---- 1 mysql mysql   7281 2008-05-10 19:14 help_relation.MYD
-rw-rw---- 1 mysql mysql  15360 2008-05-10 19:14 help_relation.MYI
-rw-rw---- 1 mysql mysql   8770 2008-05-10 19:14 help_topic.frm
-rw-rw---- 1 mysql mysql 333276 2008-05-10 19:14 help_topic.MYD
-rw-rw---- 1 mysql mysql  18432 2008-05-10 19:14 help_topic.MYI
-rw-rw---- 1 mysql mysql   9416 2008-09-20 15:19 host.frm
-rw-rw---- 1 mysql mysql      0 2008-09-20 15:19 host.MYD
-rw-rw---- 1 mysql mysql   1024 2008-09-20 15:19 host.MYI
-rw-rw---- 1 mysql mysql   9691 2008-09-20 15:19 proc.frm
-rw-rw---- 1 mysql mysql      0 2008-09-20 15:19 proc.MYD
-rw-rw---- 1 mysql mysql   1024 2008-09-20 15:19 proc.MYI
-rw-rw---- 1 mysql mysql   8875 2008-09-20 15:19 procs_priv.frm
-rw-rw---- 1 mysql mysql      0 2008-09-20 15:19 procs_priv.MYD
-rw-rw---- 1 mysql mysql   1024 2008-09-20 15:19 procs_priv.MYI
-rw-rw---- 1 mysql mysql   8947 2008-09-20 15:19 tables_priv.frm
-rw-rw---- 1 mysql mysql   2553 2008-09-20 15:19 tables_priv.MYD
-rw-rw---- 1 mysql mysql   5120 2008-09-20 15:19 tables_priv.MYI
-rw-rw---- 1 mysql mysql   8636 2008-05-10 19:14 time_zone.frm
-rw-rw---- 1 mysql mysql   8624 2008-05-10 19:14 time_zone_leap_second.frm
-rw-rw---- 1 mysql mysql      0 2008-05-10 19:14 time_zone_leap_second.MYD
-rw-rw---- 1 mysql mysql   1024 2008-05-10 19:14 time_zone_leap_second.MYI
-rw-rw---- 1 mysql mysql      0 2008-05-10 19:14 time_zone.MYD
-rw-rw---- 1 mysql mysql   1024 2008-05-10 19:14 time_zone.MYI
-rw-rw---- 1 mysql mysql   8606 2008-05-10 19:14 time_zone_name.frm
-rw-rw---- 1 mysql mysql      0 2008-05-10 19:14 time_zone_name.MYD
-rw-rw---- 1 mysql mysql   1024 2008-05-10 19:14 time_zone_name.MYI
-rw-rw---- 1 mysql mysql   8686 2008-05-10 19:14 time_zone_transition.frm
-rw-rw---- 1 mysql mysql      0 2008-05-10 19:14 time_zone_transition.MYD
-rw-rw---- 1 mysql mysql   1024 2008-05-10 19:14 time_zone_transition.MYI
-rw-rw---- 1 mysql mysql   8748 2008-05-10 19:14 time_zone_transition_type.frm
-rw-rw---- 1 mysql mysql      0 2008-05-10 19:14 time_zone_transition_type.MYD
-rw-rw---- 1 mysql mysql   1024 2008-05-10 19:14 time_zone_transition_type.MYI
-rw-rw---- 1 mysql mysql  10330 2008-09-20 15:19 user.frm
-rw-rw---- 1 mysql mysql   2164 2008-09-20 15:19 user.MYD
-rw-rw---- 1 mysql mysql   2048 2008-09-20 15:19 user.MYI

```

The only way I can get mysql to start is by setting 'user=root' in my.cfg.

I've been up for a long time, trying to install this server, but I can't see any issue that should stop mysql from running as a user.

Even though I don't believe the problem is AppArmor, I did a 'aa-complain /etc/apparmor.d/usr.sbin.mysqld' to be sure.  It didn't help.

Any ideas on how to sort this out would be greatly appreciated!

---

### Post by TomB19 on 2008-09-24
It's getting interesting.

For a laugh, I tried changing the mysql user to root.  It worked.

Further testing has revealed an interesting issue with a mdadm mounted volume.


For datadir=/mnt/data/server/mysql

# su mysql
$ ls -l /mnt/data/server
ls: cannot access /mnt/data/server/www: Permission denied
ls: cannot access /mnt/data/server/mysql: Permission denied
ls: cannot access /mnt/data/server/tftp: Permission denied
total 0
d????????? ? ? ? ?                ? mysql
d????????? ? ? ? ?                ? tftp
d????????? ? ? ? ?                ? www
$ ls /mnt/data/server/mysql
ls: cannot access /mnt/data/server/mysql: Permission denied
$

:confused:

---

### Post by TomB19 on 2008-09-24
Here's what those directories look like from root.

/mnt/data/server# ls -l
total 12
drwxr-xr-x 22 mysql    mysql    4096 2008-09-23 22:48 mysql
drwxr-xr-x  3 nobody   nogroup  4096 2008-09-20 23:03 tftp
drwxrw-rw- 18 www-data www-data 4096 2008-05-10 19:07 www
/mnt/data/server# ls -l mysql
total 20752
drwx------ 2 mysql mysql    16384 2008-05-10 19:08 alpacaledger
drwx------ 2 mysql mysql     4096 2008-06-02 21:52 bacula
drwx------ 2 mysql mysql     4096 2008-05-10 19:08 cacti
drwx------ 2 mysql mysql    12288 2008-05-10 19:08 carlson
drwx------ 2 mysql mysql    57344 2008-05-10 19:08 carlsonspeed
drwx------ 2 mysql mysql    12288 2008-05-10 19:08 danceregina
drwx------ 2 mysql mysql     4096 2008-05-10 19:08 dancesask
drwx------ 2 mysql mysql     4096 2008-05-10 19:08 dorothykopeck
drwx------ 2 mysql mysql    20480 2008-05-10 19:08 gm-marine
drwx------ 2 mysql mysql    16384 2008-05-10 19:08 havasubarney
drwx------ 2 mysql mysql    24576 2008-05-10 19:08 houseofboatparts
drwx------ 2 mysql mysql     4096 2008-05-10 19:08 huntersigns
-rw-r----- 1 mysql mysql 10485760 2008-09-23 22:48 ibdata1
-rw-r----- 1 mysql mysql  5242880 2008-09-23 22:48 ib_logfile0
-rw-r----- 1 mysql mysql  5242880 2008-05-10 19:14 ib_logfile1
drwx------ 2 mysql mysql     4096 2008-05-10 19:08 lylegrainger
drwx------ 2 mysql mysql     4096 2008-05-10 19:08 mail
drwxr-xr-x 2 mysql mysql     4096 2008-09-20 15:19 mysql
-rw------- 1 mysql mysql        7 2008-09-20 15:19 mysql_upgrade_info
-rw------- 1 mysql mysql        4 2008-05-10 19:14 mysql_upgrade.info
drwx------ 2 mysql mysql    16384 2008-06-28 13:45 mythconverg
drwx------ 2 mysql mysql     4096 2008-05-10 19:08 pmadb
drwx------ 2 mysql mysql     4096 2008-05-10 19:08 test
drwx------ 2 mysql mysql     4096 2008-05-10 19:08 thompsonmachine
drwx------ 2 mysql mysql     4096 2008-05-10 19:08 ua_mba_phpbb
/mnt/data/server#

---

### Post by alastair on 2008-09-24
For permission issues, remember to always consider all containing directories - their permissions also permit/deny access to dis within i.e. r-x to list contents. So "ls -al" is also better - to show "." and "..". This includes the mount point.

Alastair

---

### Post by TomB19 on 2008-09-24
Thanks, alastair.

It turned out, I did not have the execute bit set so it could not traverse into the directory.  I thought I had all bits set, at one point during the debug process, but perhaps I am confused with one of the other re-installs I did on that box in the last week in attempt to get it to work.

The thing that threw me off is the question marks.  I've never heard of that behavior before.


Once again, thanks!  :)

---

### Post by sds on 2008-12-16
Sorry for bringing up an old topic. 

I'm having the exact same problem (running 8.04 Server) and can't seem to fix it. 
Permissions are exactly the same between the old and new data directory and it works fine when the mysql user is set to root in my.cnf. 

When you say you did not have the execute bit set, where did it need to be set? These are permissions from the data directory.

```

sunil@ss:~$ ls -al /mnt/store/mysql/
total 28764
drwxr-xr-x 10 mysql   mysql     4096 2008-12-17 00:19 .
drwxrwxr-- 10 network samba     4096 2008-12-16 23:27 ..
-rw-r--r--  1 mysql   mysql        0 2008-11-30 22:51 debian-5.0.flag
-rw-rw----  1 mysql   mysql 18874368 2008-12-17 00:18 ibdata1
-rw-rw----  1 mysql   mysql  5242880 2008-12-17 00:19 ib_logfile0
-rw-rw----  1 mysql   mysql  5242880 2008-12-17 00:19 ib_logfile1
drwxrwxrwx  2 mysql   mysql     4096 2008-11-30 22:40 mysql
-rw-------  1 mysql   mysql        6 2008-11-30 22:51 mysql_upgrade_info
drwxr-xr-x  2 mysql   mysql     4096 2008-11-30 22:52 project
drwxr-xr-x  2 mysql   mysql     4096 2008-11-30 22:52 project2
drwxr-xr-x  2 mysql   mysql     4096 2008-11-30 22:52 project3
drwxr-xr-x  2 mysql   mysql     4096 2008-11-30 22:52 project_actual
drwxr-xr-x  2 mysql   mysql     4096 2008-11-30 22:52 project_original_data
drwxr-xr-x  2 mysql   mysql     4096 2008-11-30 22:52 S21klRSh
drwxr-xr-x  2 mysql   mysql     4096 2008-11-30 22:52 sitarato
```

---

