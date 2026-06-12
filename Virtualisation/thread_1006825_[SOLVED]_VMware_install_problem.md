---
title: "[SOLVED] VMware install problem"
date: 2008-12-09
forum: Virtualisation
---

### Post by quikone8 on 2008-12-09
I am almost there with the install, but now am encountering the following problem,  if anyone has experience with this help would be much appreciated.

sudo /usr/bin/vmware-config.pl
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

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-9-server/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.27-9-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-server'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:53:
/tmp/vmware-config2/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:16:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:84:
/tmp/vmware-config2/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config2/vmmon-only/linux/driver.c:171: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config2/vmmon-only/linux/driver.c:172: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c:175: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config2/vmmon-only/linux/driver.c:176: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function ‘__LinuxDriver_Ioctl’:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1781: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-server'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by Dedoimedo on 2008-12-10
Hello,

You many need the any-any patch:
[http://communities.vmware.com/message/76957](http://communities.vmware.com/message/76957)

Before you try, I'd make sure to have the kernel and everything fully updated. Furthermore, to compile you require the build-essential package (sudo apt-get install build-essential).

Dedoimedo

---

### Post by bodhi.zazen on 2008-12-10
The any-any patch is a life saver IF it is needed.

It is sometimes over advised and is not needed with 8.04 or 8.10.

There are links in the Virtualization Mega thread (there is a reason it is a sticky you know) for both how to install VMWare and solve the vmmon error message.

---

### Post by Dedoimedo on 2008-12-10
bodhi,

I've had all sorts of results with any-any:

1. Managed to install without.
2. Managed to install without but only after several kernel upgrades.
3. Did not manage to install without, did with.
4. Did not manage, patch or no patch.

All in all, it worked and did not work any which way for me.

Cheers,
Dedoimedo

---

### Post by bodhi.zazen on 2008-12-10
Same here.

I guess I am more sensitive to the any-any patch because it disables my wireless bridge, so if it is not needed I prefer to avoid it.

I do not think it should be the first step if someone is having a problem with his or her VMWare install.

---

### Post by quikone8 on 2008-12-11
Hi everybody,

I ended up needing the vmware-update-2.6.27-5.5.7-2.tar.gz patch.  After installing it, everything is up and running.

Thanks everyone for the help!!:lolflag:

Now, the next step.

Is there a interface for vmware, if so how and where?
Is there a tutorial for first time use?

If anyone needs the patch, use the following;
 wget -c [http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz](http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz)

After downloading change to the download directory, probably;  cd ~/vmware-update-2.6.27-5.5.7-2

And then sudo ./runme.pl

Answer the defaults, worked great for me

---

### Post by quikone8 on 2008-12-11
Hi everybody,

I ended up needing the vmware-update-2.6.27-5.5.7-2.tar.gz patch.  After installing it, everything is up and running.

Thanks everyone for the help!!:lolflag:

Now, the next step.

Is there a interface for vmware, if so how and where?
Is there a tutorial for first time use?

If anyone needs the patch, use the following;
 wget -c [http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz](http://www.insecure.ws/warehouse/vmware-update-2.6.27-5.5.7-2.tar.gz)

After downloading change to the download directory, probably;  cd ~/vmware-update-2.6.27-5.5.7-2

Don't forget to extract the files,

And then sudo ./runme.pl

Answer the defaults, worked great for me

---

