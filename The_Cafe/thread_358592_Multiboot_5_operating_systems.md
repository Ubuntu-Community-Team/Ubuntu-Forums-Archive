---
title: "Multiboot 5 operating systems?"
date: 2007-02-11
forum: The Cafe
---

### Post by Xzallion on 2007-02-11
I was just getting another hard drive, and was wondering roughly how much of a pain setting it up to boot:
[LIST]
[*]Windows 98
[*]Windows XP
[*][Ubuntu Linux]("http://www.ubuntu.com/")
[*][Desktop BSD]("http://www.desktopbsd.net/")
[*][Open Solaris]("http://www.opensolaris.org/os/")
[/LIST]
Would be.  I'm not asking for tech support so I didn't think this belongs in the general support, instead I just want a idea what I'm getting into.  I want the two windows on here for games (I seem to have no luck getting things to work in wine), I want to play around with BSD and open Solaris, so I want them on there, and then of course gotta have Ubuntu as my main OS for everything else.

---

### Post by macogw on 2007-02-11
If you partition it first and install Ubuntu last and make a separate partition for /home, not bad at all.  Reasoning: Windows likes to spread out and partitioning afterward sucks, Ubuntu's grub automatically adds everything else, you can share your files without rebooting.  As to formatting of /home, fat32 is easiest, but you can't have files larger than 4gb.  Ext2 & 3 have drivers for Windows too though that'll let you use an ext3 /home drive.

I'm currently multibooting FC6, Sabayon, Edgy, and Feisty.

---

### Post by slimdog360 on 2007-02-11
yep, Ubuntu last should solve any problems you may encounter. Grub can cope with heaps more then 5.

---

### Post by anaconda on 2007-02-11
You might want to make a separate 200MB /boot partition somewhere to the beginning of your hd, so that reinstalling ubuntu, or whatever wont affect the booting of other os:ses (other than overwriting mbr, which you should be able to correct with a liveCD..)

In some BIOS:ses there might still be limits, that it isn't possible to boot from partition, which is over 80GB (or less) from the start. If you have the bootloader (boot partition) in this area you wont have problems..

Windowses will be added to your ubuntu:s grub automatically, if you install ubuntu last. BSD and Solaris you propably have to manually add to your /boot/grub/menu.lst -file.

I have found that it is easiest if you install all os:ses bootloaders to the beginning of their partitions.. Then they are easy to add to grub:s menu.lst file.. Because then you can just chainload them (=give the control to the os:s own bootloader so that you dont ave to know where the kernel images etc are.)

---

### Post by mips on 2007-02-11
Another option would be only have grub boot, Windows 98, Windows XP & Ubuntu.

Then do all your OS testing in  VMWare Server or KVM.__

---

### Post by RandomJoe on 2007-02-11
I did a slightly different variation for one of my laptops - want to play with several versions of Linux.  (No Windows in this mix.)  I made a 20MB "bootloader" partition, then carved the rest of the disk up into equal chunks for the OSes.

I installed Ubuntu onto the first OS partition, and told GRUB to install to that partition, not the MBR.  (Changed the "GRUB will be installed to (hd0)" to (hd0,1).)  Once Ubuntu was running, I mounted the "bootloader" partition to /master-boot (just some other directory, to keep it separate).  I then copied the /boot/grub directory into here (so I have /master-boot/grub) and edited the /master-boot/grub/menu.lst file so it only chainloads the other partitions.  Each OS entry looks like:
```
title Ubuntu-6.06
root (hd0,1)
chainloader +1
```

Then I run grub and type:
```
root (hd0,0)
setup (hd0)
```

After that, I install other OSes to each of the remaining partitions, again telling its installer to put its bootloader on that partition.  Afterward, I just edit /master-boot/grub/menu.lst (I can mount it from _any_ of the OSes since I don't have to rerun GRUB) and add a chainloader for it.

This gives me a GRUB menu that lets me select which OS to boot.  When I make a selection, it transfers me to the [GRUB|lilo] menu for that OS which lets me make whatever choices it would normally give.  (It also means, when updates occur, only _that_ OS's entries get messed with - I tried a "mixed" /boot once and it got messy quick when Ubuntu updated the kernel and auto-edited the menu.lst.)

The only "catch" to this - be _very careful_ to note which partitions are which!  Especially since GRUB uses unique naming for them.  It would be pretty easy to overwrite the wrong partition's loader!

---

### Post by Xzallion on 2007-02-12
Thanks for all the advice. :D  I really appreciate it.

---

