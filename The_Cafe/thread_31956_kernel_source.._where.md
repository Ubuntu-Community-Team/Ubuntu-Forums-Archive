---
title: "kernel source.. where?"
date: 2005-05-05
forum: The Cafe
---

### Post by Gowator on 2005-05-05
Does anyone know where to look for kernel-source repositories ?  
my 
/etc/apt/sources.list
```
root@ubuntu:/home/sl # more /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb http://de.archive.ubuntu.com/ubuntu/ hoary main restricted universe
deb-src http://de.archive.ubuntu.com/ubuntu/ hoary main restricted universe

#deb-src http://de.archive.ubuntu.com/ubuntu/ hoary universe   
#deb http://de.archive.ubuntu.com/ubuntu/ hoary universe   

deb http://de.archive.ubuntu.com/ubuntu/ hoary multiverse   
deb-src http://de.archive.ubuntu.com/ubuntu/ hoary multiverse   


#deb http://de.security.ubuntu.com/ubuntu/ hoary-security main restricted   
#deb-src http://de.security.ubuntu.com/ubuntu/ hoary-security main restricted  

deb ftp://ftp.nerim.net/debian-marillat/ unstable main
```



and results of apt-cache search kernel-source    
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


note if anyone else has a better idea where to post this please say...

---

### Post by ape on 2005-05-05
do an `apt-cache search linux-source`.  This  results in a linux-source-2.6.9, linux-source-2.6.10 and linux-source-2.6.11 for me.

---

### Post by Gowator on 2005-05-05
apt-cache search **linux**-source

thanks...  I was looking for the debian equaiv kernel-source which it only finds 2.4.x for?  


somehow I got a K7 kernel on my other box!   hard know how I did it but ??


thx seems OK now

---

### Post by kvidell on 2005-05-05
> 34/kvidell: apt-cache search kernel-source | grep 2.6.10
kernel-patch-debian-2.6.10 - Debian patches to Linux 2.6.10
kernel-source-2.6.10 - Linux kernel source for version 2.6.10 with Debian patches
kernel-tree-2.6.10 - Linux kernel source tree for building Debian kernel images
Mine works.
Is that because I'm on Breezy though? *Has yet to find all the differences*

---

### Post by Gowator on 2005-05-05
that's weird!  

anyway :D I got it now so I guess Ill just recompile the kernel with AMD64 optimisation since tha'ts what its running on...  

couldn't get chroot working well with skype and win32 codecs.

---

