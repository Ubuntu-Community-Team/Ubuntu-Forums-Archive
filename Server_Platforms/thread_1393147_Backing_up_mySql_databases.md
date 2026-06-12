---
title: "Backing up mySql databases"
date: 2010-01-29
forum: Server Platforms
---

### Post by silentrebel on 2010-01-29
I'm using mySql to run a Wiki on my server.  I would like to be able to back it up every once in a while in case anything happens to it.  Could someone indicate where mySql server databases are saved?  Furthermore, a script or utility for backing up/restoring backed up databases to mySql would greatly be appreciated.
Thanks

---

### Post by lykwydchykyn on 2010-01-29
With mysql, as with most RDBMS, you probably don't want to just copy the database files (they're in /var/lib/mysql, by the way, but please read on).

For various reasons dealing with file consistency, what you want is to do a regular dump of the databases.  You can use mysqldump for this (it comes with mysql).

You could set up a local (ie. can only connect from localhost) mysql user just for backups with no database password, then the command would be something like this:

```

mysqldump -ubackup_user somedatabase > somedatabase.sql

```

Then you can just backup the somedatabase.sql file.  If the database is large, you might want to run it through gzip as well.

You put this in a script and execute it regularly with cron.

To restore, you 'd just do this:

```

mysql -uadminuser -p somedatabase < somedatabase.sql

```


I should mention at this point that if you're using Webmin, the mysql module has a very easy interface for setting up automated database backups.

---

### Post by kiranmurari on 2010-01-29
If you have shell access to your database server, you can backup the database using mysqldump. By default, the output of the command will dump the contents of the database in SQL statements to your console. This output can then be piped or redirected to any location you want. If you plan to backup your database, you can pipe the output to a sql file, which will contain the SQL statements to recreate and populate the database tables when you wish to restore your database.
```
mysqldump -u [username] -p [password] [databasename] > [backupfile.sql]
    o [username] - this is your database username
    o [password] - this is the password for your database
    o [databasename] - the name of your database
    o [backupfile.sql] - the file to which the backup should be written.
```To backup your database 'example' with the username 'admin' and password 'password' to a file example.sql, issue the command:
```
$ mysqldump -u admin -p password example > example.sql
```If you'd like restrict the backup to only certain tables of your database, you
can also specify the tables you want to backup.
```
mysqldump -u [username] -p [password] [databasename] [table1 table2 ....]
    o [tables] - This is a list of tables to backup. Each table is separated by a space
```If you want to backup only table_1 & table_2 from the 'example' database,
```
mysqldump --add-drop-table -u admin -p password example table_1 table_2 > example.sql
```You can easily restore the mysqldump file by using the mysql command. This method is usually used to recreate or rebuild the database from scratch.
```
mysql -u [username] -p [password] [database_to_restore] < [backupfile]
```Here's how you would restore your example.sql file to the 'example' database.
```
mysql -u admin -p password example < example.sql
```You can use AutoMySQLBackup Script that can take periodic database backups.
See: [http://www.debianhelp.co.uk/mysqlscript.htm](http://www.debianhelp.co.uk/mysqlscript.htm)

Hope this helps.

---

### Post by shmk on 2010-03-09
Thanks for the guide :)

Are there any parameter to add to keep export and import valid if you have InnoDB tables with Foreign Keys or myISAM tables with Triggers?

---

### Post by spynappels on 2010-03-09
You could also download and run MySQL Workbench 5.2 OSS and connect to your MySQL servers and take backups that way, this is also good for browsing and editing tables and dbs using a GUI rather than CLI from the server itself.

Just another option, not saying it is better or worse than any other.....

---

### Post by terazen on 2010-03-09
Another solution...

[http://sourceforge.net/projects/automysqlbackup/](http://sourceforge.net/projects/automysqlbackup/)

Just put your settings in the file and add it to run in crontab.  It keeps daily, weekly, and monthly backups for as many databases as you care to add.

---

