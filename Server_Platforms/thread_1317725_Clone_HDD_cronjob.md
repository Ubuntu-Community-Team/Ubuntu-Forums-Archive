---
title: "Clone HDD cronjob"
date: 2009-11-07
forum: Server Platforms
---

### Post by wattaman on 2009-11-07
I've recently bought another HDD from my server hosting company and I'm planing to use it as a back up for the first one. Is not installed yet but until then I want to learn how to make this happen.
So, I'm thinking to, somehow, backup the entire HDD I have now on the second HDD I'll receive these days; in case the first one will crash someday, the system must boot from the second HDD. I have the option to reboot the server from my customer panel, I guess all I need is:
1. the cronjob to copy the 1st HDD to the second (*maybe the MySQL files should synchronize more often, like daily, and all the other files weekly - I'm just assuming it would be better, please advice me*)
2. to make the settings so, in case of the 1st HDD fails to boot, the system will boot from the second HDD.

This is my plan. Can someone please advice me on how to do it? I'm using Webmin most of the time to access the server, BTW.
Thank you!

---

### Post by windependence on 2009-11-07
Well, I would advise learning a bit of command line for this. You could use dd and clone the drive every so often via cron, but rsync would probably be better. You can also use rsnapshot with rsync to keep the drives in sync.

-Tim

---

### Post by wattaman on 2009-12-04
OK, my hosting company finally installed my second HDD and I've also managed to install rsnapshot. Now I'm stuck :(
I've read the rsnapshot configuration file, which is very explicit, however don't know how to clone the first HDD on the second HDD. Or how to copy, at least, everything from one to another.
From the rsnapshot configuration file I could only understood how to backup folders on the HDD.
Thanks for any help you can provide!

---

### Post by HermanAB on 2009-12-04
Format the thing and use rsync, same as everybody else...
:)

---

### Post by windependence on 2009-12-04
[http://www.backupcentral.com/components/com_mambowiki/index.php/Rsnapshot](http://www.backupcentral.com/components/com_mambowiki/index.php/Rsnapshot)

[http://www.thegeekstuff.com/2009/09/linux-remote-backup-using-rsnapshot-rsync-utility/](http://www.thegeekstuff.com/2009/09/linux-remote-backup-using-rsnapshot-rsync-utility/)

[http://www.debian-administration.org/articles/217](http://www.debian-administration.org/articles/217)

There's more out there but this should get you started.

-Tim

---

### Post by wattaman on 2009-12-05
OK, thanks for the intel. Still don't get the basic's of linux:
- in the rsnapshot.conf, what should I write:
       - *backup  root@hostname:/ /dev/sdb1/* (because _Device file /dev/sdb1_, the second HDD, I mean)
OR
       - *backup  root@hostname:/ /HDD2/* (because _Mounted on /HDD2_)
By the way, I'm using Webmin.
This is the thing I don't get, what's the command to clone one HDD to another, on the same machine.

---

### Post by wattaman on 2010-01-12
K, figured it out. Thanks for helping.
One more thing I can't find is: how can I instruct rsnapshot to make only one backup (overwrite an existing backup) or to delete the old backups from time to time? 
Now I'm still testing it but it seems it creates another backup folder with every backup command (I use cronjobs, if it matters). So, soon enough, my second drive will be full with multiple backups of the first one, I'm afraid.
Thanks again!

---

