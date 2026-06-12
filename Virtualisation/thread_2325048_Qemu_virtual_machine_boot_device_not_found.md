---
title: "Qemu virtual machine boot device not found"
date: 2016-05-18
forum: Virtualisation
---

### Post by Nayab Basha Sayed on 2016-05-18
I have been using Ubuntu 16.04 64 bit OS. I tried to install Core-current.iso linux image in qemu virtual machine. I've followed the steps mentioned in the link
[https://help.ubuntu.com/community/Installation/QemuEmulator](https://help.ubuntu.com/community/Installation/QemuEmulator)
Following are the steps I've done to create qemu emulator for Core-current.iso

```
me@linux:~$ qemu-system-i386 -hda linux.qcow -boot d -cdrom ~/Desktop/Core-current.iso -m 512
me@linux:~$ qemu-system-i386 -hda linux.qcow -cdrom ~/Desktop/Core-current.iso -m 512

```
I think OS installed successfully using above commands. But when I access that installed OS through following command, it's showing 'no boot device' message.



```
me@linux:~$ qemu-system-i386 -hda linux.qcow -m 512

```
Following is the output on qemu-emulator:
> Nothing to boot: No such file or directory ([http://ipxe.org/2d03e13b](http://ipxe.org/2d03e13b))
No more network devices


No bootable device
So how to make this work.....?

---

