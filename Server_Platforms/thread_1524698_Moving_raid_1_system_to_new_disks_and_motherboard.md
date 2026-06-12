---
title: "Moving raid 1 system to new disks and motherboard"
date: 2010-07-05
forum: Server Platforms
---

### Post by Gone fishing on 2010-07-05
1.How to move a raid 1 box (root on raid) to new hardware. I've Googled this for some time and not found the answer – last weekend I, I should say we me and devi1903 solved the problem.

What doesn't work is shifting the hard drives or cloning them and the putting them in the new box booting from a Live cd and then rebuilding the raid 1 using mdadm and rebuilding grub. Unfortunately the UUID of the old Raid 1 is in the mdadm.conf of the initrd image. We tried pulling this apart and changing the UUID but the one you get from a live disk is not correct and it still wont boot.

Why blkid and mdadm report different UUIDs why the UUID in  initrd image is different I don't know?  There may be a way of fixing this from the initramfs, but if there is we could find it.

This however, does work:

1.Make an new raid similar to the one you wish to use on a new pair of disks in the new box.
2.Install a minimal version of the Linux on the new box then update it to the same as the original box (we didn't do this and so had to update later)
3.Copy fstab, the boot directory and mdadm.conf to a flash drive or similar.
4.Take the disks out of the new box. Turn off the old box and add the new disks reboot on a live CD (we used parted magic)
5.run mdadm --examine – scan  >>  mdadm.conf  then  mdadm –assemble –scan 
6.Mount the old raid and the new raid
7.Copy the files from the old boxes raid to the new boxes raid (don't forget to use the -p switch)
8.Merge the /boot from the flash disk to the new raid and copy over the mdadm.conf and fstab replacing any old files.
9.Place the new raid disks into the new box. Boot from a live cd and using mdadm --examine – scan  >>  mdadm.conf  then  mdadm –assemble –scan repair the raid so that it has the right name /dev/md0 for example.
10.Reboot and your done.
11.If you didn't update (like we didn't) you will need to update the kernel to the same as the original box.
12.Hopefully you are now done other than reconfiguring the networking.

Have fun

---

### Post by Devi1903 on 2010-07-08
This does work. However i would also be interested to hear if anyone knows how to run initramfs to rebuild the kernel when you have a system that cannot boot. Which is basically what we had when we had swapped the hdds onto the new hardware.

---

