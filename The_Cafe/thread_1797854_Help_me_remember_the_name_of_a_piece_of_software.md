---
title: "Help me remember the name of a piece of software"
date: 2011-07-05
forum: The Cafe
---

### Post by mamamia88 on 2011-07-05
i want to remove ubuntu from my laptop and use only windows 7 for now.  ubuntu won't even boot so the partition is useless.  i want to delete ubuntu from disk utility and fix the mbr from within windows.   i did this before with a piece of software that rewrites the mbr but i can't remember the name of it. can anyone tell me what I am thinking of?

---

### Post by mips on 2011-07-05
If you boot up the windows cd/dvd and select the repair console the FIXMBR command will overwrite it.

You can also overwrite from Ubuntu with
# dd if=/dev/zero of=/dev/sd**[COLOR="Red"]X[/COLOR]** bs=446 count=1

Where **[COLOR="red"]X[/COLOR]** is the hard drive you want to change the MBR on.

---

### Post by el_koraco on 2011-07-05
The Windows Recovery Disk should have this option. You have to go into CLI, but I guess you're used to it in Linux? 

[There's this as well]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/")

---

### Post by forrestcupp on 2011-07-05
> **mips said:**
> If you boot up the windows cd/dvd and select the repair console the FIXMBR command will overwrite it.

You can also overwrite from Ubuntu with
# dd if=/dev/zero of=/dev/sd**[COLOR="Red"]X[/COLOR]** bs=446 count=1

Where **[COLOR="red"]X[/COLOR]** is the hard drive you want to change the MBR on.

I have tried that before, but it never worked for me for some reason.

I've had luck using GParted Live CD to move and resize the partitions, and also Super Grub live CD to fix the MBR and Windows bootloader.

---

### Post by conradin on 2011-07-05
Windows + R type "msconfig" [ENTER]
msconfig can tweak your boot path from the boot tab.
Also you can delete the partition via the disk manager.
I think the Disk mgr in W7 will also allow you to re-alocate the partition to your original

---

### Post by and1bskbl72 on 2011-07-05
Fixing A Corrupt Master Boot Record

If you&#8217;ve got a problem with Windows&#8217; oh-so-important boot record then you can also fix that from within Ubuntu too. Assuming you&#8217;ve already booted into Ubuntu, open up Terminal and install lilo by typing:

sudo apt-get install lilo

Enter your password to proceed with the installation, you&#8217;ll get a few warnings pop-up along the way.
If you followed the first part of this tutorial you&#8217;ll know which partition Windows is installed on, if you missed it type:

sudo fdisk -l

Find the HPFS/NTFS partition that relates to your Windows install, and type:

sudo lilo -M /dev/ mbr

Replace <device name> with your Windows partition (e.g. /dev/sda2) and hit Enter. Ubuntu will attempt to restore your master boot record. You&#8217;ll probably want to restart your machine now, just make sure you take any Live CD/USB devices out as you do.

---

### Post by hhh on 2011-07-05
> **mamamia88 said:**
> i want to delete ubuntu from disk utility and fix the mbr from within windows.   i did this before with a piece of software that rewrites the mbr but i can't remember the name of it. can anyone tell me what I am thinking of?
Super Grub Disk...
[http://www.supergrubdisk.org/super-grub-disk/](http://www.supergrubdisk.org/super-grub-disk/)

---

### Post by Famicube64 on 2011-07-05
Easy BCD is a Windows program that'll do what you want.

---

### Post by mamamia88 on 2011-07-06
> **Famicube64 said:**
> Easy BCD is a Windows program that'll do what you want.

that is what i was looking for thanks

---

