---
title: "Killing infected Windows XP partition"
date: 2009-01-05
forum: Security
---

### Post by mdgibson on 2009-01-05
I'm running a dual-boot Ubuntu/XP machine and the XP partition is infected with Netsky. (I was running fully-patched Firefox, but stupidly under an admin account.) If I format the XP partition will the machine be clean? Can I safely copy a few MS Word files from the XP partition before formatting? I'm worried the thing could have infected GRUB or Ubuntu somehow. I wouldn't have thought a Windows virus would run under Ubuntu, but the last few times I logged out of Ubuntu I got an "Application still running" message and that has made me paranoid. (There's nothing suspicious showing in the system monitor, but I imagine that's no guarantee there isn't a bad process lurking.)

This is my first time posting a question, so hopefully I've included all the pertinent info. 32-bit Ubuntu, fully patched. XP and Ubuntu partions are on separate disks, with GRUB on the XP disk.

---

### Post by albinootje on 2009-01-05
> **mdgibson said:**
> I'm running a dual-boot Ubuntu/XP machine and the XP partition is infected with Netsky. (I was running fully-patched Firefox, but stupidly under an admin account.) If I format the XP partition will the machine be clean? 

Yes, unless that virus managed to infect the MBR.

---

### Post by jamesrl on 2009-01-05
partitioning should work ... i didn't see anythign about netsky infecting the master boot record.  However, you can probably remove it simpler with (that is unless you were just planning on getting rid of windows and switching to linux only):

[http://www.symantec.com/security_response/writeup.jsp?docid=2004-021816-1759-99](http://www.symantec.com/security_response/writeup.jsp?docid=2004-021816-1759-99)

---

### Post by mdgibson on 2009-01-05
Is there any way to check whether the MBR is infected?

---

### Post by Skripka on 2009-01-05
> **mdgibson said:**
> I'm running a dual-boot Ubuntu/XP machine and the XP partition is infected with Netsky. (I was running fully-patched Firefox, but stupidly under an admin account.) If I format the XP partition will the machine be clean? Can I safely copy a few MS Word files from the XP partition before formatting? I'm worried the thing could have infected GRUB or Ubuntu somehow. I wouldn't have thought a Windows virus would run under Ubuntu, but the last few times I logged out of Ubuntu I got an "Application still running" message and that has made me paranoid. (There's nothing suspicious showing in the system monitor, but I imagine that's no guarantee there isn't a bad process lurking.)

This is my first time posting a question, so hopefully I've included all the pertinent info. 32-bit Ubuntu, fully patched. XP and Ubuntu partions are on separate disks, with GRUB on the XP disk.

How did you set up GRUB?  and your 2 OSes and 2 disks?


There are several ways to go about it:  

The default is to just add GRUB to the Windows MBR.  This is not wise-as if the MBR gets nuked in repartitioning a separate Win drive--you can no longer boot Ubuntu.  This is bad because if you bork the MBR you're out 2 OSes, and have to restore the MBR and GRUB before you can boot your sys.

OR

You put GRUB on the Ubuntu drive, and didn't do anything to the MBR.  This is wise because no matter what bad things happen to either boot loader-you still have on working OS.


Which did you do.  Do NOT be quick to repartition the Windows drive!

---

### Post by albinootje on 2009-01-05
> **mdgibson said:**
> Is there any way to check whether the MBR is infected?

You should look up whether this Netsky virus can do that or not, you should also find out whether it is really only infected by that virus or more.
Different anti-virus tools sometimes find different things.

You can know more by using Clamtk in Ubuntu, but Clamtk probably only has the option to remove the infected files, not to "heal" them.
```

sudo apt-get install clamtk

```

The best would be to boot from a special bootable windows cdrom with a few anti-virus applications on that. I forgot the name of that.

---

### Post by mdgibson on 2009-01-05
If memory serves the Ubuntu installer auto-configured GRUB for me, so I'm not sure. I think I have the first (unwise) setup, with GRUB added to the Windows MBR.

---

### Post by Skripka on 2009-01-05
> **mdgibson said:**
> If memory serves the Ubuntu installer auto-configured GRUB for me, so I'm not sure. I think I have the first (unwise) setup, with GRUB added to the Windows MBR.

Depending on which SATA or IDE header your HDDS are plugged into...GRUB still might be on the Ubuntu drive and not the MBR.  There's a chance.



Easy check.  Completely power off and unplug you computer.  Pop open the case.  Physically unplug the data cable from Windows drive (leave the motherboard end plugged in).   plug your computer back in, and boot.  If GRUB appears, you can nuke your Windows drive safely.
.
.
.
If not, then you'll need to reinstall Windows, and then redo GRUB.  The later is easy-you need SuperGRUB, IIRC...the former just takes forever.

---

### Post by Skripka on 2009-01-05
> **mdgibson said:**
> If memory serves the Ubuntu installer auto-configured GRUB for me, so I'm not sure. I think I have the first (unwise) setup, with GRUB added to the Windows MBR.

After thought, hopefully not too late----Be advised with my little test-you might need to fiddle with boot orders in your BIOS to get things back to how they were if things don't boot.

---

### Post by mdgibson on 2009-01-05
Not too late. I am at work so I won't be able to try this until the evening.

---

### Post by aikiwolfie on 2009-01-05
Noramlly you don't have to worry about Windows viruses infecting Linux OSs. Windows and Linux are totally different. AVG has a free Windows and Linuxs version you can download. A[vira Personal Edition]("http://www.free-av.com/") is another good free Windows anti-virus application. It'll do root kit searches as well as standard scans. Personally I prefered it to AVG when I used Windows. If memory serves me correctly it does have a Linux version. But it's a pain to set up.

If you want to kill it by wiping Windows (always a source of great satisfaction) you can. I'd recommend you download and print off instructions for restoring Grub first though. Then boot from your Windows CD and type fixmbr. That'll write a fresh master boot record. Then nuke the Windows install with format C:

Now reinstall Windows ... if you want to and then boot froma Ubuntu CD and restore Grub.

REMEMBER TO BACK UP ALL YOUR IMPORTANT STUFF!!! If that stuffs infected you can clean it later. Just hive it off somewhere in a compressed file off of the partition you're going to format.

---

### Post by albinootje on 2009-01-05
> **Skripka said:**
> After thought, hopefully not too late----Be advised with my little test-you might need to fiddle with boot orders in your BIOS to get things back to how they were if things don't boot.

Interesting to read, but we're talking about 2 disks here.
Assuming that Ubuntu is on one disk, and Windows "is" on the other disk, then reformatting the Windows partition should not touch the MBR on *either* disk.
Since we're talking Grub here, I don't see any reason that reformatting the Windows partition could mess up the successful booting of Ubuntu.

And if the OP wants to reinstall MS-Windows, then Grub will be gone temporarily (MS Trade Marked : overwriting MBRs without asking or warning since more than 20 years) anyway. :)

---

### Post by mdgibson on 2009-01-05
Haha. I know what you mean about Windows overwriting the MBR without asking, as I had that happen once. I'm pretty strongly inclined to move the few documents I care about over to the Linux partition, then nuke the Windows one and reformat it for Linux (actually I don't know the name of the Ubuntu file system, now that I think about it).

---

### Post by masque7 on 2009-01-05
> **mdgibson said:**
> reformat it for Linux (actually I don't know the name of the Ubuntu file system, now that I think about it).
Ext3

You can use [gparted](http://gparted.sourceforge.net/), which is very simple to use, to resize your current Linux partition to whatever you like.

Gparted comes with Ubuntu I think - I'd recommended burning it to a disc and booting up from it. There are many other partition tools you can use.

---

