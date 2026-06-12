---
title: "Windows XP troubles"
date: 2008-10-19
forum: Windows
---

### Post by NintendoTogepi on 2008-10-19
My mother's computer has been messed up for a while now. 

When you try and turn it on, it goes to this screen asking whether to boot it in 

Safe Mode
Safe Mode (Networking)
Safe Mode (Command Line)

Last Successful Configurations and Settings

Start Normally

None of the five settings work. It takes it to the Windows progress bar and then freezes.

This started about 3 or 4 months ago. Somehow, 3 or 4 times, we got it to boot. I have no idea how. She never turned it off, except for the times when we had to and then it took a while to get it working.

Anyway, so she hadn't turned it off in about a month or so, only standby, and today it did a hard freeze and had to be shut off. (the improper way)

Now we're going through the screens and it just won't work. It freezes at the progress bar every time.

How to fix this? Do you know how?

What would cause it?

A. Virus
B. Hardware troubles
C. Microsoft coding Windows XP poorly

Also, incase we cannot get it working, what's a good "Recovery" Linux distro so we can back up all of her files and documents?

---

### Post by CouchMaster on 2008-10-19
Most Linux live CD's will read the NTFS file system and allow you transfer files to a second HD, thumbdrive, burn them to a CD etc.
Sounds like you have a bunch of viruses and/or a corrupt OS.
Time to reinstall Windows - you might be able to run one of those online "HouseCall" virus scanners, via Linux, and clear things up though.  It's worth a try.

---

### Post by NintendoTogepi on 2008-10-19
Puppy Linux won't work and we lost the Windows XP disc. (the computer is 7 years old)

---

### Post by CouchMaster on 2008-10-20
Golly Gee!
You need a full blown Linux distro to do what you need done - or maybe one made just for that purpose; like Knoppix, or maybe this [http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)

---

### Post by NintendoTogepi on 2008-10-20
Ubuntu wouldn't work either.

But we got it working an hour ago somehow :confused:

---

### Post by Kevbert on 2008-10-20
How much memory does the computer have ?  Firstly I'd run the Ubuntu Live CD and perform an extensive memory test using memtest in the CD boot menu. It you have any errors then you need to sort this out prior to installing any new operating system.
Depending on the amount of memory will determine what OS you can install. Using Xubuntu may be a good option, but if Puppy Linux doesn't work then you'll need to use something even slimmer like Slax.

---

### Post by guitsy on 2008-10-20
its time to change ur motherboard/memory.before that pls remove ur mem and put it back in the slot again,pls remove and reconnect ur motherboard and harddisk powerpin again.now power on.sometimes tthis might help . 
if u want to check a linux distro, check out puppy4(90mb).is very very fast in  older machine when compared to any other os .:guitar:

---

### Post by Viranh on 2008-10-21
In "Command Line" mode you should be able to watch the drivers load and see where it freezes, although I'm not sure how to fix it without a disk for a repair install or being able to get it to boot. 

If you can get it to boot:
Run chkdsk- to check for bad sectors and errors on your hard drive
Run sfc -sfc normally requires a disk, but this website explains how to set it up not to. [http://www.updatexp.com/scannow-sfc.html](http://www.updatexp.com/scannow-sfc.html)
However, you still need some files on a windows disk. Any Windows XP disk should work. You could borrow one, or if you can't find one, I might be able to copy these files and send them to you somehow.
Try online virus scanners from other companies. I have good luck with Kaspersky and NOD32.
Norton makes a bootable virus scanner that can check for viruses and fix them without running Windows and it is supposed to be more successful.

I can't really help much on a live cd suggestion. Knoppix and Ubuntu have worked well for me, but it doesn't sound like they're suitable for your hardware.

Good luck.

---

### Post by NintendoTogepi on 2008-10-22
The hardware is good, btw...a GB of RAM and an okay processor...

---

### Post by fjf on 2008-10-25
Boot from a live CD (ubuntu will do) just to see if the hardware is working of it is toasted.

---

