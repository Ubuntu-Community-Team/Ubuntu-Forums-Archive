---
title: "Recovering a Mysql Database after Crash"
date: 2008-05-28
forum: Server Platforms
---

### Post by cmfarley19 on 2008-05-28
Hi All,
Our development group set up a Linux box about ten years ago to first serve as a print server and snad box for us to play with linux. Over time we have relied more on this system and use it as a web server, samba server, PDF generator and a bug tracker.
Well after a power outage the machine will no longer boot. We've tried everything we can think of and have decided it was time for a new machine anyway. I have switched to Ubuntu and have restored all functionality with the exception of our bug tracking db. It is a LAMP based system called MANTIS. I have the source files for Mantis. What I do not have is the Mysql database that it was tied to. I can access the hardrive that the database resided on via an Ubuntu live cd. Is there anyway to get to that data, back it up, and restore it on the new system?

Any info you provide will be much appreciated.

Thanks,

Chris

---

### Post by heebus on 2008-05-28
mysqldump will dump the database to a file.  You'll have to start mysql and have it read the data files located on this hard drive.

mysqldump -u username -p --all-databases >> file.sql

This actually dumps the whole database, which might be best in your situation.  

Then on the new machine you can load it.

mysql -u username -p < file.sql

---

### Post by hyper_ch on 2008-05-29
The above way is the proper way to do things.

However you can also try a copy of the db-binary files. However this is often prone to error.

(1) on both server stop mysql
```

sudo /etc/init.d/mysql stop

```

(2) copy the binaries
By default mysql databases are located in /var/lib/mysql --> each folder is the database name

(3) restart mysql
```

sudo /etc/init.d/mysql restart

```

(4) if you just copied the tracking-db (folder) you will need to re-add the mysql user that has privilege to use the db. Copying the whole "mysql" db containing all users and authorizations it not recommended... it may lead to problems.

-----------

But as said, the recommended option is creating a mysql dump as written above (maybe not with the --all-databases option but just the tracking db one)

---

### Post by cmfarley19 on 2008-06-26
When I posted this message, I didn't "subscribe" to it so I did not receive notifications of your replies.  Thanks for helping out.  You advice is pretty much the process I used.  It worked fine.

---

