---
title: "[IDEA] unsuck install"
date: 2007-10-24
forum: Ubuntu Brainstorm
---

### Post by DFreeze on 2007-10-24
Can't the name of the OS installed on a disk be used to name the disk? 

I just tried to install Gutsy from the Desktop CD to my laptop. I have several partitions on that computer, to try different distros. But I made them exactly equal in size, and that made them hardly indistinguishable from the Desktop CD.

In Nautilus the disks show up with names that refer to their sizes, until you mount them. So I have three disks with the same size, one of which contains the distro I want to overwrite Gutsy with. In the properties the only way to recognize the disk is the UUID but the installer keeps using the /media/hda# structure.

The only way I could find out which hda# number I had to overwrite was to browse through each disk to /boot/Grub and open menu.lst. That gave me the OS that was installed. Then I checked the used space in 'Properties', to see which one of the hda# numbers corresponded to that size.

If I can see the OS installed in the /boot/Grub folder, so can Ubuntu. Even more so, Ubuntu gave me the option of importing user settings from my PCLinuxOS partition, so Ubuntu knows what's on the disk. 

Can't a disk be named after the OS that's installed on it? Or at least can the installer use the same identification method that the 'Properties' menu does? The /media/hda# numbering was obscure, but this way identifying a disk is REALLY itchty!

---

### Post by kidders on 2007-10-25
Why not just label your filesystems?

---

### Post by DFreeze on 2007-10-25
How do I do that? I didn't know I could (still learning). But you have to agree that that's not something a new user knows how to do. But then again, a new user probably doesn't have all kinds of partitions on his harddisk in the first place.

Still, when I connect a camera or a USB stick, both are called disk, or disk-1. It would be nice if the name (or the icon) gave some indication of the type of disk or the contents.

---

### Post by kidders on 2007-10-26
How to label filesystems depends on what they are. For instance, **e2label** can alter the name of Ext2 & 3 ones. Most computer users are familiar with the idea of labelling filesystems, but even if you didn't know how, something like **apropos label** would tell you.

> **DFreeze said:**
> Still, when I connect a camera or a USB stick, both are called disk, or disk-1. It would be nice if the name (or the icon) gave some indication of the type of disk or the contents.True. Unfortunately, your Linux can only know as much as your devices tell it. As far as filesystem labels goes though, I've never really understood installers that don't let you set them, for exactly the reason you mentioned ... after a while, it's the only easy way to tell them apart.

---

