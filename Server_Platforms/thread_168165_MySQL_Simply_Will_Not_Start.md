---
title: "MySQL Simply Will Not Start"
date: 2006-04-30
forum: Server Platforms
---

### Post by zuus on 2006-04-30
Okay, asking here as a last resort, I've read through every single "Help with installing MySQL" guide, followed every instruction to the best of my ability, --purged and started over countless times, but still I am getting this error message; 

```
zuus@muse:/$ sudo /etc/init.d/mysql start
Password:
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
zuus@muse:/$

```

I'm running **Ubuntu 5.10 PPC**, basically a fresh install (about 2 weeks old), **Apache 2.054**, **PHP5** and **MySQL 4.0.24**. I've enabled full 0777 access (I know it shouldn't need full access, but just in case) to all directories MySQL seems to read/write to  plus those which some other guides stated as dirs to which MySQL writes to (ie. /tmp) and made sure the owner is "mysql";

```
zuus@muse:~$ ls -ld /var/run/mysqld/
drwxrwxrwx  2 mysql root 4096 2006-04-30 14:42 /var/run/mysqld/

zuus@muse:~$ ls -ld /tmp
drwxrwxrwt  14 root root 4096 2006-04-30 14:42 /tmp

```

Also, I've read that commenting out an "Old_passwords = 1" entry in /etc/mysqld/my.cnf has fixed this problem in many cases, but the entry does not exist at all in my my.cnf.

Here's what my syslog states;

> Apr 30 14:42:08 localhost mysqld_safe[1364]: started
Apr 30 14:42:08 localhost mysqld[1368]: InnoDB: No valid checkpoint found.
Apr 30 14:42:08 localhost mysqld[1368]: InnoDB: If this error appears when you are creating an InnoDB database,
Apr 30 14:42:08 localhost mysqld[1368]: InnoDB: the problem may be that during an earlier attempt you managed
Apr 30 14:42:08 localhost mysqld[1368]: InnoDB: to create the InnoDB data files, but log file creation failed.
Apr 30 14:42:08 localhost mysqld[1368]: InnoDB: If that is the case, please refer to
Apr 30 14:42:08 localhost mysqld[1368]: InnoDB: [http://dev.mysql.com/doc/mysql/en/Error_creating_InnoDB.html](http://dev.mysql.com/doc/mysql/en/Error_creating_InnoDB.html)
Apr 30 14:42:08 localhost mysqld[1368]: 060430 14:42:08 Can't init databases
Apr 30 14:42:08 localhost mysqld[1368]: 060430 14:42:08 Aborting
Apr 30 14:42:08 localhost mysqld[1368]: 
Apr 30 14:42:08 localhost mysqld[1368]: 060430 14:42:08  InnoDB: Warning: shutting down a not properly started
Apr 30 14:42:08 localhost mysqld[1368]:                  InnoDB: or created database!
Apr 30 14:42:08 localhost mysqld[1368]: 060430 14:42:08 /usr/sbin/mysqld: Shutdown Complete
Apr 30 14:42:08 localhost mysqld[1368]: 
Apr 30 14:42:08 localhost mysqld_safe[1374]: ended
Apr 30 14:42:14 localhost /etc/init.d/mysql[1449]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Apr 30 14:42:14 localhost /etc/init.d/mysql[1449]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Apr 30 14:42:14 localhost /etc/init.d/mysql[1449]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Apr 30 14:42:14 localhost /etc/init.d/mysql[1449]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Apr 30 14:42:14 localhost /etc/init.d/mysql[1449]: 

Now, I don't know *exactly* what I'm doing considering I only started off with Linux basically two weeks ago. I do have a basic idea however, and have managed to fix every problem I've had with it so far, yet this problem has me absolutely stumped. Any help would be very appreciated!

---

### Post by Koybe on 2006-04-30
Dumb questions. 
Is there enough space on /var partition for writing?
Is /var/run directory writable for mysql user?
Did you try restarting you service instead of starting it?
Can you post your /etc/mysqld/my.cnf?
I see that your are using InnoDB. Are you sure all access set for it? Look at the link in the syslog.
> 
**14.2.5.1. Dealing with InnoDB Initialization Problems**

          If InnoDB prints an operating system error         during a file operation, usually the problem has one of the         following causes:       
 [LIST]
[*]             You did not create the InnoDB data file             directory or the InnoDB log directory.           
[*]             **mysqld** does not have access rights to             create files in those directories.           
[*]             **mysqld** cannot read the proper             my.cnf or my.ini             option file, and consequently does not see the options that             you specified.           
[*]             The disk is full or a disk quota is exceeded.           
[*]             You have created a subdirectory whose name is equal to a             data file that you specified, so the name cannot be used as             a filename.           
[*]             There is a syntax error in the             innodb_data_home_dir or             innodb_data_file_path value.           
[/LIST]
          If something goes wrong when InnoDB attempts         to initialize its tablespace or its log files, you should delete         all files created by InnoDB. This means all         ibdata files and all         ib_logfile files. In case you have already         created some InnoDB tables, delete the         corresponding .frm files for these tables         (and any .ibd files if you are using         multiple tablespaces) from the MySQL database directories as         well. Then you can try the InnoDB database         creation again. It is best to start the MySQL server from a         command prompt so that you see what is happening.       



---

### Post by zuus on 2006-04-30
Plenty of space available - ~15GB.

/var/run is writable as far as I can see;
```
zuus@muse:~$ ls -ld /var/run/mysqld/
drwxrwxrwx  2 mysql root 4096 2006-04-30 14:42 /var/run/mysqld/
```

Trying to restart the MySQL server gives the same message;
```
zuus@muse:~$ sudo /etc/init.d/mysql restart
Password:
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
zuus@muse:~$
```

The /etc/mysqld/my.cnf file (I haven't edited anything);
```
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
#
# * Basic Settings
#
user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 127.0.0.1
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
#
# * Query Cache Configuration
#
query_cache_limit	= 1048576
query_cache_size        = 16777216
query_cache_type        = 1
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log		= /var/log/mysql.log
#log		= /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
#
# Here you can see queries with especially long duration
#log-slow-queries	= /var/log/mysql/mysql-slow.log
#
# The following can be used as easy to replay backup logs or for replication.
#server-id		= 1
log-bin			= /var/log/mysql/mysql-bin.log
# See /etc/mysql/debian-log-rotate.conf for the number of files kept.
max_binlog_size		= 104857600
#binlog-do-db		= include_database_name
#binlog-ignore-db	= include_database_name
#
# * BerkeleyDB
#
# The use of BerkeleyDB is now discouraged and support for it will probably
# cease in the next versions.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
#
# * Security Feature
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# If you want to enable SSL support (recommended) read the manual or my
# HOWTO in /usr/share/doc/mysql-server/SSL-MINI-HOWTO.txt.gz
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet	= 16M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

```

I'm not sure why it's using InnoDB or if it should be, but that's basically just a stock install of MySQL, I haven't changed anything or installed anything extra. Basically I tried to set up my server like this;

```
sudo apt-get install apache2

sudo apt-get install php5

sudo apt-get install mysql-server
```

Apparently all the dependencies were met and nothing went wrong (apache2 and php worked fine - tested it using mambo) up until I installed mysql-server when that error came up. :-k

Basically I'm trying to get Mambo running as a PHP content management system which requires the MySQL server, and FluxTorrent which I haven't tried to install yet due to this error but afaik it too requires the MySQL server to be running.

---

### Post by Koybe on 2006-04-30
I can't figure out what's wrong. Anyway if it's for using mambo you can disable it.
Just try before in case :
```
apt-get install --reinstall mysql-server
``` and if not put
```
skip-innodb
``` below "skip-external-locking" in your my.cnf then try restarting.

---

### Post by zuus on 2006-04-30
Okay, did that;

```
[mysqld]
#
# * Basic Settings
#
user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
skip-external-locking
**skip-innodb**
```

Here's what the syslog says now;
```
Apr 30 21:33:48 localhost mysqld_safe[17276]: started
Apr 30 21:33:48 localhost mysqld[17280]: 060430 21:33:48 Fatal error: Can't open privilege tables: Table 'mysql.host' doesn't exist
Apr 30 21:33:48 localhost mysqld[17280]: 060430 21:33:48 Aborting
Apr 30 21:33:48 localhost mysqld[17280]: 
Apr 30 21:33:48 localhost mysqld[17280]: 060430 21:33:48 /usr/sbin/mysqld: Shutdown Complete
Apr 30 21:33:48 localhost mysqld[17280]: 
Apr 30 21:33:49 localhost mysqld_safe[17286]: ended
Apr 30 21:33:55 localhost /etc/init.d/mysql[17358]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Apr 30 21:33:55 localhost /etc/init.d/mysql[17358]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Apr 30 21:33:55 localhost /etc/init.d/mysql[17358]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Apr 30 21:33:55 localhost /etc/init.d/mysql[17358]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Apr 30 21:33:55 localhost /etc/init.d/mysql[17358]: 
```

I've reinstalled the server at least 20 times now using --purge option and even removed php5 and Apache2 just in case then re-installed them. I tried editing "my.cnf" and saving the file, then re-installing MySQL, and it did delete the file and put the new fresh one there, so at least that's working.

So damn confusing :confused:

---

### Post by Koybe on 2006-04-30
Yes quite confusing. I'm not a MySQL expert indeed. Just trying to find out with my little knowledge. After the skip-innodb, is syslog giving the same error?

Could you list your /var/lib/mysql and /var/log/mysql? Don't know if it'll help anyway let's see... ;)

Edit : Ok, just noticed you edit your previous post. It seems the basic databases are not created. Did you try apt-get with reinstall instead of purge and install?

---

### Post by zuus on 2006-04-30
Error has changed in the syslog indeed - check my last post - edited it with syslog info.

Here's the listings of those two directories;
```
zuus@muse:~$ ls -l /var/lib/mysql/
total 20556
-rw-rw----  1 mysql mysql    25088 2006-04-30 14:10 ib_arch_log_0000000000
-rw-rw----  1 mysql mysql 10485760 2006-04-30 14:10 ibdata1
-rw-rw----  1 mysql mysql  5242880 2006-04-30 14:10 ib_logfile0
-rw-rw----  1 mysql mysql  5242880 2006-04-30 14:10 ib_logfile1
drwxr-xr-x  2 mysql root      4096 2006-04-30 15:35 mysql
drwxr-xr-x  2 mysql root      4096 2006-04-30 14:10 test
zuus@muse:~$ ls -l /var/log/mysql
total 40
-rw-rw----  1 mysql adm  79 2006-04-30 14:10 mysql-bin.001
-rw-rw----  1 mysql adm  79 2006-04-30 14:10 mysql-bin.002
-rw-rw----  1 mysql adm  79 2006-04-30 14:10 mysql-bin.003
-rw-rw----  1 mysql adm  79 2006-04-30 15:34 mysql-bin.004
-rw-rw----  1 mysql adm  79 2006-04-30 15:34 mysql-bin.005
-rw-rw----  1 mysql adm  79 2006-04-30 15:34 mysql-bin.006
-rw-rw----  1 mysql adm  79 2006-04-30 15:35 mysql-bin.007
-rw-rw----  1 mysql adm  79 2006-04-30 15:35 mysql-bin.008
-rw-rw----  1 mysql adm  79 2006-04-30 15:35 mysql-bin.009
-rw-rw----  1 mysql adm 261 2006-04-30 15:35 mysql-bin.index

```

---

### Post by Koybe on 2006-04-30
Maybe you can try (make a backup of your /var/lib/mysql dir before) :

- /etc/init.d/mysql stop
- Comment skip-innodb in your my.cnf
- sudo rm /var/lib/mysql/ib*
- sudo mysql_install_db --user=mysql (if this give you an error please give us the log ;) )
- /etc/init.d/mysql start

---

### Post by zuus on 2006-04-30
Here's what happened after putting in that database;

```
zuus@muse:~$ sudo mysql_install_db --user=mysql
Preparing db table
Preparing host table
Preparing user table
Preparing func table
Preparing tables_priv table
Preparing columns_priv table
Installing all prepared tables
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
ERROR: 3  Error writing file './mysql/db.frm' (Errcode: 22)
060501  7:17:57 /usr/sbin/mysqld: Shutdown Complete


To start mysqld at boot time you have to copy support-files/mysql.server
to the right place for your system
```

---

### Post by Koybe on 2006-04-30
Sorry it gets me mad.. and you too I guess ;)
It really feels like mysql can't write on the disk. I never saw this before :(
So what are the permissions /var/lib/mysql directory?

Sorry i'm running out of "good" ideas :P

---

### Post by alcon on 2006-04-30
I've got this same problem, running the same system Ubuntu 5.10 PPC.  I have a funny feeling it might be something wrong with the package for that distro.  I've tried installing from source, and mysql runs after installation from source, but the socket ends up in /tmp/mysql.sock and then php and apache can't seem to find it (even when they are told where it is).

I've been bashing my head against this problem all weekend and am at my wits end, if you two can find a solution I'll be eternally grateful to you.

---

### Post by zuus on 2006-04-30
Yeah, It's incredibly frustrating... everything seems to be in place but it just will-not-work :( 

[QUOTE=Koybe]Edit : Ok, just noticed you edit your previous post. It seems the basic databases are not created. Did you try apt-get with reinstall instead of purge and install?[/QUOTE]

Yup, made no difference. Also tried "dpkg-reconfigure mysql-server" still no-go.

Permissions of /var/lib/mysql;
```
drwxrwxrwx  4 mysql mysql 4096 2006-05-01 07:58 /var/lib/mysql/
```

Maybe alcon is right about it being a problem with the package. I know when I've installed Ubuntu with an i386 based kernel, everything seemed to work very well. But with the PPC a lot of stuff just has wierd problems (which I've managed to fix gradually apart from this one) and a lot of good applications won't work because nobody has made a PPC port :(

Perhaps I should just build an old x86 server.

---

### Post by Koybe on 2006-05-01
Sorry if I ask you a thing you already do. Did you tryx to install db with and without ski-innodb parameter. Just to see if it makes a difference. And if yes... what are the syslog reports for both.

I don't like to give up :p

---

### Post by zuus on 2006-05-01
Lol. I got myself a PIII-800 to use as a server and running ubuntu on that now. Hopefully mysql will work now. Such a lovely speed increase from the 266Mhz G3 :cool: 

It was so much messing around for it though, and to make it worse the G3 was horribly slow, so you can imagine my frustration.

Anyway, thanks for all the help! Even though we didn't get it, I appreciate the help very much :)

---

### Post by Koybe on 2006-05-01
Ok then... better luck with your x86 system ;)

---

### Post by alcon on 2006-05-01
Yeah, I gave up on ubuntu and switched to a debian distro.  I've gotten that working beautifully, only problem was a monitor mishap which was quickly fixed.  So if anyone needs a linux distro server running on a PPC and can't get ubuntu working, take a look at Ubuntu's granddaddy.

---

### Post by possum man on 2006-05-12
I had the same problem with Ubuntu PPC.  After perusing online for a while, and reading these postings, I decided I wasn't going to get the PPC Ubuntu mysql package working any time soon.  I didn't have the time to install Debian, so instead what I did was installed the Debian version of mysql-admin.  I downloaded it from  [http://packages.debian.org/stable/misc/mysql-server](http://packages.debian.org/stable/misc/mysql-server) .  

There are two dependencies, which I added first:

   $ sudo apt-get install libstdc++5 gcc-3.3-base

These packages are actually obsolete, and thus no longer available on the online archives, however, they are still on the CD, which was still in my /etc/apt/sources.list (as "deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)/ breezy main restricted").

So the computer prompted me to insert the installation CD, and then installed those two packages.  If I hadn't had the CD, I could presumedly have found the packages online and installed them with dpkg.  

I purged  the Ubuntu mysql-admin (as was suggested in these postings):

   $ sudo apt-get --purge remove mysql-server

And then installed the Debian package:

   $ sudo dpkg --install mysql-server_4.0.24-10sarge1_powerpc.deb

I only installed  it half an hour ago, but as far as I can tell it's working fine now.

---

### Post by possum man on 2006-05-14
It's been a couple of days now and mysql has been working fine.  So I recommend the above solution [replace Ubuntu's mysql-server with Debian's] to anyone having the same PPC-Ubuntu MySql problem.

---

