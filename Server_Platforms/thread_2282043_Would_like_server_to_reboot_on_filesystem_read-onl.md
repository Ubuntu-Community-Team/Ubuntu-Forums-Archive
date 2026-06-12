---
title: "Would like server to reboot on filesystem read-only"
date: 2015-06-11
forum: Server Platforms
---

### Post by Seawhy on 2015-06-11
We have a server that has become somewhat unstable lately. The problem is that the server periodically drops the root filesystem into read-only mode, which does us no good. I would prefer the server to just reboot itself when this happens. I can deal with a few minutes of downtime if the server has to reboot, but having to call the co-location people, wait on hold, wait for them to go push the reset button, etc, is another story.

Is this possible?

---

### Post by TheFu on 2015-06-11
Yes, but you have a very serious issue and need to determine the root cause of the issue ASAP. Data corruption is never good and if you don't have it yet, it is coming shortly.

**In the near term, MOVE TO A DIFFERENT PHYSICAL SERVER!!!!!!!!!!** Soon. Today.  Now. Immediately.

This is bad.

---

### Post by Seawhy on 2015-06-11
We think the problem might be a difference between the raid card's firmware (it's ancient) and the driver built in to the newer kernels.

My understanding of the reason that the filesystem drops to read-only mode is to protect the filesystem from corruption. But once it's in read-only mode, the only thing we can do is reboot it by phoning the hosting company and having them reboot it.

It would be better for us if the system just rebooted itself.

Moving to a different physical server would be a long process. We have a lot of data on this machine, and don't have another physical server ready for immediate deployment. It would be much easier if this server were virtual, but it isn't.

---

### Post by SeijiSensei on 2015-06-11
Short-run solution would be to run a cron job as root that would check if the file system is writable, and if not, reboot:
```

* * * * * [ "$(mount | grep /dev/sda1 | grep '(ro')" != "" ] && reboot

```
Replace "sda1" with the partition where your root filesystem resides.  That checks the mount every minute.

But I agree with TheFu, you should fix the hardware problem soon.  Another short-term option would be to install the system on a USB key drive and boot from that, mounting any other partitions you need like /home from the hard drive.

---

### Post by LHammonds on 2015-06-11
Just curious, is your entire system on a single partition or did you separate it?  If you don't know what I mean, check my sig on how I install Ubuntu Server.  A section describes how to put key areas on their own partition which helps isolate issues in one from the other.  Most importantly, keeping other systems/apps from using and filling the root system which can put a damper on your day.

LHammonds

---

### Post by Seawhy on 2015-06-11
Unfortunately, when the server was originally built years ago, we went with the defaults. The entire system is on one partiton, boot is on another, and swap is on another.

I'm not aware of any way of changing it once a server is in production.

---

### Post by mastablasta on 2015-06-12
system could drop to read only if disk has errors. you actually risk loosing all your data on the disks by not replacing the disk(s). 

also what's the point of having RAID if you can't replace a disk in the array. I mean that's what RAID stands for (redundant disk array). it's not a backup.

---

