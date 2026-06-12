---
title: "VirtualBox (non-OSE) kernel not compiling"
date: 2008-12-07
forum: Virtualisation
---

### Post by philgenius on 2008-12-07
This is what I ran:

```
philip@1951-44U:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

```

Then I went to the log:

```
Attempting to install using DKMS
  removing old DKMS module vboxdrv version 

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 2.0.6
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.0.6/source ->
                 /usr/src/vboxdrv-2.0.6

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.27-9-generic cannot be found at
/lib/modules/2.6.27-9-generic/build or /lib/modules/2.6.27-9-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:142: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop. 
```

Any help?

BTW, I checked those folders mentioned in the log, and they do not exist. the kernel number does, but the build or source folders do not exist.

---

### Post by albinootje on 2008-12-07
Did you install build-essential and linux-headers-2.6.27-9-generic ?

---

### Post by philgenius on 2008-12-07
I didn't have the headers installed. Now it works. Thanks.

---

### Post by M4rotku on 2008-12-07
I have been having this same problem since I switched to 8.10.  In 8.04, VirtualBox worked fine.  I have both the header and the build essentials package.

However, my log looks a lot different than the afore mentioned one:

> make KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -Wp,-MD,/tmp/vbox.0/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-9-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/lib/modules/2.6.27-9-generic/build/include -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_X86 -DUSE_NEW_OS_INTERFACE_FOR_MM -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.0/linux/.tmp_SUPDrv-linux.o /tmp/vbox.0/linux/SUPDrv-linux.c
In file included from /tmp/vbox.0/linux/SUPDrv-linux.c:35:
/tmp/vbox.0/SUPDRV.h:99:30: error: asm/semaphore.h: No such file or directory
/tmp/vbox.0/linux/SUPDrv-linux.c: In function ‘supdrvOSGipResume’:
/tmp/vbox.0/linux/SUPDrv-linux.c:1331: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vbox.0/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [vboxdrv] Error 2

---

### Post by delgurth on 2008-12-08
It seems the error

> 
"too many arguments to function ‘smp_call_function’"


is caused by a bug in virtualbox in combination with the 2.6.27 kernel, for more information see the Ubuntu bug for it: [https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/263080](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/263080)

---

### Post by M4rotku on 2008-12-08
How would I go about upgrading to the new version of VirtualBox as the launchpad thread suggested?  Would I just reinstall over the current install and it would keep all of my virtual machines intact?  There isn't an option to download an upgrade patch on virtualbox's website, only the option to download the new release.

---

### Post by borpin on 2008-12-12
> **albinootje said:**
> Did you install build-essential and linux-headers-2.6.27-9-generic ?

Can I just add that I had the same problem on a 8.10 server with a failed compilation when adding the vboxdrv in.  Not sure why, probably a
```
sudo aptitude update
```did it.

Anyway tried several solutions including
```
sudo apt-get install kernel-package
sudo apt-get install linux-source
```
finally tired the above but still no success so I tried 
```
uname -r
```
which gave the current kernel as above but instead of generic it wanted server.  So
```
sudo aptitude install linux-headers-2.6.27-9-server
```
finally gave me a working Kernel with vboxdrv installed and working.  Phew!

HTH

---

