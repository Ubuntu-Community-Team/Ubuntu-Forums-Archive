---
title: "vmware server 1.0.9 can not compile no compute"
date: 2009-06-29
forum: Virtualisation
---

### Post by sdowney717 on 2009-06-29
dead in the water with vmware 1.0.9
cant compile.
the other one that is current runs but no usb works.

```
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
kernel? [/lib/modules/2.6.28-13-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.28-13-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/x86.h:20,
                 from /tmp/vmware-config1/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/x86apic.h:79:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/fixmap_32.h:29,
                 from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/fixmap.h:5,
                 from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/apic.h:8,
                 from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/smp.h:13,
                 from include/linux/smp.h:30,
                 from include/linux/topology.h:33,
                 from include/linux/mmzone.h:763,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/apicdef.h:132:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config1/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/paravirt.h:7,
                 from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/system.h:11,
                 from /usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.28-13-generic/arch/x86/include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config1/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:71:
/tmp/vmware-config1/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config1/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config1/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config1/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

scott@scott-desktop:~/vmware1.0.9/vmware-server-distrib$ 
scott@scott-desktop:~/vmware1.0.9/vmware-server-distrib$ 

```

---

### Post by anystupidname on 2009-06-29
[http://communities.vmware.com/message/76957](http://communities.vmware.com/message/76957)

---

### Post by fjgaude on 2009-06-30
You need to get and run doing the vmware-update-2.6.27-5.5.7-2/runme.pl script.

The vmware-update-2.6.27 has been used successfully with the later versions of Ubuntu, from 7.04 through 9.04.

This link should do it for you:

[http://ubuntu-tutorials.com/2008/11/01/vmware-server-107-on-ubuntu-810-intrepid-2627-7-generic/](http://ubuntu-tutorials.com/2008/11/01/vmware-server-107-on-ubuntu-810-intrepid-2627-7-generic/)

Let us know how things go.

---

### Post by dcstar on 2009-07-11
> **fjgaude said:**
> You need to get and run doing the vmware-update-2.6.27-5.5.7-2/runme.pl script.

The vmware-update-2.6.27 has been used successfully with the later versions of Ubuntu, from 7.04 through 9.04.

This link should do it for you:

[http://ubuntu-tutorials.com/2008/11/01/vmware-server-107-on-ubuntu-810-intrepid-2627-7-generic/](http://ubuntu-tutorials.com/2008/11/01/vmware-server-107-on-ubuntu-810-intrepid-2627-7-generic/)

Let us know how things go.

I had the exact same issue and this update patch fixed it (I overwrote my previously patched files and couldn't figure out why I suddenly had this problem......)   :oops:

That's what happens when you replace your dead motherboard and ETH0 becomes ETH1 which then requires reconfiguration of VMWare bridged networking.... :rolleyes:

---

