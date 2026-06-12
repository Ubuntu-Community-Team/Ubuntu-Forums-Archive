---
title: "MySQL server won't start"
date: 2012-01-31
forum: Server Platforms
---

### Post by mcarrara on 2012-01-31
I checked a couple of threads but I seem to have a different issue.  I am running MySQL 5.1 on Ububtu 10.04 LTS.  The server has been running since June with no issues.  Last night we had a power outage that lasted several hours.  

This morning I turned on all my servers and everything came back up except for MySQL.  When I try to start it with sudo service mysql start, the command prompt never comes back.  I check the syslog and see this series of errors repeated until I stop MySQL:

Jan 31 09:13:34 read init: mysql main process ended, respawning Jan 31 09:14:04 read init: mysql post-start process (3372) terminated with status 1 Jan 31 09:14:04 read kernel: [ 2755.910553] type=1505 audit(1328022844.198:36):  operation="profile_replace" pid=3501 name="/usr/sbin/mysqld" Jan 31 09:14:04 read init: mysql main process (3505) terminated with status 1 Jan 31 09:14:04 read init: mysql main process ended, respawning Jan 31 09:14:34 read init: mysql post-start process (3506) terminated with status 1 Jan 31 09:14:34 read kernel: [ 2785.980382] type=1505 audit(1328022874.318:37):  operation="profile_replace" pid=3579 name="/usr/sbin/mysqld" Jan 31 09:14:34 read init: mysql main process (3583) terminated with status 1 Jan 31 09:14:34 read init: mysql main process ended, respawning Jan 31 09:15:04 read init: mysql post-start process (3584) terminated with status 1

Did something get corrupted when the server shut down?  Or is there something else going on?

Mark

---

### Post by alhowat on 2012-01-31
Did you check the mysql error log /var/log/mysql/error.log? You might find more pertinent information in there.

Al

---

### Post by mcarrara on 2012-01-31
Yes I checked.  The log files are blank.  I am not very knowledgeable about Upstart.  Is there a way to add a switch to the MySQL start up to increase logging?

---

### Post by SeijiSensei on 2012-01-31
If you have a good backup of the database, I'd try this:

```
sudo mv /var/lib/mysql /var/lib/mysql.bad
sudo apt-get remove mysql-server
sudo apt-get install mysql-server

```

then see if MySQL will start.  If so, recreate the databases from the backup.

If you're not keeping nightly backups, preferably with mysqldump for portability, read [this thread]("http://ubuntuforums.org/showthread.php?t=1668840").

---

### Post by mcarrara on 2012-01-31
Of course I don't have a backup.  I am in the process of implementing Amanda for MYSQL, but it is not done.  I may be screwed.

Mark

---

### Post by mcarrara on 2012-01-31
Of course it turns out it was something dumb I did.  Some time back I edited the config file to change the default character set to UTF8, but I typed UTF-8.  Because this morning was the first time the server has restarted since then, I did not know my error.  Using Upstart gave no understandable error.  I tried to start the program directly, sudo mysqld start.  That gave me an error about UTF-8 not a valid character set.  After changing the config file to UTF8, the server started right up and it works.

---

### Post by jaspm2004 on 2012-07-27
> **alhowat said:**
> Did you check the mysql error log /var/log/mysql/error.log? You might find more pertinent information in there.

Al

thanks man! you save my life today! i saw on the log that the service where trying to restart, but there was no disk space available to complete the operation.

i made a clean-up and mysql started again without problems!

---

