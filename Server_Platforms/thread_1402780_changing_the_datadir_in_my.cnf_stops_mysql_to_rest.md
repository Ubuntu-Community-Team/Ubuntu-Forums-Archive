---
title: "changing the datadir in my.cnf stops mysql to restart on ubuntu9.10"
date: 2010-02-09
forum: Server Platforms
---

### Post by bam_usic on 2010-02-09
Hello,

I am trying to change the datadir in my.cnf and try to point it to different location where my database are residing.I have the permission to write on this directory.
datadir = /home/glucose/mysql
#datadir = /var/lib/mysql
if I do ls on my database location.Here is the result

root@bilal-laptop:~# ls -la /home/glucose/mysql
total 20512
drwxr-xr-x 7 mysql mysql 4096 2010-02-09 16:30 .
drwxr-xr-x 9 root root 4096 2010-02-03 20:06 ..
-rw-r--r-- 1 mysql mysql 0 2010-01-19 16:07 debian-5.1.flag
drwxr-xr-x 2 mysql mysql 4096 2008-08-14 09:28 glucose
-rw-rw---- 1 mysql mysql 10485760 2010-02-09 15:57 ibdata1
-rw-rw---- 1 mysql mysql 5242880 2010-02-09 15:57 ib_logfile0
-rw-rw---- 1 root root 5242880 2010-01-19 16:07 ib_logfile1
drwxr-xr-x 2 mysql mysql 4096 2007-07-26 10:51 mysql
-rw-r--r-- 1 root root 0 2010-01-25 20:46 mysql.sock
-rw------- 1 mysql mysql 6 2010-01-19 16:07 mysql_upgrade_info
drwxr-xr-x 2 mysql mysql 4096 2010-01-19 17:27 phpmyadmin
drwxr-xr-x 2 mysql mysql 4096 2008-08-14 09:46 prism
drwxr-xr-x 2 mysql mysql 4096 2007-07-26 10:51 test

Could someone please let me know what I am missing.Because of which I am not able to start mysql.
I am not able to locate actual log file as well.I looked at few log files they don't seem to tell me anything.But I am not sure which one I should be looking at as there are quite a few related to mysql.
Thanks,
Bilal

---

### Post by cariboo on 2010-02-11
You will probably get a better answer here, than where you originally posted.

---

### Post by theDaveTheRave on 2010-02-23
bam_usic,

I'm sorry I'm not going to be that helpfull but here goes....

I know that I did a similar thing to enable my data tables to reside on a separate partition.

However mysql needs to have access to the main mysql.mysql table to be able to start up correctly.

There was definately something strange about changing the value after you had installed mysql. It was best to install it with this value rather than attempt to change it later on.


What I would recomend is the following.

1st option:
copy the current tables into the new location before changing the variable value.
then you should be able to test by altering the value back and forth. work out what you need in the 2 tables.

2nd option.
create a link from your <prefered> location to the data directory, then the server should simply follow the link into the correct place where the required mysql.mysql table is.

3rd option.
createa link from the current datadir to your prefered location, this I assume will create the tables in both location (if you are doing this across different disks I'm not sure how it will work).

If you are wanting a pure copy you will need to look at a 'replication' type setup, rather than a pure master/slave setup (which may work for you also)?

hope that helps a bit.

It really depends on what you want to do with the information?

My prefered solution was to use the < /etc/fstab > file to control the mount point on a secondary disk so as to have the system think that there was a disk in the /var/lib/mysql directory. The fact that this could be any 'extra' external HDD, or a sub directory on a separate disk, didn't cause my any problems at all.

if you need more info on the fstab idea, drop me a pm (that way I will respond more quickly!) and I will put in details of how I got it going.... I have a file on my system somewhere... it is just a matter of finding it!

David

---

### Post by DaithiF on 2010-02-23
could be same issue as this thread: [http://ubuntuforums.org/showthread.php?t=1412674](http://ubuntuforums.org/showthread.php?t=1412674)
ie. apparmor

---

