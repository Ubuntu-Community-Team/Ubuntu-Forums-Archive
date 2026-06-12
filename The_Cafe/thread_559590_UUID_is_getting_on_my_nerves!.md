---
title: "UUID is getting on my nerves!"
date: 2007-09-25
forum: The Cafe
---

### Post by shane2peru on 2007-09-25
Ok, this UUID stuff is getting on my nerves!  Let me say I have little understanding of this UUID stuff, and the more I run into it, the less I want to know about it.  It has messed me up restoring my system from a .tar.bz2 file, now with the latest kernel update it left my system un-bootable.  It seems to always mess up my system in the menu.lst in my /boot/grub folder.  I had to go back in and change it from the incorrect UUID number it had inserted and put /dev/sda1 - /dev/sda1 doesn't change!!!  But with every install or every major change to the system the UUID does change.  So when I mess up my system and have to re-install and then restore my tar backup file of the system file, it really messes up the UUID numbers because my restore file has a different number than the new install has!!!  /dev/sda1 doesn't change!  It will always be /dev/sda1 for me, and not change, but this UUID changes everytime!!  ARGGGH, is there anyway to convince Ubuntu to leave the UUID stuff, or change my system to not use it?  Am I the only one fighting with this UUID stuff?

Shane

---

### Post by Kimm on 2007-09-25
> **shane2peru said:**
> Ok, this UUID stuff is getting on my nerves!  Let me say I have little understanding of this UUID stuff, and the more I run into it, the less I want to know about it.  It has messed me up restoring my system from a .tar.bz2 file, now with the latest kernel update it left my system un-bootable.  It seems to always mess up my system in the menu.lst in my /boot/grub folder.  I had to go back in and change it from the incorrect UUID number it had inserted and put /dev/sda1 - /dev/sda1 doesn't change!!!  But with every install or every major change to the system the UUID does change.  So when I mess up my system and have to re-install and then restore my tar backup file of the system file, it really messes up the UUID numbers because my restore file has a different number than the new install has!!!  /dev/sda1 doesn't change!  It will always be /dev/sda1 for me, and not change, but this UUID changes everytime!!  ARGGGH, is there anyway to convince Ubuntu to leave the UUID stuff, or change my system to not use it?  Am I the only one fighting with this UUID stuff?

Shane

Cant you change the UUID to /dev/<disk> manually? I did that to my swap and it works :)

---

### Post by igknighted on 2007-09-25
If you don't like it, don't use it.  It has some very important benefits.  Imagine if you had to boot from an external HD.  Depending on the order the drives were plugged in, your grub entries would be off each time.  By giving each drive a UUID instead of the /dev/sd** notation, you can maintain consistency.

Of course if you do stuff like rolling out a new image onto new partition, the UUID will have changed (it is specific to the partition, not the data/OS on the partition.  If you do not like UUID or have a use for it, you can easily change your fstab and menu.lst back to the /dev/sd** notation.  Also, you can give partitions labels.  This works liek UUIDs, but you can manually set them  So if you restore a .tgz of Ubuntu, you can give the new partition the same label as the previous one, thus avoiding the UUID conundrum.

I hope this helps... I personally despise UUIDs as well, but they do have their uses.  I wish Ubuntu would use labels instead as they accomplish the same thing but are easier to work with, but w/e.

---

### Post by shane2peru on 2007-09-25
> **igknighted said:**
> If you don't like it, don't use it.  It has some very important benefits.  Imagine if you had to boot from an external HD.  Depending on the order the drives were plugged in, your grub entries would be off each time.  By giving each drive a UUID instead of the /dev/sd** notation, you can maintain consistency.

Of course if you do stuff like rolling out a new image onto new partition, the UUID will have changed (it is specific to the partition, not the data/OS on the partition.  If you do not like UUID or have a use for it, you can easily change your fstab and menu.lst back to the /dev/sd** notation.  Also, you can give partitions labels.  This works liek UUIDs, but you can manually set them  So if you restore a .tgz of Ubuntu, you can give the new partition the same label as the previous one, thus avoiding the UUID conundrum.

I hope this helps... I personally despise UUIDs as well, but they do have their uses.  I wish Ubuntu would use labels instead as they accomplish the same thing but are easier to work with, but w/e.

Ahh, yes for USB external HD I could see where this would come in handy!  How many of us actually on a daily basis boot of an external hdd!  Yes, I can see the importance of this, however for the majority of their users why not set it so that if it is internal it is not UUID dependent.  I just personally think this is not a step forward, but a step backward for internal hdd.  I use labels for my two external hdd so that I don't get confused, I mean who is going to remember a UUID number.  Even the internet realizes that, and uses DNS instead of the ip addresses.  IP address would be similar to UUID while DNS would be a label.

If I change my fstab will that rid me of my UUID problems.  How can I get rid of UUID on my system?  How can I partition Ubuntu to get rid of UUID for internal hdds?  Thanks for the input!

Shane

---

### Post by Crashmaxx on 2007-09-25
Labels are the way to go if you don't like UUID:
[http://ubuntuforums.org/showthread.php?t=139535](http://ubuntuforums.org/showthread.php?t=139535)

I actually have a RAID 1 array, and whenever I upgrade the kernel, it puts the UUID back in menu.lst, but as soon as I remember to put back in /dev/md0, its not an issue. Just wish it would auto detect the array.

---

### Post by shane2peru on 2007-09-25
> **Crashmaxx said:**
> Labels are the way to go if you don't like UUID:
[http://ubuntuforums.org/showthread.php?t=139535](http://ubuntuforums.org/showthread.php?t=139535)

I actually have a RAID 1 array, and whenever I upgrade the kernel, it puts the UUID back in menu.lst, but as soon as I remember to put back in /dev/md0, its not an issue. Just wish it would auto detect the array.

That is exactly my point, that is not user friendliness, and will drive people away from Ubuntu.  A kernel upgrade should not cause such problems as making a system unbootable.  Mine always rewrites it incorrectly, and has several different installations.  I don't understand that, and that is my problem with UUIDs.
What does UUID stand for anyway?

Shane

---

### Post by igknighted on 2007-09-25
Wikipedia FTW... [http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)

---

### Post by shane2peru on 2007-09-25
> **igknighted said:**
> Wikipedia FTW... [http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)

Thanks igknighted.  Informative link.

Shane

---

### Post by notwen on 2007-09-25
Rest easy, as I also despise UUIDs. =]

---

### Post by Rumpty on 2007-09-29
Running Kubuntu 6.06. 

I can't get either ls -l /dev/disk/by-uuid or vol_id -u /dev/disk to give me the UUIDs of my drives. Is there something I have to install?

I also have Feisty on another drive, and that is the drive where I need to know the UUIDs. I think. After some partition changing, Feisty will not boot.

---

### Post by Wolki on 2007-09-29
> **shane2peru said:**
> Ahh, yes for USB external HD I could see where this would come in handy!  How many of us actually on a daily basis boot of an external hdd!  Yes, I can see the importance of this, however for the majority of their users why not set it so that if it is internal it is not UUID dependent.  I just personally think this is not a step forward, but a step backward for internal hdd.

USB HDDs are not the only reason. It also applies if you change the drive order internally (ok thats also a rather rare case) and one more important reason:

The Kernel system used to access hard drives is changing, PATA drives are by now often accessed with the SATA system (as it can now do both). Which to use is a decision depending on your kernel version and some other factors - I've seen someone where it changed every couple of boots. With UUIDs, the system will bootup just fine if this happens, with device names the system might not correctly boot anymore, as it looks for /dev/hdXY when it should be /dev/sdXY or the other way around.

Labels would of course also be a solution.

---

### Post by shane2peru on 2007-09-29
ok, I can see a use for them, however there are still a lot of cons that are out there.  Let's say for instance, you mess up your system, happens to all of us sometime or another, and more so for newbies that are learning (been there done that) but ahh, we were told to back up, so we did the tar method most recommended on the web.  We can't get into our system, so we wipe the disk and re-install, then over the install, we restore our nicely tared backup, and there are conflicting UUID's so the system still doesn't boot.  Well so much for a backup by tar (I just recently did this).  This is a serious problem to any new user of Ubuntu.  Perhaps it is a backup problem, maybe a restore problem, or even a UUID problem, but it is a problem no matter where you point your finger.  I think more people try and restore their system than try to do odd installs on a USB drive, or have super new equipment that requires this UUID thing.  Therefore making us all conform to the UUID idea, is not a good step in my opinion.  Yes, it may be a good step in the future, but for now, it is more of a problem than a solution.

Shane

---

### Post by Polygon on 2007-09-29
only time i had a problem with this was with the edgy to feisty upgrade i think, when the installer didnt convert my /etc/fstab to uuids. I fixed this by just running the command to generate uuids and then editing the /etc/fstab file and then it worked

---

### Post by Wolki on 2007-09-29
> **shane2peru said:**
> We can't get into our system, so we wipe the disk and re-install, then over the install, we restore our nicely tared backup

What's the point of the new install then, when you just end up with the old system again?

> I think more people try and restore their system than try to do odd installs on a USB drive, or have super new equipment that requires this UUID thing.

Mostly, it's not new hardware, but old hardware that benefits from UUIDs. New hardware is mostly SATA and always /dev/sdXY, whereas the kernel may choose either system for the old PATA hardware.

[edit]

> only time i had a problem with this was with the edgy to feisty upgrade i think, when the installer didnt convert my /etc/fstab to uuids. I fixed this by just running the command to generate uuids and then editing the /etc/fstab file and then it worked

I think only the dapper->edgy upgrade converted the device names to UUIDs. Edgy systems were supposed to have UUIDs already, either from the upgrade or from a new installation.

---

### Post by shane2peru on 2007-09-29
> **Wolki said:**
> What's the point of the new install then, when you just end up with the old system again?
Well, I guess it was because I had tried a restore and that didn't work, so I figured a re-install was in order.  I´m not exactly sure.  At any rate, neither way worked for me and I had to re-install and re-setup everything.  Again, this could be from my ignorance even after using Ubuntu and a few other distros for the past 4 years, imagine the problems for a newbie. 


> **Wolki said:**
> 
Mostly, it's not new hardware, but old hardware that benefits from UUIDs. New hardware is mostly SATA and always /dev/sdXY, whereas the kernel may choose either system for the old PATA hardware.


My bad then, I misunderstood that PATA thing as something NEW.  :lolflag:  Hey, I'm  just an average computer user venturing into Linux.

Shane

---

