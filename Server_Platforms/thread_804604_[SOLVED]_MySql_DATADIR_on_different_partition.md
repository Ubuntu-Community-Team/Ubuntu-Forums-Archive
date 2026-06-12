---
title: "[SOLVED] MySql DATADIR on different partition"
date: 2008-05-23
forum: Server Platforms
---

### Post by corrigang on 2008-05-23
I'm building a new 8.0 server setup and installed MySql with the install media.  I've intentionally created a 200GB partition for use for data separate from the OS partition, mounted as /srv.  I can't get MySql to start when it is pointing at this location for it's DATADIR in my.cnf:

[FONT="Courier New"]datadir         = /srv/mysql/db[/FONT]

I've disabled apparmor, set the group and user rights to mysql:mysql, copied over the original database entries from /var/lib/mysql, etc.

ls -l /srv/mysql:

drw-rw-r-- 3 mysql mysql 4096 2008-05-23 07:19 db

ls -l /srv/mysql/db:
[FONT="Courier New"]-rw-r--r-- 1 mysql mysql        0 2008-05-22 16:01 debian-5.0.flag
-rw-r----- 1 mysql mysql 10485760 2008-05-22 22:06 ibdata1
-rw-r----- 1 mysql mysql  5242880 2008-05-22 22:06 ib_logfile0
-rw-r----- 1 mysql mysql  5242880 2008-05-22 22:06 ib_logfile1
drwxr-xr-x 2 mysql mysql     4096 2008-05-22 16:01 mysql
-rw----r-- 1 mysql mysql        7 2008-05-22 16:01 mysql_upgrade_info
-rw-r----- 1 mysql mysql 10485760 2008-05-22 16:25 zibdata1
root@wilson:/srv/mysql/db#
[/FONT]

My searching has produced no results, and I've successfully used differente DATADIR's on directories sourced under the standard partition.  Also, MYSQL *will* start with the my.cnf user = root.

When MySql starts, I get:

[FONT="Courier New"]May 23 07:19:16 wilson mysqld_safe[21590]: started
May 23 07:19:16 wilson mysqld[21593]: 080523  7:19:16  InnoDB: Operating system error number 13 in a file operation.
May 23 07:19:16 wilson mysqld[21593]: InnoDB: The error means mysqld does not have the access rights to
May 23 07:19:16 wilson mysqld[21593]: InnoDB: the directory.
May 23 07:19:16 wilson mysqld[21593]: InnoDB: File name ./ibdata1
May 23 07:19:16 wilson mysqld[21593]: InnoDB: File operation call: 'create'.
May 23 07:19:16 wilson mysqld[21593]: InnoDB: Cannot continue operation.
May 23 07:19:16 wilson mysqld_safe[21600]: ended
[/FONT]

Finally, my fstab:

[FONT="Courier New"]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=8a91f433-08de-40b9-9d55-20547e09f8e3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2d9db74c-3b95-4fed-aef8-f4e8a6547c42 /srv            ext3    relatime        0       2
# /dev/sda7
UUID=deb795ea-2ac0-4b3e-84ce-3fa4be8b957a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
~[/FONT]

Is the problem's root a security issue in fstab?  Any guidance is *GREATLY* appreciated, as I've run out of hair to pull.

---

### Post by Monicker on 2008-05-23
I'm not positive, but I think you may have to specify the directories for you innodb files.  

Looking at my config, I ntoiced the following commented out lines, which I believe are the defaults unless otherwise specified:
```

#innodb_data_home_dir           = /var/lib/mysql/
#innodb_log_arch_dir            = /var/lib/mysql/
#innodb_log_group_home_dir      = /var/lib/mysql/
```

---

### Post by corrigang on 2008-05-23
Well, that was worth a shot. My  my.cnf did not have those lines commented out, but I added them.  The syslog error is now a little different - it shows the full path to the ibdata1 database (/srv/mysql/db/ibdata1); otherwise, same error:

[FONT="Courier New"]May 23 14:01:48 wilson mysqld[22332]: 080523 14:01:48  InnoDB: Operating system error number 13 in a file operation.
May 23 14:01:48 wilson mysqld[22332]: InnoDB: The error means mysqld does not have the access rights to
May 23 14:01:48 wilson mysqld[22332]: InnoDB: the directory.
May 23 14:01:48 wilson mysqld[22332]: InnoDB: File name /srv/mysql/db/ibdata1
May 23 14:01:48 wilson mysqld[22332]: InnoDB: File operation call: 'create'.
May 23 14:01:48 wilson mysqld[22332]: InnoDB: Cannot continue operation.
[/FONT]

---

### Post by corrigang on 2008-05-27
Not sure what I was doing wrong... but, instead of manually setting the permissions, I used this approach, and, yes, it's finally working:
```

/etc/init.d/mysql stop
mkdir /srv/mysql/db
cp -dpR /var/lib/mysql/* /srv/mysql/db
chown mysql:mysql /srv/mysql/db

```
I then modified the my.cnf file as before to set DATADIR to /srv/mysql/db and started MySql back up
```

/etc/init.d/mysql start

```
Success! :)

I must have been messing up the permissions by setting them using chown/chmod, even though the listings looked identical.

Unlike some posts I have seen, I **did not** have to delete the ib_logXXX files for the migrated data.

---

