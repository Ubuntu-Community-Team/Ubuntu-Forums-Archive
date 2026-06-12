---
title: "Boot from degraded mdadm raid6"
date: 2014-01-20
forum: Server Platforms
---

### Post by PavelMan on 2014-01-20
Dear friends, I have done restorations of failed mdad raids a few times in the past, sometimes even successfully ;-). But it feels like when it comes to md0 being a boot device, every time something goes wrong. So I want to try again and to it right this time around, and I need your expert advice here.

1. I have a raid6 md0 drive, which I have assembled at installation, and this raid is the only volume, and I boot from it. 

This makes it particularly important to be able to boot fro it in degraded state. In /etc/initramfs-tools/conf.d/mdadm, I have "BOOT_DEGRADED=true", but when I think about (now, when I type it ;-) ) - this setting will be able to play any role only afterthe partition is mounted, and if one drive fails - it will not.

So, I need to somehow indicate "bootdegraded=[true]" in the kernel boot line. What is the proper way to do it? Or will update-initramfs -k all -u do it automatically?

2. I assume grub is installed on every drive, but is this actually true? Right now one drive has failed, and the array is degraded. Before I reboot to replace the drive, I want to make sure I have done everything I need to make sure the restart will go through smoothly. So, do I need to make sure grub is installed everywhere? Same goes for the "boot" or "active" drive. Do I need to mark one (good) or all of them as "bootable"?

I believe I have read a number of posts on this, but it feels like it is never a complete, unambiguous guide, that works ;-). If you have a "verified" procedure - please, share it with me. Thank you all!

---

### Post by PavelMan on 2014-01-22
So far, since the array is still online, I am rsync-ing all data to an alternative location, just in case. Then I am going to shut the computer down, unplug and test and ship back the drive, as it, most likely, needs to be replaced anyway. Meanwhile, I will try to start the machine with just 4 drives in place...

---

