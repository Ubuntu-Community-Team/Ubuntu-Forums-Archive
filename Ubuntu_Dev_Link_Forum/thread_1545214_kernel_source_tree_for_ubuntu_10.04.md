---
title: "kernel source tree for ubuntu 10.04"
date: 2010-08-03
forum: Ubuntu Dev Link Forum
---

### Post by k210in on 2010-08-03
Hi,

     I am trying to LEARN writing device drivers for linux. Have installed ubuntu on my PC and am stepping through a linux device driver book. 
  
a.    Now to get started to write a simple char driver, i need to get the kernel source tree on my disk. How do i do this (get the source tree) on ubuntu 10.04? 

b.    As i am just starting to learn this, Will really appreciate any suggestions/directions that will help me orient and accelerate the learning of device driver writing. 

Thanks
-K

---

### Post by chopinhauer on 2010-08-03
> **k210in said:**
> 
a.    Now to get started to write a simple char driver, i need to get the kernel source tree on my disk. How do i do this (get the source tree) on ubuntu 10.04? 


If you want to download the kernel with Ubuntu patches, you can either download the source package of one of the binary kernels:
```
apt-get source linux-image-2.6.32-24-generic
```
which downloads and decompresses the source of the 'linux-image-2.6.32-24-generic' package, or you can install the 'linux-source' package:
```
sudo apt-get install linux-source
```
which drops a tarball of the kernel in /usr/src.

You might also need all the build dependencies for the Linux image:
```
sudo apt-get build-dep linux-image-2.6.32-24-generic
```

---

### Post by k210in on 2010-08-11
Thx for the reply. I used the below command to get the source into /usr/src but i am unable to extract it to the same directory because of permission issues. The below command has dumped a linux_2.6.32.orig.tar.gz file in /usr/src.  

sudo apt-get install linux-source
I use the following command to extract the files out. 

tar xvfz linux_2.6.32.orig.tar.gz

Any suggestions? 

Thx
K

---

### Post by chopinhauer on 2010-08-11
> **k210in said:**
> 
tar xvfz linux_2.6.32.orig.tar.gz

Any suggestions? 


Normal users can not write in the /usr/src directory, anyway compiling the kernel as 'root' is a useless abuse of privilege and according to the Filesystem Hierarchy Standard no compilation should take place in /usr/src.

You should extract the tarball somewhere in your home directory, e.g.:
```

tar -xvzf linux_2.6.32.orig.tar.gz -C /home/yourusername

```

---

### Post by k210in on 2010-08-11
Thanks.
K

BTW I enjoyed your "useless abuse of privilege" phrase. :-)

---

### Post by lupusone on 2012-09-04
Trying to upgrade the system to kernel 3.2:
After trying to make the patchkernel I get stuck. 

Sudo make patchkernel KERNELDIR=/usr/src/linux KERNEL_VER=3.2

the system complains:
The target directory /usr/src/linux is not a full kernel source tree.

How can I fix this?

---

### Post by ScumCoder on 2012-09-20
> **lupusone said:**
> 
How can I fix this?Just install SUSE and forget about galvanizing the Lucid Lynx' cold corpse for the sake of good old Gnome

---

### Post by pbrane on 2012-09-23
deleted

---

### Post by einonm on 2012-09-23
> **lupusone said:**
> Trying to upgrade the system to kernel 3.2:
After trying to make the patchkernel I get stuck. 

Sudo make patchkernel KERNELDIR=/usr/src/linux KERNEL_VER=3.2

the system complains:
The target directory /usr/src/linux is not a full kernel source tree.

How can I fix this?

I don't understand why you are trying to run make patchkernel if all you're doing is trying to compile your driver for the current kernel. Can you explain what steps you are doing and why?

---

