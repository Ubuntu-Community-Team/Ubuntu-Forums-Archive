---
title: "ubuntu won't start after installation, raid 5"
date: 2013-02-06
forum: Server Platforms
---

### Post by dziadeke on 2013-02-06
Hi,
i have intel S5000 server platform with software raid 5 witch 6 hdd.
After successful installation, ubuntu server won't start (black screen after POST and server restart). I have tried many GRUB repair tools. Here is my log:

[http://paste.ubuntu.com/1596300/](http://paste.ubuntu.com/1596300/)

---

### Post by PowerBarry43 on 2013-02-06
Hi

In the past when I've used software raid I've had to make sure that I have a /boot partition that's separate from the main raid array at raid level 1 which is of course mirroring so sda1, sdb1, sdc1 etc. are all the same. from there you can boot from any into any of these partitions and you will get grub. In hardware raid this wouldn't be necessary as the raid controller would deal with all of this but with software raid, the BIOS doesn't understand software raid partitions.

I now tend not to use software raid and instead favour lvm (Logical Volume Manager) which can be configured with parity like raid 5, the benefit of lvm is that not all of the members of the volume group need to be the same size so you can just have /boot on sda1 and have all the space on the other drives. This may suit your needs better so you may want to look into that.

Hope this helps!

Barry

---

### Post by darkod on 2013-02-06
Yeah, try installing with separate /boot raid1. I am not sure if you need it for raid5 or not. I know for sure you do need it for raid0, and that you do not need it for raid1.

It might benecessary for raid5 too since raid5 splits the files and I think it can't handle the boot files to be split. That's why you don't need it on raid1 since it's mirror and doesn't split files.

I believe LVM is created with a different purpose. While raid array can keep working if a disk fails (depending on the raid level), I am not sure whether LVM would do the same even if you install it with parity. Also, earlier you needed to have separate /boot outside the LVM to work too. Only these days you don't need this any more.

---

### Post by renee3 on 2013-02-06
Use another HDD for /boot partition.

---

