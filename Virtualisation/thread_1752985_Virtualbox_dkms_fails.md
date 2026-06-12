---
title: "Virtualbox dkms fails"
date: 2011-05-08
forum: Virtualisation
---

### Post by mellery on 2011-05-08
I'm trying to run virtualbox after ubuntu wanted to update my kernal to the following

```
Linux mike-laptop 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux

```

but running sudo /etc/init.d/vboxdrv setup gives the following

```
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  
Error! Bad return status for module build on kernel: 2.6.35-28-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/vboxhost/4.0.6/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/virtualbox-4.0.0.crash'

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong

```

make.log contains

```
DKMS make.log for vboxhost-4.0.6 for kernel 2.6.35-28-generic (x86_64)
Sun May  8 13:38:55 EDT 2011
make: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
make: execvp: make: Too many levels of symbolic links
make: *** [_module_/var/lib/dkms/vboxhost/4.0.6/build] Error 127
make: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
```

and vbox-install.log contains

```
Uninstalling modules from DKMS
  removing old DKMS module vboxhost version  4.0.6

------------------------------
Deleting module version: 4.0.6
completely from the DKMS tree.
------------------------------
Done.
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxhost/4.0.6/source ->
                 /usr/src/vboxhost-4.0.6

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....(bad exit status: 2)
make KERNELRELEASE=2.6.35-28-generic -C /lib/modules/2.6.35-28-generic/build M=/var/lib/dkms/vboxhost/4.0.6/build....(bad exit status: 2)
0
0
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 -C /lib/modules/2.6.35-28-generic/build modules
make: execvp: make: Too many levels of symbolic links
make: *** [vboxdrv] Error 127
```

Could someone help me figure out why this is failing so I can run virtualbox again?

---

### Post by mellery on 2011-05-15
little help please?  I'd like to get this working by next weekend.

---

### Post by drlock on 2011-06-09
On my machine dkms seems to become corrupted after a Kernel upgrade. I have been able to get it up and running twice now with the following steps:

```

sudo apt-get remove dkms
sudo rm -rf /var/lib/dkms/vboxhost/
sudo apt-get install dkms

```

Apparently something is not being re-built in the /var/lib/dkms/vboxhost/ directory and I have to force the re-build by deleting and re-installing.

There is probably a better way, but this has worked for me.

---

