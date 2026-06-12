---
title: "Backing up server"
date: 2009-06-01
forum: Server Platforms
---

### Post by cmwslw on 2009-06-01
I'm sure this has probably been asked before, but I couldn't find anything by searching. So I have a home server that hosts my website. Currently, it is not backed up regularly. I need to know an easy way to back it up to an additional hard drive connected to it. So, if it's hard drive ever crashes, I can restore the entire drive - programs, databases, configurations and all. What is the best way to do this? Can I just rsync the entire filesystem? Do I only need to sync certain folders? 

Sorry if this is a noobish question - this is my first server.

-Cory

---

### Post by FakeOutdoorsman on 2009-06-01
I use [AutoMySQLBackup](http://sourceforge.net/projects/automysqlbackup/) to create daily, weekly, and monthly remote backups of my databases.  I like how AutoMySQLBackup rotates the backups and will e-mail you if errors are encountered.

You don't need to backup the whole file system to backup your web site. Just backup the web directory with rsync and your server configuration files (/etc/apache2/).  For example, if my site is in */var/www/foo*, I'll just backup *foo*.  There are many scripts out there to do these sort of things.  I've been looking into [duplicity](http://duplicity.nongnu.org/) lately.  It's great for those cheap "storage clouds" such as Amazon S3 and Mosso.

---

### Post by grantemsley on 2009-06-01
rsync'ing the entire filesystem will work just fine.  If you need to restore, you simply have to replace the drive, boot from a rescue CD, format, install grub and copy everything back.

You can exclude some directories (/proc, /sys, /tmp and possibly others).  Make sure you also exclude the destination.

I used backupninja to set it all up for me, because it's a lot easier to configure than manually running rsync.  I ended up having to hand edit the config files, but it works nicely.  It will also dump mySQL databases to a .sql file before doing the backup so you can ensure you have a consistent copy.

---

