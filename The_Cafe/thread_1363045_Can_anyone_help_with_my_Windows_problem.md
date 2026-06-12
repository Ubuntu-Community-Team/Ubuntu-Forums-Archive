---
title: "Can anyone help with my Windows problem?"
date: 2009-12-23
forum: The Cafe
---

### Post by Yes on 2009-12-23
I recently added some space to my Windows XP partition. After adding the space, I rebooted into Windows and it ran chdisk, and then rebooted. When it rebooted, it gave me the page that said that last time Windows booted there was a problem, and I can either boot into Safe Mode, Safe Mode with Networking, Safe Mode with Command Line, Last Good Configuration, or Start Windows Normally. No matter what I pick it just reboots.

I just tried putting in the install disks for XP to try repairing the installation, and "Setup is scanning your hardware" comes up for a second, then the screen goes blank and it just sits there.  

Does anyone have any idea what to do?

---

### Post by Hwæt on 2009-12-23
Make a fresh install? The only possible thing I can guess is a worm. What exactly did you do the last time you were on it?

---

### Post by autonomy on 2009-12-23
tried microsoft.com knowledge base forum?

---

### Post by murderslastcrow on 2009-12-23
Try to run a full disk check if it lets you go into safe mode. You should be able to do this by right clicking the drive you need to check and going to disk cleanup, a disk check option should be present. You can also Run cmd to bring up a command line and do it from there. In my experience, Windows generally needs to do one or two different disk checks.

Also, it may be worth while to attempt to defragment the drive. If neither of these options work, it would save a lot of trouble to simply back up your data and reinstall Windows.

This is why Windows needs to use a better file system at the very least. Obnoxious to work with.

Tell us your progress. Also, it may be a good idea to go to a Windows-based forum, since a lot of us haven't used Windows for anything in years.

---

### Post by murderslastcrow on 2009-12-23
P.S. This might do better in a support category of the forum, also.

---

### Post by Yes on 2009-12-24
It's not a worm.  I don't go online in that install so I don't see how I would have gotten it.

I'd really rather not reinstall.

I can't boot at all, even in safe mode.

---

### Post by pwnst*r on 2009-12-24
what did you use to add more space?

---

### Post by Mike'sHardLinux on 2009-12-24
Exactly how did you "add space" to your partition? What tool did you use? I suspect you used Disk Management in Computer Management console??

---

### Post by Yes on 2009-12-24
I used a GParted live CD.  It said everything went fine, and the Arch partitions which I took the space from are fine so I assume the partitioning didn't screw something up.

---

### Post by alzie on 2009-12-24
Just a thought... did you change the file system to NTFS (or FAT) when you changed the partition size.  I can see this giving Windows the willies.

You might be able to check with the GParted disc?

---

### Post by lisati on 2009-12-24
Hmmmmm.... no great flash of inspiration here. Does it do anything interesting when you choose "Start Windows normally"??????

---

### Post by s3a on 2009-12-24
What about using gparted to repair errors on the drive (if any)?

---

### Post by Yes on 2009-12-24
It was NTFS before I resized it, and it's NTFS now.

"Start Windows normally" just reboots, like all the other options.

[s]I guess I'll try fixing errors with GParted now.[/s]

I checked the partition in GParted and rebooted, same thing.

e:  Actually I was wrong, I had booted it after I resized it.  I installed Half-Life 2, played a bit, and then rebooted into Linux.  Something must have happened so when I booted this last time to Windows something was screwed up.

Could it be the system clock?  I had to run fsck on my Linux partitions because the system clock got messed up and the partitions all had last write times in the future.  Would that have something to do with it, and how would I fix that?

Thanks for all the responses :)

---

### Post by cascade9 on 2009-12-24
I think I know the issue here. 

> One of the more advanced options for resizing your Windows Vista partition is to use the GParted Live CD, a bootable linux CD that takes you straight into GParted, the great linux utility for managing partitions. The problem is that if you resize your boot/system partition, you will be completely unable to boot without repairing windows.

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

Yes yes, it says 'vista' but I'm pretty sure its an issue with XP as well. 

To fix this....boot your original winXP CD. 

When you get the 'setup' screen, select 'setup windows XP' now option. (do NOT select the 'To repair a windows XP installation using the recovery console' option.) 

F8 past the EULA screen. 

Then when you get the the next screen after that one (so many screens! so blue!) select the 'to repair the selected windows XP installation, press r' (obviously, press r) 

If you only get the 'continue installing windows XP' option at this screen, then your data on your partition or drive is too corrupted for windows to repair.

---

### Post by Yes on 2009-12-24
The problem is when I stick the orignal install CDs it doesn't do anything - just says something about scanning hardware and then goes blank.

---

### Post by running_rabbit07 on 2009-12-24
> **cascade9 said:**
> Yes yes, it says 'vista' but I'm pretty sure its an issue with XP as well. 

Vista has problems when using Norton Partition Magic also, but XP is happy with it. 

Could the hardrive be taking a dump? Does BIOS menu come up?

---

### Post by amitabhishek on 2009-12-24
Did you try:

```
ntfsfix
```

from the gparted LiveCD (in the terminal window). It fixes some NTFS errors. Another option, boot the windows "recovery console" (that is command line) and run from there chkdsk /p. Normally, you would enter to the recovery console mode from the xp installation cd (booting from it).

---

### Post by cascade9 on 2009-12-24
> **Yes said:**
> The problem is when I stick the orignal install CDs it doesn't do anything - just says something about scanning hardware and then goes blank.

so its booting from CD, then goes into the blue screen with "windows setup" at the top and "press F6 to install a thrid party SCSI or RAID driver...." at the bottom, then it all goes black after that?

---

### Post by running_rabbit07 on 2009-12-24
When you start up, is the hard drive trying to work?

---

### Post by Exodist on 2009-12-24
Some how you killed your hard drives master boot record. It cant find a boot loader so it just reboots over and over.

If windows didnt fix the boot loader your gonna have to install GRUB back onto the drive. Not sure if Ubuntu has a repair utility. Other distros do tho.

EDIT: Dont feel bad, I have killed mine two or three times before like this. :)

---

### Post by Yes on 2009-12-24
My MBR is fine - all my Linux installs boot up fine so it's nothing to do with my hard drive.

When I put in the recovery CDs, the text "Setup is inspecting your hardware configuration" flashes for a second, and then it goes blank.  No startup screen or anything.

I can't boot into the recovery console.  Every single boot option from the hard drive reboots as soon as I select it, and the CDs don't work.

---

### Post by cascade9 on 2009-12-25
You really dont want to use recovery console with windows unless you really know what your doing. 

Automated recovery has worked fine the few times I've used it.  

It is possible that your WinXP discs are dodgy...that about all I can think off to be honest. (I'd suggest just reinstalling winXP but since you cant get anywhere with your current install discs thats obviously not going to fly....) Maybe try to *cough* borrow a different install disc from somewhere on the net? Or even from a friend 

Dont worry, windows install discs are not 'who wants to be a millionaire', you can make more than 1 phone call, and it doesnt have to be done in, er, 60 seconds? :mrgreen:

---

### Post by Exodist on 2009-12-25
> **cascade9 said:**
> You really dont want to use recovery console with windows unless you really know what your doing. 

Automated recovery has worked fine the few times I've used it.  

It is possible that your WinXP discs are dodgy...that about all I can think off to be honest. (I'd suggest just reinstalling winXP but since you cant get anywhere with your current install discs thats obviously not going to fly....) Maybe try to *cough* borrow a different install disc from somewhere on the net? Or even from a friend 

Dont worry, windows install discs are not 'who wants to be a millionaire', you can make more than 1 phone call, and it doesnt have to be done in, er, 60 seconds? :mrgreen:

If it is your disc you can get replacement (Alternate Media) disc from MS for $9.95. So if you got a regular 32bit XP or Vista you can purchase a 64bit disc with the most recent service packs.  I had purchased Vista32bit when it came out, just 2 weeks ago I purchased replacement disc using my original key code and got a new 32bit and 64bit disc in the mail both with service pack 2. Cost was only $9.95 and 10 days wait. You can request faster shipping for like $5 more if I remember correctly. Just FYI.

---

