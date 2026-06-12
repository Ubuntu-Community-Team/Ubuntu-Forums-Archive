---
title: "How do you do your backing up?"
date: 2009-05-31
forum: Server Platforms
---

### Post by samosamo on 2009-05-31
I need a real solution for complicated backups. rsync cronjobs aren't cutting it anymore. I need a GUI to deal with this and possibly even a way for users to restore their own files.

rsync: No real GUI. Light duty solution. Plus, if you plan to do full backups, it takes up too much space.

rdiff-backup: Love it, but just like rsync there is no real GUI. I had this idea to use rdiff-backup+archfs. I would write the cron script myself, but users would be able to browse backup volumes via network shares, and that would be their GUI. The problem with this is: I don't want to write cron scripts anymore, and archfs is alpha quality software anyway. It's not in the repos and building it from source is buggy at best. 

Bacula: Didn't try it yet. Besides it being a server/client system, it looks awesome. Why doesn't it have the option to use built in options like rsync?

BackupPC: I'm about to try this next. It sounds great. Full web GUI, many features, doesn't require a client, uses some fancy hard link stuff to only back up diffs. I hope it works out.

Honorable Mention... slbackup plugin for Webmin which uses rdiff-backup as a back end. I use it to back up /etc on each server.  They all run webmin anyway. For what it is, it's a great little tool. It even autoconfigures ssh keys for you. If I was forced to I could probably use this for all my backup needs and be happy. I'm just looking for something better.

What else is there?

---

### Post by doogy2004 on 2009-05-31
Give DirSynPro a try, it runs in java.  I use it to backup my Windows machines to my Ubuntu server, then I use rsync to backup the server to disk (I could use DirSyncPro).  I also use JungleDisk to backup to Amazon S3.

DirSyncPro - [http://directorysync.sourceforge.net/](http://directorysync.sourceforge.net/)

JungleDisk - [http://www.jungledisk.com/](http://www.jungledisk.com/)

---

### Post by Cheesemill on 2009-06-01
Take a look at rsnapshot, it's CLI but if you want you can let users browse their own backups.

Cheesemill

---

### Post by grantemsley on 2009-06-01
backupninja is a nice configuration system that uses rdiff-backup.
My systems use backupninja to backup between each other.  It even helps you setup the SSH keys if you don't know how to do it yourself.

This eliminates your need for custom built cron jobs.

As for user GUI...just share out their rdiff directory via samba or whatever.  They can browse the files just fine.  They won't have access to previous copies or any of that fun stuff without using the command line, but they can see the most recent backup without any problems.

---

### Post by slowtrain on 2009-06-27
Hi folks:  I'll probably need to rent space on something like Jungle Disk to backup my computers.  Problem is, I don't like the idea of my files ending up unencrypted so anyone with access to the company servers could read them.  While encrypting files is easy enough, this could be a hassle if I also want automated and incremental backups.  

Would an arrangement like this work:  Rent space on Jungle Disk (which I gather is webdav), use backupninja to run duplicity, with duplicity encrypting and compressing but also able to do automated and incremental backups?  Will duplicity / backupninja allow me to send files to a webdav mounted filesystem?  

Also, if I have total system crashes at my end, I guess I'll need a paper copy of my encryption key.  Anything else?

---

### Post by doogy2004 on 2009-06-29
JungleDisk has settings to encrypt the data and the filenames before they are uploaded to the server.

See Security Now! Episode #123 for details - [http://www.grc.com/securitynow.htm](http://www.grc.com/securitynow.htm)

---

### Post by slowtrain on 2009-07-02
Thanks doogy2004!

If I understood the conversation in #123 correctly, then the encryption key stays locally with the client and no one on the Jungle Disk side can readily decrypt your files, which is perhaps more than can be said about the Amazon service.  Nice set up!

---

### Post by Bas_91 on 2010-09-01
The link mentioned to DirSync Pro seems to be broken. The right link is [http://www.dirsyncpro.org](http://www.dirsyncpro.org).
 
Thanks for the tip anyway. I'm gonna give it a try.

---

