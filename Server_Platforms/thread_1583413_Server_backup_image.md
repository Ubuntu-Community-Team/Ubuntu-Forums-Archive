---
title: "Server backup image"
date: 2010-09-27
forum: Server Platforms
---

### Post by lazychris2000 on 2010-09-27
I have been searching around for a solution, but have not been able to find one, so hopefully someone in the forums can give me a hand.  Here is the situation:  I have been put in charge of a file/email server after the previous admin quit.  I have used ubuntu desktop for a few years and consider myself pretty proficient, however I have very little experience with the server edition.  What I am trying to do is make a complete backup image of the server (think Norton Ghost image or the builtin Windows Server backup).  Basically, it would be a disaster recovery image.  Should anything happen, I can throw in a disk and reimage the server and get it running with as little time/effort possible.  Ideally, I would like to be able to setup the software create backups automatically (or failing that, setup a cron job) every week, or whatever time period my boss wants.  
Server is running 10.04.1 x64 server edition, no GUI.  I don't think the hardware is relevant, but its got dual xeon processors, 6GB ram, 3ware raid controller--OS array is 3x750GB Western Digital RE3 raid5, Data array is 12x750GB WD RE3 raid10.  Currently, the OS array is using 10ish GB and I doubt it will ever exceed 50GB, and will be the only array that needs to be backed up.  I have a folder mounted on the server, which points to a SMB share on a separate server, where the data is currently being copied up to (a script that just does cp -r /home /etc /var/www /media/backupserver--not the best solution, but it is what was previously setup).
I was reading about Bacula, but it seems rather difficult to configure and use.  Are there any other (easier to use) solutions available that can accomplish this?  I am not opposed to using Bacula, but if there is a simpler program that does the same thing, I would rather use it.

---

### Post by cenwesi on 2010-09-28
ok, i am sure if you really searched you would have seen thousands of ways of backing up. One way is to use the TAR command. 

Since you are familiar with the Desktop version, there really is no difference since the server version doesn't come with the gui installed. Get webmin installed on the server and that will atleast help with some of the backend stuff and webmin those have a module for backup. 

PS: Search google on backing up linux...

---

### Post by CharlesA on 2010-09-28
I use [Clonezilla]("http://clonezilla.org/") to image my machines. So far it hasn't failed me. :)

---

### Post by lazychris2000 on 2010-09-28
> **CharlesA said:**
> I use [Clonezilla]("http://clonezilla.org/") to image my machines. So far it hasn't failed me. :)

I will look into that.  I am reading about Mondo right now, so I will take a look at Clonezilla next.  Thank you for your kind, helpful answer.

---

### Post by trundlenut on 2010-09-29
> **CharlesA said:**
> I use [Clonezilla]("http://clonezilla.org/") to image my machines. So far it hasn't failed me. :)

Me too.  Dead easy to use to backup and restore machines including upgrading hard drives.

---

### Post by Vegan on 2010-09-29
Clonezilla is definitely a handy tool.

I use my LAN and backup that way using a range of tools including tar and gzip among the choices.

---

