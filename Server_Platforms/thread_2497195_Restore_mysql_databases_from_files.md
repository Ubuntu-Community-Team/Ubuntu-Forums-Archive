---
title: "Restore mysql databases from files"
date: 2024-04-26
forum: Server Platforms
---

### Post by dam034 on 2024-04-26
Hi everyone,

a few days ago I lost my server. The motherboard no longer worked, but the hdd worked normally. The old server was ubuntu 16.04.

So I installed ubuntu 22.04 server on a new computer, and I want to restore mysql databases from /etc/mysql folder.

Is there a way?

Thanks

---

### Post by TheFu on 2024-04-26
/etc/mysql  is just for MySQL settings.  The actual DBMS files are under /var/llib/mysql (usually).  BTW, there have been huge mySQL changes over the years, so you'll need to look up the migration steps to get from the version you had to the version you will be running.  That's what release notes are all about.  READ THEM!

With the release of 24.04 yesterday, people will begin practicing the production server migrations from 22.04 to 24.04 ... practicing ... since they don't want any data corruption or data loss, but going back to 16.04 is so long ago that most of us have forgotten any issues.  Heck, we stopped using MySQL and switched to MariaDB sometime between 2026 and 2018, so there are other migrations you may want to consider.

Today, the default DBMS is MariaDB and MySQL is deprecated for a number of years on Ubuntu.

Sometimes the best method is to perform a **mysqldump** to get text files for the entire DB, then restore them into a new system with a new DBMS engine.

---

### Post by dam034 on 2024-04-29
I also have the folder /var/llb/mysql.

All the tables have three files: frm, myd and myi.

Is there a way to restore the tables?

Thanks

---

### Post by TheFu on 2024-04-29
A way?  Yes. 

Install 16.04 somewhere, place the DB on that system in the expected location, open the DB using normal DBMS commands, then use mysqldump to create a backup for everything in the DB. All tables, views, triggers, constraints, external functions, everything.  Take that dump to the new system and use the opposite of mysqldump to recreate the DB under the new OS.

It might be easiest to create a virtual machine with 16.04 on the new hardware.  It doesn't need to be a huge VM, just large enough to run the DB for 1 user and do the mysqldump.   

[https://linuxize.com/post/how-to-back-up-and-restore-mysql-databases-with-mysqldump/](https://linuxize.com/post/how-to-back-up-and-restore-mysql-databases-with-mysqldump/) shows how to backup and restore.
MySQL 5.x --> 8.x migration: [https://dba.stackexchange.com/questions/282215/migrate-mysql-5-7-to-8-0-via-mysqldump](https://dba.stackexchange.com/questions/282215/migrate-mysql-5-7-to-8-0-via-mysqldump)
Google will find lots of examples, if you need others.

---

### Post by dam034 on 2024-05-04
So I created a VM with ubuntu 16.04, installed via tasksel the lamp server.

Now, I only have to copy the files in the folder? Or is there some other to do?

Thanks

---

### Post by dam034 on 2024-05-09
Now I have some issues.

I copied the folders, each with a database name, in **/var/lib/mysql**, and used the console and phpmyadmin.

When I select a specific database, it seems to be corrupt.

Here the console:

```
root@old-ub16:# mysql -h localhost -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 6
Server version: 5.7.33-0ubuntu0.16.04.1 (Ubuntu)

Copyright (c) 2000, 2021, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| as***              |
| cretiww2           |
| dati               |
| g***               |
| g***               |
| l*********         |
| mediatomb          |
| mtasa              |
| mysql              |
| performance_schema |
| sc*********        |
| scambiointe        |
| soldi              |
| sys                |
| tut******          |
+--------------------+
16 rows in set (0.00 sec)

mysql> use soldi;
Database changed
mysql> show tables;
+-----------------+
| Tables_in_soldi |
+-----------------+
| avvisi          |
| cassa           |
| movimenti       |
| utenti          |
+-----------------+
4 rows in set (0.00 sec)

mysql> select * from avvisi;
ERROR 1146 (42S02): Table 'soldi.avvisi' doesn't exist
mysql> select * from cassa;
ERROR 1146 (42S02): Table 'soldi.cassa' doesn't exist

```
As you can see, I can see the tables, but they don't exist.

Also when I use phpmyadmin, I try to visit the database "soldi", in the side menu I can see the tables, but in the body it tells me that there are no tables:
[ATTACH=CONFIG]293745[/ATTACH]
Instead if I visit the database "cretiww2", I can see only one table, although there is a nice list in the side menu:
[ATTACH=CONFIG]293744[/ATTACH]
Lastly, the database "scambiointe" works correctly.

Now I can't understand why there are some tables which work, and some which don't work.

I want to point out that I have available the entire /var/lib/mysql folder of the old server.

How can I fix?

Thanks

---

### Post by TheFu on 2024-05-09
[https://linuxize.com/post/how-to-back-up-and-restore-mysql-databases-with-mysqldump/](https://linuxize.com/post/how-to-back-up-and-restore-mysql-databases-with-mysqldump/) is all I know.  Did you also restore the config files from the old system?   When we backup, we need to ensure that our restore process actually works.  Sometimes it is as easy as coping files, but often, there are specific config requirements, access tool requirements, and definitely user, group, permission requirements which all need to be handled properly.

I've never used phpmyadmin after seeing all the hacking attempts for it in my web servers.  Some tools are worse than the original problem.  I avoid any php-based admin tools and generally avoid any web-based admin tools that aren't built-into the software they are supposed to admin.  That's how I roll.

> How can I fix?
IDK.  Some tables work and others don't seems really vague.  You do know that DBMS systems have different types of file organization, so you need to ensure that the type used in the original version is also setup for the new location.  That's a shot in the dark.  Did you look at the log files?

Remember, I wrote this:
> 16.04 is so long ago that most of us have forgotten any issues. 
I have trouble remembering problems from last week, much less 2018.

---

### Post by dam034 on 2024-05-17
So I also copied these files:

[B]ibdata1
ibtmp1[/B]

And now it works.

Thanks for the help :popcorn:

---

### Post by thomcraver on 2024-11-29
Sorry for bumping an older thread.

What if I don't have my ib* files?

I accidentally got over-zealous doing a chmod and it included ../* effing up all my system files (litterally everything). Yeah, I know... 

After fixing perms I still couldn't get stuff to reconnect properly. I tried a apt/reinstall and that seemed to screw everything up more.

What I have:
 - My old /var/lib/mysql/database folders
 -- Some are innodb, some myisam
 - A few fresh mysql installation

Am I screwed? Anyway to do this?

I have several WP sites dead in the water at the moment.

---

