---
title: "kernel-source"
date: 2005-05-05
forum: Repositories &amp; Backports
---

### Post by Gowator on 2005-05-05
I can't find kernel source !  
My repositories

```
root@ubuntu:/home/sl # more /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb http://de.archive.ubuntu.com/ubuntu/ hoary main restricted   
deb-src http://de.archive.ubuntu.com/ubuntu/ hoary main restricted   

deb-src http://de.archive.ubuntu.com/ubuntu/ hoary universe   
deb http://de.archive.ubuntu.com/ubuntu/ hoary universe   

deb http://de.archive.ubuntu.com/ubuntu/ hoary multiverse   
deb-src http://de.archive.ubuntu.com/ubuntu/ hoary multiverse   


deb http://de.security.ubuntu.com/ubuntu/ hoary-security main restricted   
deb-src http://de.security.ubuntu.com/ubuntu/ hoary-security main restricted  

deb ftp://ftp.nerim.net/debian-marillat/ unstable main
```

```
root@ubuntu:/home/sl # apt-cache search kernel-source
avm-fritz-kernel-source - AVM Fritz! binary kernel module source
fglrx-kernel-source - ATI binary kernel module source
cpad-kernel-source - Source for the Synaptics cPad driver
freeswan - IPSEC utilities for FreeSWan
kernel-patch-2.4-lids - LIDS Kernel Patch
kernel-patch-debian-2.4.27 - Debian patches to Linux 2.4.27
kernel-source-2.4.27 - Linux kernel source for version 2.4.27 with Debian patches
kernel-tree-2.4.27 - Linux kernel source tree for building Debian kernel images
lidstools-2.4 - LIDS Admintool
nvidia-kernel-source - NVIDIA binary kernel module source
oprofile - system-wide profiler for Linux systems
wacom-kernel-source - Source for the wacom binary modules
wacom-tools - Utilities for wacom tablets and other hid devices

```

What Im a doing wrong.. where are the kernel sources?

---

### Post by kvidell on 2005-05-05
Filename: pool/universe/k/kernel-source-2.6.10/kernel-source-2.6.10_2.6.10-6_all.deb

Mine shows up in the universe repositories.
Add the word "universe" to your sources and update.
- Kev

EDIT: Or don't o.O *just read the sticky on posting in this forum*
Perhaps move your question elsewhere? Or someone explain what the sticky means, exactly?

---

### Post by Gowator on 2005-05-05
[QUOTE=kvidell]Filename: pool/universe/k/kernel-source-2.6.10/kernel-source-2.6.10_2.6.10-6_all.deb

Mine shows up in the universe repositories.
Add the word "universe" to your sources and update.
- Kev

EDIT: Or don't o.O *just read the sticky on posting in this forum*
Perhaps move your question elsewhere? Or someone explain what the sticky means, exactly?[/QUOTE]


have to admit it threw me!  Is kernel source supported or not and if not why not?  
Also its hard to know where to post, I would have expected it was somewhere but apparently not on this forum...  I have to admit I find the whole divisions a bit confusing but hey ho----

---

### Post by kvidell on 2005-05-05
[QUOTE=Gowator]have to admit it threw me!  Is kernel source supported or not and if not why not?  
Also its hard to know where to post, I would have expected it was somewhere but apparently not on this forum...  I have to admit I find the whole divisions a bit confusing but hey ho----[/QUOTE]
 Generally the divisions are not too tricky... Then again I rarely start my own thread. I mostly just hawk-eye the "New Posts" thing and help out where I can.

I think as long as no one deletes this, the worst that'll happen is they'll move it someplace and advise on where to put such topics for future reference.
I'm in no way an official voice but I think it's fine being here for the time being... Looking over the other possible choices on the main page, I don't personally see where else I would have put it if it were me... maybe in "community chat" and added a note "I have no idea where the put this, the sticky scared me away from the repository forum" or something.
*shrugs*
- Kev

---

### Post by Gowator on 2005-05-05
Hmm ..
just tried again and universe is definately in.... I guess IO need to move this thread to chat or something

---

