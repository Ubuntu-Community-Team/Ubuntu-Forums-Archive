---
title: "MySQL DB Stored... where?"
date: 2009-11-09
forum: Server Platforms
---

### Post by zzzBrett on 2009-11-09
Where in the filesystem are mysql databases stored?

---

### Post by Ocelaris on 2009-11-09
> **zzzBrett said:**
> Where in the filesystem are mysql databases stored?

/var/lib/ something by default... sorry couldn't be closer, not on my box...

---

### Post by ratcheer on 2009-11-09
You can use "show variables;" and look for datadir. On my system, that is giving /var/lib/mysql, which if correct, is not a very good place. I am new at this, too.

Tim

---

### Post by zzzBrett on 2009-11-09
Thanks for the replies.

I have a back up of the /var directory, so I assume I have the files where the databases are stored.  How would I get these files into .sql files or into my database (that was deleted)?

---

### Post by Lars Noodén on 2009-11-10
On ubuntu the mysql database usually keeps everything in /var/lib/mysql/
There will be material for the mysql server there and there will be a subdirectory for each mysql database.  

So if you have databases 'foo' and 'bar' in addition to the pre-exisiting administrative database (the one holding it all together) called 'mysql' you will see three subdirectories:

[INDENT][FONT="Courier New"]/var/lib/mysql/mysql/
/var/lib/mysql/foo/
/var/lib/mysql/bar/[/FONT][/INDENT]

You will also find configuration data in this directory:

[INDENT][FONT="Courier New"]/etc/mysql/[/FONT][/INDENT]

If you want to let the system manage the programs and only worry about the database (columns, tables, users, data, variables, etc) then you can use **mysqldump**.  Using the database's own backup facilities is the correct way to go if you are concerned about the data and maintaining database integrity.  Otherwise, just copying the files from the disk you can get partially complete transactions, etc.  

For more detail information about backup and recovery:
[http://dev.mysql.com/doc/refman/5.1/en/backup-and-recovery.html](http://dev.mysql.com/doc/refman/5.1/en/backup-and-recovery.html)

---

### Post by zzzBrett on 2009-11-10
Perfect thanks.

---

### Post by ratcheer on 2009-11-10
The reason I don't like subdirectories of /var is because it is part of the root partition, which is usually small. I would prefer it to be in the larger partitions (/home or /usr) or, even better, in a filesystem on its own partition for databases. Assuming that some databases will become quite large.

Tim

---

### Post by zzzBrett on 2009-11-10
> **Lars Noodén said:**
> On ubuntu the mysql database usually keeps everything in /var/lib/mysql/
There will be material for the mysql server there and there will be a subdirectory for each mysql database.  

So if you have databases 'foo' and 'bar' in addition to the pre-exisiting administrative database (the one holding it all together) called 'mysql' you will see three subdirectories:

[INDENT][FONT="Courier New"]/var/lib/mysql/mysql/
/var/lib/mysql/foo/
/var/lib/mysql/bar/[/FONT][/INDENT]

You will also find configuration data in this directory:

[INDENT][FONT="Courier New"]/etc/mysql/[/FONT][/INDENT]

If you want to let the system manage the programs and only worry about the database (columns, tables, users, data, variables, etc) then you can use **mysqldump**.  Using the database's own backup facilities is the correct way to go if you are concerned about the data and maintaining database integrity.  Otherwise, just copying the files from the disk you can get partially complete transactions, etc.  

For more detail information about backup and recovery:
[http://dev.mysql.com/doc/refman/5.1/en/backup-and-recovery.html](http://dev.mysql.com/doc/refman/5.1/en/backup-and-recovery.html)


It seems that the mysqldump command dumps that database from an sql server as a backup, but the sql server must be working.  For me, all I have is the /var/lib/mysql/*dbname* files such as *.frm, *.MYD, *.MYI files.  How can I get these into sql statements or into a database. (Copying the backup from /var/lib/mysql/ to the new directory did not work).

Thanks

---

### Post by zzzBrett on 2009-11-10
Figured it out.. used myisamchk to fix the databases and corrected permissions so the server could read the files. All works now.

Just one more question: what permissions should the /var/lib/mysql/dbname files have?

EDIT: should have permissions 770 with owner:group as mysql:mysql

---

