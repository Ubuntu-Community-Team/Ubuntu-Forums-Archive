---
title: "ubuntu 5.1 and Fedora Core 4 dual s/w RAID-0 boot"
date: 2005-09-20
forum: The Cafe
---

### Post by adunphy on 2005-09-20
I have two 160 GB drives (identical).  I currently have ubuntu 5.1 setup with software RAID 0 with a partition for /dev/md0--> "/" (ext3)  and a /dev/md1 --> "swap".  I also have a partiton for the boot loader /dev/hda3 --> "/boot" which only exists on one drive,(i.e. is not a RAID partition)

This works great and is super fast.  The software RAID seems to work ok for the root filesystem but would not work for "/boot" so thats why i created the partion on only 1 drive so it would be visible during boot.

The quesion is..... Can I also install Fedora in addition to ubuntu 5.1 and install it on a RAID 0 setup just like I did for ubuntu 5.1?  I have spent hours  in disk druid with no luck.  I keep getting error messages regarding the /dev/md2, ... devices.  When I finally did get through the druid, and the install started, it threw an error saying it was unable to initialize the /dev/md1 device which is my swap partition for ubuntu, not fedora.  Not sure why it even tries to touch this???

Has anyone done this dual boot of software RAID 0 linux OS's?  Any help would be appreciated.

-adunphy

---

