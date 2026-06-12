---
title: "Backup and restore MySQL innoDB databases"
date: 2012-08-19
forum: Server Platforms
---

### Post by Tac2 on 2012-08-19
Hi everyone.

I recently setup a Ubuntu 12.04 LAMP Server at home that I use to develop websites in corporation with clients. I've been using Ubuntu and other Linux distros for a few years, but I am new to servers and have been learning a lot. Especially about MySQL as I know nothing about it.

I am currently in the process of refining/rethinking my backup procedure, and I am having a problem figuring out how to backup the MySQL database, and I hope you can help me.

Both the MySQL data directory (/var/lib/mysql) and Apache root directory (/var/apache2) reside on /var, which is a LVM Logical Volume. What I want to do is take a snapshot of /var, mount this snapshot in another directory and use rsnapshot to backup /var/lib/mysql and /var/apache2 (as well as /var/log, etc). The snapshot should insure that the MySQL data directory and Apache root directory are in sync.

However, the backup of /var/lib/mysql is not going to do me any good unless the database has written everything to disk. I use the default Ubuntu implementation of MySQL which means it uses InnoDB as storage engine. In some places*, people say that it is safe to simply copy the /var/lib/mysql directory (just need to flush tables with read lock) as InnoDB always keeps the files in a consistent state. In other places**, people say that it is only safe to copy the files if mysqld is completely stopped. 

* [http://forums.mysql.com/read.php?22,184681,184700#msg-184700](http://forums.mysql.com/read.php?22,184681,184700#msg-184700)

** [http://www.pythian.com/news/22185/mysql-backup-concepts-for-linux-system-administrators-part-1/](http://www.pythian.com/news/22185/mysql-backup-concepts-for-linux-system-administrators-part-1/)

Currently I am following the last advice (just to be sure). I flush the tables, stop mysqld, take the LVM snapshot and start mysqld again (using the command: mysqladmin -uroot -ppassword flush-tables && service mysql stop && lvcreate -L 1G -s -n $SNAP_NAME $SNAP_SOURCE && service mysql start ; ). I then mount the snapshot in a different directory, take a backup of /var/lib/mysql, /var/apache2 and others using rsnapshot, after which I unmount and remove the LVM snapshot. This works fine for taking snapshots at 5 AM when no one is working on their sites.

However, I would really like to be able to take these snapshots every 1 or 2 hours during working hours, but that means I can't stop mysqld. 

So my first question is: Will the following procedure create a consistent backup without interrupting service?

# mysql -uroot -ppassword << EOF
> FLUSH TABLES WITH READ LOCK;
> \! lvcreate -L 1G -s -n $SNAP_NAME $SNAP_SOURCE ;
> UNLOCK TABLES;	
EOF
mount LVM snapshot
backup files from LVM snapshot using rsnapshot
unmount and remove LVM snapshot

If yes, my next line of questions then become: Once I have a backup of the files, how do I restore it?

I'm thinking the best idea is to spawn a second mysqld instance which loads its data from the backup, and perform a mysqldump from this second mysqld, selecting the specific databases/tables I want to restore. Would that work? Is it possible?

And lastly - in case the entire MySQL database blows up, can I simply stop mysqld, copy over the contents of /var/lib/mysql from my backup, and start mysqld again? 

Any tips will be appreciated! Thank you.

---

### Post by LHammonds on 2012-08-19
I'm fairly new to Linux so my bag 'o tricks if fairly limited and I do not run very complex setups.  However, I create backups of my database using mysqldump and has worked well for me.

My database server exports all the databases in one big transaction and another backup where each database and each table is exported and backed up in case I need to do a more granular restore.

For my web sites which are on different servers that make use of a database on my dedicated server, I have setup another backup process where I create a backup of the web site and trigger a backup of that web sites database to be done at the same time.

To see how I do it, take a look at my sig.  See the MySQL server and MediaWiki server docs.

LHammonds

---

### Post by Tac2 on 2012-08-19
Thanks for the links. Lots of text! Awesome resource! I will have a look at it ;)

---

### Post by sandyd on 2012-08-20
> **Tac2 said:**
> Thanks for the links. Lots of text! Awesome resource! I will have a look at it ;)
Tac2, have you looked at mysql replication?

You can export the stuff on the slaves without locking.

Also, Percona XtraBackup can do direct exports in innoDB databases without locking. [http://www.percona.com/software/percona-xtrabackup/](http://www.percona.com/software/percona-xtrabackup/)

I use mysql (mariadb actually, but interchangable) replication + XtraBackup though

---

### Post by Tac2 on 2012-08-20
MySQL replication is an option I haven't really considered. The thing is, I really want the MySQL database and the Apache directory to be in sync, and therefore I want to take the backup from a filesystem snapshot. Maybe I'm just being paranoid.

I didn't really consider XtraBackup just because it would be yet another tool to learn and depend on, but maybe I should.

Thanks for the suggestion.

---

### Post by sandyd on 2012-08-20
> **Tac2 said:**
> MySQL replication is an option I haven't really considered. The thing is, I really want the MySQL database and the Apache directory to be in sync, and therefore I want to take the backup from a filesystem snapshot. Maybe I'm just being paranoid.

I didn't really consider XtraBackup just because it would be yet another tool to learn and depend on, but maybe I should.

Thanks for the suggestion.
They will be in sync. 
You can do something like this.

1. LOCK the slave database tables
2. Export both apache + mysql
3. UNLOCK the slave database tables
4. The master and slave will both sync.
The queued mysql commands will run after the unlock. ;)

---

### Post by Tac2 on 2012-08-21
Indeed. That is what I am going to do.

Thank you for your help!

---

