---
title: "[SOLVED] Trouble setting up a Virtualbox"
date: 2008-12-05
forum: Virtualisation
---

### Post by ilikeroflcopters on 2008-12-05
Im trying to create a virtual machine for gOS 3 Gadgets, but after powering it on, the screen gives me an error saying 


```
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}


```

When i run "vboxdrv setup" in the command line this comes up

```
[Sparta 3] init.d > vboxdrv setup
 * Stopping VirtualBox kernel module                        
 *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

```

Im running Ubuntu 8.10 Intrepid, with 1gig of ram on a PCG-GRT360ZG Vaio laptop. Im trying to run the virtualbox on Sun xVM VirtualBox.Anyone have any tips i can try?

---

### Post by arrancaru on 2008-12-05
You could post the output of /var/log/vbox-install.log for details.

---

### Post by ilikeroflcopters on 2008-12-05
Mmmk

```
Attempting to install using DKMS
info: No menu item ` removing old DKMS module vboxdrv version ' in node `(dir)Top'.

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 1.6.2
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/1.6.2/source ->
                 /usr/src/vboxdrv-1.6.2

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-9-generic -C /lib/modules/2.6.27-9-generic/build M=/var/lib/dkms/vboxdrv/1.6.2/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-9-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/vboxdrv/1.6.2/build/ for more information.
0
0
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/tmp/vbox.1 SRCROOT=/tmp/vbox.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.1/.tmp_versions ; rm -f /tmp/vbox.1/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.1
  gcc -Wp,-MD,/tmp/vbox.1/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-9-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/lib/modules/2.6.27-9-generic/build/include -I/tmp/vbox.1/ -I/tmp/vbox.1/include -I/tmp/vbox.1/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_X86 -DUSE_NEW_OS_INTERFACE_FOR_MM -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.1/linux/.tmp_SUPDrv-linux.o /tmp/vbox.1/linux/SUPDrv-linux.c
In file included from /tmp/vbox.1/linux/SUPDrv-linux.c:35:
/tmp/vbox.1/SUPDRV.h:99:30: error: asm/semaphore.h: No such file or directory
/tmp/vbox.1/linux/SUPDrv-linux.c: In function ‘supdrvOSGipResume’:
/tmp/vbox.1/linux/SUPDrv-linux.c:1331: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vbox.1/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [vboxdrv] Error 2
```

I just didnt want the first post to be a total overload of information

---

### Post by HotShotDJ on 2008-12-06
Have you installed the package "build-essential" ?

---

### Post by ilikeroflcopters on 2008-12-06
Its already installed

---

### Post by HotShotDJ on 2008-12-06
> **ilikeroflcopters said:**
> Its already installedOk.  Let me ask you the equivalent of a TV repair shop asking "is the TV plugged in?" -- what EXACTLY is the command you entered?  It should be:```
sudo /etc/init.d vboxdrv setup
```You need to use the "sudo" before the actual command. I THINK you probably did it correctly, otherwise the "Stopping VirtualBox kernel module" would have likely failed right at the beginning.

Let's look at something... Based on the output that you posted, it looks like an older version of VirtualBox (version 1.6.2).  This might be the source of your problem.  Did you download VirtualBox directly from Sun or did you add the Sun Virtualbox repositories?  If you did not add the repositories, but just downloaded the package, follow the instructions about half way down the following page to add the sun repository:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).

You should get an upgrade notification for Virtualbox after you reload the package database.  If so, go ahead and upgrade, and all should be back to good.

If there is no upgrade notification, use Synaptic Package Manager to reinstall VirtualBox (being careful not to select the OSE version... after you add the sun repository, both versions will show up in the package manager list)

---

### Post by ilikeroflcopters on 2008-12-06
I ran ```
[Sparta 15] Desktop > sudo su
[Sparta 1] Desktop > cd /etc/init.d
[Sparta 2] init.d > vboxdrv setup
```

Is that any different than running "sudo /etc/init.d vboxdrv setup"?

I added the Sun Virtualbox repository, and i didnt get any notification for Virtualbox.

I cant choose to reinstall Virtualbox in Synaptic either, so i uninstalled it in synaptic and tried to install it, but it gave me this 

```
virtualbox:

Package virtualbox has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list.
``` So i removed virtualbox completely from Synaptic

I downloaded the .deb file instead and installed it.Im trying right now to see if it works or not.

[EDIT]It does in fact work now.I dont get any errors like i did before. Thanks for the help HotshotDJ.

---

