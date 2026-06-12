---
title: "lampp mysql move datadir"
date: 2009-10-16
forum: Server Platforms
---

### Post by michiedo on 2009-10-16
I've installed LAMPP , tested it, it works ok (no surprise)
Then i (try to) change my datadir, that's something i've already done in the past, but now it's driving me crazy :-(

it simply does not works !
i've put "datadir = /mnt/NTFS/MySQL_data" in /opt/lampp/etc/my.cnf
as i've done in the past

sudo /opt/lampp/lampp start
-> all ok
sudo /opt/lampp/lampp status
Version: XAMPP for Linux 1.7.2                                    
Apache is running.                                                
MySQL is not running.    <-- are you kidding ?

ps aux|grep ql
root     31182  0.0  0.0   1872   552 pts/1    S    15:35   0:00 /bin/sh /opt/lampp/bin/mysqld_safe --datadir=/mnt/NTFS/MySQL_data --pid-file=/mnt/NTFS/MySQL_data/kubuntu9.pid
nobody   31334  0.0  1.1 127096 23080 pts/1    Sl   15:35   0:00 /opt/lampp/sbin/mysqld --basedir=/opt/lampp --datadir=/mnt/NTFS/MySQL_data --user=nobody --log-error=/mnt/NTFS/MySQL_data/kubuntu9.err --pid-file=/mnt/NTFS/MySQL_data/kubuntu9.pid --socket=/opt/lampp/var/mysql/mysql.sock --port=3306

so it's runnig ... but when connecting to it (either via phpmyadmin, or via mysql CLI) and issuing "show databases" i see only the defauld DBs and not the DBs that are on my datadir.
the permissions on datadir /mnt/NTFS/MySQL_data are ok (i haven't changed this)

if i "rollback" removing the datadir statement, all works as expected.

what am i missing ?

thank you in advance!

---

### Post by michiedo on 2009-10-16
reply to myself:

i've done a mess with the *contents* of my datadir ...
anyway i was missing a "mysql_upgrade"

forget my post, sorry for the disturb
:-(

---

