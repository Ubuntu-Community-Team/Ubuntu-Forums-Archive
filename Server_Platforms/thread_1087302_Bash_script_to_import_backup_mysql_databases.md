---
title: "Bash script to import backup mysql databases?"
date: 2009-03-04
forum: Server Platforms
---

### Post by nandemonai on 2009-03-04
Greetings,

I've done a little searching around but due to time constraints I've been unable to find a viable solution so I thought I might pose the question here.

Essentially I'm looking for a reliable way to import mysql database backups to a secondary server for redundancy, preferably via a bash script.

So far I've managed automating the backup of the databases (along with the /var/www/ directory) in sql form to the secondary server no problems but it's actually automating the import into mysqld on the secondary server that has me stumped.

Any suggestions or pointers would be greatly appreciated.

---

### Post by ad_267 on 2009-03-05
I'm not sure if this is exactly what you're after but to restore a backup I'd do:

mysql -u USERNAME -p DATABASENAME < backup.sql

---

### Post by lykwydchykyn on 2009-03-05
I'll add that when you dump out the tables, you want to use the --add-drop-table=TRUE switch to the command.  That way tables are dropped in the resulting script before being recreated and populated with data.

---

### Post by nandemonai on 2009-03-23
Thanks guys, that looks like it should work. Haven't had time to test it properly yet though.

Wasn't expecting it to be that easy. :)

---

### Post by BkkBonanza on 2009-03-23
Also have a look at mysql replication. For a backup server this works very well and is actually quite easy to set up. Using this the backup server can be only seconds behind the real server and if you need to switch over then the database is ready to use.

---

