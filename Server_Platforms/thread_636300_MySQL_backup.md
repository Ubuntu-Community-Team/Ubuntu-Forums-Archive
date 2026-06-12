---
title: "MySQL backup"
date: 2007-12-09
forum: Server Platforms
---

### Post by Zarathu on 2007-12-09
I manually upgraded glibc, but something went wrong and now the system is screwed and wouldn't even let me boot up.

I'm using an Ubuntu LiveCD right now and I need to know which MySQL files to back up so that I don't lose all of my data.  Is there any way to go about this? I can't start the MySQLd.

---

### Post by koenn on 2007-12-09
I'd say you want /etc/mysql/my.cnf as reference to reconfigure your new installation, 
and the contents of /var/lib/mysql or whatever my.conf indicates as 'datadir", cause that's where your databases are. 

In any case, look for backup and restore procedures in the mysql manual, database recovery isn't always as easy as simply copying files. 
[http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)

---

### Post by twistedtwig on 2007-12-10
you could "dump" the whole lot, all its DB and tables into a text file from the command line mysqldump is the command, (can't remember all the params).  Then you can load this into any other mysql db later

---

### Post by koenn on 2007-12-10
> **twistedtwig said:**
> you could "dump" the whole lot, all its DB and tables into a text file from the command line mysqldump is the command, (can't remember all the params).  Then you can load this into any other mysql db later

That's a good way to *plan for* recovery if you're database is still up and running, but I don't see how it can be done from a system that doesn't even boot anymore. Unless you know of a way to do this from a live cd ? 

unless we forget about the db problem and focus an getting the system to boot again - preferably with mysqld starting up as well

---

