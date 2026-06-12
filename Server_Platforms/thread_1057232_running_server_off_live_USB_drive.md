---
title: "running server off live USB drive?"
date: 2009-02-01
forum: Server Platforms
---

### Post by anon0 on 2009-02-01
Hard drive ports are at a premium on my older computers, and I need as much space as possible for RAID. Rather than having an OS on hard drive, how about running it perpetually off a USB? Will longevity be an issue since USB drives are flash-based and have a limited number of reads and writes in theory -- how frequently will the server need to access the USB drive when serving RAID?

---

### Post by spinanicky on 2009-02-01
simple solution would be to make an image of the flash drive. Then when ever it goes down just buy a new one... copy the system onto it... and plug it in ;)

Also remember that you will be reading most of the time not writing to the usb... so your read write problem wont be as drastic as you imagined. (I think)

---

### Post by Krupski on 2009-02-02
> **anon0 said:**
> Hard drive ports are at a premium on my older computers, and I need as much space as possible for RAID. Rather than having an OS on hard drive, how about running it perpetually off a USB? Will longevity be an issue since USB drives are flash-based and have a limited number of reads and writes in theory -- how frequently will the server need to access the USB drive when serving RAID?

I run a couple file servers that contain Ubuntu Linux on a small Compact Flash memory card. The card is plugged into a CF-to-IDE adapter board which is, in turn, plugged into the motherboard IDE port.

The entire OS is on the CF card. The hard drives are solely data storage.

There is really no difference between what I'm doing and what you want to do.

Only thing you need to know is if your computer will BOOT from a USB device. If so, just plug your USB memory stick into the computer, boot up the Ubuntu install CD and install to the USB drive.

Be sure to make GRUB put the master boot record on the USB drive, *NOT* the computer's hard drive.

Also, the first time you boot the USB stick, you'll have to edit the GRUB line that says something like "root=(hd2,0)" and change it to (hd0,0). Then, once you're in, edit /boot/grub/menu.lst and make the change permanent.

It would be a good idea to also run "update-grub" to make sure everything is OK.

Good luck!

-- Roger

---

### Post by Krupski on 2009-02-02
> **spinanicky said:**
> simple solution would be to make an image of the flash drive. Then when ever it goes down just buy a new one... copy the system onto it... and plug it in ;)


I have a small script called "savecf" which just uses "dd" and makes an image of my compact flash Linux drive (which it then compresses with GZIP).

This file is stored on the RAID hard drive and I make a local copy of it once in a while so that I can restore the system to a working configuration in 5 minutes if I need to (no problems so far - fingers crossed!)

---

### Post by anon0 on 2009-02-02
So you put the swap on flash memory too? 

I read that flash memory might be good for about 10,000 writes only! That's why I'm curious about the frequency of disk writes by the server on a routine basis, if left untouched other than disk array accesses by clients.

---

### Post by Krupski on 2009-02-02
> **anon0 said:**
> So you put the swap on flash memory too? 

I read that flash memory might be good for about 10,000 writes only! That's why I'm curious about the frequency of disk writes by the server on a routine basis, if left untouched other than disk array accesses by clients.

Ah sorry I forgot to mention that. I have a 2 GB swap FILE on the RAID array and that's what I use for swap.

I USED to have the OS and swap both on the same CF card, but I thought it would be better to put it on an "infinitely writable" medium (i.e. the hard drive).

Don't be so worried about flash write cycle life. First of all, modern flash is good to 100K or more write cycles per sector, AND the controller moves the sectors around ("wear leveling"). 

You and I will be old and gray before a flash device wears out. Don't worry about it.

-- Roger

---

### Post by Thirtysixway on 2009-02-02
I thought about doing this.  Not because I need the hd space but because the cable for my harddrive broke off and I can't get it out :)

---

