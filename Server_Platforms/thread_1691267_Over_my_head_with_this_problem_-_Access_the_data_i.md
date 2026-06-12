---
title: "Over my head with this problem - Access the data in .fbd data file"
date: 2011-02-19
forum: Server Platforms
---

### Post by bobnutfield on 2011-02-19
Hello Everyone,

I am posting this here  because this seems to be where all of the database questions get asked.  We purchased a new database system at work last October, ditching the old system because of a lack of support from the vendor.  This is a retail Point of Sale and Backoffice database system.  I am not sure what system the new one runs on, but the system we replaced was a Firebird data base.

The reason I am posting is because we are now in need of the information contained in the old database which was not completely imported into the new system.  Unfortunately, we parted company with the old vendor under extremely hostile conditions, and they are not a source of help for this problem, nor are the new vendors.

Basically the problem is this:  The database in on a Windows XP system and I found a copy of SQL Manager Lite 2008 on the system, which after quite a bit of studying, I figured out how to extract the database into a removable file.  I have this file (178MB) on a USB stick in a file called Backoffice.fbd.

My studying suggests to me that I can get into this database with MySQL.  I have never used this and have no clue how to do this.  All I want to be able to do get into the database and create tab deliminated spreadsheet files for each of the database sections (Customers, Repairs, Sales History, stock files, etc.)

Is it possible to do this with Ubuntu and MySQL and if so, can expert suggest one or two things to get me started.  While a guided tutorial would be nice because I am not an expert, I am willing to learn on my own if someone could point me in the right direction.

Any thoughts or comments are appreciated in advance.

Bob

---

### Post by SeijiSensei on 2011-02-19
Firebird on Ubuntu: [http://www.firebirdsql.org/manual/ubusetup.html](http://www.firebirdsql.org/manual/ubusetup.html)

---

### Post by bobnutfield on 2011-02-20
Thank you very much for your reply.  That was very helpful and looked like what I needed.  I also installed Flamerobin to give a GUI (I am too prone to errors with the commandline.)  I actually have been able to reconstruct the database using this, so thank you.

However, I found that while I had successfully contructed the database, there was NO DATA, only the tables and structure information.  So. it is back to that machine and try to find the data folders and try to get this database to read them.

Thanks for the help

Bob

---

### Post by SeijiSensei on 2011-02-20
> **bobnutfield said:**
> Thank you very much for your reply.

You're welcome, Bob.  
> However, I found that while I had successfully contructed the database, there was NO DATA, only the tables and structure information.  So. it is back to that machine and try to find the data folders and try to get this database to read them.

Whoa, that's a drag.  Good luck with your prospecting expedition.

> **bobnutfield said:**
> We purchased a new database system at work last October, ditching the old system because of a lack of support from the vendor.  This is a retail Point of Sale and Backoffice database system.  I am not sure what system the new one runs on, but the system we replaced was a Firebird data base.

Perhaps you should find out what database underlies your new POS system?  I make daily plain-text backups of my MySQL and PostgreSQL databases.  You might want to ask your vendor how to produce platform-independent backups so you won't be stuck in a similar position in the future.  My guess is they'll drag their feet about this if it's an expensive proprietary system.  If it's running a common SQL server on Linux, you can make the backups yourself with tools like mysqldump or pg_dump.

You should probably mark this thread [Solved] now.

---

