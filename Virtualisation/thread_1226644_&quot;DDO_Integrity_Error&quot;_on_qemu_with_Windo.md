---
title: "&quot;DDO Integrity Error&quot; on qemu with Windows 3.1"
date: 2009-07-29
forum: Virtualisation
---

### Post by pytheas22 on 2009-07-29
I'm trying to boot a disk image I took of an old Windows 3.1 system.  I can mount the image as a loopback device in Linux without any errors or warnings and access its files, and gparted can read its partition table.  When I try to boot to it in qemu, however, I immediately get the message "DDO Integrity Error."  I'm not sure what this means (not much information available from Google), and am wondering if this is possibly a problem related to qemu.  The last time I booted the drive in the computer that it came from, which was a couple years ago, it worked fine, but I'm thinking maybe the Windows 3.1 system doesn't like how qemu is emulating the BIOS or hardware.

Also, the disk image I'm using is just a raw image created using a command like "dd if=/dev/sdb of=windows3.1.img".  Could this pose a problem?  Do I need to convert to a qcow image?

I'm grateful for any suggestions on how I might make this work.  I'd love to play with my first computer again without having to use the original hardware.

---

### Post by pytheas22 on 2009-08-01
In case anyone else reads this: I tried booting the disk in VirtualBox instead of qemu, and had more success.  Windows wouldn't start at first because it complained about various driver issues, but I was able to resolve them by booting to a DOS boot floppy image and running c:\windows\setup.  There are still a few weird problems that I assume are related to Windows not liking the virtualized hardware, and sound doesn't work (I didn't try at all to fix that because it's not important), but the system is usable now.

So if you're in a similar situation, my recommendation is to try booting under VirtualBox.

---

