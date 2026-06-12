---
title: "i need help {h'ep me h'ep me pleez}"
date: 2005-04-23
forum: Repositories &amp; Backports
---

### Post by necorium on 2005-04-23
i'm almost done downloading my first copy of linux. yay  ;-) 
will i have problems installing it on the same drive [c:/] as windows?
what are the no nos of installin linux on a pc with windows??
h'ep me
 :grin:

---

### Post by nad on 2005-04-23
First you need room on your hard drive. Current thought is about 5 gigs minimum.

If you wish to dual boot with winXP, please see these forums for other issues. Windows 98 is trivial to setup. The installer will do everything for you. I do not want to know about ME or 95.

Other than that, there are no no nos with linux. That is a M$ trait. Keep us posted. There are many ready to help.

Dan M

---

### Post by necorium on 2005-04-23
ok well i have 5gig free on my partition with windows and about 100gigs free on my games partition. will installing it on the windows partition make it (and windows) go all slow? there would be no space left basically. 

and if i installed it onto my d drive (games partition) would that be ok?

thanks for all the help

---

### Post by nad on 2005-04-23
Yes, you can install ubuntu on any drive in your system, and as linux will operate faster with a dedicated swap partition, you should make room for an additional 200-500M partition. It is best to do any partition resizing with an application native to that file system although there are several linux tools to resize a vfat filesystem. Here I am refering to your windows partitions. If possible, resize from within windows. This is a must for an ntfs filesystem.

The data, and your windows file system will be nothing more than this to linux, on your hard drive has very little to do with your operating system under linux, other than the fact that a file system with little room left will cause any operating system to suffer.

As I mentioned previously, if you wish to dual boot with exPee please search these forums for other issues that you need to be aware of. I am not current with exPee and do not wish to be.

Dan M

---

### Post by necorium on 2005-04-23
hmmm ok so i need space
i'll dump it in my games partition
will look up on xp in forum although i don't understand half this stuff
will my pc games run in linux or only ones specifically designed for linux?

---

### Post by nad on 2005-04-23
One of the few reasons to dual boot a computer these days is gaming. Do not expect your windows games to play within linux without the addition of additional software and serious configurating (is this a word?). You can expect to attempt this once you become more familiar with ubuntu, but it doesn't always work well and sometimes just doesn't work.

There are several big name games for linux and manufacturers are releasing more native linux versions regularly.

As far as the exPee issues, it's quite technical as far as the bootloader issues. Do your best and ask questions. You are already on your way.

Dan M

---

### Post by Jenda on 2005-04-29
The word is configuring.

Anyway, can someone please answer this question?

My friend uses Win2k. He wants dual boot with Ubuntu on a single 20 GB HDD. I do not know what file system it is. What is the recommended way of doing this and how safe is it?

---

### Post by az on 2005-04-29
You do not need to use proprietairy stuff to partition any windows drive.  The Ubuntu Hoary installer can take care of all that.  Some rare cases pop up on the forums, but 99.999 percent of people running Windows XP (or any other windows) can use the installer to shrink their windows partition to make room for Ubuntu.  If for any reason the NTFS (or other) partitoin cannot be resized, it will refuse to do it.  Don't worry.

These are the basic principles:

You boot the installer and it autodetects all your hardware.  You get presented with a partitionning step.  The default option is to blow away your first hard drive.

If this is not what you want to do (for example, you want to dual boot with windows) select manual partitioning.  Then scroll down to the partition you want to shrink (look at the partition sizes - you may not be familiar with the linux device names)  Hit enter to select that partition.
Tell it to change it's size and enter the smaller size.  Read what is on the screen. Say yes and let it shrink your partition.  It may take a few minutes if it has to move data around.

You will now go back to the partition screen and see (FREE SPACE) where you just created it.  Select guided partitionning and the installer will suggest a partitioning scheme for you that includes one partition for your root ("/") and one for swap.  Say yes and make it go. 

The rest of the install will happen.

Don't worry.  Many many many people are happily dual booting with windows XP.  Trust me, it is rarely a problem.
 
But, always:
Back up your data and I am _not_ responsible if you lose any data, though.

---

