---
title: "What is good simple way to backup a lamp server's data"
date: 2007-03-24
forum: Server Platforms
---

### Post by shoki on 2007-03-24
Hello All,

I have just installed an ubuntu 6.06.1 LAMP server on a spare PC. It is running great and I am really excited about everybody using it. Now that it is all installed and running I need to figure out how to back it up and exactly what I need to back up so I can recover if I lose a hard drive.

My original idea is to run tar from chron and just back things up to another server (that get's a tape archive nightly). Although I have been reading about rsync, rsnapshot, and cpio. I guess how it gets backed up is one problem. The other is what must I backup so I can recover in the event of a major failure.

 I am running MediaWiki, and Simple Machines Forums on top of MySQL and PHP5
 It looks like if I backup 
/var/www/ I will get all the web stuff.
/var/lib/mysql will save all my databases.
Then if the system goes south I can reinstall and rebuild the databases.

Does this sound correct or am I missing the point.

Thanks for your time and assistance,
--Shoki

PS I have installed this system with basically zero budget on a spare PC. I wanted to show the management how valuable a system like this could be. I am hoping once everything is up and running it will lead us to deploy more ubuntu systems and servers

Thanks again!

---

### Post by stokedfish on 2007-03-24
Rsnapshot is all you need.

---

### Post by koshari on 2007-03-24
you can use phpmyadmin to back the databases up to files.

---

### Post by shoki on 2007-03-25
I'll look into those. Thanks for the help!

Does anybody know if backing up those 2 directories will be enough to rebuild?

I don't mind reinstalling all the other stuff i just want to be sure the data is safe.

Thank you,
--Shoki

---

### Post by shoki on 2007-03-25
> **koshari said:**
> you can use phpmyadmin to back the databases up to files.

I am using webmin will this do the same thing or do I need both?

Thanks again and sorry for the noob questions.

---

### Post by elst on 2007-03-25
It's worth reading up on MySQL database backups, so that you are clear how it works. Ideally you should "dump" the databases to files with either mysqldump, or the specialized database backup routine in Webmin or PHPMyAdmin (which probably just runs mysqldump for you). Then backup up the resulting files with tar, or whatever file backup you use. This guarantees that you get consistent and restorable backups of the data in MySQL.

---

### Post by shoki on 2007-04-11
I am still researching this but the system is starting to fill up with useful information so I am starting to get a little nervous. 

I tried using 
[FONT=courier new, courier, mono]mysql -u [username] -p [password] [database_to_restore] < [backupfile]
to restore my databases but the wiki and forum didn't seem to pop back to life :)
[/FONT]
Question:
If I back up the entire /var directory and then restore it over a fresh install would the system function? As in would all the database structures be intact? My thinking is that rather than dumping the databases and rebuilding them if I just back up and restore the the whole thing everything should stay connected.

[FONT=courier new, courier, mono]
[/FONT] Thank you,
--Shoki

---

### Post by SjRaptor on 2007-04-11
tar and mysqldump should do the trick:

[FONT="Courier New"]tar cfvj filename.tar.bz2 <directory to backup>

mysqldump --add-drop-table -h localhost -u user -p db_name | bzip2 -c > db_name.bak.sql.bz2[/FONT]

Please reference the man pages before running these two commands. They should not affect your running data, but be sure you have the ability to backup and **recover** is most important.

edit: woops, didn't see you already tried to restore.

---

### Post by nihilocrat on 2007-04-11
I usually just keep anything that I would want to back up in a /var subdirectory, and backup that, as well as the /etc directory. This means I also backup logs as well as configuration data. Your solution sounds just fine, too. If you need quick turnover from a hard disk failure and have huge amounts of space, you can also opt to just backup the whole system. However, I don't think you'll need that for a server on a "spare PC" ;)

To recover, you would need to do a clean install, reinstall the LAMP components (apache2, MySQL, PHP, and all the modules you used), unzip your backups, and restart all the daemons with the scripts in /etc/init.d

There are several packages like bacula and backupninja that I haven't looked into which will help you handle backups.

---

### Post by elst on 2007-04-11
> **shoki said:**
> 
If I back up the entire /var directory and then restore it over a fresh install would the system function? As in would all the database structures be intact? My thinking is that rather than dumping the databases and rebuilding them if I just back up and restore the the whole thing everything should stay connected.

To be honest, that's really a doubly bad plan.

/var contains lots of different things that change a lot, and are specific to a particular system at a particular point in time - overwriting the whole lot with a restore could be messy, and is definitely unnecessary, as databases and Web servers only use specific directories.

If you read up on databases you will find that the database service can potentially be writing to the storage files at any time. You *must* use the supplied backup tool to generate consistent and current offline copies if the service is running - simply grabbing the files whilst MySQL is active may give inconsistent databases. You could shutdown MySQL and restore copies of the files in /var/lib/mysql/, then run myisamchk, but this is very much not guaranteed to work.

WRT your restore, you probably need to look inside your MySQL to see what's now there. The MySQL dump files are actually just large SQL scripts, so it's fairly easy to check what they do (or don't) do just by opening them in a text editor and having a look.

---

