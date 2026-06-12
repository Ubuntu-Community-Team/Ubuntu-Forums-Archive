---
title: "sync mysql databases"
date: 2011-03-08
forum: Server Platforms
---

### Post by dgoosens on 2011-03-08
hi Ubunteros,

I have a laptop and a desktop PC, both running Ubuntu 10.04 and both are configured the same way.

I am using Unison-gtk to sync the data between both computers... This works for everything... except for my mysql databases.

So I am wondering if you know about some way to simply sync my mysql databases on both computers.
Right now I need to do this table-per-table... and it is quite long to proceed like this...
What I need is a script or a program (open and preferably free) that would just compare both databases (all the tables) and sync them either by updating existing tables or by creating them. This should work both ways... obviously.

I could write a script for this, but I am sure there already is something for this out there.

Thanks for your suggestions;
dGo

---

### Post by wongo888 on 2011-03-08
Why wouldn't you just have one machine run the db and the other machine modify that data remotely?

---

### Post by dgoosens on 2011-03-08
hi,

thanks for you reply.

The solution you suggest is not doable...
I only use the laptop when I have no access to the desktop PC (visiting a customer or working on location).
I need to have that data with me at all times.

Putting the DB online is not an option either...
I am often traveling by train and I don't have Internet access there.

Hence, the only solution is synchronizing the data...

---

### Post by tyleruk on 2011-03-08
Maybe you could do this with replication, I would recommend reading through the replication section on the MySQL Website:

[http://dev.mysql.com/doc/refman/5.0/en/replication-howto.html]("http://dev.mysql.com/doc/refman/5.0/en/replication-howto.html")

Another, more clumsy, way of doing this is to take a backup every time you finish using one computer and restore it onto another one:

backup:
mysqldump -u [USER] -p [Database Name] > ~/backup.sql

restore:
mysql -u [USER] -p [Database Name] < ~/backup.sql

---

### Post by aeiah on 2011-03-08
so will you be making changes to the db on the laptop, and wanting this to then resync with the server's db? and the server db will likely have changed in the mean time too? eep

---

### Post by dgoosens on 2011-03-08
Hi,

Thanks a lot.

I don't think Replication is the solution...
There isn't a real master and slave, we have to consider these as clones.

The dump is the script I was thinking of... it is rather easy to write a script that would do this when called. But this would mean that I would always overwrite one version with another...
I would really need the program or script to compare the tables prior to updating one or the other and keep the most recent version.

Normally, when I am working on the laptop, no changes will happen on the server and vice versa... But this is likely to change.

I find it hard to imagine that I would be the only one facing this problem... and I have not found any tool or script that would do a sync.

But thanks a lot for your ideas !!

Any other suggestions ?

---

### Post by tyleruk on 2011-03-08
There is a piece of software that might suit your needs called [Pervasync]("http://www.pervasync.com/") it "enables mobile users to work offline and have their offline data automatically synced with a central server when a network connection becomes available."

However it is quite pricy ($1999 per server & $51 per user), personally I would stick with the backup's.

---

### Post by wongo888 on 2011-03-08
Try googling multi-master replication or dual master replication. That sort of set-up is probably overkill for what you want to accomplish though. 

There is probably a java app somewhere that someone is selling that would sync small dbs like this, but I don't know of any off-hand.

---

### Post by supremedalek on 2011-03-08
Can you find some host provider that offers mysql and then have both your machines sync with it? Analogy here is what google provides for address books, calendars, and other crap. Making the database encrypted should not be that hard to do.

---

### Post by bsntech on 2011-03-08
The only good solution to this issue - in my opinion - is the master-master replication model with MySQL.  This is what I must use for my hosting systems since I do mirrored web hosting for customers.  Both servers are setup as masters and replicate with each other.

If one system goes offline for a period of time (for a full system back or whatever the case), then upon rebooting back into the OS, it picks back up where it left off at.

Master-Master replication does allow you to choose specific databases instead of all of them if required.

Brian S.
BsnTech Networks
[http://www.bsntech.com]("http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/1802-how-to-disable-taskbar-grouping-in-windows.html")

---

### Post by supremedalek on 2011-03-08
bsntech, do I take only one is being written to or both are? If the latter, how do you handle split-brain?

---

