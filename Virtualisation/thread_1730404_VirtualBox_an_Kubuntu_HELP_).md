---
title: "VirtualBox an Kubuntu HELP :)"
date: 2011-04-16
forum: Virtualisation
---

### Post by DemonKnightDK on 2011-04-16
Okay I downloaded the latest deb from virtualbox.org it installed and I can run it. But I can't make a virtual drive, the command line gives this error



```
david@ds3l-david:~$ virtualbox
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (2.6.35-19-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
Qt WARNING: QFileSystemWatcher: failed to add paths: /home/david/.config/ibus/bus
Qt WARNING: Bus::open: Can not get ibus-daemon's address. 
```

i'm also using the 10.10 beta of Kubuntu(its all I had access to my internet is not fast enough to download a new version distro at the moment. tuesday i'll get the lastest ISO from school.

and I also got this from the log file:


```
make KBUILD_VERBOSE=1 SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 -C /lib/modules/2.6.35-19-generic/build modules
/usr/src/linux-headers-2.6.35-19-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.35-19-generic/scripts/gcc-version.sh: line 26: gcc: command not found
/usr/src/linux-headers-2.6.35-19-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -Wp,-MD,/tmp/vbox.0/linux/.SUPDrv-linux.o.d  -nostdinc -isystem   -I/usr/src/linux-headers-2.6.35-19-generic/arch/x86/include -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -msoft-float -mregparm=3 -freg-struct-return -march=i686 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -I/lib/modules/2.6.35-19-generic/build/include -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -I/tmp/vbox.0/vboxdrv/ -I/tmp/vbox.0/vboxdrv/include -I/tmp/vbox.0/vboxdrv/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DVBOX_WITH_HARDENING -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_X86 -DVBOX_WITH_64_BITS_GUESTS  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)"  -c -o /tmp/vbox.0/linux/.tmp_SUPDrv-linux.o /tmp/vbox.0/linux/SUPDrv-linux.c
/bin/sh: gcc: not found
make[2]: *** [/tmp/vbox.0/linux/SUPDrv-linux.o] Error 127
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxdrv] Error 2
```


i've been using VM in windows for a couple semesters and i'm taking linux admin classes, so i though i'll just make linux my fulltime OS and just use a VM for windows and other OSes, that way I dont have to partition and all that jazz.. nothing can be easy. Thanks in advance for any help.

---

### Post by DemonKnightDK on 2011-04-16
Okay, SO i think i fixed it. I used kpackageKit and installed the virtualbox-ose-dkms package and ran sudo /etc/init.d/vboxdrv setup and now its working. so whatever ^_^. Thanks and maybe this will help some one else.

---

### Post by varunendra on 2011-04-16
Good to see you fixed it yourself and thanks for your concerns which are appreciable.

However, be aware that virtualbox and virtualbox-ose are not same, OSE (default for Ubuntu) has no USB support. See here: [http://ubuntuforums.org/showpost.php?p=10575898&postcount=3](http://ubuntuforums.org/showpost.php?p=10575898&postcount=3)

As suggested in the above link also, you may add suitable repository entry to your existing repository from this link : [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) if you are interested in USB support (follow the instructions under "Debian-based Linux distributions"title)

By adding the above repositories, you'll have the benefit to install it (virtualbox PUEL edition) through your GUI package installer (like synaptic in default ubuntu distros) without worrying about dependencies.

As for the previous errors regarding inability to run VMs, I face it always whenever the kernel is updated. However, in my case, the fix is also suggested in the error message when trying to run VBox through GUI. It involves the following fix:

[LIST=1]
[*]Install the kernel headers for the latest kernel you are using (linux-headers-x.x.xx-xx, linux-headers-x.x.xx-xx-generic, where x.x.xx-xx is the kernel version you are using). Headers are not installed by default during a kernel update.
[*]reinstall the dkms package, and you're done!
[/LIST]
Hope it helps understanding the problems you had, or may have in future (after a kernel update through update manager).

---

### Post by DemonKnightDK on 2011-04-17
you know what ended up being the real issue? I didnt give my self permision to use my other internal drive lol I forget how much more secure this system is than windows...

---

### Post by varunendra on 2011-04-18
> **DemonKnightDK said:**
> you know what ended up being the real issue? I didnt give my self permision to use my other internal drive lol I forget how much more secure this system is than windows...
lol :D
Thanks for the update. I won't forget to include this in my future suggestions. :popcorn:

---

