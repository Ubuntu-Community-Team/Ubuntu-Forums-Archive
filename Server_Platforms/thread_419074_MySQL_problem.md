---
title: "MySQL problem"
date: 2007-04-22
forum: Server Platforms
---

### Post by strixy on 2007-04-22
I backed up my databases and server files before I did a clean install of Ubuntu 7.04. (from 6.10, previously 6.06, 5.10. and 5.04)

I installed all the LAMP packages as usual.

Unfortunately, after I replace the files, db's and users, the web pages don't seem to be accessing the data in the databases.

I've been searching and fiddling and fixing. I've reinstalled everything a dozen times. I've gone through four separate step-by-step install/ configure how-to's. I still can't seem to find a solution, so I'm posting to the forum. I've set up LAMP a hundred times over the last four years... at least. This time, however, I'm stumped.

Anyone ??

---

### Post by jtc on 2007-04-22
How did you backup and restore your databases? By simply copying the files containing the db-data or by the output of mysqldump? Did new install contain another version of MySQL?

---

### Post by strixy on 2007-04-22
I used phpmyadmin to export the data. It's worked well in the past.

---

### Post by glalpi on 2007-04-22
Are you using replication?  The reason I ask is that I just cured a problem with MySQL where replication failed because "the table didn't exist".  It turned out that MySQL 5.0.38 (the version furnished with 7.4) apparently does not do a case insensitive compasrison of table names while doing replication.  If you are reading from a replicated database, this may be your problem.  It might also be that there are other places where case insensitive comparisons are not being made, even when they are asked for.

---

### Post by strixy on 2007-04-23
I installed the software packages for the websites from scratch and those work. I'll update the content by hand. It's only a couple of sites and a little copy / paste.

---

