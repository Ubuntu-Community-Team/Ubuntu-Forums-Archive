---
title: "mysql not starting in ubuntu"
date: 2018-06-12
forum: Server Platforms
---

### Post by rcrahul60 on 2018-06-12
I have this problem from last week first problem was that after starting mysqld safe mode for reset phpmyadminpassword mysql cant find the mysqld sock so i simply start the mysql and copy the .sock file as backup and start the mysql in safe mode and place the backup file but now mysql not stating at all. 

here the ouput:

```

tbosss@tbosss:~$ sudo /etc/init.d/mysql start
[....] Starting mysql (via systemctl): mysql.serviceJob for mysql.service failed because the control process exited with error code.
See "systemctl status mysql.service" and "journalctl -xe" for details.
 failed!

```

Here the error.log file:

```

2018-06-10T18:45:57.871006Z 0 [ERROR] InnoDB: Unable to lock ./ibdata1 error: 11
2018-06-10T18:45:57.871092Z 0 [Note] InnoDB: Check that you do not already have another mysqld process using the same InnoDB data or log files.
2018-06-10T18:45:57.871137Z 0 [Note] InnoDB: Unable to open the first data file
2018-06-10T18:45:57.871168Z 0 [ERROR] InnoDB: Operating system error number 11 in a file operation.
2018-06-10T18:45:57.871190Z 0 [ERROR] InnoDB: Error number 11 means 'Resource temporarily unavailable'
2018-06-10T18:45:57.871215Z 0 [Note] InnoDB: Some operating system error numbers are described at [http://dev.mysql.com/doc/refman/5.7/en/operating-system-error-codes.html](http://dev.mysql.com/doc/refman/5.7/en/operating-system-error-codes.html)
2018-06-10T18:45:57.871227Z 0 [ERROR] InnoDB: Cannot open datafile './ibdata1'
2018-06-10T18:45:57.871239Z 0 [ERROR] InnoDB: Could not open or create the system tablespace. If you tried to add new data files to the system tablespace, and it failed here, you should now edit innodb_data_file_path in my.cnf back to what it was, and remove the new ibdata files InnoDB created in this failed attempt. InnoDB only wrote those files full of zeros, but did not yet use them in any way. But be careful: do not remove old data files which contain your precious data!
2018-06-10T18:45:57.871267Z 0 [ERROR] InnoDB: Plugin initialization aborted with error Cannot open a file
2018-06-10T18:45:58.471929Z 0 [ERROR] Plugin 'InnoDB' init function returned error.
2018-06-10T18:45:58.472025Z 0 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
2018-06-10T18:45:58.472066Z 0 [ERROR] Failed to initialize builtin plugins.
2018-06-10T18:45:58.472092Z 0 [ERROR] Aborting

2018-06-10T18:45:58.472162Z 0 [Note] Binlog end
2018-06-10T18:45:58.472292Z 0 [Note] Shutting down plugin 'CSV'
2018-06-10T18:45:58.472640Z 0 [Note] /usr/sbin/mysqld: Shutdown complete

2018-06-10T18:59:19.365551Z 2 [Note] Aborted connection 2 to db: 'unconnected' user: 'root' host: '' (Got an error reading communication packets)
```

---

### Post by LHammonds on 2018-06-12
Incorrect file / group permissions?  The files/folders in my "mysql" data folder are owned by mysql:mysql

Look in the MySQL configuration file to see where datadir is placing your database files:
```
egrep datadir /etc/mysql/my.cnf
```

Example output:
```
datadir                = /var/lib/mysql
```

Then list the files and their permissions:
```
ls -l /var/lib/mysql
```

If all else fails, make a copy of your datadir, uninstall MySQL and re-install it.

LHammonds

---

### Post by QIII on 2018-06-12
@rcrahul60 --

Please use the default font and weight except when they are really necessary to draw attention to a particular part of your post or when doing so will make your meaning clearer.

Also, please enclose code, terminal commands and terminal output in code tags.  This preserves formatting and makes your posts easier to read.

To use code tags:

1.  Either click the # button in the toolbar, position your cursor between the code tags that appear and type or past your text; or type or paste your text, highlight it and then click the # button.

2.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

Thanks!

---

### Post by rcrahul60 on 2018-06-13
i dont have mysql directory inside etc and my.cnf is inside alternative directory

---

### Post by LHammonds on 2018-06-13
MySQL was not installed from the repository?

Let's step back and see what we are working with.

What are the output of the following commands:

```
lsb_release -a
```

```
uname -a
```

```
mysql --version
```I expect some version of 5.7 based on the error log

```
which mysql
```

---

### Post by rcrahul60 on 2018-06-14
output:

tbosss@tbosss:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 18.04 LTS
Release: 18.04
Codename: bionic

tbosss@tbosss:~$ uname -a
Linux tbosss 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

tbosss@tbosss:~$ mysql --version
mysql Ver 14.14 Distrib 5.7.22, for Linux (x86_64) using EditLine wrapper

tbosss@tbosss:~$ which mysql
/usr/bin/mysql

This mysql is a single text file

---

### Post by LHammonds on 2018-06-14
Well, it has been a long time since I have installed MySQL (I switched to MariaDB when the original MySQL development team made MariaDB for further enhancements/updates).  I just installed MySQL 5.7.22 on a new 18.04 server and it mentioned that no maintenance scripts were going to run and to read "/etc/mysql/FROZEN" for more info...but the file does not exist.

The /etc/mysql/my.cnf is a link to /etc/alternatives/my.cnf

I would not recommend using MySQL with it in this state (no updates, no security fixes, etc.) and I would recommend uninstalling it and installing MariaDB instead.  MariaDB is basically a MySQL drop-in replacement so any apps connecting to it can still think they are connecting to MySQL without any compatibility issues.

Steps to remove MySQL
```

sudo apt -y remove mysql-server
sudo apt -y autoremove
sudo rm -rf /etc/mysql
sudo apt -y install mariadb-server

```

Steps to install MariaDB
```

curl -sS https://downloads.mariadb.com/MariaDB/mariadb_repo_setup | sudo bash
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
sudo apt -y install mariadb-server
sudo mysql_secure_installation

```

There are many other steps I would do when setting up a database server and I am currently working on the 18.04 LTS versions of my [Ubuntu Server](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=244), [MariaDB](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=245), etc. but are not 100% perfect just yet but are 95% complete.

LHammonds

---

### Post by david12232 on 2018-06-14
Mysql may not work properly. If you start mysql using command service mysql start it should be only stopped by service mysql stop. [COLOR=#242729][FONT=Arial]If you start mysql by any other tool init.d, then you will get an error. All these errors can be fixed by using sudo code [/FONT][/COLOR][COLOR=#242729][FONT=Arial]if you aren't logged in as root. If you get any error you can try code like sudo service mysql start and for stopping sudo service mysql stop. This may fix your problem. If you need any other support you can check [/FONT][/COLOR][Microsoft Support UK]("https://microsoftsupport.co/microsoft-support-uk")

---

### Post by rcrahul60 on 2018-06-15
Thank you man for the help

---

### Post by rcrahul60 on 2018-06-15
mariadb also not working same problem

tbosss@tbosss:~$ sudo /etc/init.d/mysql start
[....] Starting mysql (via systemctl): mysql.serviceJob for mariadb.service failed because a timeout was exceeded.
See "systemctl status mariadb.service" and "journalctl -xe" for details.
 failed!
tbosss@tbosss:~$ systemctl status mariadb.services
Unit mariadb.services.service could not be found.
tbosss@tbosss:~$ systemctl status mariadb.service
&#9679; mariadb.service - MariaDB database server
   Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor preset: 
   Active: failed (Result: timeout) since Sat 2018-06-16 00:33:42 +04; 1min 14s 
  Process: 15061 ExecStart=/usr/sbin/mysqld $MYSQLD_OPTS $_WSREP_NEW_CLUSTER $_W
  Process: 14974 ExecStartPre=/bin/sh -c [ ! -e /usr/bin/galera_recovery ] && VA
  Process: 14972 ExecStartPre=/bin/sh -c systemctl unset-environment _WSREP_STAR
  Process: 14971 ExecStartPre=/usr/bin/install -m 755 -o mysql -g root -d /var/r
 Main PID: 15061 (code=exited, status=0/SUCCESS)

&#1610;&#1608;&#1606; 16 00:32:08 tbosss systemd[1]: Starting MariaDB database server...
&#1610;&#1608;&#1606; 16 00:32:09 tbosss mysqld[15061]: 2018-06-16  0:32:09 139857805417600 [Note]
&#1610;&#1608;&#1606; 16 00:33:39 tbosss systemd[1]: mariadb.service: Start operation timed out. T
&#1610;&#1608;&#1606; 16 00:33:42 tbosss systemd[1]: mariadb.service: Failed with result 'timeout'
&#1610;&#1608;&#1606; 16 00:33:42 tbosss systemd[1]: Failed to start MariaDB database server.

---

### Post by LHammonds on 2018-06-15
Although there is probably a compatibility script in the /etc/init.d location, the correct way to interact with the database service is:
```
systemctl stop mysql
systemctl start mysql
systemctl status mysql
```

The main thing that worries me here is this line:
```
Unit mariadb.services.service could not be found.
```

/lib/systemd/system/mariadb.service is the name of the file.  Not sure why it is looking for "mariadb.services.service"

LHammonds

---

### Post by darkod on 2018-06-16
@LHammonds, I think it is "looking" for that unexisting service because he is using the systemctl status wrong.

1. He doesn't use sudo in front.
2. According to the output in post #10 what he actually tried was:
```
systemctl status mariadb.services
```

That is wrong. In such case wouldn't systemctl append .service and try to find it like that (which obviously will fail).

Right?

---

### Post by LHammonds on 2018-06-16
Ah yes, now I see, he did mistype "systemctl status mariadb.services"

---

### Post by rcrahul60 on 2018-06-17
I also tried with sudo the problem is mariadb.service not starting:

tbosss@tbosss:~$ sudo systemctl start mysql
[sudo] password for tbosss: 
Job for mariadb.service failed because a timeout was exceeded.
See "systemctl status mariadb.service" and "journalctl -xe" for details.
tbosss@tbosss:~$ sudo systemctl status mariadb.services
Unit mariadb.services.service could not be found.
tbosss@tbosss:~$

---

### Post by darkod on 2018-06-17
Can you please try the following and post the output:
```
apt-cache policy mariadb-server
sudo systemctl status mariadb
```

---

### Post by LHammonds on 2018-06-18
For reference, this is what mine looks like on my 18.04 server (but with "status mysql" since "mariadb" is not valid on a MariaDB server):

```
# apt-cache policy mariadb-server
mariadb-server:
  Installed: 1:10.3.7+maria~bionic
  Candidate: 1:10.3.7+maria~bionic
  Version table:
 *** 1:10.3.7+maria~bionic 1000
       1000 http://downloads.mariadb.com/MariaDB/mariadb-10.3/repo/ubuntu bionic/main amd64 Packages
        100 /var/lib/dpkg/status
     1:10.1.29-6 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
```

```
# sudo systemctl status mysql
&#9679; mysql.service - LSB: Start and stop the mysql database server daemon
   Loaded: loaded (/etc/init.d/mysql; generated)
   Active: active (running) since Thu 2018-06-14 09:08:03 CDT; 4 days ago
     Docs: man:systemd-sysv-generator(8)
    Tasks: 32 (limit: 1112)
   CGroup: /system.slice/mysql.service
           &#9500;&#9472;4851 /bin/bash /usr/bin/mysqld_safe
           &#9492;&#9472;4913 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plu

Jun 14 09:08:04 tema1-mariadb /etc/mysql/debian-start[4967]: information_schema
Jun 14 09:08:04 tema1-mariadb /etc/mysql/debian-start[4967]: mysql
Jun 14 09:08:04 tema1-mariadb /etc/mysql/debian-start[4967]: performance_schema
Jun 14 09:08:04 tema1-mariadb /etc/mysql/debian-start[4967]: Phase 6/7: Checking
Jun 14 09:08:04 tema1-mariadb /etc/mysql/debian-start[4967]: Processing database
Jun 14 09:08:04 tema1-mariadb /etc/mysql/debian-start[4967]: information_schema
Jun 14 09:08:04 tema1-mariadb /etc/mysql/debian-start[4967]: performance_schema
Jun 14 09:08:04 tema1-mariadb /etc/mysql/debian-start[4967]: Phase 7/7: Running
Jun 14 09:08:04 tema1-mariadb /etc/mysql/debian-start[4967]: OK
Jun 14 09:08:04 tema1-mariadb /etc/mysql/debian-start[5032]: Triggering myisam-r
```

---

### Post by rcrahul60 on 2018-06-19
output:
tbosss@tbosss:~$ apt-cache policy mariadb-server
mariadb-server:
  Installed: 1:10.1.29-6
  Candidate: 1:10.1.29-6
  Version table:
 *** 1:10.1.29-6 500
        500 [http://ae.archive.ubuntu.com/ubuntu](http://ae.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages
        500 [http://ae.archive.ubuntu.com/ubuntu](http://ae.archive.ubuntu.com/ubuntu) bionic/universe i386 Packages
        100 /var/lib/dpkg/status
     10.1.33+maria-1~bionic 500
        500 [http://sfo1.mirrors.digitalocean.com/mariadb/repo/10.1/ubuntu](http://sfo1.mirrors.digitalocean.com/mariadb/repo/10.1/ubuntu) bionic/main amd64 Packages
tbosss@tbosss:~$ sudo systemctl status mariadb
&#9679; mariadb.service - MariaDB database server
   Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor preset: 
   Active: failed (Result: timeout) since Tue 2018-06-19 19:56:26 +04; 3h 9min a
  Process: 1147 ExecStart=/usr/sbin/mysqld $MYSQLD_OPTS $_WSREP_NEW_CLUSTER $_WS
  Process: 1056 ExecStartPre=/bin/sh -c [ ! -e /usr/bin/galera_recovery ] && VAR
  Process: 1044 ExecStartPre=/bin/sh -c systemctl unset-environment _WSREP_START
  Process: 1040 ExecStartPre=/usr/bin/install -m 755 -o mysql -g root -d /var/ru
 Main PID: 1147 (code=exited, status=0/SUCCESS)

&#1610;&#1608;&#1606; 19 19:54:52 tbosss systemd[1]: Starting MariaDB database server...
&#1610;&#1608;&#1606; 19 19:54:54 tbosss mysqld[1147]: 2018-06-19 19:54:54 139890954439808 [Note] 
&#1610;&#1608;&#1606; 19 19:56:23 tbosss systemd[1]: mariadb.service: Start operation timed out. T
&#1610;&#1608;&#1606; 19 19:56:26 tbosss systemd[1]: mariadb.service: Failed with result 'timeout'
&#1610;&#1608;&#1606; 19 19:56:26 tbosss systemd[1]: Failed to start MariaDB database server.

---

### Post by LHammonds on 2018-06-19
Notice the difference here?

Mine:
```

mariadb-server:
  Installed: 1:10.3.7+maria~bionic
  Candidate: 1:10.3.7+maria~bionic

```

Yours:
```

mariadb-server:
  Installed: 1:10.1.29-6
  Candidate: 1:10.1.29-6

```

Mine:
```

1000 http://downloads.mariadb.com/MariaDB/mariadb-10.3/repo/ubuntu bionic/main amd64 Packages

```

Yours:
```

500 http://sfo1.mirrors.digitalocean.com/mariadb/repo/10.1/ubuntu bionic/main amd64 Packages

```

Your MariaDB software is not coming from the MariaDB repositories which has the latest builds available.

If that version is coming from DigitialOcean, maybe they are making changes to it and introducing bugs breaking it on the 18.04 platform.  Don't know but I do know you are not pulling it from MariaDB's official repository.  The MariaDB version only recently became "verified" to work on 18.04 platform...which delayed my how-to tutorials since I wanted the stable/supported version.

LHammonds

---

### Post by rcrahul60 on 2018-06-20
it's just different mirror I don't think its matter

---

### Post by darkod on 2018-06-21
Have you tried removing and reinstalling mariadb-server?

And did you remove your previous mysql installation first?

---

### Post by LHammonds on 2018-06-21
> **rcrahul60 said:**
> it's just different mirror I don't think its matter
The point I was trying to make is that I do not think the version you have installed was "officially" supported on 18.04 platform.  The version I am running is supported.  I halted my 16.04 to 18.04 upgrades (well, more like migrations) because I wanted to wait for MariaDB to reach a stable version on 18.04 and that only recently happened.

I am not sure that what you are experiencing is only just due to installing an older version though but it is extremely difficult to say since I was not looking over your shoulder while you installed Ubuntu Server and then the database software.

You can however see the exact steps I take whenever I setup [Ubuntu Server]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=244") and [MariaDB]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=245") on my website and compare that to how you are installing it.  Please note that my 18.04 documentation is not what I call 100% complete but 95% complete at this point.

You might also have something messed up on your server after doing multiple install/uninstall.  I'd recommend using VirtualBox and install a fresh copy of Ubuntu Server 18.04 and MariaDB right after that.  If you still get the same problem, then it has to be something you are (are not) doing rather than it being a left-over install remnant or bug in the version.

I wish I could throw out a single-sentence answer to fix your problem but I'm just not that adept at trouble-shooting other peoples setups.  Sorry.

LHammonds

---

### Post by rcrahul60 on 2018-06-21
Its okay man you were a big help..

---

### Post by darkod on 2018-06-21
You seem to have missed one of my questions. Did you remove the mysql manual installation before installing maridb-server? If you didn't, there will probably be conflicts. Using the same port is the first thing coming to mind...

---

