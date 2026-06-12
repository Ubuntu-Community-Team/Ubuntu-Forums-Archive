---
title: "Backup for Ubuntu 16.04 - which folders?"
date: 2016-11-17
forum: Ubuntu, Linux and OS Chat
---

### Post by notso23 on 2016-11-17
Which folders are best to backup - Personal ones are a given, but what about the programs etc that I have downloaded since the install of Ubuntu.

If I wanted particular programs do I find the folder and select it for backup, or would it be best just to backup /home and be done with it. :p

---

### Post by kpatz on 2016-11-17
Backup /home obviously, maybe /etc as well if you customized anything in there.  Or just do like I do, and backup everything-- Ubuntu installs are only a few GB total.  Then if something happens, I can just pop in a new drive, create partitions, rsync everything back, install grub and pick up where I left off.

---

### Post by TheFu on 2016-11-17
What you need to backup depends on where information is stored and how you use the system.


/etc - tiny. I never understand why people don't grab this.
$HOME - on a single-user box, this might be the most important.
Any scheduled jobs via cron?  Get the crontabs.
Grab the package manager list of installed packages.  Relatively tiny.
I grab the current system information - CPUs, RAM, networking, disk layouts (LVM, encryption, partitions), drivers used, stuff like that.
If you installed any servers - like apache or nginx or MariaDB - then you want that data too. Each requires a little different way of backup which changes based on the data, how it is stored, and whether it can be unavailable or not.
If you installed anything manually, that stuff usually goes into /usr/local/ ... grab that too.

I haven't backed up everything on a system in about a decade, but if any of my systems die, I'm 100% confident it can be restored in about 45 min to the point of the last automatic backup from last night (around 2am). Zero data loss. I have a mix of desktops and servers. Each has a slightly different backup script, but they all can be restored.  There are between 60 and 120 days of versioned backups for each system, thanks to some amazing tools.  

Not all data is the same from a backup perspective.  Large media files are very different from tiny document files or system settings or manually installed programs in /usr/local/ ... 

So, only you can decide what is necessary to backup.  And the only way I know to determine that you have everything you need is by testing the restore process.  Backups are onyl 10% of the problem. The other 90% is the restore. Backups that cannot be restored are a complete waste, until the backup is updated to be restorable.  Expect that process to require about 3 attempts before it is successful and it is best to discover the failure **before** you need it.

[https://ubuntuforums.org/showthread.php?t=2330130](https://ubuntuforums.org/showthread.php?t=2330130) has lots-o-links for prior backup discussions and techniques.

---

### Post by notso23 on 2016-11-18
Thank you for your information, I was thinking along the line of backing up everything. 
Great advice ... great forum for a newbie.

---

### Post by kevdog on 2016-11-18
> 
Any scheduled jobs via cron? Get the crontabs.
Grab the package manager list of installed packages. Relatively tiny.
I grab the current system information - CPUs, RAM, networking, disk layouts (LVM, encryption, partitions), drivers used, stuff like that.


You have a script to get this information?

---

### Post by TheFu on 2016-11-18
> **kevdog said:**
> You have a script to get this information?

Sure - a few of them. Think I just run the same commands in my backup scripts.  Pretty sure those have been posted here a few times.

A) All the tiny system information stuff goes to /root/backups/, daily.
B) I use perl for my backups. This runs as root - just setup the variables to useful values for your system.
```
# ####################################################
# ##########################
# Daily dump of important crontabs to $HOME/backup - crontab -l -u root
`$crontab -l -u root > $local_backup/crontab.root`;
`$crontab -l -u thefu > $local_backup/crontab.thefu`;

# ##########################
# Daily dump of current packages to $HOME/backup
`$dpkg --get-selections  > $local_backup/dpkg.list`;

# ##########################
# Daily dump of current hardware to $HOME/backup
`$lshw > $local_backup/lshw.list`;

`$pvdisplay > $local_backup/pvdisplay.txt`;
`$vgdisplay > $local_backup/vgdisplay.txt`;
`$lvdisplay > $local_backup/lvdisplay.txt`;
`$blkid > $local_backup/blkid.txt`;
`$df -h > $local_backup/df.txt`;

# ##########################
# Daily dump of current ruby gems to $HOME/backup - 
 `$gem list --local > $local_backup/gem.list`;

# ##########################
# Daily dump of current CPAN modules to $HOME/backup - cpan -l
 `$cpan -l > $local_backup/cpan.list ` if ( -e "/usr/local/lib/site_perl");

```

Capturing them daily means those files are updated daily and tied to the specific backup to be restored.  On some systems, also get SW-RAID setup info - just not on the one I pulled this from.  $local_backup is in the set of directories (/root/backup) which rdiff-backup captures daily.

I'm loath to post an entire backup script because my systems are different from yours.  Each of my systems has a slightly different backup script, but they are all very similar.  I also delete unwanted things before running backups - like flash-caches and other local object storage for flash, html5, and other Adobe crap.
[http://blog.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup](http://blog.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup) - old blog about this.
[http://blog.jdpfu.com/2011/10/08/optimized-backups-for-physical-and-virtual-machines](http://blog.jdpfu.com/2011/10/08/optimized-backups-for-physical-and-virtual-machines) another.

The articles may seem old, but it is still working that way, basically.  Early on, I had issues with backups when I attempted to grab huge files (VMs) from outside the VM.  All librsync tools have this issue with large files. By treating VMs like they are physical machines for backup purposes, those issues are gone and have been gone for 5+ yrs.

More links for this stuff in my signature.

---

