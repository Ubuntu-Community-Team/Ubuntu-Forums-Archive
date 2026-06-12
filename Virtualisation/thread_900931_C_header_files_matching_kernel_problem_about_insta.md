---
title: "C header files matching kernel problem about installing VMware Workstation"
date: 2008-08-25
forum: Virtualisation
---

### Post by desperadoshaw on 2008-08-25
Well...I'm desperately fed up with it.I've googled much and tried nearly every way..but I still can't fix the problem...I'm just a newbie and I just follow the instruction and don't know the principle under it.
I've installed buildessential,gcc and linux-header-`uname -r` and linux-image,linux-source,and I also use the any any patch and also do the ln -s linux-`uname -r` linux thing under /usr/src...... but they never work.
I tried three directories,this is the output information
> Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /lib64/modules/2.6.24-20-generic/build/include

The path "/lib64/modules/2.6.24-20-generic/build/include" is a kernel header 
file directory, but it is not part of kernel source tree.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.24-20-generic/include

The path "/usr/src/linux-headers-2.6.24-20-generic/include" is a kernel header 
file directory, but it is not part of kernel source tree.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

So are there anybody who can help me? Any reposes well be appreciated!

---

### Post by Mister.Vash on 2008-08-25
run "uname -a" to verify the current kernel version on your system
I have 2.6.24-21


Does /usr/src/linux-headers-2.6.24-20 or /usr/src/linux-headers-2.6.24-20-generic work for you?

So when it asks the first time, have you tried
```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.24-20-generic
```

---

### Post by desperadoshaw on 2008-08-26
> **Mister.Vash said:**
> run "uname -a" to verify the current kernel version on your system
I have 2.6.24-21


Does /usr/src/linux-headers-2.6.24-20 or /usr/src/linux-headers-2.6.24-20-generic work for you?

So when it asks the first time, have you tried
```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.24-20-generic
```

Thank you Mister.Vash! /usr/src/linux-headers-2.6.24-20-generic didn't work for me...but I found the problem...the difference in the release number between linux-header and linux-source ...'cuz there are no available linux-source compatible with my image so  I installed one with different release number....now I installed 2.6.24.21 image and the same source....and the problem is fixed....

and the next problem came out...haha...

> Unable to complete wizard: Unable to register the virtual machine: Unable to add virtual machine "/usr/virtual\ machines/Panther/Panther.vmx" to the inventory: Invalid virtual machine
.
.
This is the error information when I created my client on Vmware Server...
 Sigh...

---

