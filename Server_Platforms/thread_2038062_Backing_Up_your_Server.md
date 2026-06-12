---
title: "Backing Up your Server"
date: 2012-08-05
forum: Server Platforms
---

### Post by iToasterman on 2012-08-05
Hey So I just red [this]("http://ubuntuforums.org/showthread.php?t=35087") and I'm a bit confused. Some people say to backup /dev and others say no to.

The machine I'm backing up is running a older 40gb HDD with a 200gb one for backups. When I do a backup (Im going for bzip2)if I ever need to restore can I just install a Fresh ubuntu install and un-bzip it to the root directory? Also after I do that will it be possible to do apt-get update and upgrade?

I can't find a rock solid guide on it as I'm just going to use cron to automate this every midnight.

Also, anything that starts with the system will continue to start with it after a restore, correct?

---

### Post by LHammonds on 2012-08-06
I use LVM (Logical Volume Manager) and FSArchiver.  Check my signature for how I setup an Ubuntu Server.  I have a section dedicated to backup/restore.

This of course depends on how you've setup your system.  If you use LVM, you will need sufficient unallocated space in your LVM.  You can see how I setup my system in the earlier posts which also explain how my volumes are defined...which give me a lot of control over the system.

LHammonds

---

### Post by iToasterman on 2012-08-06
> **LHammonds said:**
> I use LVM (Logical Volume Manager) and FSArchiver.  Check my signature for how I setup an Ubuntu Server.  I have a section dedicated to backup/restore.

This of course depends on how you've setup your system.  If you use LVM, you will need sufficient unallocated space in your LVM.  You can see how I setup my system in the earlier posts which also explain how my volumes are defined...which give me a lot of control over the system.

LHammonds

Thats not the kind of solution I'm looking for... :|

But I will! backup /var only, maybe /home. Those seem to be the only important directories  :)

---

### Post by CharlesA on 2012-08-06
Not that it will help you much, but I only backup /home/ if the system is hosed, I can just reinstall and throw the backed up /home/ back where it belongs. ;)

---

### Post by HermanAB on 2012-08-06
/dev, /sys, /proc and also /tmp are not real directories and there no point in backing them up.

---

### Post by HugoSerrano on 2012-08-06
Hi!

It really depends on what the server does and how it's organized...

For example, by default, if you got apache running, you should backup /var/www
If you got dhcpd server, you should backup /etc/dhcpd, and so on...

Best Regards!

---

### Post by CapnKirk on 2012-08-06
> **CharlesA said:**
> Not that it will help you much, but I only backup /home/ if the system is hosed, I can just reinstall and throw the backed up /home/ back where it belongs. ;)

Configurations of email and web servers (not to mention version control servers, bugzilla, etc.) and backups of sql databases (mysql, postgresql, etc.) are also worthwhile, especially if you've spent a lot of time customizing them. I use WordPress heavily, have a lot of plugins and data. I also back up the entire blog directory.

There's also something to be said for backing /etc up as well. When restoring a hosed system, /etc can be a helpful reference to how you configured things before.

Kirk

---

### Post by CharlesA on 2012-08-06
> **CapnKirk said:**
> Configurations of email and web servers (not to mention version control servers, bugzilla, etc.) and backups of sql databases (mysql, postgresql, etc.) are also worthwhile, especially if you've spent a lot of time customizing them. I use WordPress heavily, have a lot of plugins and data. I also back up the entire blog directory.

Good point. I've just been using mysqldump instead of backing up the database itself. Maybe I am just doing it wrong.

---

### Post by HugoSerrano on 2012-08-06
> **CharlesA said:**
> Good point. I've just been using mysqldump instead of backing up the database itself. Maybe I am just doing it wrong.

Mysqdump it's the right way to do it. 
If you backup the mysql directory, you need to restore it to exactly the same version of the mysql, else it may not work... 

With mysqldump, you should use -R to backup also your functions and procedures.

Best Regards!

---

### Post by CharlesA on 2012-08-06
Oh cool. I've never used -R before. Thanks for the info!

---

### Post by LHammonds on 2012-08-07
> **HugoSerrano said:**
> With mysqldump, you should use -R to backup also your functions and procedures.
Thanks for pointing that out.  I've added "--routines" to my backup script (version 1.2 of mysql-backup.sh in my sig for MySQL server)

My apps don't use functions or procedures but if they ever do, I'm covered now!

LHammonds

---

### Post by HugoSerrano on 2012-08-07
Glad I could help :-)

Best Regards!

---

