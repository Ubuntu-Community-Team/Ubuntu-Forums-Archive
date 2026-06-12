---
title: "Best method to back up MySQL database?"
date: 2008-12-30
forum: Server Platforms
---

### Post by Twizzle on 2008-12-30
I am trying to work out the best way to back up a MySQL database which is on my home server. The server is set up as follows:

120 Gb HDD containing / , swap and /var
2 x 320 Gb HDD in software RAID 1 containing /home

I have Ubuntu 8.10 server edition installed and use Samba, Zoneminder and Zarafa. I use the /home partition to store my media files (which I access from a media PC) and to run backups to from my office PC.

I also use Zarafa to manage my emails, contacts and calendar. Zarafa (as far as I understand) stores all the data in a MySQL database (forgive me if I am using the wrong terminology), and I would obviously like to have this backed up.

The original plan was to have /var on a RAID1 partition but because Zoneminder was writing and deleting so much data to it I was worried it would reduce the lifespan and slow things down.

Can I move a MySQL database easily (into /home) or is it a better idea to run a daily cron job to back up the database to the /home partition. Or should I reinstall the lot and put /var back onto a RAID partition?

I am worried that as I download all my email to the server from my ISP, if it goes t**s up and a disk fails, I will loose some important stuff!

---

### Post by namdung on 2008-12-30
[http://www.zmanda.com/](http://www.zmanda.com/)

U may use the Paid or Free Community version.

---

### Post by aurelieng on 2008-12-30
It is very easy to use mysqldump to backup your database to your /home, see [http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html](http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html) , and implement it in a cron job for instance.

You can also move your /var/lib/mysql to /home/mysql, and create the appropriate symlink (if you do so, don't forget to stop mysqld first !). Finally, I don't think that MySQL over RAID1 is a problem ;)

Cheers,

Aurelien.

---

### Post by cpetercarter on 2008-12-30
You can install phpMyAdmin (in the repos). It provides an excellent interface for managing all aspects of mySQL, including database backup in a number of different formats.

---

