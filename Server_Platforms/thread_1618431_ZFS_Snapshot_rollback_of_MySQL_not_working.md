---
title: "ZFS Snapshot rollback of MySQL not working"
date: 2010-11-10
forum: Server Platforms
---

### Post by bundacia on 2010-11-10
I'm trying to test out using zfs snapshots to backup a mysql server. I start up the mysql server using a zfs filesystem for the data directory. Then I create a database and table, stick 500 rows in the table, then stop mysql and take a snapshot. Next I start the mysql server back up, and add 500 more rows. Finally, stop mysql again, rollback to the snapshot and check to see how many rows are in that table. I expect to see just 500, but all 1000 are still there. What's weird is that I can see that the files in the mysql datadir do get rolled back because their timestamps change.

Anyway, any help you could provide would be great. Here's the full output of the steps I just described. I'm using mysql 5.1 and  zfs-fuse.

```
tlittle@ubuntu ~ $ sudo zfs list -t all
NAME            USED  AVAIL  REFER  MOUNTPOINT
pool1          22.2M  4.87G    21K  /pool1
pool1/mysql    22.1M  4.87G  21.0M  /var/lib/mysql
pool1/mysql@1  1.16M      -  21.0M  -
tlittle@ubuntu ~ $ sudo service mysql start
mysql start/running, process 18220
tlittle@ubuntu ~ $ mysql -uroot -pXXXX -e "drop database if exists test; create database test";
tlittle@ubuntu ~ $ mysql -uroot -pXXXX test -e 'CREATE TABLE `time` ( `id` int(11) NOT NULL AUTO_INCREMENT, `time` datetime NOT NULL, PRIMARY KEY (`id`)) ENGINE=InnoDB';
tlittle@ubuntu ~ $ for i in {1..500}; do mysql -uroot -pXXXX test -e "insert into time values (null, now())"; done;
tlittle@ubuntu ~ $ mysql -uroot -pXXXX test -e 'select * from time order by id desc limit 1'
+-----+---------------------+
| id  | time                |
+-----+---------------------+
| 500 | 2010-11-10 13:10:15 |
+-----+---------------------+
tlittle@ubuntu ~ $ sudo service mysql stop
mysql stop/waiting
tlittle@ubuntu ~ $ sudo ls -l /var/lib/mysql/
total 20496
-rw-r--r-- 1 root  root         0 2010-11-10 12:18 debian-5.1.flag
-rw-rw---- 1 mysql mysql 10485760 2010-11-10 13:10 ibdata1
-rw-rw---- 1 mysql mysql  5242880 2010-11-10 13:10 ib_logfile0
-rw-rw---- 1 mysql mysql  5242880 2010-11-10 12:18 ib_logfile1
drwx------ 2 mysql root        71 2010-11-10 12:18 mysql
-rw-rw---- 1 root  root         6 2010-11-10 12:18 mysql_upgrade_info
drwx------ 2 mysql mysql        4 2010-11-10 13:10 test
tlittle@ubuntu ~ $ sudo zfs snapshot pool1/mysql@1
cannot create snapshot 'pool1/mysql@1': dataset already exists
tlittle@ubuntu ~ $ sudo zfs destroy pool1/mysql@1
tlittle@ubuntu ~ $ sudo zfs snapshot pool1/mysql@1
tlittle@ubuntu ~ $ sudo service mysql start
mysql start/running, process 18810
tlittle@ubuntu ~ $ for i in {501..1000}; do mysql -uroot -pXXXX test -e "insert into time values (null, now())"; done;
tlittle@ubuntu ~ $ mysql -uroot -pXXXX test -e 'select * from time order by id desc limit 1'
+------+---------------------+
| id   | time                |
+------+---------------------+
| 1000 | 2010-11-10 13:11:01 |
+------+---------------------+
tlittle@ubuntu ~ $ sudo service mysql stop
mysql stop/waiting
tlittle@ubuntu ~ $ sudo ls -l /var/lib/mysql/
total 20497
-rw-r--r-- 1 root  root         0 2010-11-10 12:18 debian-5.1.flag
-rw-rw---- 1 mysql mysql 10485760 2010-11-10 13:11 ibdata1
-rw-rw---- 1 mysql mysql  5242880 2010-11-10 13:11 ib_logfile0
-rw-rw---- 1 mysql mysql  5242880 2010-11-10 12:18 ib_logfile1
drwx------ 2 mysql root        71 2010-11-10 12:18 mysql
-rw-rw---- 1 root  root         6 2010-11-10 12:18 mysql_upgrade_info
drwx------ 2 mysql mysql        4 2010-11-10 13:10 test
tlittle@ubuntu ~ $ sudo zfs rollback pool1/mysql@1
tlittle@ubuntu ~ $ sudo ls -l /var/lib/mysql/
total 20497
-rw-r--r-- 1 root  root         0 2010-11-10 12:18 debian-5.1.flag
-rw-rw---- 1 mysql mysql 10485760 2010-11-10 13:10 ibdata1
-rw-rw---- 1 mysql mysql  5242880 2010-11-10 13:10 ib_logfile0
-rw-rw---- 1 mysql mysql  5242880 2010-11-10 12:18 ib_logfile1
drwx------ 2 mysql root        71 2010-11-10 12:18 mysql
-rw-rw---- 1 root  root         6 2010-11-10 12:18 mysql_upgrade_info
drwx------ 2 mysql mysql        4 2010-11-10 13:10 test
tlittle@ubuntu ~ $ sudo service mysql start
mysql start/running, process 19396
tlittle@ubuntu ~ $ sudo ls -l /var/lib/mysql/
total 20498
-rw-r--r-- 1 root  root         0 2010-11-10 12:18 debian-5.1.flag
-rw-rw---- 1 mysql mysql 10485760 2010-11-10 13:10 ibdata1
-rw-rw---- 1 mysql mysql  5242880 2010-11-10 13:11 ib_logfile0
-rw-rw---- 1 mysql mysql  5242880 2010-11-10 12:18 ib_logfile1
drwx------ 2 mysql root        71 2010-11-10 12:18 mysql
-rw-rw---- 1 root  root         6 2010-11-10 12:18 mysql_upgrade_info
drwx------ 2 mysql mysql        4 2010-11-10 13:10 test
-rw-rw---- 1 mysql mysql        6 2010-11-10 13:11 ubuntu.pid
tlittle@ubuntu ~ $ mysql -uroot -pXXXX test -e 'select * from time order by id desc limit 1';
+------+---------------------+
| id   | time                |
+------+---------------------+
| 1000 | 2010-11-10 13:11:01 |
+------+---------------------+

```

---

