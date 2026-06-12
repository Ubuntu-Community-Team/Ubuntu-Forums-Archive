---
title: "[SOLVED] Zenwalk LILO help"
date: 2008-06-15
forum: Slackware and derivatives
---

### Post by timzak on 2008-06-15
Hi all,

Apparently I borked my Zenwalk install.  I've only used Ubuntu before, so I am unfamiliar with LILO. A bit of background:

System had Ubuntu 7.10 on it, no other OS. I copied my data to hdd2 formatted as ext3. I formatted hdd1 (where Ubuntu was installed) as xfs and installed / and /home there (keeping hdd2 as ext3 since it was holding my data files). Picked "simple" during LILO setup in Zenwalk install process. After install completed, I booted and was given a grub error 17. I thought formatting the drive and installing LILO would wipe out grub? Any help greatly appreciated. I don't want to have to reinstall the entire OS again.

Thanks.

---

### Post by saulgoode on 2008-06-15
***EDIT: Sorry. I spaced and thought you were asking about Slackware. The following procedure might work for Zenwalk, but you will need to substitute the name of the Zenwalk kernel image for "hugesmp.s" in the boot command.***

Insert your Slackware CD #1 and boot. When you get to the "boot:" prompt, use the command "hugesmp.s root=/dev/hdd1 rdinit= ro" (no quotes). This should boot you into your installed Slackware system so that your can fix LILO. 

Log in as root, and then perform "lilo -M" to replace the Grub setup in the Master Boot Record with a Lilo bootloader. You should be able to remove the CD and reboot into Slackware. 

If that doesn't work, I would recommend boot into Slackware (again, using the CD), log in as root, and then run "liloconfig". After running liloconfig, remember to run "lilo -M" to install your changes.

---

### Post by timzak on 2008-06-16
Someone at the zenwalk forums suggested I boot up with the Zenwalk Live CD and there is a LILO fix utility to run from there.  I will try that first.  It almost seems easier to try to reinstall the OS than try to troubleshoot this sort of problem.  

Thanks for trying to help.

---

### Post by cardinals_fan on 2008-06-16
I recommend booting up Puppy and using the included GRUB installer.  LILO is evil.

---

### Post by timzak on 2008-06-16
I honestly don't have enough experience w/LILO to have an opinion of it.  What do you not like about it?

---

### Post by cardinals_fan on 2008-06-16
> **timzak said:**
> I honestly don't have enough experience w/LILO to have an opinion of it.  What do you not like about it?
Editing the lilo.conf file always feels like a chore to me, while it's simple to fix up a menu.lst for GRUB.  And Puppy's GRUB installer is very good at picking up almost any OS.

---

### Post by timzak on 2008-06-17
Alright, this is odd.  I tried the ZenLive CD's LILO fix app and that didn't work.  So I booted into gparted liveCD and deleted all partitions on both hard drives in the computer to start with a clean slate.  From there, I reinstall Zenwalk 5.2, selected autoinstall, selected simple LILO setup, finished install, and when I rebooted, I STILL got a grub error 17!  Any more ideas?

---

### Post by cardinals_fan on 2008-06-17
> **timzak said:**
> Alright, this is odd.  I tried the ZenLive CD's LILO fix app and that didn't work.  So I booted into gparted liveCD and deleted all partitions on both hard drives in the computer to start with a clean slate.  From there, I reinstall Zenwalk 5.2, selected autoinstall, selected simple LILO setup, finished install, and when I rebooted, I STILL got a grub error 17!  Any more ideas?
WHAT?!?! You're getting a **_GRUB_** error 17 with LILO?!  I'm confused... :confused:

---

### Post by Antman on 2008-06-17
> **cardinals_fan said:**
> WHAT?!?! You're getting a **_GRUB_** error 17 with LILO?!  I'm confused... :confused:
That used to happen to me when I would install Zenwalk 5.0. But I would just install again and manually partition the drive (using the Zenwalk disk) and then do the autolilo install and it would be ok. I haven't had this issue with 5.2 though. But than again, I always do the manual partition option within Zenwalk.

I'm surprised that the LiloFix on the Zenwalk Live CD didn't fix the issue:confused:

---

### Post by timzak on 2008-06-17
Sorry, guys.  I found the problem.  Somehow, the 2nd hdd (the one holding my data, not the OS) got grub on it.  You can see why I'd keep getting the grub error 17...

Once I disabled the 2nd hdd, I was able to load ZW 5.2 without problems.  I ended up reinstalling ZW probably half a dozen times through the trouble-shooting process. I also tried the ZenLive CD, Puppy CD, a bunch of suggestions from here and the Zen forums.  Nothing worked.  Now we know why.  :oops:

I apologize for wasting everyone's time with this.  Hopefully someone else will come along this thread someday and benefit from it.

Anyhow, I ended up keeping LILO because once I figured it out, I was done with tinkering.  Maybe another day I will replace LILO w/grub.

Thanks again.

---

