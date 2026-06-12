---
title: "Customization: initramfs failed to be unpacked"
date: 2020-06-04
forum: Ubuntu/Debian BASED
---

### Post by fweng322 on 2020-06-04
Hi, I'm doing customization from (k/x/L)ubuntu to our own distributions for promoting FOSS and educational use.  We've done it for many years since Ubuntu 6.06.

Before Ubuntu 18.04.1 the initrd inside the iso/casper has its own filesystem structures and we can customize (or copy from live file system) and use cpio and lzma to create an initrd.lz for boot to use.
Since 18.04.4 (maybe?) the structure of casper/initrd is changed.  when using cpio -i < initrd it could no longer show the whole init ramdisk.  

So at that time I extract the live file system (filesystem.squashfs) and then chroot into it, mount /proc /sys /dev/pts, and use mkinitrams -o initrd <kernel_version> and the generated initrd is useful.

When I tried it with 20.04 I got some problems.  Please see what I've tried:

[https://pastebin.com/8sWVyaQe](https://pastebin.com/8sWVyaQe)

I found that using the same way the generated initrd couldn't be booted.  It would show "initramfs unpacking failed: Decoding fail".  I googled a bit and found a solution saying that changing the compress method from lz4 to gzip would solve this issue.  However, when I tried with gzip (or lzma) it would not show the error messages; instead it just directly jump into initramfs, not booting the kernel.

In the pastebin:
Line 31: Get filesystem.squashfs from iso/casper, and extract it in Line 75
Line 99: chroot into the live filesystem, then mount /proc, /sys, /dev/pts
Line 116: use mkinitramfs to generate an initrd in the root of live filesystem
Line 118: During the generation of initrd, it showed  cryptsetup ERROR: couldn't resolve device /dev/sda6 <-- no idea why sda6
Line 119: umount /proc /sys /dev/pts
Line 123: Put the generated initrd into iso/casper, and put live filesystem squashfs into casper/ too
Line 128: Regenerate iso file

The screenshot is at:
 [IMG]https://images.plurk.com/3SFHv4Jgt3PdsLFQpzcnJ5.png[/IMG]

Any help and suggestion will be highly appreciated.  Thanks.

---

### Post by TheFu on 2020-06-08
[https://wiki.ubuntu.com/FocalFossa/ReleaseNotes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes) says they switched to lz4.

---

### Post by VMC on 2020-06-08
That error message is a Red Herring. Look at my [bug report,]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1835660") and several developers stated as such. 
We get that same message even on gorilla ISO's, and it still boots. Something else is causing the issue. 
I went though your re-creation and nothing stands out. Besides this worked for you in the past.

Its been a long time since I compiled a kernel. So this all worked on 18.04 release, but not since updates?
You might try the 20.04 kernel just to be sure.

---

