---
title: "MySQL Server more than once"
date: 2009-12-04
forum: Server Platforms
---

### Post by gunja99 on 2009-12-04
Dear all,
   Have been hunting around for this on the net for the last hour or so, but can't seem to find it, which is strange. Basically I need to setup MySQL Master/Slave, but wanted to do this for a number of live servers to ONE backup server. Now I need to sync ALL the databases on each of the live servers, so I thought that I could run multiple MySQL servers on the backup/slave box basically.

   Is this the best way to do things, or is there a better way, and how do I go about installing MySQL more than once on a server? Or is a case of having multiple config files, and then starting MySQL multiple times pointing to different my.cnf files? If anyone has this experience, please let me know.

Regards,
 Martin

---

### Post by Lars Noodén on 2009-12-04
It's been years since I've tried anything like that, but I would say to try the first option:  sync the live servers to a single backup server.

Did you find the MySQL documentation on replication?
[http://dev.mysql.com/doc/refman/5.1/en/replication-howto.html](http://dev.mysql.com/doc/refman/5.1/en/replication-howto.html)

---

### Post by gunja99 on 2009-12-04
Thanks Lars, but I was hoping to backup ALL the databases on each of the live servers, including the mysql database which has the user information, so there will be multiple mysql databases, hence I wanted to to have separate mysql servers on the slave server one for each of the live mysql instances. This slave server can then be used as a mirror/backup.

I know how to setup master/slave replication, done it lot's, it's just the best way to run multiple MySQL servers on one Ubuntu/Debian installing.

Hope you understand my requirement, and why :)

Martin

---

### Post by Lars Noodén on 2009-12-04
Thanks.  I see now (I think)

If the regular way to run [multiple instance of mysqld](http://linux.die.net/man/1/mysqld_multi) keeps separate mysql databases for users, table, etc. then that might work.  

Multiple instances of chrooted mysqld, each on a different port, to receive the replications, would be a sure way to keep the data separate in separate parts of the filesystem.  Or they could be on the same port, but just not run at the same time.  Either way, it may not be best to have them try to sync all at the same time. 

When setting them up, once the first one is chrooted, the chroot jail can be duplicated in other directories.

Or a VM can be slapped together using qemu.  VMs are not efficient, but are easy to set up and copy snapshots of.

---

### Post by peridot on 2009-12-28
I am attempting something similar, using mysqld_multi and an active/passive master/master setup. Each server has one main mysql, and the other server's passive mysql. Each server has a virtual IP address associated with it, and will be switched over to the other server if the heartbeat monitor detects a failure. I've managed to get mysqld_multi running and a master/master setup with heartbeat, but working on putting the two together now. Do you think this is a feasible solution?

---

### Post by Vegan on 2009-12-29
I have looked into MySQL quite a bit as I was looking at using it as my database with PHP in my site generally.

There are a lot of things to help, rsync is a popular choice. Using a virtualized platform is another way to go.

---

### Post by BkkBonanza on 2009-12-29
I think multiple instances is likely the way to go, although periodic rsync would also work and be efficient. Multiple instances isn't as bad as you would think as most of the mysql program code would be shared libraries and only loaded once. Also for the slave instances you can optimize the cnf files to have very small memory use as they won't be used for active querying. 

There is also specialized block level replication file systems that can solve this. They were/are commonly used on Amazon EC2 for replicating a file mount on a block level to a backup store in realtime. You set it up to replicate the mysql data directory tree and any time blocks get changed there they get relayed to a backup remote filesystem. I don't recall the name of this but I'm sure a little google would find something. It has the advantage of being generic.

---

### Post by Lars Noodén on 2009-12-29
@ BkkBonaza : these are all valid methods without a live database.  With a live database, transactions need to be taken into account as do records that span multiple tables.  For example you could back up one table while it is waiting to be updated and then back up the next table after it has been updated.  Voila.  Part of a record.  

Some more thorough documentation and tutorials are needed.

---

### Post by BkkBonanza on 2009-12-29
Understood. You wouldn't be able to use the backup servers unless you stopped & sync'd the live servers. If the live server crashes mid transaction then the only valid backup would be with the replication method. I haven't checked but I'm fairly sure that replication takes transactions into account. I have only used replication for backup like this and the other ways just came to mind as alternatives I've read about.

I believe the block-filesystem method was designed to provide reliable backup on EC2 and S3 and was meant to work for mysql. I don't know how they would have solved that. Perhaps the block only get sync'd to disk upon transaction commits. Have not read about this for a while and so don't recall details.

---

