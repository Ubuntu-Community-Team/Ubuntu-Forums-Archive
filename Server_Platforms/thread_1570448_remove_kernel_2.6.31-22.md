---
title: "remove kernel 2.6.31-22"
date: 2010-09-08
forum: Server Platforms
---

### Post by bobwdn on 2010-09-08
My file server (running 10.04.1LTS) has a kernel 2.6.31-22 installed. This what I did and see:
```
sudo aptitude remove linux-image-2.6.31-22-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Couldn't find any package whose name or description matched "linux-image-2.6.31-22-generic"
Couldn't find any package whose name or description matched "linux-image-2.6.31-22-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading extended state information       
Initializing package states... Done
```
I checked my desktop machine (a different machine) and synaptic does not show a 2.6.31-22 kernel on the apt servers.

How do I remove this entry?

---

### Post by CharlesA on 2010-09-08
Check to make sure the kernel is actually listed in dpkg:

```
dpkg -l | grep linux
```

Then just do an apt-get purge.

---

### Post by bobwdn on 2010-09-09
Well, that presented me with some configuration files for other kernel's I had not purged, so I purged those. Now when I 'ls' my /boot, I can still see:```
me@server:/boot$ ls
abi-2.6.31-22-generic	      lost+found
abi-2.6.32-22-generic	      memtest86+.bin
abi-2.6.32-24-generic	      System.map-2.6.31-22-generic
config-2.6.31-22-generic      System.map-2.6.32-22-generic
config-2.6.32-22-generic      System.map-2.6.32-24-generic
config-2.6.32-24-generic      vmcoreinfo-2.6.31-22-generic
grub			      vmcoreinfo-2.6.32-22-generic
grub_OLD		      vmcoreinfo-2.6.32-24-generic
grub_OLD2		      vmlinuz-2.6.31-22-generic
initrd.img-2.6.31-22-generic  vmlinuz-2.6.32-22-generic
initrd.img-2.6.32-22-generic  vmlinuz-2.6.32-24-generic
initrd.img-2.6.32-24-generic
```
And when I 'dpkg -l | grep linux', I now get:```
me@server:~$ dpkg -l | grep linux
....
ii  linux-generic                     2.6.32.24.25                                    Complete Generic Linux kernel
ii  linux-image-2.6.32-24-generic     2.6.32-24.42                                    Linux kernel image for version 2.6.32 on x86
ii  linux-image-generic               2.6.32.24.25                                    Generic Linux kernel image
```
I hate to guess, but I guess I can just remove each "2.6.31-22-generic" files? Suggestions?

---

### Post by bobwdn on 2010-09-10
As much as I would like to clear this wasted space on my hard drive, I am going to leave this alone. I am afraid that simply rm the various files will break my server and not allow a restart.

So, thanks for your help.

---

