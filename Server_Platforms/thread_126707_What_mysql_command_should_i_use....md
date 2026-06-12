---
title: "What mysql command should i use...?"
date: 2006-02-07
forum: Server Platforms
---

### Post by Packard Dell on 2006-02-07
Hi. How can i point **mysql** to save or put my created database to other directories (like in my home folder or my FAT32 partition) rather than to its default directory which is */var/lib/mysql*?

Anyone pls?...i'd really appreciate your help. thanks.

---

### Post by joselin on 2006-02-07
For create a database you can use:
> $ mysql -u <username> -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 20562 to server version: 4.1.14

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> create database test;
Query OK, 1 row affected (0.04 sec) 

For changing the files for your database you must edit the file /etc/my.cnf

---

### Post by tomski on 2006-02-07
you may find these helpful,
command reference:
[http://www.pantz.org/database/mysql/mysqlcommands.shtml](http://www.pantz.org/database/mysql/mysqlcommands.shtml)

official online manual:
[http://dev.mysql.com/doc/refman/5.0/en/index.html](http://dev.mysql.com/doc/refman/5.0/en/index.html)

---

### Post by Packard Dell on 2006-02-07
Thanks guys! But what i actually want to know is that; when i create database, it will be saved directly to my* /media/hdb6/mysql* directory.

---

### Post by LordHunter317 on 2006-02-07
Why do you want your databases save there?

If you dont want your databases on the disk that currently houses /var/lib/mysql, do one of two things:[list=1][*]Down the database server, copy the catalog to a different location, and then mount that location as /var/lib/mysql[*]Down the database server, copy the catalog to a different location, and the symlink that location to /var/lib/mysql[/list]I'm not sure it's even possible to change the data location for MyISAM.  It is possible for InnoDB, but logfiles and schema files still go in the catalog root folder.

Why do you care anyway?

---

### Post by souki on 2006-02-07
take a look at /etc/mysql/my.cnf
there is a [mysqld] section where you can change the datadir location

steps (not tested!):

1- stop mysqld
2- backup your datadir
3- restore the datadir to the new location
4- change /etc/mysql/my.cnf to specify the new datadir location
5- restart mysqld

---

### Post by Packard Dell on 2006-02-07
> Why do you want your databases save there?

Because, i have a triboot system (WinXP, Fedora, & Ubuntu) and i am writing a JDBC application so that when i switch between these OS and test my program, i can access the same database that i've been working on from the other OS (if it is possible) that's why i want all my database files to be saved on my FAT32 partition.

> If you dont want your databases on the disk that currently houses /var/lib/mysql, do one of two things:

   1. Down the database server, copy the catalog to a different location, and then mount that location as /var/lib/mysql
   2. Down the database server, copy the catalog to a different location, and the symlink that location to /var/lib/mysql

Wow! Sorry, but it only just recently that i've been playing around with mysql that's why i don't get what you mean by these yet! Please enlighten me.

I tried to change **datadir** in my */etc/mysql/my.cnf* from **datadir = /var/lib/mysql** to **datadir = /media/hdb6/mysql** but i am getting this error message  when i open mysql server:
> ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)
...i don't know why.

Cheers anyway.

---

### Post by Packard Dell on 2006-02-07
[QUOTE=souki]take a look at /etc/mysql/my.cnf
there is a [mysqld] section where you can change the datadir location

steps (not tested!):

1- stop mysqld
2- backup your datadir
3- restore the datadir to the new location
4- change /etc/mysql/my.cnf to specify the new datadir location
5- restart mysqld[/QUOTE]

As mentioned above, i have already tried changing **datadir** location, but not the stopping and restarting mysqld as what you have said. So i did all your steps, and now i can't even restart mysqld. There must be some additional tweaks aside from changing **datadir**

Thanks mate.

---

### Post by LordHunter317 on 2006-02-07
[QUOTE=Packard Dell]Because, i have a triboot system (WinXP, Fedora, & Ubuntu) and i am writing a JDBC application so that when i switch between these OS and test my program, i can access the same database that i've been working on from the other OS (if it is possible) that's why i want all my database files to be saved on my FAT32 partition.[/quote]You won't have any data integrity that way, and will likely loose the whole catalog if you crash.

I would run 3 seperate instances unless there's some pressing reason not to, like lack of diskspace or no trivial way to keep the changes you need to make in sync.

> I tried to change **datadir** in my */etc/mysql/my.cnf* from **datadir = /var/lib/mysql** to **datadir = /media/hdb6/mysql** but i am getting this error message  when i open mysql server:If you didn't move the existing catalog there first, then there's no database catalog for MySQL to work with with, so it won't start.

Don't move the catalog while the server is running either, down that path lies only madness and corruption.

>  There must be some additional tweaks aside from changing datadir
**Yes, you must move the files.**

---

### Post by wrtrdood on 2006-02-07
Go through /etc/mysql/my.cnf and have a look at every entry that begins with /var.  To completely move the data directories you'll have to duplicate the structure then change those entries in the my.cnf file.  Take mysql down first.  It might be as simple as a sudo cp -r of the mysql directories to the new location.  Keep in mind that the mysql.cnf changes will need to be reflected in the configuration for each OS.

I agree that it's not a good policy to keep important info on a FAT partition but I understand the issues.  Another potential option might be to create a single /var partition formatted ext2.  Then you could access it from all OSes.  Barring that, be sure to copy the updated database (by default found under /var/lib/mysql) back to the Linux side for safe keeping.  At least that way you'll not have to worry about losing schema changes and the like. I use *mysqldump* for that.

---

### Post by souki on 2006-02-07
my previous post about changing the **datadir** location is not suitable for sharing data between linux and windows, it's only to have the data stored on a different location

such a setup is, in my opinion, is very tricky (I don't know if it's possible, I would not try)

why don't you use a vmware instance and communicate to a single mysql server on one host ? dual booting, is not an easy way for desktop migration

---

### Post by Packard Dell on 2006-02-08
[QUOTE=LordHunter317]You won't have any data integrity that way, and will likely loose the whole catalog if you crash.

I would run 3 seperate instances unless there's some pressing reason not to, like lack of diskspace or no trivial way to keep the changes you need to make in sync.

If you didn't move the existing catalog there first, then there's no database catalog for MySQL to work with with, so it won't start.

Don't move the catalog while the server is running either, down that path lies only madness and corruption.

**Yes, you must move the files.**[/QUOTE]

Thanks LordHunter317, yes you are right i also need to copy the files from */var/lib/mysql* to its new directory. And i understand now what you meant from your first post. It is now working and managed to set what i really wanted to do, though i understand that this is a messy setup, but so far, my JDBC application and mysql are working smoothly fine (at the moment) and no problem at all running them when i swith OS. Well i don't know how's gonna be like though when i start working with PHP and Apache, let's see! That's gonna be another experiment.

You've been great guys! thanks for all your helps.

---

