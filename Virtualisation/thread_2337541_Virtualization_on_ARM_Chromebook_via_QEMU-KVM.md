---
title: "Virtualization on ARM Chromebook via QEMU-KVM"
date: 2016-09-19
forum: Virtualisation
---

### Post by verdigris2 on 2016-09-19
Hello everyone:I have an ARM Chromebook and need to run 2 programs:QGIS: Available on Ubuntu but not on ARM archictecturePythagoras: A Windows database programThe best solution that I have come up with is to run Ubuntu (XFCE) via Crouton, then run a 32bit virtual machine (Puppy Linux 6.0 Tahr CE) via QEMU-KVM. This is very cumbersome, so if anyone comes up with a better suggestion, please let me know! I have been following instructions at [https://www.unixmen.com/how-to-install-and-configure-qemu-in-ubuntu/](https://www.unixmen.com/how-to-install-and-configure-qemu-in-ubuntu/) and have run into several errors:1) After running qemu-system-x86_64 -hda ubuntu.img -boot d -cdrom /home/sk/Soft_Backup/OS\ Images/New/ubuntu-15.04-server-amd64.iso -m 640The Puppy Linux boot screen shows up, but when I hit "enter" to install, I get a segmentation fault (core dumped).2) When I tried opening up the Virtual Manager GUI, I got the error "Unable to connect to libvirt"-I have checked that the libvirt-bin package is installed-I am a member of the libvirtd group-I have tried running Virtual Manager with gksudo-The error message recommends checking that the libvirtd daemon is started----not sure how to check thisAny help would be greatly appreciated. Thank you!

---

### Post by MAFoElffen on 2016-09-20
Reformatted so that others may be able to read the original post easier:
> **verdigris2 said:**
> Hello everyone:

I have an ARM Chromebook and need to run 2 programs:
 - QGIS: Available on Ubuntu but not on ARM archictecture
 - Pythagoras: A Windows database program

The best solution that I have come up with is to run Ubuntu (XFCE) via Crouton, then run a 32bit virtual machine (Puppy Linux 6.0 Tahr CE) via QEMU-KVM. This is very cumbersome, so if anyone comes up with a better suggestion, please let me know! 

I have been following instructions at [https://www.unixmen.com/how-to-install-and-configure-qemu-in-ubuntu/](https://www.unixmen.com/how-to-install-and-configure-qemu-in-ubuntu/) and have run into several errors:
1) After running ```
qemu-system-x86_64 -hda ubuntu.img -boot d -cdrom /home/sk/Soft_Backup/OS\ Images/New/ubuntu-15.04-server-amd64.iso -m 640
```The Puppy Linux boot screen shows up, but when I hit "enter" to install, I get a segmentation fault (core dumped).
2) When I tried opening up the Virtual Manager GUI, I got the error "Unable to connect to libvirt"-I have checked that the libvirt-bin package is installed-I am a member of the libvirtd group-I have tried running Virtual Manager with gksudo-

The error message recommends checking that the libvirtd daemon is started----not sure how to check thisAny help would be greatly appreciated. Thank you!
Reformatted in a organised and logical format, it may be easier for others to follow, read and understand what you were trying to say and were asking. I hope that helps.

There are two resources which I would read and follow in the diagnostics of your problem.
As it relates to Libvirt specifically:
[https://help.ubuntu.com/community/KVM/Installation#Verify_Installation](https://help.ubuntu.com/community/KVM/Installation#Verify_Installation)
Then this:
[http://wiki.libvirt.org/page/The_daemon_cannot_be_started](http://wiki.libvirt.org/page/The_daemon_cannot_be_started)
 
Libvirt is a virtualization management library, that consists of three utilities:
 &#8211; an API library
 -  a daemon (libvirtd) 
 - the virsh command line tool -virsh. 

Libvirt is quite effective and it can manage a lot of hypervisors altogether. It is not a hypervisor, but rather a it is a hypervisor toolset. 

The hypervisor you are using is QEMU, which is a software based emulator/translator, that when used alone, is without any hardware virtualization.Meaning with a 64bit processor, you can run 32bit VM Guests.

---

