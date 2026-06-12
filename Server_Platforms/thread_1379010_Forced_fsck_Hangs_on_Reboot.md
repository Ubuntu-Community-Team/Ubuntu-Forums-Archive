---
title: "Forced fsck Hangs on Reboot"
date: 2010-01-12
forum: Server Platforms
---

### Post by jcsuperstar on 2010-01-12
I am running 9.04 Server (standalone). It had been running fine since I installed in last autumn. Upon reboot, fsck of the root filesystem was forced and it hangs at the same point (16.5%) every time. I was able to break out somehow with cntl-alt-del but the boot was to a read-only filesystem. So I couldn't disable the forced fsck. Instead, I tried to fsck there. It started, but hung. I couldn't do e2fsck -v as it needed the device and, although I worked on UNIX systems for decades, I am not familiar with the /dev/mapper stuff.
 
Looking at other threads, all involving the desktop GUI Ubuntu, I tried some of the suggestions. Went into the BIOS to see what I could disable. I killed the serial port and similar. (Some said that onboard modems interfered with the checks in /dev.) I also tried to boot from my original installation disk. That does work.
 
The suggestion is to choose "Try without any change to your computer". The problem is that is not available on the server installation, apparently only the desktop (GUI). I had install, check CD for defects, test memory, boot from first hard disk, and something like repair or recover a broken disk. I started the last of them, as it seemed to be the only option. It failed because it couldn't get a dhcp address. I could manually configure it (as it is hard addressed anyway), but I didn't want to start screwing up configurations not knowing where it was going, whayt it would ry to do, and risk losing months of hard work.
 
Without help, I think I will be forced to install the OS on a second drive, use that install to fsck the original filesystem on the original disk, edit the fstab (or whichever has the config) on the original disk to disable fsck, and return to the original boot. Any ideas would be greatly appreciated. I am building this server for a nonprofit and have put in many hours writing mysql/perl apache cgi code for them as a free service and hate to lose it all and set back everything. I thank anyone, in advance, for whatever help they can offer.

---

### Post by jcsuperstar on 2010-01-12
This time the fsck completed.  It would still be nice to know what, if anything, is suggested to set up a working environment if boot should fail in the future.  Is there a way to do this from the server installation CD or can I write a boot CD for doing repairs?  These are things I obviously should have looked into before I started it all.  After all, I think I have had to do these sorts of things on practically every UNIX and UNIX-ish OS I've been on in the past.

---

### Post by Vegan on 2010-01-12
Might be time for a new hard disk and a fresh install of 9.10 which now supports ext4 which might be a bit less flaky.

---

