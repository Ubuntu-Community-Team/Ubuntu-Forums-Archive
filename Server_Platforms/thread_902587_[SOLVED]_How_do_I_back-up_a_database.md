---
title: "[SOLVED] How do I back-up a database?"
date: 2008-08-27
forum: Server Platforms
---

### Post by Bliepo32 on 2008-08-27
Alright. I have a computer (a laptop actually), and I need to reformat it. However, I have some rather important information stored in mysql (installed from source), and want to make a back-up of it. How do I do this? And how do I restore the information contained within the back-up once I am done with reinstalling?

---

### Post by de0xyrib0se on 2008-08-27
Google mysqldump

---

### Post by Oldsoldier2003 on 2008-08-27
> **de0xyrib0se said:**
> Google mysqldump

Although I am sure you had good intentions, replies like "google it" and "read the (expletive goes here) manual" aren't really in the spirit of the Ubuntu Forums. 

Try to be helpful when posting or just pass on it.

Cheers,
OS

---

### Post by fjgaude on 2008-08-27
A person with ubuntu is open and available to others, affirming of others, does not feel threatened that others are able and good, for he or she has a proper self-assurance that comes from knowing that he or she belongs in a greater whole and is diminished when others are humiliated or diminished, when others are tortured or oppressed. -- Archbishop Desmond Tutu, 1999

---

### Post by fjgaude on 2008-08-27
Okay, how big is the database?

Normally to backup you either use an online storage place or to a local hard drive.

If your database is small you might consider copying it to a DVD or to an external USB hard drive.

Programs like Grsync and Unison are great to to the backups. Both on in the respository.

Let us know if you have any questions.

---

### Post by de0xyrib0se on 2008-08-27
The mysqldump client is a backup program. It can be used to dump a database or a collection of databases for backup or transfer to another SQL server (not necessarily a MySQL server). The dump typically contains SQL statements to create the table, populate it, or both. However, mysqldump can also be used to generate files in CSV, other delimited text, or XML format.

If you are doing a backup on the server and your tables all are MyISAM tables, consider using the mysqlhotcopy instead because it can accomplish faster backups and faster restores. See Section 4.6.8, “mysqlhotcopy — A Database Backup Program”.

There are three general ways to invoke mysqldump:

shell> mysqldump [options] db_name [tables]
shell> mysqldump [options] --databases db_name1 [db_name2 db_name3...]
shell> mysqldump [options] --all-databases

If you do not name any tables following db_name or if you use the --databases or --all-databases option, entire databases are dumped.

mysqldump does not dump the INFORMATION_SCHEMA database. If you name that database explicitly on the command line, mysqldump silently ignores it.

---

### Post by Bliepo32 on 2008-08-27
Alright, thanks for your replies. The database is small, so making a back-up shouldn't be a problem. If I have any questions, I will google for it, and if I can't find the answer there, I will ask about it here.

---

### Post by jonabyte on 2008-08-27
Here is a script for a mysql server that is on a Centos box, might work for you as well.

```

/etc/init.d/mysqld stop
cp /var/lib/mysql /tmp/backup
cd /tmp
tar -cvf backup.tar backup
gzip backup.tar
/etc/init.d/mysqld start

```

basically it stops the mysql server, copies the entire directory to a temp directory and zips it.

I have tested this on my existing setup and can confirm it works.

Maybe someone can comment on this, whether it would work for all or not...

---

### Post by Bliepo32 on 2008-08-27
Allright, I made a mysqldump by doing the following:

```
sudo /usr/local/mysql/bin/mysqldump --password=[blablabla] --all-databases --result-file=[my_home_dir]/Desktop/mysqldump
```

My question is, will this make an exact copy of my databses? And how do I 'load' the dump file once I reinstalled mysql?

---

### Post by de0xyrib0se on 2008-08-27
[http://dev.mysql.com/doc/refman/5.1/en/mysqlimport.html](http://dev.mysql.com/doc/refman/5.1/en/mysqlimport.html)

---

### Post by Bliepo32 on 2008-08-27
> **de0xyrib0se said:**
> [http://dev.mysql.com/doc/refman/5.1/en/mysqlimport.html](http://dev.mysql.com/doc/refman/5.1/en/mysqlimport.html)

Thank you for your reply, it was really helpful. But one question remains: did I make an exact copy?

---

### Post by de0xyrib0se on 2008-08-27
Yes you did, you can open the dump file you generated and you will see your data in there.

By the way Ubuntu has the MySQL GUI tools in its repositories, one you should play with is MySQL Administrator, can do backups and restores via a nice GUI.

---

### Post by Bliepo32 on 2008-08-27
Thank you. QATC.

---

