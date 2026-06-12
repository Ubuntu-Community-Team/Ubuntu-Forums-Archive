---
title: "ZFS and encryption for root file system"
date: 2019-10-10
forum: Ubuntu, Linux and OS Chat
---

### Post by david509 on 2019-10-10
I don't know if this is the right place to post, but would it be possible in (the near) future to have *native* encryption in ZFS on Ubuntu? 

I'm aware that 19.10 will have experimental support for ZFS as the root file system.

Also on the subject of encryption: is it possible, with ZFS native encryption, to fully encrypt the whole drive (or partition) where Ubuntu is installed?

---

### Post by TheFu on 2019-10-10
Out today.  [https://arstechnica.com/information-technology/2019/10/a-detailed-look-at-ubuntus-new-experimental-zfs-installer/](https://arstechnica.com/information-technology/2019/10/a-detailed-look-at-ubuntus-new-experimental-zfs-installer/)  Jim knows his ZFS and storage in general. He's a nice person to boot.

> assuming the final version of Eoan follows this one, we'll get ***native encryption***, TRIM, device removal, and zpool checkpoints. These features have been in the ZFS on Linux master since 0.8, but this is the first time they've shown up in Ubuntu's native ZFS.

---

### Post by cruzer001 on 2019-10-10
Not real sure what this means to full encryption users, but found this.
[https://www.phoronix.com/scan.php?page=news_item&px=ZFS-On-Linux-0.8-Released](https://www.phoronix.com/scan.php?page=news_item&px=ZFS-On-Linux-0.8-Released)

@TheFu
Thanks for the link.  I am also trying to keep up on ZFS and what will happen in 20.04 testing.

---

### Post by kevdog on 2019-10-10
Does the Linux mainline kernel ship with ZFS drivers?  I thought this was necessary for it to boot?

---

### Post by Matthew_John_Bulfi on 2019-10-21
I put 19.10 on a virtual drive, and enabled the ZFS filesystem by default. The only thing I've really noticed is higher-than-anticipated memory usage (~50%). But that's supposed to be normal as I understand it. And wasted RAM sucks :D

---

### Post by lammert-nijhof on 2019-10-21
That memory is NOT wasted, it is used as memory cache L1ARC! Which means that approx 90% of your disk IO will be served from the L1ARC (see arc_summary), resulting in instantaneous response times. You can limit the maximum size by changing the corresponding parameter at /sys/module/zfs/parameters/zfs_arc_max. For a desktop/laptop I limit the size to 20-25% of my memory size.

---

