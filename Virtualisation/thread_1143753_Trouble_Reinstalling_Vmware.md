---
title: "Trouble Reinstalling Vmware"
date: 2009-04-30
forum: Virtualisation
---

### Post by dasajed on 2009-04-30
I installed vmware a while back, no issues. Long story short, I was messing around with the executable, and broke it. 

I uninstalled it, and then tried to reinstall. I had an issue with the config.pl. 

i'm running 8.04.

```

sudo ./vmware-install.pl
Creating a new VMware Workstation installer database using the tar4 format.

Installing VMware Workstation.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

In which directory do you want to install the daemon files? 
[/usr/sbin] 

In which directory do you want to install the library files? 
[/usr/lib/vmware] 

In which directory do you want to install the manual files? 
[/usr/share/man] 

In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware] 

The path "/usr/share/doc/vmware" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

The installation of VMware Workstation 6.0.1 build-55017 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall.pl".

Before running VMware Workstation for the first time, you need to configure it 
by invoking the following command: "/usr/bin/vmware-config.pl". Do you want 
this program to invoke the command for you now? [yes] 

Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the theme icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-23-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config7/vmmon-only'
make -C /lib/modules/2.6.24-23-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  CC [M]  /tmp/vmware-config7/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config7/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.c:83:
/tmp/vmware-config7/vmmon-only/./include/vm_basic_types.h:170: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config7/vmmon-only/./include/x86.h:23,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.c:84:
/tmp/vmware-config7/vmmon-only/./include/x86cpuid.h:383:1: warning: "BIT_MASK" redefined
In file included from include/linux/kernel.h:15,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.c:11:
include/linux/bitops.h:7:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config7/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config7/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.c:84:
/tmp/vmware-config7/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config7/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config7/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config7/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config7/vmmon-only/linux/driver.c:84:
/tmp/vmware-config7/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config7/vmmon-only/linux/driver.c:198: warning: initialization from incompatible pointer type
make[2]: *** [/tmp/vmware-config7/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config7/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config7/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

---

### Post by HermanAB on 2009-05-01
Howdy,

Install the kernel source, compile it, install it, reboot, then re-install Vmware.

$ sudo su -
# make mrproper; make oldconfig; make modules, make bzImage; make modules_install; make install; reboot
:)

---

### Post by dcstar on 2009-05-01
> **dasajed said:**
> I installed vmware a while back, no issues. Long story short, I was messing around with the executable, and broke it. 

I uninstalled it, and then tried to reinstall. I had an issue with the config.pl. 

i'm running 8.04.
........

As it says in the FAQ at the top of this forum, install the kernel headers and the **build-essential** package.

---

