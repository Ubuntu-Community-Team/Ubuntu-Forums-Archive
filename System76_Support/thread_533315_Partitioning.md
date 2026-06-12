---
title: "Partitioning"
date: 2007-08-23
forum: System76 Support
---

### Post by palintheus on 2007-08-23
I know that when you image the machines you use LVM, under LVM is there a way to have a seperate /home, incase of reinstalls, or if I was to use 2 distro's? 

The reason I am asking is because I re-imaged my machine to ext3 with a /boot, /, /home, and swap. But, if this is possible with LVM, I would prefer to use it since I could grow/shrink partitions on the fly. 

If this is possible, is there a way to convert my current setup to LVM, if not, will the thread regarding the new Santa Rosa chips and the custom LiveCD work to get me back to a usable desktop right after install. Before I had to use an alternate cd and install xorg-xserver-video-intel and mess around with the xorg-xserver reconfigure tool.

If I need to clarify anything, let me know.

EDIT: I have found this, and it gives me hope about converting, but don't quite follow it.
[http://www.linux.com/feature/118645](http://www.linux.com/feature/118645)

---

### Post by octathlon on 2007-08-23
Hope this isn't a distraction, but I wondered about the partitioning too.  I noticed that the / partition was LVM, and /boot was a regular partition.  
I wondered if I could shrink it and then make a separate partition for my data using gparted, just like I would do with a regular partition, or if doing that would mess up the LVM.

I also noticed that sudo fdisk -l did not list a swap partition, yet System Monitor|Resources does show 4 GB swap available.

---

### Post by thomasaaron on 2007-08-24
First of all, forget what I said about LVM partitioning being necessary for suspend/hibernate. I was mistaken about that.

Second, I've found it quite difficult to resize LVM partitions on our current setup. So, if you want to dual boot, you don't want to start by setting up your entire HD with LVM. To shrink an LVM partition, you have to remove Physical Volumes (I think I have the terminology right, there). There are none on our setup to remove, so you can't shrink the LVM volumes.

Third, A quick google search indicates that you can set up separate home partitions with LVM. EVMS is a tool that might be useful for this. 

Fourth, I think I've read that you can convert other FS's to LVM, but, after messing around with LVM's, I'm not sure I'd want to deal with the risk/hassle. It only takes an hour to back up and cleanly re-install. Just my opinion.

---

### Post by palintheus on 2007-08-24
OK, so there should be no issue with my current setup, and since I have it setup this way, will I ever need more than 10G for /

---

### Post by octathlon on 2007-08-28
BTW, What would be the advantage of using LVM for the whole drive on a laptop? Since you won't ever be adding additional drives, you won't be able to increase the logical volume size, and it prevents you from shrinking the partition?

---

