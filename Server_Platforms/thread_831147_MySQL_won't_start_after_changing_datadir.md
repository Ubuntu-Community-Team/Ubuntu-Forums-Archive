---
title: "MySQL won't start after changing datadir"
date: 2008-06-16
forum: Server Platforms
---

### Post by christonabike on 2008-06-16
I'm attempting to change the datadir of a fresh MySQL install. After changing the datadir, MySQL will no longer start. It doesn't give any reasons, it simply says [fail]. When I change the datadir back to the default (/var/lib/mysql), MySQL starts fine. Ultimately, I would like the datadir to be a folder on a different partition and disk, but for testing purposes I have tried using a folder on the same partition and disk (/home/jeremy/test) but cannot get it to work.

Things I have tried:

[LIST]
[*]Following the directions in this [[COLOR="Blue"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=804604"), to the letter.
[*]Copying the files from /var/lib/mysql to /home/jeremy/test and running chown -R mysql:mysql on the folder. I've also tried various permutations of permissions and ensured the permissions and owners match exactly between the 2 directories.
[*]Both copying and not copying the ib_log* and ibdata* files.
[/LIST]

I've also made sure that mysql is stopped before making any changes to any files whatsoever. Once again, this is a fresh install with nothing created. It starts/works fine when the datadir is set to the default but not when I change it to anything else.

Any help is greatly appreciated!

---

### Post by christonabike on 2008-06-19
After spending way, way, way, way, way, way, way (each way equals ~ an hour of my time) on this, the solution was disgustingly simple.

Basically, you need to add the directories you want MySQL to be able to access to MySQL's apparmor profile. These steps, in order, should allow you to change MySQL's datadir even if you have existing databases.

Run the following commands (as root when necessary):

/etc/init.d/mysql stop
cp -rp /var/lib/mysql /new/mysql/dir
vi /etc/apparmor.d/usr.sbin.mysqld

Add the following two lines to the bottom:
/new/mysql/dir r,
/new/mysql/dir/** rwk,

/etc/init.d/apparmor restart
vi /etc/mysql/my.cnf

Change datadir from:
datadir=/var/lib/mysql
to:
datadir=/new/mysql/dir

/etc/init.d/mysql restart


Why does this seem so easy retrospectively?

---

### Post by sandboy10000 on 2008-09-08
hi christonabike. I follow your thread step by step.
But still can't start mysql after changing datadir.

My ubuntu version is 
Linux version 2.6.24-16-server (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:58:00 UTC 2008.

---

### Post by sandboy10000 on 2008-09-08
this is my error log in /var/log/syslog

Sep  9 00:41:54 www kernel: [46577.909134] audit(1220892114.838:76): type=1503 operation="inode_create"
requested_mask="w::" denied_mask="w::" name="/ape/mysqldata/www.lower-test" pid=10522 profile="/usr/sbin
/mysqld" namespace="default"
Sep  9 00:41:54 www mysqld[10524]: 080909  0:41:54 [Warning] Can't create test file /ape/mysqldata/www.l
ower-test
Sep  9 00:41:54 www mysqld[10524]: 080909  0:41:54 [Warning] Can't create test file /ape/mysqldata/www.l
ower-test
Sep  9 00:41:54 www kernel: [46577.931154] audit(1220892114.858:77): type=1503 operation="inode_permissi
on" requested_mask="rw::" denied_mask="rw::" name="/ape/mysqldata/ibdata1" pid=10522 profile="/usr/sbin/
mysqld" namespace="default"
Sep  9 00:41:54 www mysqld[10524]: 080909  0:41:54  InnoDB: Operating system error number 13 in a file o
peration.
Sep  9 00:41:54 www mysqld[10524]: InnoDB: The error means mysqld does not have the access rights to
Sep  9 00:41:54 www mysqld[10524]: InnoDB: the directory.
Sep  9 00:41:54 www mysqld[10524]: InnoDB: File name ./ibdata1
Sep  9 00:41:54 www mysqld[10524]: InnoDB: File operation call: 'open'.
Sep  9 00:41:54 www mysqld[10524]: InnoDB: Cannot continue operation.
Sep  9 00:41:54 www mysqld_safe[10530]: ended
Sep  9 00:42:08 www /etc/init.d/mysql[10680]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file
=/etc/mysql/debian.cnf ping' resulted in
Sep  9 00:42:08 www /etc/init.d/mysql[10680]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' fa
iled
Sep  9 00:42:08 www /etc/init.d/mysql[10680]: error: 'Can't connect to local MySQL server through socket
 '/var/run/mysqld/mysqld.sock' (2)'
Sep  9 00:42:08 www /etc/init.d/mysql[10680]: Check that mysqld is running and that the socket: '/var/ru
n/mysqld/mysqld.sock' exists!
Sep  9 00:42:08 www /etc/init.d/mysql[10680]:

---

### Post by shosta on 2008-10-12
Thank you for your information. 
I run into this problem and solved with this thread.
I was running mysql installed through the synaptic - edit - mark packages by task - LAMP Server  in Hardy.

---

### Post by 4835jack on 2009-08-27
Moving Mysql Databases to a different drive.

Open the Terminal
[INDENT]Root -i  This makes you the root user.
/etc/inin.d/mysql stop   This stops MYSQL
mv -rp /var/lib/mysql /Path to where you want the database to reside/mysql

This command moves your database.

[/INDENT]Now we need to edit some files so that MYSQL can find the database.
We will be using the VI editor so if you don't know how to use it, please do a google search before you begin.

[INDENT]vi /etc/apparmor.d/usr.sbin.mysqld

Go to the bottom of this file and add these two lines.

/the new patth to your database/ r,
/the new path to your database/** rwk,

Save the file and quit the VI editor

/etc/init.d/apparmor restart

vi /etc/mysql/my.cnf

Look for the line that starts with datadir
change this line to
datadir = the path to the new location of your database.

Save the file and quit the VI editor

/etc/init.d/mysql restart

exit

[/INDENT]If you have made it to the end with no errors your databases will now be accesable in there new location.

---

### Post by acracker on 2010-03-27
Thank you!!

---

### Post by cavh on 2010-06-16
I'm on Lucid, and MySQL would not start when I had both the old datadir and the new datadir listed in /etc/apparmor.d/usr.sbin.mysqld. 

Removing the old datadir entries and restarting apparmor allowed MySQL to start.

---

### Post by camouflageX on 2013-03-13
Thank you christonabike, I had the same problem in Ubuntu Server 12.04 and this pointed me to the solution. I would recommend to add the lines to the file /etc/apparmor.d/local/usr.sbin.mysqld, which may not have been available back then. However, mysql still could not load the databases which resulted in the following error message in /var/log/syslog:

kernel: [86306.624525] type=1400 audit(1363180626.080:214): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/mysqld" name="/mnt/drbd0/mysql/" pid=10216 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=106 ouid=106

And this error in mysql:
#1018 - Can't read dir of '.' (errno: 13)


I was able to fix it by adding a slash to the end of the mysql dir, like this:

```
/new/mysql/dir/ r,
/new/mysql/dir/** rwk,
```

---

### Post by khoshalar on 2013-05-18
many thanks :-)

---

### Post by adrian89 on 2013-05-18
Can someone help me with this issue I tried these answers and got nowhere.
I want to use my home directory for storing the mysql data, I've done the following:

The home directory is ```
/home/panzervi
```
```
sudo service mysql(and sudo /etc/init.d/mysql stop)...tried with both commands
sudo cp -R -p /var/lib/mysql /home/panzervi/mysql for copying
sudo nano /etc/mysql/my.cnf 
changed datadir=/var/lib/mysql to /home/panzervi/mysql
```
Saved and closed
```
sudo nano /etc/apparmor.d/usr.sbin.mysqld
```
changed 
```
/var/lib/mysql/ r,
/var/lib/mysql/** rwk,
```

to


```
/home/panzervi/mysql/ r,
/home/panzervi/mysql/** rwk,

```
Saved and closed
```
sudo /etc/init.d/apparmor reload
```

And mysql will not start,I also mention that I have the user's home directory encrypted can that be the issue?

Update: I've made a user and changed the mysql datadir to it's home directory and it worked.

---

