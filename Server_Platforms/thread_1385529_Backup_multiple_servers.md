---
title: "Backup multiple servers?"
date: 2010-01-19
forum: Server Platforms
---

### Post by ThomWilhelm on 2010-01-19
Hello there,

I currently have a group of 3 servers connected to a local network. One is a web server, one is a mysql server, the other used for a specific function on my site (calculation of soccer matches!).

Anyway, I have been working on the site a lot lately but it is tedious connecting my USB hard drive to each computer and copying the files. This means I am not backing up as often as I should...

I have a laptop connected to this same network that I use for development so I can SSH into to the computers, is there any software for ubuntu that can take backups of files that I choose on multiple computers? I know I could rsync but is there something with more or an GUI?

Then I can just every 2 days move the most recent backup from my laptop to the USB drive. Then I will have the backup stored in 2 places if things go kaboom somewhere.

Thanks in advance,
Thom.

---

### Post by wirelessmonkey on 2010-01-19
Bacula and BackupPC are both good, but maybe more than you're looking for.

---

### Post by Girya on 2010-01-19
> **wirelessmonkey said:**
> Bacula and BackupPC are both good, but maybe more than you're looking for.

+1 backuppc 

If you go that route Install backuppc on LVM so you can add disks when you fill disks with backups. 

Whatever you choose make sure that it is automatic. It's way to easy to blow off making a backup when you're busy.

---

### Post by pirateghost on 2010-01-19
> **Girya said:**
> +1 backuppc 

If you go that route Install backuppc on LVM so you can add disks when you fill disks with backups. 

Whatever you choose make sure that it is automatic. It's way to easy to blow off making a backup when you're busy.
+2
backuppc has saved my butt on more than one occasion

---

### Post by Lars Noodén on 2010-01-20
As @ wirelessmonkey points out, [Backula](http://www.bacula.org/en/) and [BackupPC](http://backuppc.sourceforge.net/)

But since you needs are rather simple, making a simple shell script and then using rsync over ssh might do just as well.

---

### Post by steven.jones on 2010-01-20
> **ThomWilhelm said:**
> Hello there,

I currently have a group of 3 servers connected to a local network. One is a web server, one is a mysql server, the other used for a specific function on my site (calculation of soccer matches!).

Anyway, I have been working on the site a lot lately but it is tedious connecting my USB hard drive to each computer and copying the files. This means I am not backing up as often as I should...

I have a laptop connected to this same network that I use for development so I can SSH into to the computers, is there any software for ubuntu that can take backups of files that I choose on multiple computers? I know I could rsync but is there something with more or an GUI?

Then I can just every 2 days move the most recent backup from my laptop to the USB drive. Then I will have the backup stored in 2 places if things go kaboom somewhere.

Thanks in advance,
Thom.

I would tend to install Bacula and 2 or more large (1~1.5TB) sata drives on one of your servers. My setup is a 1TB R5(3+1) (300GB for samba, 600Gb for ESXi) with 2 x 300 pata disks to backup to (at present) for bacula...so I mount 1 for one month and one for the next...I do two full backups per backup disk. When I first mount the disk, I manually trigger a full backup....it then runs incrimentals and differentials for a month then does a full backup. At that point I unmount that disk and mount the other and trigger a full backup and off I go again. When I can afford it Im looking at the WD 1.5tb (or 2tb) green disks, 6watts energy (instead of 11watts) and big enough for about 6 months backups...I will I suspect still swap over montlhy though. At some satge I also want to have bacula backing up to eSATA or usb2~3 or fwire, then just swap out disk packs...again I have 2 of these as 300gb pata's....

The key here is to automate it so you dont forget or get lazy...bacual isnt hard to setup, the only slightly tricky part is to backup its mysql info.

regards

---

### Post by ThomWilhelm on 2010-01-20
Ok thanks for all the info guys, really appreciate it. I have gone with "backuppc" which after a bit of early problems have got it working on the first server, all the automation is very good and it looks like eventually i will get it doing everything I need automatically. ;)

Looks like there are a lot of interesting options to play around with, per server configuration is really needed as with a web server I would like to keep lots of separate copies of the website files as they are just php scripts and images so only about 20mb so I can keep like 200 copies and everything will be fine, but then the database backup is 300mb so I only want to download the most recent file every 3/4 days.

Thanks again, very impressed with the responses I got on an important question.

I can now sleep peacefully with my backups sorted nicely. :D

---

### Post by pirateghost on 2010-01-20
backuppc performs excellent deduplication and compression.  play around with your compression level, by default it is set to 5 i think.  i prefer 7 on mine, eats up more CPU while its running but compression level is better

---

### Post by ThomWilhelm on 2010-01-23
I have backuppc backing up my servers daily now, I'm getting around 70% compression and the incremental backups feature make this an amazing program! Each day only adds very little disk space to the backup pool as not much changes, mainly a new database backup file is downloaded, when compressed its only about 100MB. I love the web interface as well. Very easy to add extra computers from now, just setup password-less SSH and away you go.

I find it amazing people pay lots of money for Apple's OSX and talk about programs like Time Machine and Bootcamp, when Ubuntu offers such amazing programs for free.

Thanks your help again, I can now sleep easily knowing I can't lose my files.
Thom :D

---

### Post by HermanAB on 2010-01-23
Hmmm, a backup system should be simple and a rsync script is a one liner, which is a simple as it gets.  OK, you have three servers, so you need three lines, put shose in a bash script and drop it into /etc/cron.daily and you are done.  

Mount your USB disk on one of the machines and share it with NFS.  There is no need to plug it in and out all the time.

The trick is to specify a whole directory such as /home to backup, then you --exclude the schtuff that you *don't* want to backup.  The result is a super simple maintenance free backup system.

If your backup system is more than a four liner including the #! line at the top, then you are doing something wrong...

---

### Post by ThomWilhelm on 2010-01-23
Hi Herman,

I had thought about this, but its nice that compression and incremental backups (giving a simple versioning system) are included without writing a script, added to this the number of per-server config options backuppc has. Also if say 2 servers are added in future I'd rather be able to login and have a main status console rather than checking all the files myself that backups are working.

I always think its best to do things once and for all rather than fix things quickly for now, and then realise I will need to change the backup system again :(

Thom.

---

