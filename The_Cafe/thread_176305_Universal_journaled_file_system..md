---
title: "Universal journaled file system."
date: 2006-05-14
forum: The Cafe
---

### Post by YourSurrogateGod on 2006-05-14
I've recently bought a new hard-drive and I would like to put into my PC in such a way so that I could read/write to it from Windows and Ubuntu. Anyone know of such an FS? Remember, it has to be journaled.

---

### Post by tkjacobsen on 2006-05-14
There are plenty of windows drivers for ext3 file systems. Try to check out: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

### Post by Seq on 2006-05-14
Unless somebody can prove otherwise, I don't think you will be able to have a filesystem that is both jorunaled and accessible from Linux and Windows.

A previous poster already pointed to the windows ext2 IFS driver. This is actually an ext2 driver, and works with ext3 filesystems by mounting them as ext2 -- ext3 is basically just ext2 + an optional journal. You would only have the journalling features in Linux.

NTFS is right out due to sketchy write support on Linux.

Personally I favour Fat32 as I've also got a Mac i need compatability with.

---

### Post by YourSurrogateGod on 2006-05-14
[QUOTE=Seq]Unless somebody can prove otherwise, I don't think you will be able to have a filesystem that is both jorunaled and accessible from Linux and Windows.

A previous poster already pointed to the windows ext2 IFS driver. This is actually an ext2 driver, and works with ext3 filesystems by mounting them as ext2 -- ext3 is basically just ext2 + an optional journal. You would only have the journalling features in Linux.

NTFS is right out due to sketchy write support on Linux.

Personally I favour Fat32 as I've also got a Mac i need compatability with.[/QUOTE]
Damn... I knew I could do that, but wasn't sure if I could get journaled support as well.

---

### Post by YourSurrogateGod on 2006-05-14
Ok, question number two. How would I mount the hard-dirve (after I connected it) and then form an ext3 partition on it?

---

### Post by aysiu on 2006-05-14
[QUOTE=YourSurrogateGod]Ok, question number two. How would I mount the hard-dirve (after I connected it) and then form an ext3 partition on it?[/QUOTE] You'd actually want it *not* mounted if you're going to format it. If it automounts, unmount it. Then ```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
``` Use GParted to reformat it as Ext3.

---

### Post by YourSurrogateGod on 2006-05-14
[QUOTE=aysiu]You'd actually want it *not* mounted if you're going to format it. If it automounts, unmount it. Then ```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
``` Use GParted to reformat it as Ext3.[/QUOTE]
Thanks. I'll try that.

---

### Post by sup on 2006-05-14
if gparted for some reason does not work for you (it does not for me), you can always use terminal utilities cfdisk/fdisk (whichever you will like better,they are pretty straightforward I think) for creation of a partition table and then use mkdosfs or mke2fs to actually create the filesystem. Hint:do not forget to se&#7831; volume label/name, it will be used fot automounting then so that the volume always mounts in the same place (/media/volume_label)

---

### Post by YourSurrogateGod on 2006-05-14
Ok, I just did something very n00bish and stupid. I didn't check if my case had a free 3.5 inch slots available before buying a hard-drive (it's an HP.) Turns that there is only one there and that is occupied by my current hard-drive. Now I need to get a kit so that I could convert my internal hard-drive into an external one :roll: .

---

