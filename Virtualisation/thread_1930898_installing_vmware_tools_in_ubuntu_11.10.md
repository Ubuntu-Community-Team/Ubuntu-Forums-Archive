---
title: "installing vmware tools in ubuntu 11.10"
date: 2012-02-24
forum: Virtualisation
---

### Post by Mia_tech on 2012-02-24
guys, I'm trying to install vmware tools in my ubuntu vm mahcine; however, after installing linux-headers-`uname -r` and linux-essential, I still can't finish the tools installation, I get stock right here
```

If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ]

```

any help appreciated

---

### Post by Diametric on 2012-02-24
Are the packages mentioned installed?

---

### Post by drmrgd on 2012-02-24
> **Mia_tech said:**
> guys, I'm trying to install vmware tools in my ubuntu vm mahcine; however, after installing linux-headers-`uname -r` and linux-essential, I still can't finish the tools installation, I get stock right here
```

If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ]

```

any help appreciated

Try installing build-essential:

```
sudo apt-get install build-essential
```

I believe that has all of the stuff you're missing to finish the VMware tools installation.

---

### Post by Mia_tech on 2012-02-24
> **drmrgd said:**
> Try installing build-essential:

```
sudo apt-get install build-essential
```

I believe that has all of the stuff you're missing to finish the VMware tools installation.

root@ubuntu-vm:~# apt-get install build-essential gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu-vm:~#

---

### Post by drmrgd on 2012-02-24
> **Mia_tech said:**
> root@ubuntu-vm:~# apt-get install build-essential gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu-vm:~#

Hmmm...well looks like you have those packages, it's not that.  At what stage are you getting this error?  Usually,  you'll have to answer a bunch of questions like "gcc is located in /usr/bin/gcc.  Would you like to change the path?" and "Generic Linux Kernel headers were found..." blah, blah, blah.  I sort of remember trying to install once before I had installed gcc and some other things, and got that error when it was looking for the gcc path.  When is this coming up for you?  That might help indicate what you're missing.

---

### Post by dcstar on 2012-02-25
> **Mia_tech said:**
> guys, I'm trying to install vmware tools in my ubuntu vm mahcine; however, after installing linux-headers-`uname -r` and linux-essential, I still can't finish the tools installation, I get stock right here
```

If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ]

```

any help appreciated

Stuck?, that is the message you get after successful installation.

Did you simply "Press Enter" as it asked you?

---

### Post by Mia_tech on 2012-02-25
> **dcstar said:**
> Stuck?, that is the message you get after successful installation.

Did you simply "Press Enter" as it asked you?

yes, I pressed enter, and it promps me for the same message. if you read the errors, it seems that it installed, but the errors is related to file sharing features... correct me if I'm wrong!

```
/. \
	  MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-16-generic'
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/backdoor.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/backdoorGcc32.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/bdhandler.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/cpName.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/cpNameLinux.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/cpNameLite.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/dentry.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/dir.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/file.o
  CC [M]  /tmp/vmware-root/modules/vmhgfs-only/filesystem.o
/tmp/vmware-root/modules/vmhgfs-only/filesystem.c:48:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/tmp/vmware-root/modules/vmhgfs-only/filesystem.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-16-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmhgfs-only'

The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.

If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ]
```

---

### Post by eclecticsol on 2012-03-09
> fatal error: linux/smp_lock.h: No such file or directory compilation terminated.Your compiler and associated tools appear to be working correctly. 

I have the same problem. A search for the above error message suggests that the version of VMware Tools available in VMWare7.1.5 is not compatible with Linux kernel 3.x sources.

My searchs suggest that there are others with a similar problem and the solutions where they have been found involve patching the VMware-tools sources to match the new kernel headers. 

See the discussion [here]("http://communities.vmware.com/thread/333694"). Note the comment "Ubuntu 11.10 is not officially supported by VMware Workstation 7.x as a guest."

Now that VMware 8 is out, it seems less likely that VMware will provide a solution. But VMware 8 and the associated VMware-Player-4.0.2 require 64 bit hosts, so for those of us struggling on on 32 host machines there is no easy solution.

If I find a better solution, I'll let  you know!

---

### Post by dcstar on 2012-03-12
> **eclecticsol said:**
> 
..........
Now that VMware 8 is out, it seems less likely that VMware will provide a solution. But VMware 8 and the associated **VMware-Player-4.0.2 require 64 bit hosts**, so for those of us struggling on on 32 host machines there is no easy solution.


Really, then why do VMware offer 64-bit and 32-bit downloads?

---

