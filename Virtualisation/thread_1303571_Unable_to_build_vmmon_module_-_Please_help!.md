---
title: "Unable to build vmmon module - Please help!"
date: 2009-10-28
forum: Virtualisation
---

### Post by leviathanpr on 2009-10-28
I'm on Ubuntu 9.04- the Jaunty Jackalope - released in April 2009. New updates were available for ubuntu, and after restarting VMWARE won't compile.

Usually when new updates are available for Ubuntu, I apply them. And usually, Vmware Server Console breaks down, for example, when I try to load the console, it tries to start and then unexpectedly disappears (it does not load). If I try from the console, I always get this:

sudo vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

So...in the past, using vmware-config.pl would fix the problem. I would recompile and it would work.

After the last Ubuntu update, however, it doesn't work. I get the following errors:

Trying to find a suitable vmmon module for your running kernel.

[COLOR=Red]None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.28-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config8/vmmon-only'
make -C /lib/modules/2.6.28-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-16-generic'

  CC [M]  /tmp/vmware-config8/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config8/vmmon-only/./include/x86.h:20,
                 from /tmp/vmware-config8/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.c:49:
/tmp/vmware-config8/vmmon-only/./include/x86apic.h:79:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/fixmap_32.h:29,
                 from /usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/fixmap.h:5,
                 from /usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/apic.h:8,
                 from /usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/smp.h:13,
                 from include/linux/smp.h:30,
                 from include/linux/topology.h:33,
                 from include/linux/mmzone.h:763,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/apicdef.h:132:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config8/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.c:49:
/tmp/vmware-config8/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from /usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/paravirt.h:7,
                 from /usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from /usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/system.h:11,
                 from /usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config8/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config8/vmmon-only/linux/driver.c:71:
/tmp/vmware-config8/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config8/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config8/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config8/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config8/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config8/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config8/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config8/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config8/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config8/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.[/COLOR]

               
My VMWARE experience on ubuntu has been frustrating thus far. Help would be very much appreciated.

---

### Post by albandy on 2009-10-28
I don't use vmware, I use VirtualBox, and there are problems too if you don't have the sources and the building tools installed in the system, try installing this packages:

sudo apt-get install build-essential linux-headers-$(uname -r)

---

### Post by leviathanpr on 2009-10-28
thanks for the reply. It says it's already at the newest version.



> **albandy said:**
> try installing this packages:
sudo apt-get install build-essential linux-headers-$(uname -r)
[COLOR=Red]
[/COLOR]
[COLOR=Red]sudo apt-get install build-essential linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=DarkOrange]build-essential is already the newest version.
linux-headers-2.6.28-16-generic is already the newest version.[/COLOR]
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]

---

### Post by leviathanpr on 2009-10-29
Can anyone help? I really need that VM running.

---

### Post by fjgaude on 2009-10-29
Well, yes, you need to download a program called **vmware-update-2.6.27**. Here's a HOW-TO:

[http://symbolik.wordpress.com/2009/02/04/howto-repost-vanilla-kernel-26283-vmware-server-108-and-kubuntu-804/](http://symbolik.wordpress.com/2009/02/04/howto-repost-vanilla-kernel-26283-vmware-server-108-and-kubuntu-804/)

This update 2.6.27 works with kernel 2.6.28 also... but anything higher will have to be worked out at a later time.

---

### Post by tombott on 2009-12-01
I had the same problem with VmWare Server running on Ubuntu 9.10 with and Linux headers 2.6.31-15.

I used the script linked on this [page]("http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/") and now all working.

---

### Post by dcstar on 2009-12-03
> **fjgaude said:**
> Well, yes, you need to download a program called **vmware-update-2.6.27**. Here's a HOW-TO:

[http://symbolik.wordpress.com/2009/02/04/howto-repost-vanilla-kernel-26283-vmware-server-108-and-kubuntu-804/](http://symbolik.wordpress.com/2009/02/04/howto-repost-vanilla-kernel-26283-vmware-server-108-and-kubuntu-804/)

This update 2.6.27 works with kernel 2.6.28 also... but anything higher will have to be worked out at a later time.

And it still works with VMware Server 1.0.10 (on a 9.04 64-bit system).

---

### Post by fjgaude on 2009-12-03
Yes, David, this is true.

When, oh when will 1.0.10 work with 9.10, without having to manually add a patch to kernel 2.6.31? <smile>

---

### Post by dcstar on 2009-12-04
> **fjgaude said:**
> Yes, David, this is true.

When, oh when will 1.0.10 work with 9.10, without having to manually add a patch to kernel 2.6.31? <smile>

Dunno, but I will let you know if it will work with the 10.04 LTS release (coz I ain't touching 9.10 as my host OS, I have it in a VM and just don't see enough to put up with the myriad of problems people are having with it).

Perhaps by them VMware will have released a version that works with current kernels?

---

### Post by fjgaude on 2009-12-04
Well, I'm using Player 3.0 which does everything I want at the moment. Still have 1.0.10 working on 8.10 if I need to go down the LAN to access a VM. That's the only thing the Player doesn't do. Builds new VMs just fine.

For me, 9.10 is the best Ubuntu has come out with... but I guess it depends on what hardware you have.

---

