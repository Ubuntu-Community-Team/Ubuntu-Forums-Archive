---
title: "MySQL Database Recovery - bare metal"
date: 2011-03-02
forum: Server Platforms
---

### Post by raz230 on 2011-03-02
Hello,

I had a project pier web application running on an older machine.  It's a PHP Web app w/ a MySQL backend.  It wasn't really a production machine but I did amass an amount of articles on the project pier that I would hate to have to redo manually.

The hard drive is toast on this machine and I can't use it.  I've replaced the hard drive and reinstalled Ubuntu and all it's server apps.

I can access files on the old drive still and can pull out the MySQL database files.

Does anyone know how you do a files only recovery on MySQL?  I don't know the terminology for MySQL but in SQL Server there's an easy way to do this with some SQL commands if you have the database file and the log file - is there something similar for MySQL?

Joey Greybeard.

---

### Post by Vegan on 2011-03-02
10:1 you do not have a backup

learn how to use mysqldump

google for it

as for the manual recovery, may or not work depending on any damage

---

### Post by wongo888 on 2011-03-02
You may be able to restore your db by moving the right files off the old drive and onto the new drive. Read these sections

[http://dev.mysql.com/doc/refman/5.1/en/backup-methods.html](http://dev.mysql.com/doc/refman/5.1/en/backup-methods.html)

[http://dev.mysql.com/doc/refman/5.1/en/myisam-repair.html](http://dev.mysql.com/doc/refman/5.1/en/myisam-repair.html)

If your articles were indexed by Google, you might be able to pull them off the Google cache or off the Internet Wayback Machine.

[http://www.archive.org/](http://www.archive.org/)

---

### Post by SeijiSensei on 2011-08-24
I recovered a MySQL database simply by transferring /var/lib/mysql onto the new machine and starting mysqld.  The server process discovered that the database files were in an older MySQL format and updated them automatically!

In general, though, I recommend running mysqldump nightly to create backups.  These files consist of the commands and data required to rebuild the database and are highly portable.

---

### Post by #Reistlehr- on 2011-08-24
> **SeijiSensei said:**
> I recovered a MySQL database simply by transferring /var/lib/mysql onto the new machine and starting mysqld. 

Same here, but i had to make changes to the log files on the server as they did not match the DB's.

I set up replication between 2 of my devices and have been golden for 3 years :D

---

