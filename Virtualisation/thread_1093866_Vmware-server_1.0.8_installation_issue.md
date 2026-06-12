---
title: "Vmware-server 1.0.8 installation issue"
date: 2009-03-12
forum: Virtualisation
---

### Post by jms1989 on 2009-03-12
Hi, I am having trouble installing vmware-server 1.0.8.

It install correctly I suppose but it will not configure. This is as far as I get with /usr/bin/vmware-config.pl.

> 
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-11-server/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.27-11-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-server'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:71:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-server'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


Am I missing something? I believe I got the kernel sources installed along with gcc, make, the whole gang.

Help Appreciated.

---

### Post by gtdaqua on 2009-03-12
You need these packages too:

Server:
```

sudo apt-get install install libxtst6 libxt6 libxrender1 xinetd

```
On 64-bit, add these too:
```

sudo apt-get install ia32-libs libc6-i386

```

And hopefully you have the build-essential package as well.

---

### Post by alenz on 2009-03-12
same exact error for me.  I'm trying to install 1.0.6.

I have installed all the mentioned packages.

==============
Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config4/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config4/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:53:
/tmp/vmware-config4/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/pda.h:8,
                 from include/asm/current.h:19,
                 from include/asm/processor.h:15,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:16:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config4/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:84:
/tmp/vmware-config4/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config4/vmmon-only/linux/driver.c:171: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config4/vmmon-only/linux/driver.c:172: warning: initialization from incompatible pointer type
/tmp/vmware-config4/vmmon-only/linux/driver.c:175: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config4/vmmon-only/linux/driver.c:176: warning: initialization from incompatible pointer type
/tmp/vmware-config4/vmmon-only/linux/driver.c: In function ‘__LinuxDriver_Ioctl’:
/tmp/vmware-config4/vmmon-only/linux/driver.c:1781: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config4/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config4/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
==================

---

### Post by jms1989 on 2009-03-13
> **gtdaqua said:**
> You need these packages too:

Server:
```

sudo apt-get install install libxtst6 libxt6 libxrender1 xinetd

```
On 64-bit, add these too:
```

sudo apt-get install ia32-libs libc6-i386

```

And hopefully you have the build-essential package as well.

Nope, sorry. I installed libxtst6, libxt6, libxrender1, xinetd, and build-essential packages but its a no go. Same error.

---

### Post by andradaq on 2009-03-16
I am running Ubuntu 8.10 kernel 2.6.27-11-server and I got the same error when trying to install vmware-server-1.0.8.

This solution worked perfectly for me: [http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627](http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627)

Hope this helps!

---

### Post by tiris on 2009-03-16
The VMWare workstation seems to be picky about the version of kernel that you are running.

On machines that use VMWare workstation (or server) I disable the kernel updates so that I don't have to deal with it breaking and then having to wait for VMWare to issue a new download (or having to change the kernel that I boot from when VMWare is needed).

I haven't tried the patch offered in the above post.

---

### Post by jms1989 on 2009-03-17
> **andradaq said:**
> I am running Ubuntu 8.10 kernel 2.6.27-11-server and I got the same error when trying to install vmware-server-1.0.8.

This solution worked perfectly for me: [http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627](http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627)

Hope this helps!

Excellent! Will try this patch when I get home. Right now I'm using someone elses pc. :D

According to the comments, this file should work for me and you. :)

[http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz](http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz)

---

### Post by jms1989 on 2009-03-18
Well, how 'bout that. It works! Now I can run VM systems on my ubuntu os. Yay! :) One tiny problem, the program itself will not allow a guest use more than 3.2GB. Is there a way to make vmware-server 1.x series allow more or would I need a 64bit host with a 64bit vmware-server?

---

