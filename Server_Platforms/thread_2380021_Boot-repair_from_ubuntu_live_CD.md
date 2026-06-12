---
title: "Boot-repair from ubuntu live CD"
date: 2017-12-12
forum: Server Platforms
---

### Post by dascencio-opt on 2017-12-12
Hi Guys, i have a problem my system i not booteable. This is My URL to check my partition table:


[http://paste.ubuntu.com/26170246/](http://paste.ubuntu.com/26170246/)


It's recommended automatic repair with boot-repair app?






Regards.

---

### Post by oldfred on 2017-12-12
Moved to server sub-forum as those that know RAID may then be able to help.

Do not run any autofix with Boot-Repair. Especially if you have more than one drive (or more than one install).
You may be able to use advanced mode, it you want grub2?

I do not know RAID, but it looks like you are booting from sdf?
And sda is missing? Is that a RAID issue?

You also show syslinux boot loader on sdf. Normally grub2 is used with full installs. But Ubuntu installer does use syslinux for BIOS boot.
Boot-Repair is recommending reinstalling grub, but with a gpt partitioned drive you need a bios_grub partition 1 or 2MB unformatted with bios_grub flag if using gparted or code ef02 if using gdisk.
I gather syslinux with gpt does not need the bios_grub partition. Seen 100's of installs, usually syslinux is used for Windows boot.
And most do use grub2, now.

Your sdf2 is also not shown. Does it need file repair?

And you have mount of ISO in fstab, which is a bit unusual.

---

### Post by yancek on 2017-12-12
You might have to wait awhile for a response as you are using LVM and RAID and many users here are not familiar with either.  My understanding of LVM is that it requires a separate boot partition which I don't see on any of the drives?  I'm not familiar with whatever Xenserver is either.  You don't have the Grub bootloader anywhere outside the installation usb.   It also tells you at the end of the output that with GPT partitioning you need a BIOS boot partition which you do not have.  Apparently, you should create this on sdf (150GB drive) and then install Grub from it to the MBR and then set that drive to first boot.  You may have to use Advanced options so it doesn't install Grub on every device.

---

