---
title: "/boot is using ?"
date: 2010-05-12
forum: Server Platforms
---

### Post by PeterK2003 on 2010-05-12
i am getting this "/boot is using 91.2% of 227MB" message.

What should I do?

Thanks,
Peter

---

### Post by oldfred on 2010-05-12
One disadvantage of a separate /boot is that you have to manage space or make it large and waste space.

Uninstall extra kernels:-------------------------
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by PeterK2003 on 2010-05-12
> **oldfred said:**
> One disadvantage of a separate /boot is that you have to manage space or make it large and waste space.


I think i just took the defaults during the install should i have done something different?

---

### Post by volkswagner on 2010-05-12
```
ls -alt /boot/initrd.img*
```

If you have a collection of old initrd.img files you can move them (starting with the oldest).  You may have to comment out the reference of said images in the grub/menu.list file, or you may get a different issue, especially if you try to boot to one.

---

### Post by oldfred on 2010-05-12
You only need a /boot under special circumstances. If you have an old computer that has BIOS limits you need to make sure boot files are at the start of the disk. If you have RAID it is often easier to have boot in a drive outside the RAID array. Servers usually have many of the root folders in separate partitions for management of the server. There is little need for standard desktops to have more than / (root), swap and the often recommended but not required /home.

I only had root and swap with a NTFS shared data partition for about 3 years. I now have separate /home, other data partitions, and other boot partitions.

---

### Post by PeterK2003 on 2011-03-07
> **PeterK2003 said:**
> I think i just took the defaults during the install should i have done something different?

Is there any way to stop using a separate partition without redoing the machine?

---

### Post by bsntech on 2011-03-07
It is possible.

You'd need to boot up in a live CD and copy the /boot structure over to your main hard drive.

Then you'd need to chroot into that directory and install grub.

First, find out what hard drive it is:

sudo fdisk -l

Then after you find out the /dev name of the hard drive that is the one holding everything (including the new /boot folder), do the following:

sudo mkdir /media/new
sudo mount /dev/<HARD DRIVE> /media/new
sudo mount --bind /proc /media/new/proc
sudo mount --bind /dev /media/new/dev

Replace <HARD DRIVE> with the hard drive name - like sda1, sda2, etc.

Now, chroot:

chroot /media/new

And install grub:

grub-install /dev/<HARD DRIVE>

Again, where <HARD DRIVE> is the drive you just copied everything to.

Now, lastly:

update-grub

Power off the PC and remove the old hard drive.  That should do it.

Brian S.
BsnTech Networks
[http://www.bsntech.com]("http://www.bsntech.com/downloads.html")

---

