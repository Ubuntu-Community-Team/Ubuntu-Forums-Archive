---
title: "wrong drive... lvm grub root problem"
date: 2010-06-14
forum: Server Platforms
---

### Post by howardtan on 2010-06-14
Hi,

So when I install 10.04 LTS server with all the defaults. ie root parted with lvm, I get a grub error. Apparently the install script at the end of the installation does not take into account that I might install ubuntu on a different drive.

Without LVM, I can get it to work. If I drop down to shell and mount the root drive, then run: 

grub-install --root-directory=/ /dev/sdc

And all is good. But I want LVM on my boot drive. Does anybody out there know of an easy way of doing this? 

This really should be a bug. But I'm too much a noob to know where to issue this.

Thanks,
Howard

---

### Post by howardtan on 2010-06-14
Nevermind. I figured it out.

boot Livecd...
disk utility...
mount boot drive (ext2,256mb) to /media/boot
terminal...
sudo grub-install --root-directory=/media/ /dev/sdc
reboot

and life is good.

---

