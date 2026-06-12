---
title: "Setup a security diskless PC with a usb key"
date: 2016-02-17
forum: Security
---

### Post by neogeo1128 on 2016-02-17
I have some friends living in some countries which have tight censorship (police with come to your home and get caught just if you surfing websites like CNN)

They want to setup a diskless pc or a hard drive pc + usb key  to control the pc.

When the usb key was plugged out. the pc cannot be use and the content in the hard disk cannot be seen.

Which software should l use? Any ideas?

---

### Post by xenon3 on 2016-02-17
Google sold Thin Client laptops a while a go, they don't had hard disks

---

### Post by sudodus on 2016-02-17
There is a linux distro for it, Tails. See this link

[https://tails.boum.org/](https://tails.boum.org/)

---

### Post by gordintoronto on 2016-02-17
They could set up a computer with a hard drive full of innocuous stuff, and a flash drive for the serious computing. Power down, pull the flash drive, "of course you can search my computer."

---

### Post by patrikmellq on 2016-02-18
I know a secure distro you can run from USB stick and it does not mounting your hard drive.
It says so at there home site.
If i understand it correct so does it only run in memory.

The Linux distro is form the American Air Force:

[SIZE=2]http://www.spi.dod.mil/lipose.htm

Cheers

[/SIZE]

---

### Post by patrikmellq on 2016-02-18
I should also mention that my USB key has a button for read only, so i can have it open and write to it and lock it.
So my secure linux distro is read only.

---

### Post by haplorrhine on 2016-02-18
I would make a bootable external harddrive.  Some connect by bluetooth.  What do the experts think?

Other components and their firmware are already running before Ubuntu boots from the harddrive.  It sounds like you want some third-party firmware to lock basic components like the BIOS chip, but I don't see how the flashdrive is going to mount if nothing is running yet.  Regardless, if this flashdrive will connect to other computers, you might want to write-protect the microcontroller ([BadUSB]("http://www.wired.com/2014/10/code-published-for-unfixable-usb-attack/")).  I say patch it yourself since most commercial products are writable with the manufacturer key.

---

