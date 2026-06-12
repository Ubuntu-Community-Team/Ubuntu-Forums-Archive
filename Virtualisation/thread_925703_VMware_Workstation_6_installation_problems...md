---
title: "VMware Workstation 6 installation problems.."
date: 2008-09-20
forum: Virtualisation
---

### Post by Pas_sa on 2008-09-20
Everytime I attempt to install VMware, I get this problem (see the quote below).
I tried following a guide elsewhere to modify one of the source files vmmon, still get the same error. Any ideas?

```
andrew@andrewdesktop:~/Desktop/vmware-distrib$ sudo ./vmware-install.pl 
A previous installation of VMware Workstation has been detected.

The previous installation was made by the tar installer (version 4).

Keeping the tar4 installer database format.

Uninstalling the tar installation of VMware Workstation.

Stopping VMware services:
   Virtual machine monitor                                             done

The removal of VMware Workstation 6.0.0 build-45731 for Linux completed 
successfully. Thank you for having tried this software.

Installing VMware Workstation.  This may take from several minutes to over an 
hour depending upon its size.

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

The path "/usr/lib/vmware" does not exist currently. This program is going to 
create it, including needed parent directories. Is this what you want? 
[yes] 


In which directory do you want to install the manual files? 
[/usr/share/man] 
In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware] 

The path "/usr/share/doc/vmware" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

The installation of VMware Workstation 6.0.0 build-45731 for Linux completed 
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

/usr/share/applications/vmware-workstation.desktop: warning: value "vmware-workstation.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-player.desktop: warning: value "vmware-player.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-19-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config3/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:48:
/tmp/vmware-config3/vmmon-only/./include/vm_basic_types.h:170: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config3/vmmon-only/./include/x86.h:23,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:49:
/tmp/vmware-config3/vmmon-only/./include/x86cpuid.h:381:1: warning: "BIT_MASK" redefined
In file included from include/linux/kernel.h:15,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:11:
include/linux/bitops.h:7:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config3/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config3/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:49:
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config3/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config3/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:49:
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config3/vmmon-only/linux/driver.c:150: warning: initialisation from incompatible pointer type
/tmp/vmware-config3/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config3/vmmon-only/linux/driver.c:1715: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config3/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

andrew@andrewdesktop:~/Desktop/vmware-distrib$ 
```

---

### Post by overdrank on 2008-09-20
moved :)

---

