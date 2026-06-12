---
title: "Migrating MySQL from Windows to Linux Server"
date: 2008-06-07
forum: Server Platforms
---

### Post by sakid on 2008-06-07
Hi everyone,

I will soon have the task of moving a mysql database from Windows to Linux.

How hard is this to do?  Can someone point me in the right direction?

I'm pretty new to MySQL.

Cheers

---

### Post by Titan8990 on 2008-06-08
Mysqldump is the standard command for backing up a DB on either Linux or Windows. Here is the Mysql reference page on mysqldump:

[http://dev.mysql.com/doc/refman/5.0/en/mysqldump.html](http://dev.mysql.com/doc/refman/5.0/en/mysqldump.html).


It is going to be as easy use mysqldump to backup and then you will use mysql to restore like this:

#mysql -u [USERNAME] -p [MYDATABASE] <./[MYDATABASEBACKUP]


Just did this recently myself, good luck.

---

### Post by hyper_ch on 2008-06-09
yes, mysqldump will be the preferred way. Although you might be able to copy the database binaries - but that often leads to problems.

---

