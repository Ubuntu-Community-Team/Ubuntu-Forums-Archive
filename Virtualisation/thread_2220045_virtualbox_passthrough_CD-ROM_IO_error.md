---
title: "virtualbox passthrough CD-ROM IO error"
date: 2014-04-26
forum: Virtualisation
---

### Post by asgard2 on 2014-04-26
Hi,

since upgrading to 14.04 on all my machines, passthrough is not working anymore on the windows VM's.

I tested:
Lubuntu 64 Bit 14.04 (upgraded) - not working
Xubuntu 64 Bit 14.04 (upgraded) - not working
```
ii  virtualbox                                                   4.3.10-dfsg-1                         amd64        x86 virtualization  solution - base binaries
ii  virtualbox-dkms                                              4.3.10-dfsg-1                         all          x86 virtualization  solution - kernel module sources for dkms
ii  virtualbox-guest-dkms                                        4.3.10-dfsg-1                         all          x86 virtualization  solution - guest addition module source for dkms
ii  virtualbox-guest-utils                                       4.3.10-dfsg-1                         amd64        x86 virtualization  solution - non-X11 guest utilities
ii  virtualbox-guest-x11                                         4.3.10-dfsg-1                         amd64        x86 virtualization  solution - X11 guest utilities
ii  virtualbox-qt                                                4.3.10-dfsg-1                         amd64        x86 virtualization  solution - Qt based user interface


```
Lubuntu 64 Bit 14.04 (clean install) - not working
Ubuntu 13.10 64 Bit - working
```
    ii  unity-scope-virtualbox                        0.1+13.10.20130723-0ubuntu1             all          VirtualBox scope for Unity
    ii  virtualbox                                    4.2.16-dfsg-3                            amd64        x86 virtualization solution - base  binaries
    ii  virtualbox-dkms                               4.2.16-dfsg-3                            all          x86 virtualization solution - kernel  module sources for dkms
    ii  virtualbox-ose                                4.1.18-dfsg-1ubuntu1.1                  all          transitional package for virtualbox
    ii  virtualbox-qt                                 4.2.16-dfsg-3                            amd64        x86 virtualization solution - Qt  based user interface


```
Lubuntu 12.04 LTS 32 Bit (clean install) - working

It is irrelevant if I use windows 7 or windows xp as guest.

I also tested the virtualbox versions from [virtualbox.org]("https://www.virtualbox.org/wiki/Linux_Downloads"), the raring deb Package, the Repo and the "All distributions" variant. It is the same problem.

If I try to use the a burnung program it is stuck at scanning for devices and the vm is not reacting anymore, most time it is not possible to close the vm at the host.

Here is the virtualbox log from lubuntu, virtualbox (all versions 64bit) from virtualbox.org installed:
[http://pastebin.com/5EE1sjZ1](http://pastebin.com/5EE1sjZ1)

```
00:00:19.939822 PIIX3 ATA: LUN#2: CD-ROM passthrough cmd=0x28 sense=5 ASC=0x21 ASCQ=0x0 VERR_DEV_IO_ERROR
```

[http://pastebin.com/MhApuXeK](http://pastebin.com/MhApuXeK)
```
00:03:35.410618 PIIX3 ATA LUN#2: Async I/O thread probably stuck in operation, interrupting
00:03:35.420561 PIIX3 ATA LUN#2: Async I/O thread probably stuck in operation, interrupting


```



Can someone help me, please?

Regards

EDIT:
The problem only exist with an emulated IDE drive (passthrough).

If I try windows 7 and an emulated sata drive (passthrough), the drive is working.

---

### Post by asgard2 on 2014-04-30
hm...nobody with the same problem?

If not, can some try this with the same conditions at ubuntu 14.04?
It would be strange, if the bug only exists at my machines.

bug report: [https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1312459](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1312459)

---

### Post by QIII on 2014-04-30
If you could spare one of your machines for a bit and install an rpm-based distro (Fedora 20 installs quickly) and fully update it, try that as your host and see what happens.  It would be good to know if this is isolated to the deb side.

If you have time and the resources, of course!

---

### Post by asgard2 on 2014-04-30
I tested at fedora with the [repo]("https://ask.fedoraproject.org/en/question/40926/trying-to-install-virtualbox-or-vmware-fedora-20/") ([http://download.virtualbox.org/virtualbox/rpm/fedora/virtualbox.repo](http://download.virtualbox.org/virtualbox/rpm/fedora/virtualbox.repo)).

The problem is the same, there are also the Async I/O errors in the log file. :/

---

### Post by QIII on 2014-04-30
Interesting.  

I only have a license for the one machine I am running Win 7 on, so I can't install it on a VM to mess around with it.

This is a bit disconcerting.

You might want to raise a flag on their forum and see what you can find out there.  (If you do find some help there, would you be so kind as to come back here and share it?)

Best wishes.

---

### Post by asgard2 on 2014-05-01
@ QIII
You do not need a license for testing. 
w7 give you several days before an activation is required.

---

### Post by QIII on 2014-05-01
I have a single retail disk with a license and a EULA that says it's for installation on one machine at a time.  A EULA is a EULA, even if the world hates Microsoft.

I'm a bit persnickity about that sort of thing, since I'm a software developer myself...

---

