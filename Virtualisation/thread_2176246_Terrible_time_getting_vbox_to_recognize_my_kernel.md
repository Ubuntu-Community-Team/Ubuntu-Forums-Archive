---
title: "Terrible time getting vbox to recognize my kernel"
date: 2013-09-23
forum: Virtualisation
---

### Post by josephellengar2 on 2013-09-23
I'm trying to create a Win 7 virtual machine in my ubuntu 13.10 installation. But every time I try to run it first I get this message: 

```

 The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

```

When I run that command I get this:

```

 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  Error! Bad return status for module build on kernel: 3.11.0-8-generic (x86_64)
Consult /var/lib/dkms/vboxhost/4.2.18/build/make.log for more information.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong

```

And the tail of the log says this:


```

Building module:
cleaning build area....(bad exit status: 2)
make KERNELRELEASE=3.11.0-8-generic -C /lib/modules/3.11.0-8-generic/build M=/var/lib/dkms/vboxhost/4.2.18/build....(bad exit status: 2)
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 CONFIG_MODULE_SIG= -C /lib/modules/3.11.0-8-generic/build modules
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make: *** [vboxdrv] Error 2

```

Now I have been debugging this all morning and I can clearly say that the computer is correct about the makefile. The only makefile I have is a symlink that links back to itself, so there is no make file. But I have installed and reinstalled the kernel headers and images multiple times and nothing seems to help. I have all of the other necessary packages installed-- build-essential, dkms, generic kernel images and headers, etc. I also tried installing the .deb package of virtualbox from Oracle and that didn't help. I got:

this:

```

(Reading database ... 182899 files and directories currently installed.)
Preparing to replace virtualbox-4.2 4.2.18-88780~Ubuntu~raring (using virtualbox-4.2_4.2.18-88780~Ubuntu~raring_amd64.deb) ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
Unpacking replacement virtualbox-4.2 ...
Setting up virtualbox-4.2 (4.2.18-88780~Ubuntu~raring) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  Error! Bad return status for module build on kernel: 3.11.0-8-generic (x86_64)
Consult /var/lib/dkms/vboxhost/4.2.18/build/make.log for more information.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong

```

And this log:


```

Uninstalling modules from DKMS
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxhost/4.2.18/source ->
                 /usr/src/vboxhost-4.2.18

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....(bad exit status: 2)
make KERNELRELEASE=3.11.0-8-generic -C /lib/modules/3.11.0-8-generic/build M=/var/lib/dkms/vboxhost/4.2.18/build....(bad exit status: 2)
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 CONFIG_MODULE_SIG= -C /lib/modules/3.11.0-8-generic/build modules
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make: *** [vboxdrv] Error 2

```

Any ideas?

---

### Post by josephellengar2 on 2013-09-23
Nevermind. I just uninstalled and reinstalled a bunch more things and it works now. I don't know what they were or I'd put them here for posterity.

---

