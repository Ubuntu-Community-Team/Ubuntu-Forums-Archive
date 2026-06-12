---
title: "mySQL Incremental Backup - Binary Log file names"
date: 2011-03-15
forum: Server Platforms
---

### Post by John Raycheba on 2011-03-15
I am currently using a script to backup my Ubuntu 10.04.1 system. The mySQL databases are backed up separately from the the system / data.
 
My problem is with the mySQL incremental / binary log backups.
 
The problem is that the binary log file(s) are always named xxxx-bin.1.
 
Up to about a month ago the binary logs were named xxxx-bin.000001, xxxx-bin.000002, etc.
 
I did make some changes at about the time that this change in file naming ocurred, but I can not identify what, if any, setting I may have changed that has caused all of the binary log files to always have the same name.
 
My back up script uses both mysqldump and mysqladmin flush-logs to create the binary logs.
 
All of the setting for mysqldump and mysqladmin are contained in the my.cnf file.
 
The my.cnf file contents that are relavent are as follows:
 
```
 
log-bin  = /mnt/sdb1/backups/mysqldbs/xxx-mysql-bin
expire_logs_days = 10
max_binlog_size = 100M
[mysqldump]
quick
quote-names
max_allowed_packet = 16M
#JR: added following lines for sql dumps.
user  = root
password  = xxxxx
all-databases
comments
delete-master-logs
dump-date
extended-insert
flush-logs
flush-privileges
lock-tables
master-data=2
routines
single-transaction
triggers
[mysqladmin]
password = xxxxx

```
 
The statements in the backup script that do the backup are:
 
mysqladmin flush-logs
 
or
 
mysqldump | gzip > $DB_BACKUP_DIR/$ARCHIVE_FILE   #Note: delete-master-logs in my.cnf

Any and all suggestions will be greatly appreciated.
 
Regards,
 
John

---

### Post by BkkBonanza on 2011-03-16
"flush logs" should close the binary log and start a new one with the next number. If you removed the flush logs statement then the number would stay the same. I would make sure the flush is still happening and maybe do a manual flush to see that the file number changes.

I use a similar method during my backups and the only time I've seen the number stay the same is when there was a problem with my cron daemon that prevented the backup from running. I'm not aware of any config that stops the number advancing even in the case of a flush. 

(After all the purpose of the flush is to commit the log before continuing and ensure the log file is valid - which it can't do if it's still held open and incomplete)

On the other hand, perhaps the delete-master-log causes it to always start a new log during flush and that would always be at #1 - so removing that seems like a good choice. I'd read up on that command...

---

### Post by John Raycheba on 2011-03-16
BkkBonanza,
 
Thank you for the suggestion.
 
I received your suggestion 15 minutes before my backup script was scheduled to run.
 
I edited the my.cnf file to comment out the "delete-master-logs" line and after saving the new my.cnf file restarted mySQL.
 
Unfortunately, the result was the same -- The binary log file is still named xxxx.log.1
 
What am I / we missing?
 
Regards,
 
John

---

### Post by BkkBonanza on 2011-03-16
I don't think the cnf file change will take effect unless you restart mysql - but I may be wrong on that. I believe restarting mysql would also flush the log and increment the log number. It has for me in the past. 

There is a reload option from the mysqladmin command line but from what I read it is version dependent.

Also see this page in the docs with some warnings about delete-master-logs. It says logs are removed even if the slave hasn't processed them yet. Since it doesn't keep anything I would assume it starts at #1 each time.

[http://dev.mysql.com/doc/refman/5.0/en/backup-policy.html](http://dev.mysql.com/doc/refman/5.0/en/backup-policy.html)

---

