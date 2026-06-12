---
title: "USB drive from command line"
date: 2007-05-17
forum: Server Platforms
---

### Post by chimerical_brio on 2007-05-17
So I've recently set up a computer with Ubuntu Server edition to check it out, get comfortable with it. But I need to install ndiswrapper, because it currently has no internet access, so I need to transfer files over using my USB drive. How do I find/use my USB drive? I guess I need to mount it, how do I do this from the command line? Thanks a lot.

---

### Post by gradedcheese on 2007-05-17
Just plug it in, and it should be mounted in something like /media/usbdisk (look in /media after a few seconds and see).  if not, then look at dmesg to see how the drive was recognized and what device it came up as.  Usually these come up as SCSI disks, for example /dev/hda0, and you can mount it like this:

sudo mkdir /mnt/usbdisk
sudo mount /dev/hda0 /mnt/usbdisk

If it's a FAT (windows) formatted disk,

sudo mount -t vfat /dev/hda0 /mnt/usbdisk

If it's not the first partition that you need, change the 0 to a 1 and so on...

---

