---
title: "Edgy server rebooting at, Staring up..."
date: 2006-12-19
forum: Server Platforms
---

### Post by PisstMSTRCHIEF on 2006-12-19
I recently installed Ubuntu Edgy server on an Compaq Presario 7478, after installation, grub loads and says 'Starting up...' in the upper left hand corner as it should. But, it never makes it past this point. It then reboots.

Here are some specs on the machine:

- 533 MHz AMD K6®-2 processor 
- 256 MB RAM
- 10 GB hard drive
- 512KB L2 Pipeline Burst Cache
- 3.5" 1.44 MB diskette drive
- Netgear gigabit Internet adapter GA311

I ran Memtest86+, some of the numbers had me concerned:
L2 Cache: Unknown
Memory: 248M

Shouldn't that be:
L2 Cache: 512KB
Memory: 256MB 

booting from CD and booting Memtest86+ works

I just bought the hard drive (works great), and the Internet adapter worked wonderful in my other computer.

Any questions or comments is greatly appreciated.

---

### Post by az on 2006-12-19
> **PisstMSTRCHIEF said:**
> I recently installed Ubuntu Edgy server on an Compaq Presario 7478, after installation, grub loads and says 'Starting up...' in the upper left hand corner as it should. But, it never makes it past this point. It then reboots.




Here are some specs on the machine:

- 533 MHz AMD K6®-2 processor 

The server kernel will only run a 686 or better -  you need the generic kernel which is 386.  Chroot into your installed system and run

sudo apt-get install linux-image-generic


> **PisstMSTRCHIEF said:**
> 
I ran Memtest86+, some of the numbers had me concerned:
L2 Cache: Unknown
Memory: 248M

Shouldn't that be:
L2 Cache: 512KB
Memory: 256MB 

Maybe your BIOS cannot tell memtest what the cache is?

And it sounds like you have an onboard video card using 8 megs of ram.

> **PisstMSTRCHIEF said:**
> 

booting from CD and booting Memtest86+ works


That's because it does not use the linux kernel - it is written in ASM.  As well, the installer boots the 386 kernel which is why you are able to boot it.

You can also install a base system using the alternate cd.  The alternate cd installs the 386 kernel too, just like the desktop cd.

---

### Post by PisstMSTRCHIEF on 2006-12-19
WOW:shock: , I hope you get paid for this....

That was a very well drawn out explanation for everything I asked.

Nothing more I could say but thank you and have a marry christmas!:KS

---

