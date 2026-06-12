---
title: "Windows Question"
date: 2008-02-12
forum: Windows
---

### Post by sabatron on 2008-02-12
I'm trying to re-format my brother's hard drive because it hasn't been done in about 5 years and  according to AVG, he's got about 200 infected files and it's really slowing down his compy.  He has a Gateway (integrated) and I couldn't find the original Windows XP 2000 Home edition disk (just found the cover >.>) so I grabbed my operating system disk from my e-machine (Windows XP Media Center Edition 2005) and popped it in.  When I restarted, it didn't boot from disk so I went into BIOS (pressed F2) and I did Boot>Boot Priority Device>

1st Boot Device [ATAPI CD-ROM]
2nd Boot Device [Removable Dev]
3rd Boot Device [Hard Drive]
4th Boot Device [IBA 4.1.08 Slot 0140]

That's how it was set up.  Is there something wrong with that?  I can't think of anything wrong except that the only way to re-format is to somehow find the original OS disk that came with the Gateway...but I don't know how integrated systems work.  Can I even use the e-machine Disk?

Any ideas here will help

---

### Post by taurus on 2008-02-12
Don't you have a Ubuntu LiveCD handy somewhere?  It has gparted, System -> Administration, that you can use to delete and format your harddrive.

And if you don't have Ubuntu LiveCD, you can download the GParted LiveCD then.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by sabatron on 2008-02-12
So you want me to use the LiveCD just to wipe the drive and then install Windows via e-machine disk?  I guess that's ok...but what if the e-machine disk didn't work for copyright reasons or the fact that the Gateway is integrated?  he would be left with no OS on his compy at all.  And what if the boot from disk option still doesn't work?

---

### Post by stalkingwolf on 2008-02-12
The emachines disk may be oem specific.  Many manufacturers use machine specific information.
If you cant find the disk for his machine you will have to buy a new one, either from the manufacturer 
or a MS licensed one.  Or install Ubuntu.   Remember what ever you do to make a backup of critical info.

---

### Post by frankhdz on 2008-02-12
The e machines recovery CD might not work on a gateway PC. You may have to buy another copy of windows if you cannot find the original Gateway recovery disks. On E machines the recovery software is placed on a separate partition. Check if the Gateway PC is setup the same way. See if you can find a recovery program and run a full install of the original software. 

You can try running the emachines recovery disk I doubt it will work but hey you have nothing to loose. If you do not want to buy another copy of windows then I would go with a free OS like Ubuntu. Check and make sure the hardware works with Ubuntu with a live CD first. I'm a seasoned computer user and have had an extremely tough time getting ubuntu to run properly on my machine. Do not intall it blindly or you will regret it.

---

### Post by stchman on 2008-02-12
> **sabatron said:**
> I'm trying to re-format my brother's hard drive because it hasn't been done in about 5 years and  according to AVG, he's got about 200 infected files and it's really slowing down his compy.  He has a Gateway (integrated) and I couldn't find the original Windows XP 2000 Home edition disk (just found the cover >.>) so I grabbed my operating system disk from my e-machine (Windows XP Media Center Edition 2005) and popped it in.  When I restarted, it didn't boot from disk so I went into BIOS (pressed F2) and I did Boot>Boot Priority Device>

1st Boot Device [ATAPI CD-ROM]
2nd Boot Device [Removable Dev]
3rd Boot Device [Hard Drive]
4th Boot Device [IBA 4.1.08 Slot 0140]

That's how it was set up.  Is there something wrong with that?  I can't think of anything wrong except that the only way to re-format is to somehow find the original OS disk that came with the Gateway...but I don't know how integrated systems work.  Can I even use the e-machine Disk?

Any ideas here will help

Are you wanting to install Ubuntu on his system?

You won't have to worry about viruses and spyware anymore.

---

### Post by Golem XIV on 2008-02-12
You are in a Linux user group, so it's kind of expected to get Linux - related answers.  This forum may not be the ideal place to ask the question you just did.  This being said...

Your BIOS setup looks OK, except that the removable drive entry is unnecessary for what you are trying to do.  I usually keep only the hard disk & CD boot options on, but that's me.  Remember to switch back to hard disk as first boot option when you start rebooting during the Windows  installation process.

Be careful because system recovery disks that come bundled with brand-name systems will in many cases nuke the entire drive.  A stand-alone Windows installation disk will give you the option of partitioning and/or installing into a specific partition, but the bundled disks will simply erase everything and create a " factory default" install, i.e. return the system to the state it was before you bought it (software-wise only, of course).

Also, bundled disks usually have pre-installed drivers for that system only.  I am pretty certain that the e-machines disk will NOT have the drivers you need for the system you're trying to install it on.  Some disks will even detect that the system is not the one they were designed for and will refuse to install.

The solution would be to get a retail or OEM version of XP, pre-download all drivers and burn them on a separate CD (to be installed after Windows is up and running).  These drivers should be available for download from Gateway's web site.  Then, use the Windows CD to install the system and then install the drivers from the driver CD you burned.

When you install Windows, you can install fresh over an old install (by using a different WINDOWS directory); you can try to repair the original installation or you can repartition/reformat your disk and do a "clean" install. 

A fresh install will keep your files but not your settings, drivers & software installation, you will have to install all the software packages again.  It will also keep all virus-laden dross on your system and it will create problems with badly written software (any software that, for example, has WINDOWS hard-coded as the Windows directory.  You'd be surprised at the amount of sloppily programmed crap that is out there.) 

A system repair will keep your drivers, settings, software packages and files but it will kill all downloaded updates.  This method is also fairly unsafe and leads to an unstable system.  In my experience, it should be used only as a temporary measure to recover files & folders from a non-bootable system and should be followed by a "clean" install.

Your best bet is to do a clean install, backing up all of your files first.  This is most time-consuming but it's the safest way and it gives you a stable system to work with.  You can later scan/clean/restore your files at your leisure. 

There is also the option to install Ubuntu, of course...  This *is* an Ubuntu forum, after all :)

---

### Post by Technoviking on 2008-02-12
Moved to the Windows discussion area.

---

### Post by sabatron on 2008-02-12
Thanks so much for all of these responses.  I know it's an Ubuntu forum but it's the only forum I trust with stuff like this and the response time is down right impressive.  I dug up a driver's CD that came with the Gateway and popped it in...what do you know...it let me boot from disk!  I guess that's the step I missed...because it let me delete all files and now all I have to do is pop in an OS disk...which my brother thinks he can find.  I would love to put Ubuntu on there but he has enough trouble with windows so I don't think he's quite ready for it.  Thanks again for your input!

---

### Post by frankhdz on 2008-02-12
Actually your emcahines might work. I just remembered a while back my wife's emachine computer's motherboard went out  and I had to replace it. I simply moved the disk drive to this new board and did a system restore with the restore discs. Now this board is newer it has an intel core duo CPU with onboard graphics and audio which is way different from the original. I was able to install windows (it might require activation of windows). Make sure you have the drivers for the motherboard and it should work. Good luck.

---

