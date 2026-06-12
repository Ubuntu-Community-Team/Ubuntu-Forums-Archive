---
title: "Ubuntu 10.04 - upgrade to MYSQL causing &quot; Can't connect to local MySQL server&quot;"
date: 2012-03-13
forum: Server Platforms
---

### Post by AntiBodies on 2012-03-13
Hello

Ive have had Zabbix 1.8.1 (from official repositories) running on Ubuntu 10.04 for some time now and has been working great. I've just applied some recent updates (which included mysql updates.. and stupidly I did not run snapshot of the server (or recent backup) beforehand).. Ever since I cannot gain access to Zabbix due to mysql connect errors:

mysql_connect(): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)[/usr/share/zabbix/include/db.inc.php:58]

This points to mysql not running but it is running and I can confirm processing information.

when I restart the mysql service I can initially connect the one time using commandline mysql.. but trying again gives similar error to above on the commandline: 

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)

Ive researched the error and possibly looking to permission errors but im not sure where. Ive adjusted the mysql config file but to no avail. mysql looks to be there and appears to be working it appears to be some communication from the local console. I have also seen issues around communication to 127.0.0.1 as opposed to "localhost" etc but the bind address is 127.0.0.1 in the mysql config file.

The errors.log file is basically repeating over and over again with the following log entries:

```
InnoDB: Doing recovery: scanned up to log sequence number 110 695459004
120314 11:03:15  InnoDB: Starting an apply batch of log records to the database...
InnoDB: Progress in percents: 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96 97 98 99
InnoDB: Apply batch completed
120314 11:03:16  InnoDB: Started; log sequence number 110 695459004
120314 11:03:16 [Note] Event Scheduler: Loaded 0 events
120314 11:03:16 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.61-0ubuntu0.10.04.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
InnoDB: Error: tried to read 49152 bytes at offset 0 3751936.
InnoDB: Was only able to read 32768.
120314 11:03:18  InnoDB: Operating system error number 0 in a file operation.
InnoDB: Error number 0 means 'Success'.
InnoDB: Some operating system error numbers are described at
InnoDB: http://dev.mysql.com/doc/refman/5.1/en/operating-system-error-codes.html
InnoDB: File operation call: 'read'.
InnoDB: Cannot continue operation.
120314 11:03:18 [Note] Plugin 'FEDERATED' is disabled.
120314 11:03:18  InnoDB: Initializing buffer pool, size = 8.0M
120314 11:03:18  InnoDB: Completed initialization of buffer pool
InnoDB: Log scan progressed past the checkpoint lsn 110 695455190
120314 11:03:18  InnoDB: Database was not shut down normally!
InnoDB: Starting crash recovery.
InnoDB: Reading tablespace information from the .ibd files...
InnoDB: Restoring possible half-written data pages from the doublewrite
InnoDB: buffer...
InnoDB: Doing recovery: scanned up to log sequence number 110 695459004
120314 11:03:18  InnoDB: Starting an apply batch of log records to the database...
InnoDB: Progress in percents: 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96 97 98 99
InnoDB: Apply batch completed
120314 11:03:18  InnoDB: Started; log sequence number 110 695459004
120314 11:03:18 [Note] Event Scheduler: Loaded 0 events
120314 11:03:18 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.61-0ubuntu0.10.04.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
InnoDB: Error: tried to read 49152 bytes at offset 0 3751936.
InnoDB: Was only able to read 32768.
120314 11:03:20  InnoDB: Operating system error number 0 in a file operation.
InnoDB: Error number 0 means 'Success'.
InnoDB: Some operating system error numbers are described at
InnoDB: http://dev.mysql.com/doc/refman/5.1/en/operating-system-error-codes.html
InnoDB: File operation call: 'read'.

```


If anyone has any pointers that would be great..

---

### Post by AntiBodies on 2012-03-14
Fixed Issue

check out this link. [http://www.softwareprojects.com/resources/programming/t-how-to-fix-mysql-database-myisam-innodb-1634.html](http://www.softwareprojects.com/resources/programming/t-how-to-fix-mysql-database-myisam-innodb-1634.html)

Has a lot of info on recovering Mysql

I had to do number 7.. I could get access to mysql dialog direct after a restart so:

Step 1: Add this line to your /etc/my.cnf configuration file:

```
[mysqld] 
innodb_force_recovery = 4
```

Step 2: Restart MySQL. Your database will now start, but with innodb_force_recovery, all INSERTs and UPDATEs will be ignored. 

Step 3: Dump all tables 

mysqldump --force --compress --triggers --routines --create-options -uUSER -pPASSWORD --all-databases > /home/yourhome/databases.sql
 

Step 4: Shutdown database and delete the data directory.

i moved folder so:
```
sudo mv /var/lib/mysql /var/lib/mysql.old
```

Step 5: Run mysql_install_db to create MySQL default tables

Step 6: reset your root password back or a different one
```
mysqladmin -u root password NEWPASSWORD
```

Step 7: restore all databases back.
```
mysql -u root -p </home/yourhome/databases.sql
```


This worked well.

---

