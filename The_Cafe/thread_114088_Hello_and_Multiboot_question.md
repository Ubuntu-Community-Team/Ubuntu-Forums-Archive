---
title: "Hello and Multiboot question"
date: 2006-01-07
forum: The Cafe
---

### Post by martyfelker on 2006-01-07
Hi All:
   

    Since I was asked to make my first post here, why I will!

    My name is Marty Felker and I've playing (and working) with these foolish machines ;) since 1962 I've seen a few changes!

    Anyway,  My question is the following.  I have a machine (64-bit Athlon 2800 running at 2GZ - 2 GB RAM -ASUS K8V-X mobo and other specs if you wish).  The machine has 3 80GB WD drives.  I have Windows 2000 (the best of the hokey M$ OS's) dual booting Windows Fedora Core 4 (64 bit - 64 bit Windows will be "ready real soon now").  I wish to install one more Linux on my "real machine" (have VMware to fool with several others).  I like Ubuntu because I can get software RAID during install.  I already have md0 setup in Fedora as the / partition (reiserfs).  So my question is - will the Ubuntu install program be able to properly setup GRUB so I can boot to Windows AND Fedora?  I really don't want to screw up Fedora since I've put a lot of work into it.  Is this going to be impossible?  Hard I can live with.

  Thanks to all of you.

---

### Post by GreyFox503 on 2006-01-07
Although I'm not sure I understand your setup entirely, you can configure GRUB to boot several different operating systems.  On my computer, it automatically made a menu entry for Windows, but I didn't have any other OS's at that time.  I was able to modify GRUB later to boot additional operating systems.

Here's something you might want to try:  When installing Ubuntu, if the drive to which you are installing has no boot loader present, Ubuntu will install GRUB to it.  If it detects something there (like a Windows bootloader), it will ask you what you want to do.

At this point, if you don't feel comfortable installing GRUB to your hard drive, you can install it somewhere else, like a floppy disk.  Then, whenever you want to use Ubuntu, you just boot from the floppy.

Once you have done this, you can work from within Ubuntu to tweak GRUB to boot your other OS's if it doesn't do it automatically.  Then later when you are satisfied, you can tell GRUB to write itself to your hard drive's MBR so you don't have to stick in a floppy every time.

For future reference, the file to edit your GRUB menu is at /boot/grub/menu.lst

It comes with lots of comments, and it's not too hard to edit by hand.

---

