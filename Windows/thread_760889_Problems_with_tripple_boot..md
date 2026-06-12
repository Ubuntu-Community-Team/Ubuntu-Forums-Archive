---
title: "Problems with tripple boot."
date: 2008-04-20
forum: Windows
---

### Post by jrharvey on 2008-04-20
Ok so my computer came with Vista and i dual booted with ubuntu shortly after i recieved it. Its been a while and i am so fed up with vista and its crap so i want to install xp on a third partition. Right now i have 1 partition for vista, 1 for ubuntu and 1 vista recovery partition. Below is the problem i run into when i try to install xp. This is basically what i get when i get to the partition editor of the xp setup. 



```

This portion of the Setup program prepares Microsoft(R) Windows(R) XP to run on your computer.

-To set up Windows XP now, Press Enter.
-To repair a Windows XP installation using Recovery Console, press R.
-To quit Setup without installing Windows XP, press F3.


If I hit ENTER, this is what it says:

The following list shows the existing partitions and unpartitioned space on this computer.

Use the UP and DOWN ARROW keys to select an item in the list.

-To set up Windows XP on the selected item, press ENTER.
-To create a partition in the unpartitioned space, press C.
-To delete the selected partition, press D.

Unknown Disk
(There is no disk in this drive.)
Unknown Disk
(There is no disk in this drive.)
Unknown Disk
(There is no disk in this drive.)
Unknown Disk
(There is no disk in this drive.)



if I hit D to delete the partitions(?), a blue screen pops up showing this:

A problem has been detected and Windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this Stop error screen, restart this computer......

etc...etc... (I'm sure you know what this screen says)

Technical information:

*** STOP: 0x0000008E (0xc0000005, 0xf7418cad, 0xf6fd57e4, 0x00000000)
*** setupdd.sys - Address f7418cad base at f73ec000, DateStamp 41107c8f

    * 3 weeks ago
```

I know this is an ubuntu forum but linux guys seem to always know better than anyone else and they arent biased about why you would want to trpple boot. Oh and I did contact microsoft but they basically told me there was no reason to install xp and that i shouldnt waste my time.

---

### Post by smoker on 2008-04-20
i could be wrong, but i suspect you will have to format the partition you want to install xp on, and make the partition primary and active. i know the xp install disk should do this, but it's crap.

easiest way to do this would be with the gparted live-cd, ( [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) ) or maybe the partitioner on the ubuntu live-cd will do it. you could also maybe ready the partition through 'disk management' in vista, though i'm not that familiar with vista. a win98 boot floppy, using fdisk and format would be fine also,

> Oh and I did contact microsoft but they basically told me there was no reason to install xp and that i shouldnt waste my time.Hmm, great customer service!

best of luck

---

### Post by jrharvey on 2008-04-21
I have already readied a partition from the gparted. Im whats going on but its saying the same thing when i try to install xp on my laptop (xps 1530). I have 2 xp cds and neither one work.

---

### Post by smoker on 2008-04-21
i suspect it may be the cds, are they actual microsoft xp install cds, or are they oem install/recovery disks? some oems customize their disks so they will be unable to install on other makes of computer, or perhaps they are just faulty.

can you possibly borrow a working disk from a friend, if only to disprove faulty disks?

---

### Post by jrharvey on 2008-04-21
its not the disk. I have tried 6 different cds (All types). the vista setup recognizes them all for some reason and so does ubuntu.

---

### Post by smoker on 2008-04-21
hi, only other thing i can think off at this moment, is it a sata drive on your pc and laptop? if so, you may have to press f6 shortly after windows install starts and load a driver to enable xp to recognize the sata drive. the driver is usually included with the motherboard driver cd, along with installation instructions, but if not, try the motherboard manufacturers support website where you should be able to download them along with install directions.

it could also be a ram issue, based on the error code: [http://support.microsoft.com/kb/315335](http://support.microsoft.com/kb/315335) maybe check the ram if you can,

---

