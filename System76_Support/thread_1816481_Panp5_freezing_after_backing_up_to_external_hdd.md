---
title: "Panp5 freezing after backing up to external hdd"
date: 2011-08-02
forum: System76 Support
---

### Post by japhyr on 2011-08-02
Hello,

I have a panp5 which has worked quite well for the last couple years.  It is now running 10.04.  I have been backing up to an external hard drive periodically for the last year without any trouble.  Space is not an issue - I am using about 150G on a 500G hard drive on my laptop, and the 500G external drive is less than half full.

A few days ago my computer started freezing after running my backup script and removing the external drive.  The only thing different is the number of programs I have running while doing the backup.  I have been working on a web development project, so I have been leaving openoffice, gedit, nautilus, emacs, firefox, and probably a couple other programs running while I do the backup.  I am not actively working while running the backup, but I don't close all those programs before running the backup script.

Is that a likely cause for the problem?  Is there a log I should look at to find out what is causing the freeze?  I looked through the logs but didn't really know what to look for.

---

### Post by isantop on 2011-08-02
Make sure your swap partition is active and functional, since running out of RAM would cause freezes. You can find out if the swap is active and check the current RAM/Swap usage from the System Monitor application under System > Administration in 10.04.

---

### Post by Furball588 on 2011-08-02
So everything is fine as long as the external is plugged in?

My initial thought is nautilus...

So whats your script look like anyways?

---

### Post by japhyr on 2011-08-03
I will look at the RAM and swap usage next time I do a backup.

Yes, the freeze happens after I "safely remove" the external drive.  The script is a simple series of rsync commands.  Why do you suspect nautilus?

---

### Post by Furball588 on 2011-08-03
> **japhyr said:**
> Why do you suspect nautilus?

Just a gut reaction.    

Thinking about what you just said...I have to wonder if the drive is trying to mount again after clicking "safely remove drive"  Certainly if that's the case I can see why it would freeze.

There's nothing exotic you've done with the drive like encrypting it right?

---

### Post by japhyr on 2011-08-03
No, it is not encrypted.  I have not changed anything about the backup process.  Now that I think of it, though...

The files for the development project I have been working on recently are under a new directory, /srv.  I am running a virtual environment from a subdirectory of /srv.  I just added the /srv directory to the backup script.  This is a django project, so I have had a virtual environment running from that directory, and the django development server is also running in a subdirectory of /srv.

I wonder if I should stop the virtual environment and the django server before starting the backups?  The backup script does complete, so I'm not sure that's the issue.

---

### Post by Furball588 on 2011-08-03
Couldn't hurt to try that...

I also wonder if going into a terminal and doing a sudo umount on the device would do (or even selecting unmount rather then remove from the menu)

I've always viewed the remove device and unmounting the same thing when dealing with a single partition, so maybe either of those two methods would shed a little light.

---

### Post by japhyr on 2011-08-05
I tried backing up again tonight, with no other programs open.  I watched the memory usage in the system monitor.  RAM never went above 600MB out of 4GB, and swap sat around 285MB out of 6GB.  The backup worked, but the computer froze after I chose "Safely Remove Device".

I looked at the logs again, and I found this in syslog:
```
Aug  4 17:28:12 eric-laptop ntfs-3g[17272]: Mounted /dev/sdb1 (Read-Write, label "Iomega HDD", NTFS 3.1)
Aug  4 17:28:12 eric-laptop ntfs-3g[17272]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077
Aug  4 17:28:12 eric-laptop ntfs-3g[17272]: Mount options: rw,nosuid,nodev,uhelper=udisks,silent,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096,default_permissions
Aug  4 17:28:12 eric-laptop ntfs-3g[17272]: Global ownership and permissions enforced, configuration type 1
Aug  4 22:08:03 eric-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
```I connected the drive at 5:28, and the backup finished at 5:31.  Should there be a log message from the removal of the drive?  This is pretty frustrating, because I can't imagine these hard shutdowns are very good for the system.

Any chance a huge log file from the backup script would be causing this?  I never set up log file rotation, and I just noticed that the backup script's log file was approaching 10MB.  I just archived the log and emptied the log that the script uses, so I will test that next time I run a backup.

---

### Post by isantop on 2011-08-05
Let us know how your testing goes. If those are the entries in your log, then there isn't any log output indicating what's going on. 

Can you try running memtest? You can download the latest 4.20 version as an ISO file from here:

[http://memtest.org](http://memtest.org)

---

