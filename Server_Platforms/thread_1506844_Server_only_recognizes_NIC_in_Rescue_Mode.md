---
title: "Server only recognizes NIC in Rescue Mode"
date: 2010-06-10
forum: Server Platforms
---

### Post by Reid_PMP on 2010-06-10
Two days ago my HP Pavilion a335w on board NIC stopped working. I've tried putting in another NIC in the PCI slots #1 & 2 of the three available and the system does not pickup the card. I thought it was because it was an old 3com 3c905b and was not supported.

I took the box to Best Buy and purchased a new Linksys card and had them install it.

The Geek Squad told me that the Motherboard was bad, no charge.

I took it to a refurbishing store and the very patient gentlemen tried to get a Netgear FA310TX card to be recognized with no luck.

I took the Netgear FA310TX card home and put in slot #3 and booted up with the install disk. In Rescue Mode it recognizes the NIC and gets an IP address from the router.

If I boot up normally without the install disk, then it does not recognize the NIC.

What do I have to do to get the OS to recognize the NIC?

Your help is appreciated.

---

### Post by mechdave on 2010-06-10
Reid_PMP,
I need some more specifics please, could you please post the output of dmesg (found by opening a terminal and typing dmesg > dmesg.txt) and pasting the file here. That way I might be able to see what is going on a bit more easily. Also what is your version of Ubuntu? 
Cheers,
Mechdave

---

### Post by Reid_PMP on 2010-06-10
I am not very savvy with the command line, I can get the output of dmesg > dmesg.txt to a floppy, but I cannot read the floppy with my windows machine that does not have a floppy drive. AAAGGGHHHH!

I can possibly mount the DVD ROM and copy the file to a CD. I'll try that.

---

### Post by mechdave on 2010-06-10
Just put the file onto a usb stick or something like that :)

---

### Post by Reid_PMP on 2010-06-10
do I have to mount the usb stick? This is a server and there's no GUI to make things simple.

---

### Post by mechdave on 2010-06-10
Ok easy way is fins where the usb stick has been put, eg: /dev/sd* <-- use dmesg to do that

then type sudo mount -t vfat /dev/sd* /mnt
or if the format is ntfs just replace the vfat with ntfs

If you join IRC at irc.freenode.net I am in #ubuntu... I can post our fix here later for other users :)

---

### Post by Reid_PMP on 2010-06-10
I'm not having any luck with the USB either. I'll try again tomorrow.

If I reinstalled the OS would that overwrite all of my configuration? It appears the install disk can recognize and setup the NIC, would a reinstall be like starting from scratch?

---

### Post by Reid_PMP on 2010-06-12
I have bigger problems than the network card not being recognized. My harddrive is dying. There are bad sectors and other errors, now it won't even boot up.

I'm buying a new server, aaagggghhhhhh!

---

