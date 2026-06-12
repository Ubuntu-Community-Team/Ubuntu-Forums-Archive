---
title: "mysqld.sock missing?"
date: 2006-03-05
forum: Server Platforms
---

### Post by TDave on 2006-03-05
All

First of all let me apologise for being a complete n00b in terms of server setups. I have a few slight ideas about some aspects but on the whole I'm  an utter n00b.

Basically I am part of a small project starting to launch our own self-hosted site and wanted to use my Powerbook to let me try out various options on design etc. Basically setting up a local LAMP server. I followed the outlines in UbuntuGuide and all was fine up until installing the MySQL server. When I try to run mysql admin I get an error regarding the missing mysqld.sock file and when following what appeared similar problems in such posts as here
[http://ubuntuforums.org/showthread.php?t=111292](http://ubuntuforums.org/showthread.php?t=111292)

I still get errors. Below are a some various things I get. I don't know if all or any are of much help, but hopefully so.
Syslog
```
localhost mysqld_safe[5846] started
localhost mysqld[5850] InnoDB: No valid checkpoint found.
localhost mysqld[5850] InnoDB: If this error appears when you are creating an InnoDB database,
localhost mysqld[5850] InnoDB: the problem may be that during an earlier attempt you managed
localhost mysqld[5850] InnoDB: to create the InnoDB data files, but log file creation failed.
localhost mysqld[5850] InnoDB: If that is the case, please refer to
localhost mysqld[5850] InnoDB: http://dev.mysql.com/doc/mysql/en/Error_creating_InnoDB.html
localhost mysqld[5850] 060228  9:33:22 Can't init databases
localhost mysqld[5850] 060228  9:33:22 Aborting
localhost mysqld[5850] 
localhost mysqld[5850] 060228  9:33:22  InnoDB: Warning: shutting down a not properly started
localhost mysqld[5850] InnoDB: or created database!
localhost mysqld[5850] 060228  9:33:22 /usr/sbin/mysqld: Shutdown Complete
localhost mysqld[5850] 
localhost mysqld_safe[5856] ended
localhost /etc/init.d/mysql[5920] 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
localhost /etc/init.d/mysql[5920] ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
localhost /etc/init.d/mysql[5920] error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
localhost /etc/init.d/mysql[5920] Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
localhost /etc/init.d/mysql[5920] 
```

Bash
```
dave@minimus:/var/lib/mysql$ ls
ib_arch_log_0000000000  ibdata1  ib_logfile0  ib_logfile1  mysql  test
dave@minimus:/var/lib/mysql$ mv mysql mysql_bkp
mv: cannot move `mysql' to `mysql_bkp': Permission denied
dave@minimus:/var/lib/mysql$ sudo mv mysql mysql_bkp
dave@minimus:/var/lib/mysql$ ls
ib_arch_log_0000000000  ibdata1  ib_logfile0  ib_logfile1  mysql_bkp  test
dave@minimus:/var/lib/mysql$ sudo mysql_install_db
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
060228  9:31:25 /usr/sbin/mysqld: Shutdown Complete


To start mysqld at boot time you have to copy support-files/mysql.server
to the right place for your system

PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
To do so, start the server, then issue the following commands:
/usr/bin/mysqladmin -u root password 'new-password'
/usr/bin/mysqladmin -u root -h minimus password 'new-password'
See the manual for more instructions.

You can start the MySQL daemon with:
cd /usr ; /usr/bin/mysqld_safe &

You can test the MySQL daemon with the benchmarks in the 'sql-bench' directory:
cd sql-bench ; perl run-all-tests

Please report any problems with the /usr/bin/mysqlbug script!

The latest information about MySQL is available on the web at
http://www.mysql.com
Support MySQL by buying support/licenses at https://order.mysql.com

dave@minimus:/var/lib/mysql$ sudo chown mysql:mysql mysql
dave@minimus:/var/lib/mysql$ sudo chmod 750 mysql
dave@minimus:/var/lib/mysql$ sudo chown mysql:mysql test
dave@minimus:/var/lib/mysql$ sudo chmod 750 test
dave@minimus:/var/lib/mysql$ ls -lrt
total 20560
drwxr-x---  2 mysql mysql     4096 2006-02-26 09:26 test
drwxr-xr-x  2 mysql root      4096 2006-02-26 09:26 mysql_bkp
-rw-rw----  1 mysql mysql  5242880 2006-02-26 09:26 ib_logfile1
-rw-rw----  1 mysql mysql    25088 2006-02-26 09:26 ib_arch_log_0000000000
-rw-rw----  1 mysql mysql  5242880 2006-02-26 09:26 ib_logfile0
-rw-rw----  1 mysql mysql 10485760 2006-02-26 09:26 ibdata1
drwxr-x---  2 mysql mysql     4096 2006-02-28 09:31 mysql
dave@minimus:/var/lib/mysql$ sudo /etc/init.d/mysqld
sudo: /etc/init.d/mysqld: command not found
dave@minimus:/var/lib/mysql$ sudo /etc/init.d/mysql
Usage: /etc/init.d/mysql start|stop|restart|reload|force-reload
dave@minimus:/var/lib/mysql$ sudo /etc/init.d/mysql start
Starting MySQL database server: mysqld^[[B^[[A
...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
dave@minimus:/var/lib/mysql$ sudo /etc/init.d/mysql start
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
dave@minimus:/var/lib/mysql$ mysqladmin -u root password 322415zh
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
dave@minimus:/var/lib/mysql$ sudo mysqladmin -u root password 322415zh
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

my.cnf
```
[mysqld]
#
# * Basic Settings
#
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
language        = /usr/share/mysql/english
skip-external-locking
```

I've just removed mysql-server an associated files again (already did one reinstall) and wait to see any possible pieces of advice that might help.

I'm running Breezy on a Powerbook G4, 512Mb RAM.

Many thanks

Dave

---

### Post by alcon on 2006-04-28
I'm getting the exact same problem.  I installed it following the instructions found in the user wiki here:
[https://wiki.ubuntu.com/ApacheMySQLPHP?action=show&redirect=ApachePHPMySQL](https://wiki.ubuntu.com/ApacheMySQLPHP?action=show&redirect=ApachePHPMySQL)

> $ sudo apt-get install mysql-server
$ sudo apt-get install libapache2-mod-auth-mysql
$ sudo apt-get install php5-mysql

After installing MySQL

Type this for creating standard configuration:

cd /usr
sudo ./bin/mysql_install_db --user=mysql

The first time for setting the password by console you need to type:

sudo mysql -u root

My output is exactly the same as above.

---

### Post by Cogito on 2006-05-03
yep, exact same problem on my box.  Ive tried complining it from source and using apt-get.  I also made a hole in my firestarter firewall for it but still no avail!

---

### Post by mek1 on 2006-05-03
I'm also having this problem, running 5.10 PPC on a powerbook G4

---

### Post by zuus on 2006-05-04
Had the [same problem as described]("http://www.ubuntuforums.org/showthread.php?t=168165") on my PPC. 

After spending countless hours and lost hair trying to diagnose it, the solution came to me - I went forth, installed Ubuntu on a x86 PC and mysql-server worked flawlessly from the word go. So far this is the only solution (well... not really a solution) I've found for this problem. Seems to be a bug in the PPC versions ](*,)

---

### Post by mek1 on 2006-05-04
got it working last night after much hacking.  i had installed mysql-server and -admin from apt-get, so I reversed that process.  Then I went into synaptic and checked the latest MYSQL server (4.1 I believe) and admin.  I was prompted to keep or replace 'my.cnf' (which is refferenced quite a bit with this issue) so I went ahead and replaced the file.  After a service restart I was up and running, completing my Cacti install.  The mysqld.sock file has also magically appeared where as previously it didn't exist on my system at all.

hope this helps

-matt

---

### Post by lvanderree on 2006-05-05
I had this problem too, but I solved it! Maybe this solution helps for you too.

The problem hadn't had to do too much with mysql settings itself, but with your client application, in my case postfix (for user lookup).

In debian I connected postfix with mysql by its name: "localhost", but for some reason (don't know exactly why, read it in a postifx howto) mysql is much more happy when you use ip-addresses in Ubuntu. So use 127.0.0.1 instead, and my problem dissapeared.

Hopes this helps you all out.

---

### Post by TDave on 2006-05-31
Well... kinda worked... :-)

Tried a combination of the suggestions here.

I'd actually tried the 4.1 approach earlier on but given your stated success I retried it and it worked! I now have a working mysql--server setup, complete with mysqld.sock but it somehow managed to bork my apache2 setup... I have NO idea how.. basically apache, even after multiple restarts and blank-faced stares through the config files would not serve up the pages locally one mysql was installed.

So I've wiped all out of the way and trying the start from scratch approach once more... at least Dapper's here tomorrow!

:-)

Thanks for everyones feedback.

---

### Post by cosine7 on 2006-06-01
Agree here, i had 4 not 4.1 on my ppc, now mysql is all good

---

