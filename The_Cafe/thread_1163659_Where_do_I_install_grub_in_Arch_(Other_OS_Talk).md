---
title: "Where do I install grub in Arch? (Other OS Talk)"
date: 2009-05-18
forum: The Cafe
---

### Post by gymophett on 2009-05-18
I installed the bootloader in Arch. I think it was in the wrong one. I installed grub in dev/sda. There were dev/sda2, dev/sda3, etc. 
Now when I try to boot this is what I get:

> : : Checking Filesystems [BUSY]
/dev/sda3: Superblock last mount time is in the future. FIXED.
/dev/sda3: Superblock last write time is in the future. FIXED.
/dev/sda3 has filesystem last checked last time in the future, check forced. Error reading block 113163 (Attempt to read block from filesystem resulted in short read) while reading directory block. [FAIL]

[CENTER]*****FILESYSTEM CHECK FAILED*****[/CENTER]
Please repair manually and reboot. Note that the root file system is currently mounted read-only. To remount it read-write type: mount -n -o remount,rw /
When you exit the maintenance shell the system will reboot automatically.
[CENTER]********************[/CENTER]

Then it says:

Give root password for maintenance
(or type Control-D to continue):


What do I do?

EDIT: It also gives some error over and over about something like this:
end_request: I/O error, dev sda 713301 
ata1: EH complete
sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.00GB/74.5 GiB)
sd 0:0:0:0: [sda] Write protect is off
sd 0:0:0:0: [sda] Write Cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by penguindrive on 2009-05-18
> **gymophett said:**
> I installed the bootloader in Arch. I think it was in the wrong one. I installed grub in dev/sda. There were dev/sda2, dev/sda3, etc. 
Now when I try to boot this is what I get:



Then it says:

Give root password for maintenance
(or type Control-D to continue):


What do I do?
control-D

---

### Post by gymophett on 2009-05-18
> **penguindrive said:**
> control-D

Reboot and same thing again.

---

### Post by penguindrive on 2009-05-18
> **gymophett said:**
> Reboot and same thing again.

Then type the root password.

---

### Post by gymophett on 2009-05-18
> **penguindrive said:**
> Then type the root password.

Yeah, then what? I type in the mount -n -o remount,rw /
and I reboot, and again. NO-THING.

---

### Post by penguindrive on 2009-05-19
> **gymophett said:**
> Yeah, then what? I type in the mount -n -o remount,rw /
and I reboot, and again. NO-THING.

You installed wrong, I suggest reinstalling.

Make sure grub is installed to /dev/sda.

And read this if you haven't already: [http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

---

### Post by Polygon on 2009-05-19
it should of had you install grub during the install....

you can always just boot any live cd and install it there

grub
find /grub/stage1
root (whatever the output was above)
setup (same as above)

---

### Post by handy on 2009-05-19
> **penguindrive said:**
> You installed wrong, I suggest reinstalling.

Make sure grub is installed to /dev/sda.

And read this if you haven't already: [http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

+1

If you follow the Beginners Guide to the letter, the only problems you should be vulnerable to are hardware issues.

If you don't follow the Beginners Guide, you will be lucky to find success, at least not without an enormous amount of help from others.

In the time taken doing it the hard way (that is NOT using the Beginners Guide) you could have installed & set up Arch multiple times.

---

