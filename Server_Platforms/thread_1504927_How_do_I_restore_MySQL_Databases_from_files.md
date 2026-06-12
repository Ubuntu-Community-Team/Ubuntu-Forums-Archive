---
title: "How do I restore MySQL Databases from files?"
date: 2010-06-08
forum: Server Platforms
---

### Post by alexlaban on 2010-06-08
How do I restore MySQL Databases from an old hdd with Ubuntu on it which won't boot? 

Information below is not necessary just explaining how I ended up in this situation.


This is the story 
> Today the harddrive crashed on one of my development servers and I have no recent backup of the MySQL databases on the server. 

The stuff on the server weren't horrible important but it would still be nice if I were able to recover some of the files. 

This is the thing, I don't think the harddrive is entirely dead because it comes to a screen saying harddrive error something enter to continue then it says GRUB in the upper left corner before the computer crashes/reboots. 

So I installed Ubuntu server on a new HDD and now I want to attempt to recover the databases from the old HDD by mounting it in Ubuntu but before trying I would like to know who one does that. As I've understood it's a bit more complicated then one might thing because MySQL uses binaries and not plain-files.

---

### Post by mspieth on 2010-06-08
Most of the time you can just copy the contents of /var/lib/mysql from the old drive to the new drive. Also make sure your permsissions are correct after you copy the files.

---

### Post by noway2 on 2010-06-09
+1 to mspieth's comment.  According to the MySQL Book I have, copying the files is the best and easiest way to back up the database.  Otherwise you can use the mysql dump command to get a text file output that will issue the commands to recreate the database.  You can then restore it by dropping the old database if necessary and load it with the source command.  You should also stop the MySQL daemon/server before backing up to ensure that no files are modified during the process to help maintain data consistency, even in Linux doesn't have a problem with it.

---

