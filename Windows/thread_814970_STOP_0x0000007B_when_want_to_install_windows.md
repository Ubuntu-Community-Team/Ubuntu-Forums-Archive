---
title: "STOP: 0x0000007B when want to install windows"
date: 2008-06-01
forum: Windows
---

### Post by reyhan on 2008-06-01
hey i want to install windows xp on my old harddisk but why 
is i got this error messeges 

if i not wrong

> "Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it's properly configured and terminated. Run CHKDSK /F to check for hard drive corruption and then restart your computer."

is there something wrong :confused::confused::(:(:(

---

### Post by Playa1313 on 2008-06-02
I got this same message the other day when trying to install!

I became so frustrated that I gave up on XP and just made Vista as slim as XP using a program called Vlite.

This error is really weird because it has not happened before to me.

One question: Was this on your first partition, second, third, extended?  I ask this because I had mine on an extended logical partition and am wondering if that might have been the problem.

I also found that XP completely screws up your partition table if you attempt to format with it.  Therefore I formatted with gparted.

Hope this helps - I'm interested in what you do/did because this happened to me also.

~Brian

---

### Post by r76 on 2008-06-02
As above, check what partition type you're trying to install into - make sure it's primary.  Next, is this a SATA drive, you may get that error trying to install XP on SATA drives - you need to get the drivers in there first - this happened to me last year when I wiped Vista and went to install XP on a laptop.  What I did was installed XP using ATA compatibility mode rather than AHCI for SATA (a setting in the BIOS), then installed AHCI compatibility afterwards.

For other possibilities, try [microsoft's page on the topic]("http://support.microsoft.com/kb/324103"), your vendor, or [google]("http://www.google.com/search?hl=en&client=opera&rls=en&hs=8HT&q=0x0000007B+xp&btnG=Search").

---

### Post by dca on 2008-06-02
Be careful, all MS OS' are designed to be the only OS installed on a hard drive.  Thus the long partitioning/formatting when doing new install.  In the case of a dual-boot it's easier w/ less issues if you install Windows fresh, then re-partition space to add Linux distro.  In the case of Ubuntu, if that's your second OS I believe it automatically fixes GRUB after install...

---

