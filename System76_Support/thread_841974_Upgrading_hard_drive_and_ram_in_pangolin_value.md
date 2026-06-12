---
title: "Upgrading hard drive and ram in pangolin value?"
date: 2008-06-26
forum: System76 Support
---

### Post by Pethegreat on 2008-06-26
I have a Pangolin value(purchased in march 2008 ). I have 320gb SATA hard drive on order. What do I have to do to change out the hard drive? Will I void the warranty?

I also want to clone my current hard drive over to the new 320gb HD. I have an enclosure for the hard drive. Also is it possible to expand my root partition and not destroy other data? 

How do you go about removing ram and adding larger capacity sticks? Will that also void the warranty?

---

### Post by logos34 on 2008-06-26
Check with System76 about the warranty (but at the very least you should be able to add certified/approved memory without voiding it)

You could use [Gparted]("http://gparted.sourceforge.net/larry/move/move.htm") or clozezilla.  But **dd** is simpler (takes longer though cuz it copies even unused space)

>  Cloning an entire hard disk:
 
[ dd if=/dev/sda of=/dev/sdb conv=notrunc,noerror]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_To_Do_Eveything_With_DD")
 
In this example, sda is the source. sdb is the target. Do not reverse the intended source and target. Surprisingly many people do. notrunc means to not truncate. noerror means to keep going if there is an error. Normally dd stops at any error. if you have a question about a hard drive on whether or not it works, you can try to use it as the source drive for the dd command. You should get an error if it is not working. target drives need to be really messed up to give an error in dd.(you'll have to boot from a live cd to run it since the partitions cannot be mounted)
> 
Also is it possible to expand my root partition and not destroy other data? 

yes, with gparted

---

### Post by thomasaaron on 2008-06-27
It will not void your warranty to upgrade your RAM and HD, as long as they are within the specifications of your computer.

---

### Post by Pethegreat on 2008-07-03
I am just about done dd'ing all my sda1 and sda3 to the new disc. I made sure to make a 2.5gb swap file. 

Will I have to fix my grub? I have my root and swap drives on an extended partition. The root drive is sdb 6 and swap is sbd5. home drive is sdb 2.

---

### Post by logos34 on 2008-07-04
yeah, [install grub to the new drive's MBR]("http://ubuntuforums.org/showthread.php?t=224351") and boot from that

---

### Post by Pethegreat on 2008-07-04
Well something got messed on the drive when I dd'ed it. I cannot mount it. It gives me the error sign with no message. 

This is becoming a pain for me. I am just going to install HH on the drive and then figure out how to install the system 76 driver.

---

### Post by logos34 on 2008-07-04
Runa filesystem check on it from the live cd:

sudo fsck /dev/sdb6 

or whatever new root is

---

### Post by Pethegreat on 2008-07-04
Well it took me less time to drop out my old hd, stick in the new one, install ubuntu, and then take all my important files from the old hd. 

So, everything is solved with the HD. 

Now what brands of ram fall in the specifcations? I know I need ddr2 667mhz notebook sticks.

---

### Post by crichell on 2008-07-07
> Now what brands of ram fall in the specifcations? I know I need ddr2 667mhz notebook sticks.

Any brand is fine... As long as you use DDR2 667 Mhz you'll be OK. Up to 4GB is supported (although you can only use up to 4 GB with 64-bit Ubuntu.)

---

### Post by darkknight045 on 2008-07-07
> **crichell said:**
> Any brand is fine... As long as you use DDR2 667 Mhz you'll be OK. Up to 4GB is supported (although you can only use up to 4 GB with 64-bit Ubuntu.)

Ubuntu can only support up 4 GB of RAM?

Doesn't that defeat a large part of the purpose of a 64bit OS? I know 32 can only handle 3.25, it seems odd that 64 bit nets you only 0.75 more ram capacity.

---

### Post by thomasaaron on 2008-07-08
darkknight,

32-bit Ubuntu actually supports 4GB of RAM. The problem is, part of that 4GB is taken up by mapped memory devices in the machine. Then remainder is claimed by your memory cards (3.something GB). 

64-bit Ubuntu can support much more than 4GB. However, according to the specs for the motherboard of your computer, it can only handle 4GB max.

In other words, the OS isn't limited to 4GB, but the motherboard is.

---

### Post by darkknight045 on 2008-07-08
I understood the limit with Laptops, I was concerned for Desktop systems, I planned to upgrade my Desktop to 6GB of RAM. I had planned to put HH 64-bit on it, but if it couldn't handle more than 4GB RAM well... that would have been disappointing.


Thanks for the clarification!

---

