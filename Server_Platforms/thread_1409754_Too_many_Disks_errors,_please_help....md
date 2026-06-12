---
title: "Too many Disks errors, please help..."
date: 2010-02-18
forum: Server Platforms
---

### Post by sgb77 on 2010-02-18
Hello,
I have been using linux for over 6 or 7 years and I have always thought of it as a reliable system, until recently.
Most of my experience has been with Suse, however since they were bought by novel we decided to move to another distribution, we wanted to stay away from the rpm distributions so the logical choice was either Debian or Ubuntu, so I chose Ubuntu, being that I was already familiarizing myself with the desktop version of ubuntu installed in my laptop.

I installed ubuntu server 9.08 I believe in one of my test servers, I had on disk and the following partitions
/
/boot
/swap
/home (lvm)
All the partitions were ext4, except for swap of course, I had it running and familiarizing myself with it for about a month or two and Ubuntu 9.10 was released, so I decided to upgrade. This was the first sign of trouble, after the upgrade completed, I was greeted by a big fsck error, tried hitting contol-D to retry, but it did not work, I was hoping to get the prompt shell, but nothing, all I got was a flashing prompt. In any case, I thought maybe my hardware was going bad and since I was getting a brand new server in a few days I just dismissed it.

I installed  Ubuntu server 9.10 in my brand new server and it seemed fine, the server has the same partition structure as my test server. I have restarted a few times over the course of the last two or three months, normally. 

Until yesterday, I got the same error message I got on my test server, which I will post below. The system started its system check and jumped from 10% to 80% in a few seconds which gave me an indication something was wrong, and surely enough, when it got to 90% it was stuck for about an hour, so I hit the esc button. At which point I was presented with the hit Control-D  shell will terminate this shell and retry, and so I did, and I got an even longer message, which will be posted below. After the message is displayed just as my test server nothing, I just get a flashing prompt but it is dead, I can not type anything, at which point I hit Alt+Ctl+Del to restart the whole process again.

On a side note, I have to say I have also been asked to run the fsk tool in my laptop several times in the past few months, which I find not only annoying, but totally inexplicable, since I always shutdown my laptop properly, but yet somehow the filesystem finds corrupted files.

What is going on? I never had these many problems with any other linux distro, Suse, Redhat... or Freebsd

---

### Post by sgb77 on 2010-02-18
General error filesystems
A maintenance shell will now be started
Control-D shell wil terminate this shell and retry
root@myhost# could not access PID file for nmbd
exit
mountall start/starting
swapon:/dev/disk/by_uuid/2845d5e5-172f-424f836e-53e79d06479b:swapon failed:
Device or resource busy
mount all: swapon /dev/disk/by-uuid/2845d5e5-172f-424f836e-53e79d06479b terminated with status 255
mount all: Problem with activating swap: /dev/disk/by-uuid/28
fsck from util-linux-ng 2.16
/dev/mapper/home_Vg-home_Lv has been mounted 21 times without being checked, checked forced
Filesystem checks are in progress (esc to cancel)
[------------------------------------------------------------]
mount all: Cancelled
/dev/mapper/home_Vg-home_Lv: e2fsck cancelled
fsck.ext4: Inode bitmap not loaded while setting block group checksum info.
mount all: fsck/home [858] terminated with status 8
mount all: General fsck error.

---

### Post by sgb77 on 2010-02-18
Does someone has any ideas how to fix this problem? :cry:

Thanks for any help, beforehand.

---

### Post by Vegan on 2010-02-18
First off, never use fsck on a live run as it will trash you disk.

So you will have to wipe your disk and start over. IF there is a problem, use the single user mode for disk repair.

for example

```
sudo touch /forcefsck
```

as this will check you disk safely.

So start over and get some books on Linux to help you learn more about the way of the OS.

---

### Post by sgb77 on 2010-02-18
Thanks, but this is hardly my problem, if you read up top I never got to run fsck, after rebooting, the system's default option to check the system after a certain amount of restarts kicked off, and that's when I got the error message.

---

### Post by Timothy Taylor on 2010-02-26
* moved to correct forum category *

---

### Post by Timothy Taylor on 2010-02-26
* moved to correct forum category *

---

### Post by wirelessmonkey on 2010-02-26
I don't think that /boot can be ext4, though that may not be correct anymore, it may be causing you problems.

---

### Post by Jive Turkey on 2010-02-26
My next step would be to try and check and repair the disk from a liveCD if you arent being dropped to a root shell after the failed checking process.

How old is the HDD?

---

### Post by BobVila on 2010-02-26
> **wirelessmonkey said:**
> I don't think that /boot can be ext4, though that may not be correct anymore, it may be causing you problems.

I've got /boot on ext4 on a few machines... don't think that's causing his problems.

---

### Post by Vegan on 2010-02-26
/boot is by default ext2 and it should be left as ext2 as this is the standard configuration.

Messing with the low level systems is a sure fire way to trash a server.

Better to leave it alone. If you have a spare machine use that for experimentation.

---

### Post by sgb77 on 2010-02-26
Thank you guys,
I booted from a live cd and ran the fsck tool and that did the trick, but I'm not sure what to do at this point. I'm kind of nervous about migrating all my data to this system now. This is a new system, including the harddrive. Could it be that the LV is causing problems?

Thanks for all the help ;)

---

