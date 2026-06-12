---
title: "File System Could not be mounted"
date: 2010-07-31
forum: Server Platforms
---

### Post by ptmuldoon on 2010-07-31
I'm a newbie at ubuntu, but am slowly picking it up.  And things were going so well until this error just popped up on me.

I've installed the latest Ubuntu Server 32 bit on to VIA NSD7800 (has 8 sata swappable drive).

I followed this guide here to get up and running:
[http://www.smallnetbuilder.com/nas/nas-howto/30573-build-your-own-atom-based-nas-part-2](http://www.smallnetbuilder.com/nas/nas-howto/30573-build-your-own-atom-based-nas-part-2)

I did alter off the guide to the point where I have drives with existing data on them.  Thus, didn't format them into ext3.

These drives are coming with data on them in the ext2 format used by NasLite.

I had mounted the drives under ext2, set up samba, and was able to navigate the drives, and add/delete files off the mounted drives.

I than did a reboot of the system, and am now getting the error the drives can't be mounted, and system seems to stop its boot up process.

I'm going to pull the drives out to see what may happen on another reboot.

But any ideas?

Thanks
PT

---

### Post by HermanAB on 2010-07-31
Howdy,

Learn how to read the log files.

$ dmesg

$ sudo tail -n 1000 /var/log/messages

and so on.

---

