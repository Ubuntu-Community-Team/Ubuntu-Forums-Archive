---
title: "Ubuntu 14.04 and shared folder virtual box"
date: 2015-09-15
forum: Virtualisation
---

### Post by tom206 on 2015-09-15
Hi,

i have Ubuntu 14.04 as a virtual machine in virtualbox.
In my virtualmachine i have added a shared folder clicking in Devices -> Shared Folders Settings and added a Machine Folder (Folder name: "website" and checked only "Make Permanent").

So in /etc/fstab i have added the following line (i must give write and read permission to all):
website /media/sf_website   vboxsf  rw,uid=33,gid=33,dmode=777,fmode=777    0   0

If i give the command mount -a all is ok.

The problem is when i reboot the machine. I get the following error:
/sbin/mount.vboxsf: mounting failed with the error: no such device.

What's the problem? I have installed the guest addition in the ubuntu with the option ->Devices ->Insert Guest Addition CD Image.

My host pc is Linux Mint.

---

### Post by jdeca57 on 2015-09-15
You're making it way too complicated. Do not mess with fstab. On the host, set automount and full access for the shared folder website in VB.
After installing the guest additions there is a vboxsf in /etc/group and you need to add your user to that.
Reboot.
Afterwards, you find that /media/sf_website is rw accessible by the user you added to vboxsf.
(Host: Ubuntu 14.04, guest Ubuntu 15.04)

---

