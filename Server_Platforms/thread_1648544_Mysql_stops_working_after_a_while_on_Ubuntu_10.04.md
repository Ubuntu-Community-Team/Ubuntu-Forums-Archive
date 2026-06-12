---
title: "Mysql stops working after a while on Ubuntu 10.04"
date: 2010-12-18
forum: Server Platforms
---

### Post by nidal22 on 2010-12-18
> My Server Info: Ubuntu Linux 10.04.1 Server | MySQL version 5.1.54 

mysql server stopped working, tried to use /etc/init.d/mysql start, for some reason it's no longer working, I get this message

> Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.8" (uid=1000 pid=2015 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init))


Then I tried service mysql start
> start: Rejected send message, 1 matched rules; type="method_call", sender=":1.9" (uid=1000 pid=2065 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init))

cat /var/log/syslog | grep mysql
[HTML]Dec 19 03:09:53 sv2 kernel: [11775.003777] type=1505 audit(1292717393.730:36):  operation="profile_replace" pid=7351 name="/usr/sbin/mysqld"
Dec 19 03:09:53 sv2 init: mysql pre-start process (7349) terminated with status 1
Dec 19 03:10:09 sv2 init: mysql pre-start process (7366) terminated with status 1
Dec 19 03:10:09 sv2 kernel: [11790.713786] type=1505 audit(1292717409.442:37):  operation="profile_replace" pid=7368 name="/usr/sbin/mysqld"
Dec 19 03:10:42 sv2 init: mysql pre-start process (7413) terminated with status 1
Dec 19 03:10:42 sv2 kernel: [11823.500245] type=1505 audit(1292717442.227:38):  operation="profile_replace" pid=7415 name="/usr/sbin/mysqld"
Dec 19 03:21:02 sv2 init: mysql pre-start process (7507) terminated with status 1
Dec 19 03:21:02 sv2 kernel: [12444.252381] type=1505 audit(1292718062.982:39):  operation="profile_replace" pid=7509 name="/usr/sbin/mysqld"
Dec 19 03:23:09 sv2 kernel: [12571.065476] type=1505 audit(1292718189.795:40):  operation="profile_replace" pid=7533 name="/usr/sbin/mysqld"
Dec 19 03:23:09 sv2 init: mysql pre-start process (7531) terminated with status 1
Dec 19 03:35:04 sv2 kernel: [13285.663756] type=1505 audit(1292718904.390:41):  operation="profile_replace" pid=7835 name="/usr/sbin/mysqld"
Dec 19 03:35:04 sv2 init: mysql pre-start process (7833) terminated with status 1
Dec 19 03:39:48 sv2 kernel: [13569.561937] type=1505 audit(1292719188.290:42):  operation="profile_replace" pid=7911 name="/usr/sbin/mysqld"
Dec 19 03:39:48 sv2 init: mysql pre-start process (7909) terminated with status 1
Dec 19 04:02:37 sv2 kernel: [14939.192715] type=1505 audit(1292720557.922:43):  operation="profile_replace" pid=8126 name="/usr/sbin/mysqld"
Dec 19 04:02:37 sv2 init: mysql pre-start process (8124) terminated with status 1
Dec 19 04:14:15 sv2 kernel: [15636.525877] type=1505 audit(1292721255.254:44):  operation="profile_replace" pid=8230 name="/usr/sbin/mysqld"
Dec 19 04:14:15 sv2 init: mysql pre-start process (8228) terminated with status 1
Dec 19 04:26:26 sv2 kernel: [16368.174413] type=1505 audit(1292721986.903:45):  operation="profile_replace" pid=8434 name="/usr/sbin/mysqld"
Dec 19 04:26:26 sv2 init: mysql pre-start process (8432) terminated with status 1
Dec 19 04:31:00 sv2 mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Dec 19 04:31:00 sv2 mysqld: 101219  4:31:00 [Warning] Can't create testDec 19 05:07:25 sv2 kernel: imklog 4.2.0, log source = /proc/kmsg started.
[/HTML]

Please see the attached PDF file for "/var/log/mysql/error.log

I reinstalled mysql server, the server worked fine, even I tried the command sudo /etc/init.d/mysql start/stop/restart, also was working, however, within 1 hour, mysql stopped and longer I can't start it using either init/upstart. I tried  all solutions in the following forums:

[http://bugs.mysql.com/bug.php?id=54256](http://bugs.mysql.com/bug.php?id=54256)

[http://reformedmusings.wordpress.com/2010/05/03/administering-ubuntu-lucid-10-04-lts-and-karmic-9-10-with-webmin/](http://reformedmusings.wordpress.com/2010/05/03/administering-ubuntu-lucid-10-04-lts-and-karmic-9-10-with-webmin/)
[http://ubuntuforums.org/showthread.php?t=1467115](http://ubuntuforums.org/showthread.php?t=1467115)
[http://ubuntuforums.org/showthread.php?t=1467115&page=2](http://ubuntuforums.org/showthread.php?t=1467115&page=2)
[http://ubuntuforums.org/showthread.php?t=1475798](http://ubuntuforums.org/showthread.php?t=1475798)
[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/566736](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/566736)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1506533](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1506533)

I still can not solve the problem!

Thanks for your help

---

### Post by CharlesA on 2010-12-18
I haven't run into any problems with 10.04.

Do you have a database created already?

---

### Post by nidal22 on 2010-12-18
I have 3 database:2 wordpress around 1GB each, the third around 10 GB, 
been running mysql and apcahe with no problem until last night, no longer mysql is working, however my apache2 still working.

Why init.d does not work anymore and suddenly ubuntu server asking me to use
> Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql

I tried to start mysql server from webmin with no luck

---

### Post by CharlesA on 2010-12-18
Where there any updates to mysql recently?

Note: I moved your posts to a new thread, as to not derail the other thread.

---

### Post by nidal22 on 2010-12-18
I did not update mysql.

Mysql server is working now

> :~$ sudo /etc/init.d/mysql start
[sudo] password for nidal: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
mysql start/running, process 9765


This is what I did, I removed my sql backup files from 
/mysqldumper/work/backup, then tried **mysql start** again, it worked process 9765. after 7 hrs trying to fix the problem.

Strange, I guess this problem could be related to mysqldumper, today when I was restoring one of my database "1GB" using mysqldumper, mysqldumper gave an error "www-data@localhost password: no". I reinstalled mysql and worked fine, then I used mysqldumper again to restore my databases, the first database succesfully was installed, however when I tried to restore the second database I got the error "www-data@localhost password: no" from mysqldumper again.

I would like to keep this thread open for 2 days, before it solved, I just want to monitor mysql and see if the problem is really caused by mysqldumber or something else.

Thanks CharlesA

---

### Post by nidal22 on 2010-12-19
I thought the initial problem with (init.d/mysql start) finally is gone after many hours of troubleshooting, but mysql does not want to start again. mysql worked for 24 hrs after was fixed.

/etc/init.d/mysql start
[HTML]:~$ sudo /etc/init.d/mysql start
sudo: /etc/init.d/mysql: command not found[/HTML]

I checked the mysql under /etc/init.d, link is broken!  please see the pic.

service mysql start
[HTML]:~$ service mysql start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.7" (uid=1000 pid=2469 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init))[/HTML]

mysql is getting into my nerver, behind with my project, not sure even if the problem with mysql or upstart. After reading many threads regarding /init.d/mysql and upstart, thought to switch to PostgreSQL, but again worry about init.d and upstart again.

thanks for your help

---

### Post by CharlesA on 2010-12-19
How strange.

Can you post the output of this:

```
ls -l /etc/init.d/mysql
```

Mine (that is working fine) looks like this:

```
charles@lucid:~$ ls -l /etc/init.d/mysql
lrwxrwxrwx 1 root root 21 2010-12-10 03:30 /etc/init.d/mysql -> /lib/init/upstart-job

```

---

### Post by nidal22 on 2010-12-19
```
$ ls -l /etc/init.d/mysql
lrwxrwxrwx 1 nidal nidal 21 2010-12-20 01:21 /etc/init.d/mysql -> /lib/init/upstart-job
```

How come mysql in /etc/init.d shows link (broken)

---

### Post by CharlesA on 2010-12-19
I think it's because the link is owned by nida1, not root.

Run this:

```
sudo chown root:root /etc/init.d/mysql
```

---

### Post by nidal22 on 2010-12-19
Intersting! No such file or directory

```
$ sudo chown root:root /etc/init.d/mysql
[sudo] password for nidal: 
chown: cannot dereference `/etc/init.d/mysql': No such file or directory
nidal@sv2:/lib/init$ cd /etc/init.d
nidal@sv2:/etc/init.d$ ls
apache2                   module-init-tools           saned
apparmor                  mysql                       screen-cleanup
apport                    mysql.dpkg-new              sendsigs
atd                       networking                  single
avahi-daemon              network-interface           skeleton

```


the file upstart-job in /lib/init is not there, strange

```
:/lib/init$ ls -l
total 32
-rw-r--r-- 1 root root 1801 2010-10-07 13:02 fstab
-rwxr-xr-x 1 root root 9824 2010-03-30 10:17 readlink
drwxr-xr-x 2 root root   40 2010-12-20 01:13 rw
-rw-r--r-- 1 root root 2847 2009-09-07 21:58 splash-functions-base
-rw-r--r-- 1 root root 5791 2009-09-07 21:58 usplash-fsck-functions.sh
-rw-r--r-- 1 root root  571 2009-09-07 21:58 vars.sh

```

---

### Post by nidal22 on 2010-12-19
I checked my other server sv1:

```
nidal@sv1:~$ ls -l /etc/init.d/mysql
lrwxrwxrwx 1 root root 21 2010-10-04 04:31 /etc/init.d/mysql -> /lib/init/upstart-job

```

```
nidal@sv1:/lib/init$ ls -l
total 36
-rw-r--r-- 1 root root 1801 2010-09-02 01:56 fstab
-rwxr-xr-x 1 root root 9824 2010-03-30 10:17 readlink
drwxr-xr-x 2 root root   40 2010-10-18 21:16 rw
-rw-r--r-- 1 root root 2847 2009-09-07 21:58 splash-functions-base
-rwxr-xr-x 1 root root 1830 2010-08-13 03:26 upstart-job
-rw-r--r-- 1 root root 5791 2009-09-07 21:58 usplash-fsck-functions.sh
-rw-r--r-- 1 root root  571 2009-09-07 21:58 vars.sh
```

---

### Post by CharlesA on 2010-12-19
Wow that's really weird. Is sv1 is working fine?

---

### Post by nidal22 on 2010-12-19
sv1 is working fine, but sv2 not at all, 

What's the best way to completely **remove** mysql from sv2 and **install** it again, Just want clean remove, no file or log left on sv2 belong to mysql?

---

### Post by CharlesA on 2010-12-19
Purge it.

```
sudo apt-get purge mysql
```

---

### Post by nidal22 on 2010-12-20
I unistalled mysql with apt-get purge mysql, but got an error message

```
~$ sudo apt-get purge mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mysql

```

Then I uninstalled with
```

sudo apt-get mysql-server-5.1 mysql-client-5.1
sudo apt-get autoclean
Remove most mysql files:
sudo rm -fr /var/log/mysql*
sudo rm -fr /var/lib/update-rc.d/mysql*
sudo rm -fr /var/lib/dpkg/info/mysql-*
sudo rm -fr /var/lib/mysql/
sudo rm -fr /var/lib/dpkg/info/libmysqlclient1*

``` 

I tried to install mysql unsuccessfully 
```
sudo aptitude install mysql-server-5.1
```

I get warning messages about missing packages:
```


nidal@sv2:~$ sudo aptitude install mysql-server-5.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  libreadline5{a} mysql-client-5.1{a} mysql-server-5.1 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/16.2MB of archives. After unpacking 37.3MB will be used.
Do you want to continue? [Y/n/?] Y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  mysql-client-5.1 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package libreadline5.
(Reading database ... 
dpkg: warning: files list file for package `mysql-server-core-5.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-gui-tools-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmysqlclient16' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-admin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-query-browser' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-client-core-5.1' missing, assuming package has no files currently installed.
(Reading database ... 108539 files and directories currently installed.)
Unpacking libreadline5 (from .../libreadline5_5.2-7build1_i386.deb) ...
Selecting previously deselected package mysql-client-5.1.
Unpacking mysql-client-5.1 (from .../mysql-client-5.1_5.1.54-0.dotdeb.0_i386.deb) ...
Selecting previously deselected package mysql-server-5.1.
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.54-0.dotdeb.0_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up libreadline5 (5.2-7build1) ...

Setting up mysql-client-5.1 (5.1.54-0.dotdeb.0) ...
Setting up mysql-server-5.1 (5.1.54-0.dotdeb.0) ...
101220 15:45:55 [Note] Plugin 'FEDERATED' is disabled.
101220 15:45:55  InnoDB: Initializing buffer pool, size = 8.0M
101220 15:45:55  InnoDB: Completed initialization of buffer pool
101220 15:45:55  InnoDB: Started; log sequence number 0 44233
101220 15:45:55 [ERROR] /usr/sbin/mysqld: Can't find file: './mysql/user.frm' (errno: 13)
ERROR: 1017  Can't find file: './mysql/user.frm' (errno: 13)
101220 15:45:55 [ERROR] Aborting

101220 15:45:55  InnoDB: Starting shutdown...
101220 15:46:00  InnoDB: Shutdown completed; log sequence number 0 44233
101220 15:46:00 [Note] /usr/sbin/mysqld: Shutdown complete

update-rc.d: warning: /etc/init.d/mysql missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.1 (5.1.54-0.dotdeb.0) ...
update-rc.d: warning: /etc/init.d/mysql missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.1
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

```

Three days trying to troubleshoot mysql with no light in the end of the tunnle, 

Can anybody please, let me know how to get all missing packges, or where to download the complete deb package for mysql?

Thanks!

---

### Post by CharlesA on 2010-12-20
Hrm, I checked what packages were installed and got this:

```
charles@lucid:~$ dpkg -l | grep mysql
ii  libdbd-mysql-perl                     4.012-1ubuntu1                                  A Perl5 database interface to the MySQL data
ii  libmysqlclient16                      5.1.41-3ubuntu12.8                              MySQL database client library
ii  mysql-client-5.1                      5.1.41-3ubuntu12.8                              MySQL database client binaries
ii  mysql-client-core-5.1                 5.1.41-3ubuntu12.8                              MySQL database core client binaries
ii  mysql-common                          5.1.41-3ubuntu12.8                              MySQL database common files (e.g. /etc/mysql
ii  mysql-server                          5.1.41-3ubuntu12.8                              MySQL database server (metapackage depending
ii  mysql-server-5.1                      5.1.41-3ubuntu12.8                              MySQL database server binaries
ii  mysql-server-core-5.1                 5.1.41-3ubuntu12.8                              MySQL database core server files
ii  php5-mysql                            5.3.2-1ubuntu4.5                                MySQL module for php5

```

I'm not quite sure how it got all messed up, but if it's that hosed up, perhaps a starting with a clean slate would be easier then trying to figure out what caused the problem.

---

### Post by nidal22 on 2010-12-20
Thanks CharlesA, It looks like reinstalling ubuntu 10.04 easier than solving mysql problem

---

### Post by CharlesA on 2010-12-20
> **nidal22 said:**
> Thanks CharlesA, It looks like reinstalling ubuntu 10.04 easier than solving mysql problem
Indeed. The really strange part is the permissions and that it's not letting you install the sql server again.

Hope you have a smooth reinstall. :)

---

### Post by nidal22 on 2010-12-23
***Mysql stops working after a while on Ubuntu 10.04: Mysql problem is SOLVED***

Mysql on SV1 stopped working, same problem I had early with mysql on sv2.

I tried to remove mysql with
```
sudo apt-get purge mysql
```
then reinstall mysql with 
```
sudo apt-get install mysql-server  

```
mysql could not find commands:
```
sudo /etc/init.d/mysql start
service mysql start

```
then I tried to reinstall it with
```
sudo aptitude install mysql-server-5.1
```
mysql did not start and also some packges problem

After searching countless hours with no real solution, did not want to reinstall ubuntu 10.04 on my sv1 as I did on sv2 to solve the problem, 

Before you proceed, make sure your already have a backup of your database, if you did not do already, just copy the following folder
```
/var/lib/mysql
```

This what I did to have mysql running again: 


Remove mysql: finish all steps even if you get error!
```

sudo  apt-get remove mysql-server-5.1 mysql-client-5.1
sudo apt-get autoclean
sudo rm -fr /var/log/mysql*
sudo rm -fr /var/lib/update-rc.d/mysql*
sudo rm -fr /var/lib/dpkg/info/mysql-*
sudo rm -fr /var/lib/mysql/
sudo rm -fr /var/lib/dpkg/info/libmysqlclient1*

``` 
You need Webmin, if you do not, this how you install it:
1. install and update Webmin via APT, edit the /etc/apt/sources.list file on your system and add the lines : 
```
deb http://download.webmin.com/download/repository sarge contrib
deb http://webmin.mirror.somersettechsolutions.co.uk/repository sarge contrib 
```
2. You should also fetch and install my GPG key with which the repository is signed, with the commands : 
```
cd /root
wget http://www.webmin.com/jcameron-key.asc
apt-key add jcameron-key.asc 
```
3. You will now be able to install with the commands : 
```
apt-get update
apt-get install webmin
```
Webmin installation can be found [http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

1. log to webmin [http://yourdomain.com:10000](http://yourdomain.com:10000)

2. under 
```
System -> Software Packages -> Installed Packages -> Search for Package
```
Enter the following in Search for Package
```
mysql
```
Remove all mysql packages except for following packages:
```

libmysqlclient16 5.1.54-0.dotdeb.0
mysql-common 5.1.54-0.dotdeb.0
php5-mysql 5.3.2-1ubuntu4.2

```

3. Install mysql with webmin: Webmin will inform you "Mysql is not install/module" and give you option to install mysql
```
Servers -> MySQL Database Server
```

Webmin will install all the required packages for mysql, and mysql should start

4. Stop mysql with webmin and copy your database back to 
```
/var/lib/mysql
```
or if you backed up your database with mysqldumper, just restore it and make sure mysql is running

None of the solutions posted on the Internet worked for me, even it was a common problem, could not find a solution.

I hope this work for you and save you many days of frustration as did to me for the past few days.

---

### Post by CharlesA on 2010-12-23
Thanks for the info.

Do you happen to know if it's an update that breaks mysql?

Might be worth reporting it as a bug.

---

### Post by nidal22 on 2010-12-23
I did not update mysql, so no issue with update.

The problem with mysql in both sv1 and sv2 happened when I was restoring my data (10 GB) using mysqldumper, it freezed, so I shut mysql and tried restart it again with no success.
take alook at [https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/566736](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/566736)

The question is, Why its so hard to remove Mysql and reinstall it using:

```

apt-get purge mysql-server-5.1
sudo apt-get install mysql-server

```

When I looked at the packages for mysql using webmin, mysql pakages still there even its already been removed earlier as I thought.

The only way I was able to install and run mysql, is using webmin, so using the following command is not doing what's supposed to do
```
sudo apt-get install mysql-server
```

---

### Post by CharlesA on 2010-12-23
Does the same thing happen if you use aptitude? I'm curious, since webmin uses apt-get.

That's confusing.

---

### Post by nidal22 on 2010-12-23
aptitude I use

```
sudo aptitude install mysql-server-5.1
```

I got errors regarding missing packages, I used the following command fix
the broken packages:
```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get install --reinstall *package name*

```

Then I tried to start mysql, got the following error

```

Dec 23 07:26:23 sv1 /etc/init.d/mysql[2486]: ERROR: The partition with /var/lib/mysql is too full!
Dec 23 07:29:49 sv1 /etc/init.d/mysql[2576]: ERROR: The partition with /var/lib/mysql is too full!
Dec 23 07:31:30 sv1 /etc/init.d/mysql[2636]: ERROR: The partition with /var/lib/mysql is too full!

```

I checked my drive, it was not full

```

$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/mapper/VolGroup1-root
              ext3     36G  8.6G   26G  26% /
none      devtmpfs     55M  244K   55M   1% /dev
none         tmpfs     59M     0   59M   0% /dev/shm
none         tmpfs     59M  316K   59M   1% /var/run
none         tmpfs     59M     0   59M   0% /var/lock
none         tmpfs     59M     0   59M   0% /lib/init/rw

```

I know that's confusing because All what I did
```

remove:     sudo apt-get purge mysql
install:    sudo apt-get install mysql-server

```
I could not start mysql, got the error "mysql could not find commands:"
```

sudo /etc/init.d/mysql start
service mysql start

```

For some reason, mysql was missing from
```
/etc/init.d/
```

---

### Post by nidal22 on 2010-12-23
Regarding Webmin:

Webmin install command for mysql included a few packages with it's command and also used -f force, I can not remember The exact command

```
sudo apt-get install -f --force ?? mysql-server .... other packages 

```

SV2: Ubuntu fresh install see attached picture sv2-ubuntu for the installed mysql packages
SV1: webmin installed mysql see attached picture sv1-webmin for the installed mysql packages

I guess apt-get install mysql-server was not installing all the required packages

Take a look mysql.wbm.gz module for webmin, you can find it at
[http://www.webmin.com/standard.html](http://www.webmin.com/standard.html)

If you have an extra server, try to remove mysql and reinstall it again with theses commands:

remove:     sudo apt-get purge mysql
install:    sudo apt-get install mysql-server

---

### Post by CharlesA on 2010-12-23
Thanks for the info, I'll try it on one of my 10.04 VMs and report back.

---

### Post by CharlesA on 2010-12-23
Hrm, I did it like you did in [post 21]("http://ubuntuforums.org/showpost.php?p=10270728&postcount=21"). That machine is running Ubuntu 10.04.1 x64, with all the latest updates.

Purge:

```
charles@mars:~$ sudo apt-get purge mysql-server-5.1
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  mysql-server* mysql-server-5.1*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 15.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 43281 files and directories currently installed.)
Removing mysql-server ...
Removing mysql-server-5.1 ...
mysql stop/waiting
Purging configuration files for mysql-server-5.1 ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
```

Reinstall:

```
charles@mars:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  mysql-server-5.1
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  mysql-server mysql-server-5.1
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7,205kB of archives.
After this operation, 15.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.1.
(Reading database ... 43197 files and directories currently installed.)
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.41-3ubuntu12.8_amd64.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.41-3ubuntu12.8_all.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up mysql-server-5.1 (5.1.41-3ubuntu12.8) ...
mysql start/running, process 1802

Setting up mysql-server (5.1.41-3ubuntu12.8) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

Upstart:

```
charles@mars:~$ sudo service mysql stop
mysql stop/waiting
charles@mars:~$ sudo service mysql start
mysql start/running, process 1346
charles@mars:~$ sudo service mysql restart
mysql start/running, process 1422

```

Init.d script:

```
charles@mars:~$ ls -l /etc/init.d/mysql
lrwxrwxrwx 1 root root 21 2010-12-23 13:42 /etc/init.d/mysql -> /lib/init/upstart-job

```

---

### Post by nidal22 on 2010-12-23
That's good no bugs, both commands are working. I guess something went wrong when mysql freezed while I was restoring with mysqldumper and did not shut as suppose to. Or could be InnoDB took too long to shut which causes mysql problem. Honestly do not know! 

Thanks CharlesA for the info and doing the test.

---

### Post by CharlesA on 2010-12-23
I don't know either. The only thing I didn't do was run sqldumper, as I don't have any DBs on that machine.

Glad to help. :)

---

### Post by digz6666 on 2011-12-08
I've had this issue today on my Ubuntu 11.10.
I've installed mysql server and client from Ubuntu software center.

I cannot start/stop mysql:
```
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop mysql ; start mysql. The restart(8) utility is also available.
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.329" (uid=1000 pid=12255 comm="stop mysql ") interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply="0" destination="com.ubuntu.
```

I've tried following command and it worked:
```
sudo service mysql stop
sudo service mysql start
```

It's related to permission issue, you should grant execute permission to current user or run as root.

---

