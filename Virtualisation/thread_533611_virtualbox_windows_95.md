---
title: "virtualbox windows 95?"
date: 2007-08-24
forum: Virtualisation
---

### Post by proalan on 2007-08-24
I stumbled upon my windows 95 disk recently. Knowing full well that windows 95 wouldn't run on modern hardware I thought, lets give this a go in virtual machine. 

I've not had any successes with it so far but I was wondering if anyone else has managed to get it working.

Why do this? 
Just for pure nostalgia, it was the first operating system on the first pc i had 11 years ago.

---

### Post by init1 on 2007-08-24
> **proalan said:**
> I stumbled upon my windows 95 disk recently. Knowing full well that windows 95 wouldn't run on modern hardware I thought, lets give this a go in virtual machine. 

I've not had any successes with it so far but I was wondering if anyone else has managed to get it working.

Why do this? 
Just for pure nostalgia, it was the first operating system on the first pc i had 11 years ago.
> windows 95 wouldn't run on modern hardware
What makes you think that? Windows 2.x runs on my laptop.

---

### Post by wolfen69 on 2007-08-24
if your gonna install 95, install it on the right computer. it's not hard to get ahold of pentium1's and 2's.

---

### Post by angryfirelord on 2007-08-25
What specific errors were you getting?

---

### Post by Pouncer1_1 on 2008-02-13
i managed to get 95-98-xp-vista going in vbox, with 95 you have to get the boot disks first, then since 95 doesnt recognize your cdrom drive you have to load up a virtual fat partition in xp, copy the disk files from the install cd, then go back and attach it to 95, boot 95 with floppy, then change your directory to the c:\ drive and run setup, you can delete the install files later, the only problems i am having are with video  drivers, its only 16 colors atm but still runs fine.  the first ever 95 machine with 512 of ram:popcorn:

---

### Post by K.Mandla on 2008-02-14
Moved to Virtualization.

---

### Post by Pouncer1_1 on 2009-05-31
1. collect floppy images
2. created a virtual FAT16 drive (2gb)
3. collect an iso of win 95
4. construct a windows xp VB with the FAT 16 drive mounted.
5. copy the win 95 cd contents to the FAT 16 drive.
6. create a win 95 vb with the FAT16 drive containing the win95 contents.
7. boot with floppy DOS disk.
8. cd c:\ then run setup.exe
9. set up as you like.

---

### Post by Tabo58 on 2010-10-03
I recently installed win95 on a dual core amd 64 system running Ubuntu 10.04  kernel 2.6.32-24. 

Fairly simple to install and quick. Only issue I have with the install,  I can only boot into safe mode. When trying to boot into normal mode I get a "Windows protection error. You must reboot your computer".

Needless to say, rebooting the VB or the whole system never resolves this issue. and I have no cd-rom support for the windows VBox.  

I was hoping to return to playing an old game I really enjoyed,  Command Aces of The Deep.  but so far no joy

---

### Post by damo12 on 2011-10-17
Hi Tabo58,

Not sure if you're still having this problem but the answer is to limit your RAM to 512Mb or less and to disable acceleration in the "System" settings.

you can find some other useful hints and tips at [https://forums.virtualbox.org/viewtopic.php?t=9918]("https://forums.virtualbox.org/viewtopic.php?t=9918")

---

### Post by adam worth on 2012-02-06
Hey!Don't really have a solution for you. The last time I have seen Windows 95 was on a Pentium I. Anyway...just wanted to say that your nostalgia is shared. Personally I miss Wiondows 98..and a lot of games from that period. I just got Heroes III working on my Windows 7 and I related to your post. 
Have a great day!
_____________________
Adam Worth
[best gaming laptop 2012]("http://www.best-gaminglaptop.net/best-gaming-laptop-in-2012/")

---

### Post by robsoles on 2012-02-06
> **proalan said:**
> ... I was wondering if anyone else has managed to get it working.I have startable VMs under virtualbox in 10.04 with Windows 3.11, 95 & XP.

Short answer: Yes.

Please elaborate what problem you are encountering in trying to install???

---

### Post by japzone on 2012-02-06
And you guys dug up a 4 year old topic... Why?

---

### Post by robsoles on 2012-02-06
Not clever enough to read the post date on the OP this time :roll: :face-palm:

---

