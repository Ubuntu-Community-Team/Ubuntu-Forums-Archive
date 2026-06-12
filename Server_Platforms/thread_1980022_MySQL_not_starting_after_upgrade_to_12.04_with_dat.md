---
title: "MySQL not starting after upgrade to 12.04 with data on another partition"
date: 2012-05-14
forum: Server Platforms
---

### Post by guyfromfl on 2012-05-14
I had to cleanly install 12.04 on this machine, and everything seems to be coming back to life fairly easily, except MySQL.

My MySQL data is being stored at ```
/media/Storage/data/MySQL
```

The error that I am getting is:
```

# service mysql restart
stop: Unknown instance: 
start: Job failed to start

```

and the mysql log says:
```

120514 11:28:26 InnoDB: Mutexes and rw_locks use GCC atomic builtins
120514 11:28:26 InnoDB: Compressed tables use zlib 1.2.3.4
120514 11:28:26 InnoDB: Initializing buffer pool, size = 128.0M
120514 11:28:26 InnoDB: Completed initialization of buffer pool
120514 11:28:26  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name /media/Storage/data/MySQL/ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.

```

I tried to import my original my.cnf file from 11.10, then replaced it with the default one from the 12.04 install.  When datadir is set to the default mysql starts no problem.  The only thing I change is datadir in my.cnf.

I have checked my apparmor config and restarted with no effect.

I hope I'm missing something simple and stupid..

Any ideas?

---

### Post by ian dobson on 2012-05-14
Hi,

what do you see when you run

sudo ls -o /media/Storage/data/MySQL/

list files and owners. Maybe mysql isn't the owner anymore.

Regards
Ian Dobson

---

### Post by LHammonds on 2012-05-14
Type the following:

```
ls -l /media/Storage/data/MySQL
```

Now look at the 3rd and 4th columns.   Do they say mysql mysql or do numbers appear.

If they are numbers, then there was a disconnect from the permissions set on the files/folders and the IDs currently on your system.

You may need to reset the ownership of all the files again.

I don't know what they would be exactly but you can start with this command and make changes where necessary later:

```
chown mysql:mysql -R /media/Storage/data/MySQL
```

---

### Post by guyfromfl on 2012-05-14
Thanks everybody, here is the result of the ls with permissions:

```

total 28764
drwxrwxrwx 2 mysql     4096 Aug 31  2011 contract
drwxrwxrwx 2 mysql     4096 Aug 31  2011 dev
-rw-rw---- 1 mysql 18874368 May 11 12:33 ibdata1
-rw-rw---- 1 mysql  5242880 May 11 12:33 ib_logfile0
-rw-rw---- 1 mysql  5242880 May 11 12:32 ib_logfile1
drwxrwxrwx 2 mysql     4096 Apr 24 17:54 leads
drwxrwxrwx 2 mysql     4096 Apr 25 11:10 mysql
-rw-rw---- 1 mysql        6 Apr 25 11:10 mysql_upgrade_info
drwxrwxrwx 2 mysql     4096 Aug 31  2011 reference
drwx------ 2 mysql     4096 Feb 24 17:24 test
drwx------ 2 mysql     4096 Apr 19 15:38 World


```

And the result for ls-l /media/Storage/data/MySQL was the same except there was another column so group:user was mysql:mysql.


It definately looks like a permission issue, but it also looks like they are correct.

I also tried installing MySQL Workbench and editing my.cnf from there to make sure I wasn't doing something stupid, but I get the same result.

---

### Post by guyfromfl on 2012-05-14
On a side note, I am using InnoDB, and rememeber having to set something to make that work, after moving the data source, but have no recollection of what it was. Is that possibly the problem?

---

### Post by guyfromfl on 2012-05-14
anybody have any suggestions?

I have been working on this for 2 days..

I have tried everything google has to offer on this and related searches.

tail /var/log/mysql/error.log says
```

120514 11:28:26 InnoDB: Mutexes and rw_locks use GCC atomic builtins
120514 11:28:26 InnoDB: Compressed tables use zlib 1.2.3.4
120514 11:28:26 InnoDB: Initializing buffer pool, size = 128.0M
120514 11:28:26 InnoDB: Completed initialization of buffer pool
120514 11:28:26  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name /media/Storage/data/MySQL/ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.


```

---

### Post by LHammonds on 2012-05-14
> **guyfromfl said:**
> Thanks everybody, here is the result of the ls with permissions:

```

total 28764
drwxrwxrwx 2 mysql     4096 Aug 31  2011 contract
drwxrwxrwx 2 mysql     4096 Aug 31  2011 dev
-rw-rw---- 1 mysql 18874368 May 11 12:33 ibdata1
-rw-rw---- 1 mysql  5242880 May 11 12:33 ib_logfile0
-rw-rw---- 1 mysql  5242880 May 11 12:32 ib_logfile1
drwxrwxrwx 2 mysql     4096 Apr 24 17:54 leads
drwxrwxrwx 2 mysql     4096 Apr 25 11:10 mysql
-rw-rw---- 1 mysql        6 Apr 25 11:10 mysql_upgrade_info
drwxrwxrwx 2 mysql     4096 Aug 31  2011 reference
drwx------ 2 mysql     4096 Feb 24 17:24 test
drwx------ 2 mysql     4096 Apr 19 15:38 World

```
Why is there a missing column?  It should show mysql in two colums to show the user/group ownership...assuming it is mysql for both the user and group.

Here is the result when I run **ls -l**

```

-rw-r--r-- 1 root  root         0 2011-12-15 15:22 debian-5.1.flag
-rw-rw---- 1 mysql mysql 44040192 2012-05-14 18:42 ibdata1
-rw-rw---- 1 mysql mysql  5242880 2012-05-14 18:42 ib_logfile0
-rw-rw---- 1 mysql mysql  5242880 2012-05-14 14:33 ib_logfile1
drwx------ 2 mysql mysql     4096 2012-05-12 20:07 mediawiki
drwx------ 2 mysql root      4096 2012-04-25 06:34 mysql
-rw-rw---- 1 mysql mysql        5 2012-01-12 20:08 mysql.pid
-rw-rw---- 1 root  root         6 2012-04-25 06:34 mysql_upgrade_info
drwx------ 2 mysql mysql    20480 2012-03-02 15:25 phpbb
drwx------ 2 mysql mysql     4096 2011-12-15 16:45 phpmyadmin
-rw-rw---- 1 mysql mysql        4 2012-05-03 14:09 srv-mysql.pid
drwx------ 2 mysql mysql     4096 2012-01-12 19:24 wordpress

```

---

### Post by SeijiSensei on 2012-05-14
> **guyfromfl said:**
> My MySQL data is being stored at ```
/media/Storage/data/MySQL
```

What kind of file system is mounted at /media/storage/data/MySQL?  Is it ext3/4 or NTFS?  I wouldn't use the latter as the basis for a MySQL database with a Linux server instance.  Reformat it with ext4 first.

If it is ext3/4 then do this:

```

cd /media/storage
sudo chmod a+x *
cd data
sudo chmod a+x *
sudo chown -R mysql.mysql MySQL 

```

Give that a try. The chmod command grants execute privileges to all the subdirectories of /media/storage. Obviously we can't make a directory "executable."  Instead the execute privilege on a directory controls who can list the contents of the directory.  If everyone cannot list /media/storage/data and /media/storage/data/MySQL, then the unprivileged mysql user cannot see these subdirectories.

---

### Post by guyfromfl on 2012-05-15
SeijiSensei,

/media/Storage is etx3/4 and tried the permission commands you suggested, but still the same error. The files did change color tho.

As far as the ls with only 1 mysql column from earlier, people suggested I try ls -o and ls -al, I only posted the -o but mysql:mysql were the owners for all files and folders.

---

### Post by SeijiSensei on 2012-05-15
What does 'ls -l /media' show?  Does /media/storage have execute permissions for all users?  What about "mount"?  Is the filesystem with the MySQL data on it mounted as rw?

Have you run fsck against the mounted filesystem recently?  If the filesystem has errors, Linux will only mount it read-only.

---

### Post by LHammonds on 2012-05-15
If you type "mount" with no options, it should show you all the mounted file systems.  All system (except for ones like CDROMs) should have (rw) to the side.

LHammonds

---

### Post by guyfromfl on 2012-05-15
here is the result of mount:
```

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda6 on /home type ext4 (rw,nosuid,nodev)
/dev/sda4 on /media/Storage type ext2 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mark/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mark)
/dev/sdb1 on /media/Lexar type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


```

and ls -l /media:
```

total 108
drwx------ 12 mark   mark 106496 Dec 31  1969 Lexar
drwxrwxrwx 10 nobody root   4096 Apr 10 13:50 Storage


```

---

### Post by SeijiSensei on 2012-05-16
Well, I'm running out of suggestions.  First I'd look at "ls -l /media/Storage" to see the permissions on the data subdirectory.

Next while I'm pretty sure mysqld should be running as the mysql user, maybe it's not?

Worst case, you could make all of /media/Storage/data/MySQL world readable/writable and make sure you can launch the service that way.  If that works, then it is a permissions problem.  If it doesn't, there's something more profoundly wrong.

---

### Post by guyfromfl on 2012-05-16
The data folder was set to be owned by me. I changed it with chown mysql:mysql /media/Storage/Data, but still same problem.

When I run service mysql start all I get is the start: Job failed to start error.

Nothing has been written in /var/log/mysqlerror.log for 2 days, even though I've been here putting in extra hours to get this running since Sunday.

In my.cnf, user=mysql.

I am at a complete loss.

I am going to try to restore the default my.cnf file, and migrate the data to the default data directory and see if it will come up there.  The company relies on this database to make money so we are sinking as it is right now.  If at least moving data works, that will get some of the preasure off me.

Thanks for all your help!

---

### Post by guyfromfl on 2012-05-16
Well.

I removed MySQL altogether, and reinstalled it.  When it came up, it was working fine. I could log in the client and got phpMyAdmin to sort of work.

The database tables that I need will not show up in phpMyAdmin, so I'm assuming my client as well.

Also, I tried to restart the mysql service and it failed.  Nothing is being written to /var/log/mysql/error.log so I have no idea what "start: Job failed to start" means.

---

### Post by SeijiSensei on 2012-05-16
Do you have a backup of the database using mysqldump?  If so, I'd just recreate the database with the mysql client from the dump file.

If you don't use mysqldump to create daily backups, here's a script you can use or modify for the future:  [http://ubuntuforums.org/showpost.php?p=10368151&postcount=3](http://ubuntuforums.org/showpost.php?p=10368151&postcount=3)

---

### Post by guyfromfl on 2012-05-16
Thanks for that link.  I will def start using that, because it seems better than the way I've been doing it.

Quick update, from my own stupidity, mysql wouldn't start with the data in the default folder because I didn't copy with permissions lol.  So everything is working in the default location, just can't print which has nothing to do with this issue.

For now, I'm going to leave it in the default data dir since I can finally use the data again.  I'll revisit this after my blood preasure goes back down and am ready to try to put it back on that partition.

Thank you for all your help!

---

### Post by Cheesemill on 2012-05-16
Do you have apparmor on your system?

I was having the same problems as you a while back and seem to remember having to edit the MySQL apparmor profile to allow it to access the new data location.

Also have you tried just leaving the my.cnf file as-is and symlinking the new location to /var/lib/mysql ?

---

### Post by guyfromfl on 2012-05-16
Cheesemill,

I did edit the apparmor files, but didn't help..either I did it wrong or that wasn't the issue.

As far as sym-linking i just learned about this the other day, haven't tried it tho. Maybe when I decide to migrate everything to the partition again, I'll try that

Thanks!

---

### Post by SeijiSensei on 2012-05-16
Apparmor sounds like a good bet to me.  Read [this howto](https://wiki.ubuntu.com/DebuggingApparmor) on identifying Apparmor problems.  You'll see denials in /var/log/kern.log, or in /var/log/audit.log if you have auditd installed.  The discussion about "complain" mode looks useful as well.

---

### Post by qasimazam on 2013-03-13
Have you change chmod of /etc/ directory to 777 ? This error comes when you change chmod of /etc/ directory to 777. Change it back to 705 , most probably it will work. Let me know, if this works ?
**sudo chmod 705 -R /etc/mysql  **

---

