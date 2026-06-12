---
title: "I can't access the mySQL prompt. Tried 100's of guides. Please help!"
date: 2011-07-22
forum: Server Platforms
---

### Post by Unknown Frequency on 2011-07-22
Hi there**. **This is my first post on your well established forum, which I have read from numerous times already. I erased Windows a week ago and is loving Ubuntu 10.04 (which changed to xubuntu after installing Qimo for Kids??) ever since. 
Now I want to get coding again and PHP is working fine, but I can't access mysql!?

I followed a ton of guides, completely removed, reinstalled etc. Nothing works.
Here some stuff that might be interresting. I can't remember the "ls" and "awk" and "grep" commands to use, so please guide me if you need more info. I'll be back again tonight. THANKS ALOT!
[B]
sudo mysql status[/B]
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

**sudo update-rc.d mysql defaults**
update-rc.d: warning: /etc/init.d/mysql missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/mysql ...
   /etc/rc0.d/K20mysql -> ../init.d/mysql
   /etc/rc1.d/K20mysql -> ../init.d/mysql
   /etc/rc6.d/K20mysql -> ../init.d/mysql
   /etc/rc2.d/S20mysql -> ../init.d/mysql
   /etc/rc3.d/S20mysql -> ../init.d/mysql
   /etc/rc4.d/S20mysql -> ../init.d/mysql
   /etc/rc5.d/S20mysql -> ../init.d/mysql


**service mysql start**
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.50" (uid=1000 pid=2518 comm="start mysql ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

**sudo service mysql start**
start: Job is already running: mysql

**sudo mysql -u root -p **
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

Some stuff from **/var/log/mysql/error.log**

110722 10:58:27 [Note] Plugin 'FEDERATED' is disabled.
110722 10:58:27  InnoDB: Initializing buffer pool, size = 8.0M
110722 10:58:27  InnoDB: Completed initialization of buffer pool
110722 10:58:27  InnoDB: Started; log sequence number 0 44233
110722 10:58:27 [Note] Event Scheduler: Loaded 0 events
110722 10:58:27 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.54-1ubuntu4'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
110722 11:00:25 [Note] Plugin 'FEDERATED' is disabled.
mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
110722 11:00:25 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110722 11:00:25  InnoDB: Initializing buffer pool, size = 8.0M
110722 11:00:25  InnoDB: Completed initialization of buffer pool
110722 11:00:25  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
110722 11:00:34 [Note] Plugin 'FEDERATED' is disabled.
110722 11:00:34  InnoDB: Initializing buffer pool, size = 8.0M
110722 11:00:34  InnoDB: Completed initialization of buffer pool
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.

110722 11:02:14  InnoDB: Unable to open the first data file
InnoDB: Error in opening ./ibdata1
110722 11:02:14  InnoDB: Operating system error number 11 in a file operation.
InnoDB: Error number 11 means 'Resource temporarily unavailable'.
InnoDB: Some operating system error numbers are described at
InnoDB: [http://dev.mysql.com/doc/refman/5.1/en/operating-system-error-codes.html](http://dev.mysql.com/doc/refman/5.1/en/operating-system-error-codes.html)
InnoDB: Could not open or create data files.
InnoDB: If you tried to add new data files, and it failed here,
InnoDB: you should now edit innodb_data_file_path in my.cnf back
InnoDB: to what it was, and remove the new ibdata files InnoDB created
InnoDB: in this failed attempt. InnoDB only wrote those files full of
InnoDB: zeros, but did not yet use them in any way. But be careful: do not
InnoDB: remove old data files which contain your precious data!
110722 11:02:14 [ERROR] Plugin 'InnoDB' init function returned error.
110722 11:02:14 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
mysqld: Too many arguments (first extra is 'start').
Use --verbose --help to get a list of available options
110722 11:02:14 [ERROR] Aborting

110722 11:02:14 [Note] mysqld: Shutdown complete

---

### Post by Unknown Frequency on 2011-07-22
Is reinstalling Ubuntu the only way?

---

### Post by drdos2006 on 2011-07-22
Load Webmin and see if you can control MySQL via Webmin.
```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb
###  	web site is here: http://sourceforge.net/projects/webadmin/files/webmin/1.550/webmin_1.550_all.deb
Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by cariboo on 2011-07-22
Are you using the password you created when you install mysql?

I would also suggest you learn to read the log files, as they tell you what you need to do:

```
mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
110722 11:00:25 [ERROR] Can't open the mysql.plugin table. **Please run mysql_upgrade to create it.**
110722 11:00:25 InnoDB: Initializing buffer pool, size = 8.0M
```

---

### Post by Unknown Frequency on 2011-07-23
I got it working now with webmin. Thanks alot guys! Means alot!

---

