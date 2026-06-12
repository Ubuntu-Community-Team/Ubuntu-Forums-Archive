---
title: "How to move mysql data to another server?"
date: 2013-02-20
forum: Server Platforms
---

### Post by darkod on 2013-02-20
Hi all. I know there are many tutorials on google on the subject, I'm not lazy to look, but because some procedures might be very old, and because I haven't done this before and have limited experience with mysql, I wanted to ask for an advice what is best to do.

Lets say I have machine A and machine B with mysql. On both machines I have the same database and table (only one table in the DB). The user is different. The machines are not clustered, or synced, or anything. Completely separate, only the same DB and table exists because they both serve as Asterisk PBX.

I have done all the configuration on machine B and it does all the work now. Before decommissioning machine A, all that is left is move the call records history, the mentioned table.

Now start the questions:
1. Is mysqldump the way to go? What would the exact syntax be?
2. Do I need to somehow stop or freeze the DB on machine A before that? Calls are not entering in that PBX now so that won't be a problem.
3. What syntax would I use to import on machine B?
4. Will that affect existing data? How to protect myself from any mess or losing the data I want to transfer and the data existing now on the server?
5. Since the DB and table are the same, will the data populate itself automatically where it needs to go? Anything I need to do during the import command to make sure it goes into the existing table, instead of creating some new table?

On another note, and as a sort of backup, is it possible first to export the data in sort of CSV file, that I can later open with Excel for example? How would that syntax be?

Thanks a lot in advance.

---

### Post by darkod on 2013-02-20
In addition, if the helps the more experienced ones, I have just checked the mysql versions.
old server: 4.1.22
new server: 5.0.77

---

### Post by wlraider70 on 2013-02-20
I'm not super experienced here. but if you use phpMyAdmin. There is a backup/export tool, it has a LOT of advanced options to make sure you get just how you want.

---

### Post by darkod on 2013-02-20
> **wlraider70 said:**
> I'm not super experienced here. but if you use phpMyAdmin. There is a backup/export tool, it has a LOT of advanced options to make sure you get just how you want.

Thanks, but I don't mind using the CLI and unless phpmyadmin is the best way, I would prefer mysql commands. I don't know how phpmyadmin work neither, so I would need guidance about it too. :)

---

### Post by lykwydchykyn on 2013-02-20
I generally use mysqldump to create a sql export of the database, then re-import using the mysql command.  The exact syntax depends on how you are authenticating, but more or less it's like this:

```

mysqldump -u username -p databasename > dumpfile.sql

```

Copy this file over to a machine that can access the new database, and run:
```

mysql -u username -p databasename < dumpfile.sql

```

That's pretty much it.

---

### Post by Habitual on 2013-02-20
> **darkod said:**
> 
1. Is mysqldump the way to go? What would the exact syntax be?

That's rather subjective.
I use mysqldump on each of the individual dbs by name using something like this
as root:

```
WORKDIR=/edit/me
#!/bin/bash
mysql -e "show databases;" -Ns > "$WORKDIR"/DBs.in
for i in $(cat "$WORKDIR"/DBs.in) ; do mysqldump $i > "$WORKDIR"/$i.sql ; done
#EOF
```

It's something to consider, I guess. :)

---

### Post by darkod on 2013-02-20
> **lykwydchykyn said:**
> I generally use mysqldump to create a sql export of the database, then re-import using the mysql command.  The exact syntax depends on how you are authenticating, but more or less it's like this:

```

mysqldump -u username -p databasename > dumpfile.sql

```

Copy this file over to a machine that can access the new database, and run:
```

mysql -u username -p databasename < dumpfile.sql

```

That's pretty much it.

This is what I found on other websites too. Further query: Do I have to think of keys, indexes, etc? For example the procedure above, will everything go where it's supposed to?

---

### Post by darkod on 2013-02-20
Googling around about the secondary question, how to export/dump in csv format, I found something like:
```
mysqldump -u username -p -t -T/path database --fields-terminated-by=,
```

Does this still work?

Why does the example have the -t option? The docs say that's --no-create-info, not to make CREATE TABLE statements.

Do I need to use the -T option too as the example?

---

### Post by GordThompson on 2013-02-20
If you're comfortable with the command line then just keep it simple and use the `mysqldump` command to dump the table to a .sql file, then use the `mysql` command on the other machine to import it into MySQL there. My MySQL backups use the general form...

```
mysqldump --opt --quote-names dbName > dbName.sql
```...although, as mentioned, you may have to add options like --user and --password as required.

In fact, the man page for mysqldump includes its own simple examples, including:

```
mysqldump is also very useful for populating databases by copying data from one MySQL server to another:

    shell> mysqldump --opt db_name | mysql --host=remote_host -C db_name
```Years ago I tried to use phpMyAdmin to create the backup file but it would fail for larger databases. It also created individual INSERT statements for each row of data, and that was much slower and more bulky than the --extended-insert method (implied by --opt). However, those issues may have been fixed in phpMyAdmin by now.

Using the -T option will normally produce two files: a .sql file with the DDL and a .txt file with the data. However, the example you cited also included the -t option which will (presumably) suppress the DDL and just dump the data, so you'd have to create the table yourself on the target server.

If you've never used `mysqldump` before why not just try it? If the production table is huge then you could create a little test table with a couple of rows of data and see what the various `mysqldump` options do.

---

### Post by jonobr on 2013-02-20
I was put into the position a few months ago of having to create a bug tracking system for the company.

I have two machines like you and I use one for the back (an old piece of c) and the other for the production system.

I have used mysqldump for backing up on one and restoring on the other.
I have also found it useful when people ask for changes on the system, to make changes on the backup, allow myself and others to test and roll put to production.

So, when It comes to mysql I am no expert but have found the copy from one to the other went fine and without a hitch.

Since installing bugzilla3, I installed mediawiki and mantis and all work fine with the backup and restore.
I found it copied everything I needed

---

### Post by darkod on 2013-02-20
> **jonobr said:**
> I was put into the position a few months ago of having to create a bug tracking system for the company.

I have two machines like you and I use one for the back (an old piece of c) and the other for the production system.

I have used mysqldump for backing up on one and restoring on the other.
I have also found it useful when people ask for changes on the system, to make changes on the backup, allow myself and others to test and roll put to production.

So, when It comes to mysql I am no expert but have found the copy from one to the other went fine and without a hitch.

Since installing bugzilla3, I installed mediawiki and mantis and all work fine with the backup and restore.
I found it copied everything I needed

Just to clarify, we are talking about the pair of commands from post #5 right?

Everything goes into place without the need to worry about any indexes, primary keys, etc?

---

### Post by jonobr on 2013-02-20
Yep


That worked for me with Bugzilla3, mediawiki and mantis.

Im no genius and I had two systems that had all the exact same info after the restore.

Can you not do a dummy run first importing to your second machine to make sure its good?

There should be no harm in exporting from production and importing to the second machine.
[Here]("http://www.thegeekstuff.com/2008/09/backup-and-restore-mysql-database-using-mysqldump/") is the nice quick tutorial I keep going back to


One big word of warning
Watch out for which machine your working on at any one time ,
and which way your '><' is facing.

If you get into the habit of leaving your backup in the same directory as your restore and have the >< in the wrong direction then you could end up restoring to an older point.

When you get into doing backups regularly , you need to ensure its backedup and moved off for storage elsewhere and most likely automate the whole thing so it does it itself.

Actually, I think I have gone off topic a bit here....

---

### Post by LHammonds on 2013-02-20
I have done this very same thing a couple of times.

I made an automated backup script which uses mysqldump and exports all the database in 3 different ways.  One creates a file containing everything which would be used in a full server restore.  It also creates individual database files in case you only want to restore one single database and the 3rd level backs up individual tables to file in case you need to restore a corrupted table.

The link in my sig will take you to how I configured my MySQL server as well as the backup script I have scheduled and there is even a section on the steps I used to migrate the database to a brand new server using my backup method.

If you are new to this, I recommend making a test run of the entire process without actually taking down the database.  Simply put the backup on the new server and restore the databases and verify that your user accounts, databases, tables and data (row counts) are there.  Then drop all the databases in preparation for restoring it again.  When ready, stop your applications from writing to the database, make a backup, transfer the backup to the new machine and do the restore.  Depending on your environment, you will either need to update the address of the new database server in your applications or shutdown the old server and configure the new server with the same IP (which is what I did).  Then start up your applications and make sure they connect.

LHammonds

---

### Post by JCC955i on 2013-02-21
Nothing to add here really except a +1 on the advice LHammonds and jonobr are giving. I've used the same sequence for backing up, moving and testing MySQL databases numerous times.

It's really very worthwhile to replicate in a test environment before you go ahead on your live systems.

---

### Post by darkod on 2013-02-21
Update: I used the mysqldump on the older server and then restored the file with the mysql command to a test VM (third machine for quick test). I'm impressed. It seems great.

It spooked me a little first when doing a quick query in MySQL Workbench until I realised it limited the output to only 1000 entries.

Everything seems to be there.

On another topic, when I tried exporting into CSV I got this:
> mysqldump: Got error: 1045: Access denied for user 'asteriskuser'@'localhost' (using password: YES) when executing 'SELECT INTO OUTFILE'

I was under the impression this user has GRANT ALL PRIVILEGES on this DB. What is missing?

---

### Post by GordThompson on 2013-02-21
Make sure that the 'mysql' user has permission to write to the folder where you want to save the output file(s). From the `mysqldump` man page:

> [The '-T'] option should be used only when mysqldump is run on the same machine as the mysqld server. You must have the FILE privilege, and the server must have permission to write files in the directory that you specify.

---

### Post by darkod on 2013-02-21
> **GordThompson said:**
> Make sure that the 'mysql' user has permission to write to the folder where you want to save the output file(s). From the `mysqldump` man page:

Thanks, I think you are spot on. I specified the /root as destination by the mysql user I am using is not root and can't write there.

I´ll give it another go later.

PS. If I don't use the -T option, what is the alternative? On the right side of the command to use something like > filename? So, it would be like:
```
mysqldump -u username -p -t database --fields-terminated-by=, > filename
```

In this case do I need the -t too?

---

### Post by SeijiSensei on 2013-02-21
The MySQL username is irrelevant to file permissions.  What matters is the user the mysqld daemon runs as which is "mysql" by default.  (Same issue as Apache running as the "www-data" user.)  Try writing to /tmp and see if that works.

Even if you log in as 'root'@'localhost' in MySQL, you won't be the root user from the perspective of the operating system.  You'll still be executing processes as the "mysql" user.

PostgreSQL works the same way.

The solution you give at the end is the best workaround.  Run the command as root and pipe the results to a file.  From my reading of the "-t" option, it suppresses CREATE TABLE statements which would seem to make sense in a CSV file.  

Don't you also need for text fields to be wrapped in quotation marks for CSV, or is ```
,this is a string,another string,37
``` acceptable CSV syntax?  What about fields with values that include commas?

If you want to migrate all the databases in a MySQL instance, you can use the "--all-databases" option to mysqldump when creating the backup file.  For PostgreSQL users like me, the equivalent commands are pg_dump for individual databases and pg_dumpall for all databases.

---

### Post by darkod on 2013-02-21
> **SeijiSensei said:**
> The MySQL username is irrelevant to file permissions.  What matters is the user the mysqld daemon runs as which is "mysql" by default.  (Same issue as Apache running as the "www-data" user.)  Try writing to /tmp and see if that works.

Even if you log in as 'root'@'localhost' in MySQL, you won't be the root user from the perspective of the operating system.  You'll still be executing processes as the "mysql" user.

PostgreSQL works the same way.

Yeah, slipped my mind we are only talking about the mysql user and not the linux user. I'll give it a go to a folder where everyone can write. Thanks.

---

### Post by darkod on 2013-02-21
The export into CSV didn't work, but I'm quite satisfied how the rest works.

If I wanted to start showing off ( :) ) and use conditions with the mysqldump, would something like this be correct:
```
mysqldump -u username -p database --where='calldate=>2007-01-01 AND calldate<=2007-12-31' > sqldump.sql
```

Or the column calldate can't be expressed like that, it needs to be the "full" expression like database.table.calldate?

I'm attaching my latest export to CSV try, I made a new folder and gave read/write permissions to all, so the error is definitely not because the mysql user can't write to the folder. It might be that the mysql user running the dump doesn't have as high permissions as I think.

---

### Post by darkod on 2013-02-21
OK, the mysqldump works with --where='calldate<=2007-12-31' for example, but i can't make it work with two dates to make a time period. I'm trying with:
--where='calldate=>2007-01-01 AND calldate<=2007-12-31'

and replacing the AND with &&. Both failed. I'm sure you can do a time period statement, I just don't know how yet. :)

---

### Post by SeijiSensei on 2013-02-21
If you have a Windows machine around with Office installed, you might consider installing the [ODBC Connector for MySQL]("http://dev.mysql.com/downloads/connector/odbc/") and using Excel or Access to extract data, especially if you want to create CSV files.  The MySQL server configuration will have to permit external connections, and you'll need a 'user'@'windows_box_ip' entry, too, I suspect, or a 'user'@'%' entry.

I find this method much easier when I want to import or export tables between and SQL server and spreadsheets.  I've used LibreOffice Base on occasion for this, but the Microsoft tools just have more features.

---

### Post by darkod on 2013-02-21
I spoke too fast. :)

That --where condition I specified doesn't work as intended. It only creates empty 4K file. I'll play around with it.

I already have root@windows_box user to use it with Workbench, and both Office and LibreOffice. I can give that a shot too.

But I'm using the ocassion to learn little bit about mysql commands too, so I'm not jumping into windows right away. Not that we mentioned it, I can probably do the csv export in Workbench.

Right now I have the test machine set with a user for Workbench (the root@windows_box mentioned above), but I can try granting privileges to the same user on the servers too.

---

### Post by GordThompson on 2013-02-21
> **darkod said:**
> OK, the mysqldump works with --where='calldate<=2007-12-31' for example, but i can't make it work with two dates to make a time period. I'm trying with:
--where='calldate=>2007-01-01 AND calldate<=2007-12-31'

and replacing the AND with &&. Both failed. I'm sure you can do a time period statement, I just don't know how yet. :)
Once again, referring to the man page for `mysqldump`, one of the examples they give is

```
--where="user='jimf'"
```Given that MySQL normally likes to see quotes around date literals, your option might work better if it was something like

```
--where="calldate=>'2007-01-01' AND calldate<='2007-12-31'"
```

---

### Post by darkod on 2013-02-21
Yeah, I tried that too but it failed. After a bit trial and error, this is what worked (note that on the old server the mysql is 4.1.22 so it might have something to do with options syntax):

For single date:
```
--where="calldate<='2007-12-31'"
```

to get all records before 2008.

For time period it actually worked with two separate options:
```
--where="calldate=>'2008-01-01'" --where="calldate<='2008-12-31'"
```

That gave me a 103MB file as opposed to empty 4KB file. :)

---

### Post by jonobr on 2013-02-21
I wish I could help more here, but as said originally
My knowledge is limited to mysql backup restore, query tables and items etc,.....You know , the stuff you show your boss that looks impressive but is really basic stuff


best of luck

---

### Post by darkod on 2013-02-21
You all helped a lot, don't worry.

As I said, after trial and error I found how to dump the data only for a specific period, using the --where option.

I will play more with export to csv, both on the command line and using something like Workbench/Office/LibreOffice.

I will close the thread since the main thing is answered. Thanks all. Further comments are welcomed still.

---

### Post by darkod on 2013-02-22
I have to add to my post #25. The --where condition in it is not correct, and I found out what was bothering the syntax using only one --where condition to specify time period. It was the = sign.

So, to use mysqldump for only a period, what worked at the end is:
```
--where="calldate=>'2008-01-01 00:00:00' AND calldate<='2008-12-31 23:59:59'"
```

Of course, the above is only the condition that worked for me, you still have to add the full mysqldump syntax.

---

