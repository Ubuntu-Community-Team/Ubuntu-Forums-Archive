---
title: "VirtualBox broke on upgrade and won't recompile"
date: 2008-11-14
forum: Virtualisation
---

### Post by corwinspyre on 2008-11-14
Hi!  Thanks in advance for your help.  Upgrading from 8.04 (64) to 8.10 (64) broke VirtualBox.  I am in the vboxusers group, so that is not the problem.

Trying to start VirtualBox comes up with this error:
> VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

So, I try running 
```
sudo /etc/init.d/vboxdrv setup
```

which results in:
```
  $ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                                                                                                          *  done.
 * Recompiling VirtualBox kernel module                                                                                                                      
 * Look at /var/log/vbox-install.log to find out what went wrong

```

Here is vbox-install.log
>   $ cat /var/log/vbox-install.log
Attempting to install using DKMS
info: No menu item ` removing old DKMS module vboxdrv version ' in node `(dir)Top'.

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 1.6.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/1.6.4/source ->
                 /usr/src/vboxdrv-1.6.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-8-generic -C /lib/modules/2.6.27-8-generic/build M=/var/lib/dkms/vboxdrv/1.6.4/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-8-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/vboxdrv/1.6.4/build/ for more information.
0
0
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-8-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-8-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -Wp,-MD,/tmp/vbox.0/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-8-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/lib/modules/2.6.27-8-generic/build/include -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_AMD64 -DUSE_NEW_OS_INTERFACE_FOR_MM -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.0/linux/.tmp_SUPDrv-linux.o /tmp/vbox.0/linux/SUPDrv-linux.c
In file included from /tmp/vbox.0/linux/SUPDrv-linux.c:35:
/tmp/vbox.0/SUPDRV.h:104:30: error: asm/semaphore.h: No such file or directory
/tmp/vbox.0/linux/SUPDrv-linux.c: In function ‘supdrvOSGipResume’:
/tmp/vbox.0/linux/SUPDrv-linux.c:1331: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vbox.0/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-8-generic'
make: *** [vboxdrv] Error 2


That says to look at make.log, which gives the same error:
>   $ cat /var/lib/dkms/vboxdrv/1.6.4/build/make.log
DKMS make.log for vboxdrv-1.6.4 for kernel 2.6.27-8-generic (x86_64)
Fri Nov 14 10:30:27 EST 2008
make: Entering directory `/usr/src/linux-headers-2.6.27-8-generic'
  LD      /var/lib/dkms/vboxdrv/1.6.4/build/built-in.o
  CC [M]  /var/lib/dkms/vboxdrv/1.6.4/build/linux/SUPDrv-linux.o
In file included from /var/lib/dkms/vboxdrv/1.6.4/build/linux/SUPDrv-linux.c:35:
/var/lib/dkms/vboxdrv/1.6.4/build/SUPDRV.h:104:30: error: asm/semaphore.h: No such file or directory
/var/lib/dkms/vboxdrv/1.6.4/build/linux/SUPDrv-linux.c: In function ‘supdrvOSGipResume’:
/var/lib/dkms/vboxdrv/1.6.4/build/linux/SUPDrv-linux.c:1331: error: too many arguments to function ‘smp_call_function’
make[1]: *** [/var/lib/dkms/vboxdrv/1.6.4/build/linux/SUPDrv-linux.o] Error 1
make: *** [_module_/var/lib/dkms/vboxdrv/1.6.4/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-8-generic'


Within vbox-install.log, I can see this error but am not sure how to do what it says, though I believe there are further problems:
> echo " ERROR: Kernel configuration is invalid."; \
echo " include/linux/autoconf.h or include/config/auto.conf are missing."; \
echo " Run 'make oldconfig && make prepare' on kernel src to fix it."; \
echo; \

What do I need to do to get VB up and running again?  Thank you very much.

---

### Post by ideebe on 2008-11-15
Idee jewelry wholesale,supply,necklace supply, earrings supply,ring supply, hangs falls supply, jewelry wholesale,925 silver jewelry wholesale,gem,makeup,hairdressing[img]http://www.ideewomen.com/cn/uploads/1.jpg[/img]http://www.ideejewelry.com/

---

### Post by frozenjim on 2008-11-15
Yeah, I had the same errors after upgrading to Ibex.  Not finding a resolution, I just gave up and downloaded the .deb from sun.

[http://dlc.sun.com/virtualbox/vboxdownload.html#linux](http://dlc.sun.com/virtualbox/vboxdownload.html#linux)

Now I'm back up again.  So it's one fix for your problem.

---

### Post by corwinspyre on 2008-11-15
> **frozenjim said:**
> Yeah, I had the same errors after upgrading to Ibex.  Not finding a resolution, I just gave up and downloaded the .deb from sun.

[http://dlc.sun.com/virtualbox/vboxdownload.html#linux](http://dlc.sun.com/virtualbox/vboxdownload.html#linux)

Now I'm back up again.  So it's one fix for your problem.

Wow, that was easy.  No need to do anything beyond installing the package again, including removing the previous or recompiling via "/etc/init.d/vboxdrv setup".  Thanks a lot!

---

### Post by Ed Elmo on 2008-11-24
> **frozenjim said:**
> Yeah, I had the same errors after upgrading to Ibex.  Not finding a resolution, I just gave up and downloaded the .deb from sun.

[http://dlc.sun.com/virtualbox/vboxdownload.html#linux](http://dlc.sun.com/virtualbox/vboxdownload.html#linux)

Now I'm back up again.  So it's one fix for your problem.
Thnx a lot. I had exactly the sam problem. This also wordked for me

---

