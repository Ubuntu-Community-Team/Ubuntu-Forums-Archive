---
title: "Virtual Box raw disk/grub  problem"
date: 2009-12-15
forum: Virtualisation
---

### Post by aikiko on 2009-12-15
Hello,

I have problem with mounting an existing Win7 partition on VirtualBox.

Ubuntu 9.10 AMD64
VirtualBox non free 3.1 
Win 7 64

I followed the tuto for Vista from here : 
[http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

The only thing a changed is the -partitions 1,3,6 
sda1 is the small boot partition from Win7, sda3 is the Win7 partition and sda6 is some extra ntfs partition :

VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/Win7.vmdk -rawdisk /dev/sda -partitions 1,3,6 -relative -register

I read that the iso file has to be able to read from the Virtual Machine so i put it on C: 

The Grub is starting fine but then I got Error 15 : File not found
I think some changes to the menu.lst has to be done but no idea what it is.

---

