---
title: "growfs after increasing Ubuntu Guest OS Virtual Disk"
date: 2009-02-22
forum: Server Platforms
---

### Post by shebangs on 2009-02-22
VMWare ESXi 3.5 I have a Ubuntu JeOS Hardy guest.

It was a simple deployment, 10G disk with automatic guided disk partitioning during the install.  

This created (as expected) the following partitioning:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.5G  5.9G  3.2G  66% /
varrun               1014M   64K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   40K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm

```


For the identical task on Windows, it's trivial.  Shutdown the OS, increase size, boot into gparted and 'resize' by dragging the NTFS partition all the way across.

How do I do this with Ubuntu Server?  When I tried booting into gparted, it showed me the below.  It didn't allow me to 'move' the swap to the end.  If it allowed me to do that, I would have moved it to the end then resized root.


[[IMG]http://img18.imageshack.us/img18/618/gparted.th.jpg[/IMG]](http://img18.imageshack.us/my.php?image=gparted.jpg)

Any thoughts? 

I'm sure this is pretty standard and many many people have done what I'm trying to do.

Cheers

---

### Post by shebangs on 2009-02-23
I thought I'd mention the fix here because it's already number 1 hit for "Increasing Ubuntu Guest OS Virtual Disk"

You need to do the following:
[LIST=1]
[*]Boot gparted live CD
[*]Click on the *extended partition* at the bottom and click *Resize/Move* at the top.  Drag it all the way across to the right thus making it take up the remaining unallocated space.
[*]Click on the *linux-swap* partition at the bottom, click *Resize/Move* and drag it across to from the left to the right.  Don't resize, move.
[*]Now *resize* the *Extended* partition from above, and shrink it.  Drag it from the left to the right so it's just the extended partition and the swap space taking up the right most of the disk.
[*]Now *resize* the left most primary root partition *ext3* to utilize the unallocated space in the middle of the drive.
[*]Apply changes, and reboot.
[/LIST]

Being VMWare, it's quick, easy and wise to perform a quick offline backup before making these changes.  

[LIST=1]
[*]Shutdown VM
[*]vmkfstools -i source.vmdk backup_source.vmdk
[/LIST]

---

