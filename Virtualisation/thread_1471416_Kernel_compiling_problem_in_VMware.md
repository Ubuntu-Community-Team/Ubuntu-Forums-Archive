---
title: "Kernel compiling problem in VMware"
date: 2010-05-03
forum: Virtualisation
---

### Post by pepsifx357 on 2010-05-03
Hey guys, I have a VMware server set up and I was compiling 2.6.33.3 inside a virtual machine.

I'm not an experienced compiler, but I keep running into this kernel panic when rebooting into the new kernel.

[    1.788318] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown wn-block(0,0)
root  (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.33.3 root=/dev/sda1 ro quiet
	[Linux-bzImage, setup=0x3600, size=01d61e0]

I've compiled this 4 times now, and can't seem to figure out what is causing it.  It looks like the kernel can't find the hard drive or something, but I don't know what buss hardware that VMware emulates.

---

### Post by pepsifx357 on 2010-05-04
Bump?

---

### Post by burgechris on 2010-05-04
Exact same issue but for 32

---

### Post by pepsifx357 on 2010-05-09
I think I know what it is.  I tried running knoppix, to try it out, and got the same error.  So it looks like you have to change your SCSI-0 drive in VMware to an IDE-0 drive.  Or whatever numbered drive you have, as long as you change it to IDE.  Unless you know the exact SCSI hardware that VMware emulates, and then add it to the kernel at the make-menuconfig stage.  Someone said the IDE hard drives/Busses in VMware were slow...??  Don't know about that one, but whatever works.

Hope this helped!

Ben

---

