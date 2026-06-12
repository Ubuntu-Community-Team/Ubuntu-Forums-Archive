---
title: "Cannot set up raid 1 during installation"
date: 2009-10-02
forum: Server Platforms
---

### Post by mixmaster on 2009-10-02
I've been trying to install 64 bit server with RAID 1.

Unfortunatey, when I set up the partitions for the raid it is impossible to make them bootable if they are set to "User for Raid".  After installation I end up with an unbootable system with and empty /boot directory.  I have attempted to fix this up in rescue mode but fdisk complains about all sorts of partition limit problems and I can never make anything bootable.

Any suggestions?

---

### Post by lmlypfan on 2009-10-02
I've found this guys tutorial helpful: <url snipped>
Good luck!

---

### Post by mixmaster on 2009-10-03
> Set all sda1 partition to be ext3 and bootable and mounted as /boot, set sdb1 and sdc1 partitions to be Linux Software Raid, bootable, but not mounted. Configure the RAID and create a new RAID device, tell it to use three devices and add to it sda2, sdb2, and sdc2.
This is where I fall down.  The 9.04 64 bit installer will not allow me to set a raid partition as bootable, although most guides tell you to do this.

I'm seriously thinking about installing a downlevel version and then doing a software upgrade in place.

---

### Post by sunstriker on 2009-10-03
This excellent article should help you out, has a lot of information about booting RAID and recovery too.

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/")

---

### Post by mixmaster on 2009-10-03
Ahhh, well, I managed to shoehorn the raid array on via the back door - creating a single boot disk, copying it to a degraded raid on the second disk then resyncing after having patched grubs menu and fstab.

It would appear that in 9.04/64bit the BOOT and RAID flags are incompatible.  Furthermore, install writes a partition table that fdisk does not understand - you have to use parted.

If anyone else has similar issues I used the single-disk to RAID 1 migration method outlined here : [http://www.informit.com/articles/article.aspx?p=1381888&seqNum=2](http://www.informit.com/articles/article.aspx?p=1381888&seqNum=2)

Thanks for the suggestions guys

---

### Post by huuan on 2009-11-06
yeah 9.10 64 bit has same problem. As you say the guides all tell you to set the bootable flag to on but the installer :( won't allow that.
Thanks for a possible way out I will try your solution. :D

---

### Post by huuan on 2009-11-19
mixmaster was right first time.

 I filed a bug about that here:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/477167](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/477167)
but it isn't being taken seriously.

I spent several days trying to get this running and had many bum steers from posts about similar problems.

Finally I looked in the install log and found these two lines:

grub-installer: grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!

grub-installer: grub-setup: error: Embedding is not possible, but this is required when the root device is on a RAID array or LVM volume.


and the penny dropped.

I had wanted to make /boot on a sperate partition for security purposes so why not forget RAID1 for /boot and just do it as a regular bootable partition and put one one each drove, install grub to both.
So I did that and made RAID1 for / and /var in separate partitions. 
I left swap out of the RAID instead going for swap areas on both drives with equal priority.

The install went flawlessly, :popcorn: I have a few tweaks left to make it boot when the first drive fails but for now I am up and running RAID1 on two 2TB SATA drives and its on a mobo with intel ICH10  and an i7 cpu.

Hope this helps some folks.

---

