---
title: "Journal - which one?"
date: 2013-02-03
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2013-02-03
Raring install for the umpteenth time, and it asks what journalling format to use on the partition - EXT3,EXT4, btrfs (? spelling) and several others.  Raring instsll didn't give me a clue what one ubuntu development thinks we should be using.

This latest install was on a USB 3.0 SSD.  I picked EXT4 out of ignorance.  Is there a list somewhere of what ubuntu says these choices are and what to use, any advantages/disadvantages.  I didn't see anything like this on AskUbuntu.

Ubuntu wiki LinuxFilesystemsExplained has some info on some types of journal, not all, but it didn't rub my nose into what I'm supposed to use for raring development test.

Thanks, I'm sure I'll be installing raring a bunch more times.

---

### Post by jfernyhough on 2013-02-04
The one you'd normally choose is Ext4. It's the best all-round filesystem at the moment, balancing speed, journalling, and stability.

Ext3 is more stable, but lacks Ext4 features.

BTRFS has the largest number of new, nice features (like TRIM support for SSDs, compression, snapshots, COW). It's also the least stable (I haven't had data loss but a 'scrub' wouldn't complete on my external disk so I switched it to ZFS) but it's where the future of Linux file systems is heading. It can be quite nice to play with.

---

### Post by TheFu on 2013-02-04
The short answer is most probably, use EXT4.

Which file system to use is an extremely complicated question and completely dependent on your needs and how comfortable you are with possible data loss.

For most people running normal desktops, EXT4 is a good choice, but there are issues with some older tools - like image-based backup tools - that cannot handle EXT4 as efficiently as EXT3.  This is not important to most end-users.

If you are running servers and performance and advanced features are needed in your file system(s), then much more reading will be necessary to understand the pros/cons for each.

If you are just curious, there is a wikipedia article on each of those file systems.

There are places where running **ext4** does not make the most sense, so **ext3,** **ext2,** zfs, xfs,** jfs,** are better choices. Each has drawbacks and strengths.  There are probably 50 other file systems available to use under Linux too. I am actively running the **bolded** **text**  file systems on my work machines right now.

If you want MS-Windows to be able to directly access a Linux file system, then ext3/ext2 is probably the best answer, unless a network connection (which is much, much, much,  1,000,000x better solution) can be used.

Complex.

---

### Post by grahammechanical on 2013-02-05
This thread got me curious. I found this

[http://www.phoronix.com/scan.php?page=news_item&px=MTEwMDE]("http://www.phoronix.com/scan.php?page=news_item&px=MTEwMDE")

and this but it is old.

[https://help.ubuntu.com/community/btrfs]("https://help.ubuntu.com/community/btrfs")

I would say that btrfs on Ubuntu should definitely be tested. That is what you were talking about. Was it not? But does anybody want us to test it?

Still, it is in the list of file systems. The Devs will need bug reports before it becomes the default file system. No one can stop us from trying it out.

Regards.

---

### Post by ventrical on 2013-02-05
Here goes ....

---

### Post by ventrical on 2013-02-05
Wow...

---

### Post by ventrical on 2013-02-05
I am trying again ...

Edit:

Ok .. for some reason it  borked the USB .iso to smithereens so I have to use SDC again to correct this problem.

Edit:

Thie above is  incorrect. What happened is that the hdd will not be recognized on reboot and system will lock up. You have to physically disconnect the hdd from the cables and system will reboot normally.

 All kinds of apport bells and whisltes trying to glean information when trying that new files system protocol.

trying .. again..

---

### Post by ventrical on 2013-02-05
It installed seemingly successfully, then . after bootup

 error: sparse file not allowed

then
<press any key to continue>

waited and it just booted on it's own .

sudo apt-get updates and locked up on:xxxx:xxxx radeon : failed to reset GPU

  I will zsync the daily and see if they got the ATi driver problem fixed..
*EDIT*Ok .. ATI driver problem seems to be fixed now with i386.

  Just one observation... the (btrfs) seems to force Ubiquity into some type of 'contrite' mode if that makes any sense..

---

