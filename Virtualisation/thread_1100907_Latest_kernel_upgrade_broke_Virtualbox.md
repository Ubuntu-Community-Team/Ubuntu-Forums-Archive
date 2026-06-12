---
title: "Latest kernel upgrade broke Virtualbox"
date: 2009-03-19
forum: Virtualisation
---

### Post by lolwhites on 2009-03-19
Since the kernel upgraded to 2.6.27-14, Virtualbox has stopped working. Starting a virtual machine gives the message > VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908)
A swift check of the forum suggested I type  sudo /etc/init.d/vboxdrv setup but that just gives me the following:

> * Look at /var/log/vbox-install.log to find out what went wrong

The contents of the /var/log/vbox-install.log are:

[PHP] Attempting to install using DKMS
  removing old DKMS module vboxdrv version 

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>

------------------------------
Deleting module version: 2.1.4
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.1.4/source ->
                 /usr/src/vboxdrv-2.1.4

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-14-generic -C /lib/modules/2.6.27-14-generic/build M=/var/lib/dkms/vboxdrv/2.1.4/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-14-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/vboxdrv/2.1.4/build/ for more information.
3

DO YOU HAVE gcc INSTALLED???
0
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-14-generic/build SUBDIRS=/tmp/vbox.3 SRCROOT=/tmp/vbox.3 modules
/usr/src/linux-headers-2.6.27-14-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.27-14-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: gcc: Command not found
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.3/.tmp_versions ; rm -f /tmp/vbox.3/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.3
  gcc -Wp,-MD,/tmp/vbox.3/linux/.SUPDrv-linux.o.d  -nostdinc -isystem  -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-14-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -msoft-float -mregparm=3 -freg-struct-return -march=i586 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -Iinclude/asm-x86/mach-default -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -I/lib/modules/2.6.27-14-generic/build/include -I/tmp/vbox.3/ -I/tmp/vbox.3/include -I/tmp/vbox.3/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DVBOX_WITH_HARDENING -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_X86 -DVBOX_WITH_64_BITS_GUESTS -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.3/linux/.tmp_SUPDrv-linux.o /tmp/vbox.3/linux/SUPDrv-linux.c
/bin/sh: gcc: not found
make[2]: *** [/tmp/vbox.3/linux/SUPDrv-linux.o] Error 127
make[1]: *** [_module_/tmp/vbox.3] Error 2
make: *** [vboxdrv] Error 2[/PHP]

How should I proceed?

---

### Post by loomsen on 2009-03-19
You gotta compile the kernel module for each new kernel. Make sure you have the kernel headers and sources, then do this to initially compile the module:

```

sudo /etc/init.d/vboxdrv setup

```

You should have to run it only once I think.

---

### Post by lolwhites on 2009-03-20
OK, but how do I make sure I have the kernel headers and sources?

---

### Post by subject117 on 2009-03-21
I'm having the same problem.  I searched through a lot of threads and I can not find the solution.  When I type:

# /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}

"setup" is not an option for my vboxdrv but it seems to be for everyone else.  Why?

I try the restart option but it doesn't help:

# /etc/init.d/vboxdrv restart
 * Stopping VirtualBox kernel module vboxdrv                                                                                    [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                                                                           
 * No suitable module for running kernel found.

I have installed the latest virtualbox modules:

# apt-get virtualbox-ose-modules-generic
E: Invalid operation virtualbox-ose-modules-generic
root@dell:~# apt-get install virtualbox-ose-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-ose-modules-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

And I know I have the latest headers because when I type:

# apt-get install linux-headers-generic build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by subject117 on 2009-03-22
I figured it out!  I have it working!

I did many things to try to figure it out and I am not sure what all of the necessary steps are.  I did install the kernel-source and finally I did this as root:

apt-get install virtualbox-ose-source
module-assistant auto-install virtualbox-ose-source
/etc/init.d/vboxdrv start

Now it works!

---

### Post by Koraq on 2009-03-23
This doesn't work for me.

This goes fine:
apt-get install virtualbox-ose-source

This fails:
module-assistant auto-install virtualbox-ose-source

I get a lot of errors which I don't understand, trying to build. I can't even tell which is relevant to post for getting feedback. :(

---

### Post by arak on 2009-03-24
I'm a noobe.  Here is what I did/have done to fix the problem.  I would reinstall Virtualbox and everything would work again.  I did not have to reinstall Windows or any of the stuff I had loaded into Windows, because the reinstall found what I previously had installed.

I have done this reinstall a few times, as I have loaded updates to Ubuntu.

---

### Post by loomsen on 2009-03-25
If you wanna make sure you always have the latest sources installed, grab a metapackage.

Those are packages, which basically only depend on other pkges.

the package linux-image for instance will always depend on the latest linux-image available. So, whenever theres an update, this pkg will make sure you won't miss the latest image.

these pkges will prlly do what u want them to:
linux --> will always grab latest linux-image
linux-headers-generic --> will always grab latest source files.

To find out whether you have the latest sources installed, do this:

```

ls /usr/src | grep `uname -r`

```

If you get output like 
*-headers-<your-kernel-version>-*
you're fine.

example:
> 

[color=red]docter[~][/color] ls /usr/src | grep `uname -r`
linux-headers-2.6.28-11-generic
sysprof-module-2.6.28-11-generic_1.0.12-1+2.6.28-11.37_amd64.deb
[color=red]docter[~] [/color]

---

### Post by HermanAB on 2009-03-26
The moral of the story is: When you are running a virtual server, don't upgrade the host, unless you enjoy re-installing lots of stuff every time.  I upgrade my hosts on an 18 month schedule, otherwise it is just too much work.

Cheers,

Herman

---

### Post by NorthernSuze on 2009-10-26
> **loomsen said:**
> You gotta compile the kernel module for each new kernel. Make sure you have the kernel headers and sources, then do this to initially compile the module:

```

sudo /etc/init.d/vboxdrv setup

```

Thank-you for you help, loomsen, a quick easy command that worked for me.
Suze

---

