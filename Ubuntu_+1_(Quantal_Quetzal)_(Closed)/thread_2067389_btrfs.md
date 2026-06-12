---
title: "btrfs"
date: 2012-10-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Rukiri on 2012-10-06
I'm curious has anyone tried 12.10 with btrfs? I gave it a go with my funtoo desktop while I had it installed and it was certainly faster than ext4 and had no problems for months.

I'm wondering what the state is with ubuntu?

---

### Post by jbicha on 2012-10-07
I thought btrfs was slower than ext4 but I haven't tried running it in a while.

---

### Post by LiamOS on 2012-10-07
I haven't tried it in Ubuntu, but I've had no btrfs problems with kernels >=3.5.

As for being faster than ext4, it's faster as long as COW isn't holding it back.

---

### Post by Rukiri on 2012-10-07
The only issue I'm seeing with ubuntu + btrfs is if you want multi-device for a specific mount like '/'   but this is only if you use the ubuntu installer and not if you install ubuntu manually. 

The ubuntu installer only lets you have one mounted drive per device and that kinda sucks because I prefer the way zfs/btrfs handle multiple devices over using an LVM because the pool is direct with the hardware where as lvm is an abstract layer/software layer.

Or should I just stick with LVM + raid0 and than just the logical volume as btrfs?

I'm going to see if 
btrfs device add /dev/sdb /mnt after the install as I can't seem to add sdb to / during the install as I can only have 1 mount per mount location.

---

### Post by Rukiri on 2012-10-07
I decided to give btrfs a try, and while I made a previous topic it'd be better if we started clean.

With zfs or btrfs you do not have to use lvm as they can handle volumes perfectly. however most documentation you find is generic and generally meant if your installing from scratch which you would if your using the server edition(well you should).  

The reason why you don't have to use lvm or you should not use lvm is because lvm is abstract/software layer and can cause slow boot times, or even slow application loads.  I have about 12TB of disk space using 1TB SSDs(yes, crazy expensive) but only 1 is an actual SD and the others are 4TB and 1TB drives.

So for installation here is what you may want to use for your partition layout.
256MB for boot
2XRAM for swap (for me it's 128GB) but on this machine it's 16gb so X2 is 32GB.
The rest will go for btrfs.

now for the other drives just create 1 partition and partition them as btrfs.

Now install ubuntu like normal.

Now once you boot into your system your going to need to do the following.
btrfs device add /dev/xxx /xxx (XXX is what your device and mount points are) 
if you used the ubuntu installer it would create 2 sub volumes @ and @home, so the mount point is /home.

Well, now your using btrfs in ubuntu and expect a quicker boot, it takes 1 second to boot past my bios screen so I seriously can't wait for a stable release! (1 second gets me to the login, 3-5 seconds to where I can start working)

For production environments BTRFS can work but never ever ever save anything on your drives, use external hard drives, flash drives, thumb drives, floppies, anything but on your hard drives.

You may notice 1 crash or 2 but I've noticed nothing and actually find btrfs pretty stable moving large files around.

I personally would not use ZFS and actually find btrfs not only a replacement(when stable) but in many ways better.  
ZFS and BTRFS are both unstable in linux, use at your own risk.

---

### Post by Elfy on 2012-10-07
merged

---

### Post by scradock on 2012-10-07
I've been using BTRFS for one of my PP installs (alongside 2 QQ test installs), and have one major problem - GRUB does not include the BTRFS install as a boot option. I have to add it as a 40_custom file and edit by hand whenever the kernel version changes.

Other than that, I'm not experiencing problems.

Does anyone have any ideas about getting GRUB (1.99 or 2.00) to recognize and include a BTRFS install in a normal boot list?

---

### Post by LiamOS on 2012-10-09
This seems more like an upstream problem with grub. Perhaps it's a feature in development?

---

### Post by benmoran on 2012-10-10
What problems with grub? There is a sparse file warning, but I've been running many pure btrfs Ubuntu installs recently. All have btrfs / with no seperate boot partitions. The 12.10 beta 2 (Gnome version) installs to Btrfs fine, as I've just done it today. 

Af for multi device files systems, it's fairly easy to set up after the fact. Say you have two disks:
**   /dev/sda**
**   /dev/sdb**
Just do your installation to /dev/sda. Don't touch /sdb during the install. After the system is running, format sdb as btrfs and install the "btrfs-tools" package. 
Then do a:
**sudo btrfs device add /dev/sdb1 /**
or similar, depending on what your devices are. By default, this command will combine the two devices into a RAID1-ish array. After you add the disk, do a balance. A balance will take care of the initial data duplication, and only has to be done once. It's:
**sudo btrfs balance start /**   or similar. 


Btrfs is a really nice file system, but does take some learning if you want to take advantage of the advanced options.

---

### Post by gspe on 2012-10-10
> **benmoran said:**
> What problems with grub? There is a sparse file warning, but I've been running many pure btrfs Ubuntu installs recently. All have btrfs / with no seperate boot partitions. The 12.10 beta 2 (Gnome version) installs to Btrfs fine, as I've just done it today.

You can take a look here [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/736743]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/736743") and here [http://askubuntu.com/questions/100329/message-sparse-file-not-allowed-after-succesfull-install-without-swap-partitio]("http://askubuntu.com/questions/100329/message-sparse-file-not-allowed-after-succesfull-install-without-swap-partitio")

---

### Post by benmoran on 2012-10-11
Yes, but that is non-critical, is it not? The bug was reduced to wishlist level. A fix will be available in the future, but booting is not affected currently anyway. 

If there is any concern, it's easy to make a few hundred MB boot partition if desired. I don't bother anymore, though.

---

