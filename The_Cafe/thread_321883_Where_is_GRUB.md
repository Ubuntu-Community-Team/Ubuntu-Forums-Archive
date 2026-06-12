---
title: "Where is GRUB?"
date: 2006-12-19
forum: The Cafe
---

### Post by cactaur on 2006-12-19
I'm the type of person who likes installing several different operating systems on the same computer. I was wondering, if all of them have a boot manager, namely grub, where does the computer know which one to use. For example, I recently installed Solaris (not for WiFi people) and it replaced the Ubuntu grub. I was able to put Ubuntu onto the Solaris menu.lst, so it's not a problem for me, but I'm just wondering, where is the location stored? Is it somewhere in the BIOS? If I wanted to change the Solaris one to the Ubuntu one, how would I do so? If anyone knows, that would be great, I'm really curious about this.

---

### Post by bigken on 2006-12-19
in ubuntu its in filesystem/ boot/grub ;)

grub has nothing to do with bios

---

### Post by 5-HT on 2006-12-19
Most likely on your Master Boot Record (MBR, first sector of a hard disk) unless you specified otherwise during install. There are lots of great HOW-TO's on the forums and wiki detailing how to reinstall GRUB.

---

### Post by niko7865 on 2006-12-19
If you boot into ubuntu, i think its something like this, really simple. Of course you'll have to replace it with the right info for your system.
sudo grub
>root (hd0,1)
>setup (hd0)

---

### Post by cactaur on 2006-12-19
Well, what I'm wondering is, lets say you have like, Ubuntu, Fedora, FreeBSD, SuSE, etc. And they all have a /boot/grub file. How does the computer know which one to use? Is it just the last one that was installed? And if it was, is there a way to rotate between the Ubuntu grub and the Suse grub, etc.?

---

### Post by niko7865 on 2006-12-19
I'm not sure exactly how it works, but there is a file or pointer of some sort on the MBR of whatvere hard drive you have set to boot from. That points to where the actual loader is installed, so yes the last one installed will be used since it would have over written the MBR with a pointer to itself. If you wanted to use different grub loaders you could have a different boot floppy for each one, and just throw that into the computer depending on which one you felt like booting from.

---

### Post by cactaur on 2006-12-20
Yikes, so I couldn't just like, edit something in the computer? I need a floppy for each one? Dang!

---

### Post by Polygon on 2006-12-20
not really,

you need:

grub on the master boot record of the hard drive that your computer is set to boot first from

and a special partiton on one of your hard drives that contains the "boot" partition, which is where grub, and all of the necessary files / kernels and the information on what os lives on what partiton goes.

---

