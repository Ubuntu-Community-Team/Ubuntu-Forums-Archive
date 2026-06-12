---
title: "VirtualBox on Ubuntu 13.04 Problem"
date: 2013-06-06
forum: Virtualisation
---

### Post by DBQ on 2013-06-06
Hi everybody.

I recently upgraded from Ubuntu 12.10 to 13.04.
I also installed virtualbox to 4.4.12

Now, when I try to start any VM, I get the error:

```

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

```

Hence, I run 

```

~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  Error! Your kernel headers for kernel 3.5.0-31-generic cannot be found.
Please install the linux-headers-3.5.0-31-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong


```

When I try running 

```

:~$  sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.5.0-31-generic
E: Couldn't find any package by regex 'linux-headers-3.5.0-31-generic'

```

Any ideas?  Thanks!

P.S. I tried specifying kernelpathdir to point to existing, installed headers, to no avail.

---

### Post by 2F4U on 2013-06-07
You are running quite an old kernel version for 13.04:

[https://wiki.ubuntu.com/RaringRingtail/ReleaseNotes#Linux_kernel_3.8.8](https://wiki.ubuntu.com/RaringRingtail/ReleaseNotes#Linux_kernel_3.8.8)

Is there a particular reason for using kernel 3.5 instead of the default 3.8 kernel?

---

