---
title: "Hardy + Mylex AcceleRaid 170 &amp; MBR"
date: 2008-11-25
forum: Server Platforms
---

### Post by Goobie81 on 2008-11-25
I cannot install Grub or Lilo on this system 

Intel SR1400SYS with Mylex AccelRaid 170. Raid 5 Logical drive.

Physical disk /dev/rd/c0d0
/boot partition /dev/rd/c0d0p1
LVM partition /dev/rd/c0d0p2

/ = LVM LV 'rootlv' 

After the installation finishes , i get an error with both Grub and Lilo. They both just fail to install. I would prefer Grub, but if i have to use Lilo thats fine. 

On the log tty, Grub just says 'grub-installer failed with exit status 1'. The first attempt says "/dev/rd: is a directory", following attempts don't show this error.

When i try with Lilo manually entering /dev/rd/c0d0 or /dev/rd/c0d0p1 or /dev/rd they all say its not a valid partition?

I found this article, but it's for a 2.2 kernel! [http://www.redhat.com/archives/guinness-list/2001-March/msg01015.html](http://www.redhat.com/archives/guinness-list/2001-March/msg01015.html)

Do i still have to go through the floppy disk process? Or is there a modern way around this issue?

---

