---
title: "Installed 8.10 - wont let me re-install vmplayer!"
date: 2008-11-11
forum: Virtualisation
---

### Post by twistedneck on 2008-11-11
Help..  i keep getting this error when it gets to the compile part of the install

Ubuntu is my main computer OS but i use vmplayer to run virtual windows xp so i can access my zune.  installed the 8.10 upgrade, and was re-installing vmplayer like i usually have to when ever new headers get released.. and this error cropped up during install!

```
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-7-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:84:
/tmp/vmware-config2/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:115:
/tmp/vmware-config2/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

twistedneck@twistedubuntu:~/Desktop/vmware/vmware-player-distrib$ 

```

i checked and those headers are installed.  i also ran uname-a and it gave me the same kernel

```
twistedneck@twistedubuntu:~$ uname -a
Linux twistedubuntu 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

```

---

### Post by posterberg on 2008-11-12
I have the exact same problem.

I also tried to copy /usr/include/semaphore.h to /usr/src/kernel-headers/include/asm.

That gave a whole bunch of new errors, I suppose that it's not the same version of semaphore.h.

Anyone got any secret tricks? ;-)

---

### Post by posterberg on 2008-11-12
I also just check my other ubuntu machine that has kernel 2.6.22-15-generic, also being Fiesty Fawn. This one does have the file asm/semaphore.h.

I am not sure if this has to do with Intrepid or the kernel, but I suppose that the kernel is more probable reason to the problem...

---

### Post by twistedneck on 2008-11-12
> **posterberg said:**
> I also just check my other ubuntu machine that has kernel 2.6.22-15-generic, also being Fiesty Fawn. This one does have the file asm/semaphore.h.

I am not sure if this has to do with Intrepid or the kernel, but I suppose that the kernel is more probable reason to the problem...

Thanks for trying that out. i have no idea what to do now! i need vmplayer to work or Ubuntu won't run my critical apps.  what to do! next steps, contact vmware.  what ever they say i'll post here.

---

### Post by posterberg on 2008-11-12
I tried using the bundle as this page suggests. It worked perfectly for me, good luck with it!

[http://kubuntuforums.net/forums/index.php?topic=3097965.0](http://kubuntuforums.net/forums/index.php?topic=3097965.0)

:guitar:

---

### Post by posterberg on 2008-11-12
I still have issues with host only networking, but bridged networking works.

So there's probably still some kind of issue with compiling the network modules. But it is at least possible to get it to work this way.

---

### Post by twistedneck on 2008-11-13
> **posterberg said:**
> I tried using the bundle as this page suggests. It worked perfectly for me, good luck with it!

[http://kubuntuforums.net/forums/index.php?topic=3097965.0](http://kubuntuforums.net/forums/index.php?topic=3097965.0)

:guitar:

That worked GREAT!  For some reason the TAR would not install.  This .bundle software makes it a lot more windows like..

---

### Post by kelargo on 2008-11-13
The bundle will not work for me... :(

> root@htpc:/home/papa/vmplayer# uname -a
Linux htpc 2.6.27-8-generic #1 SMP Thu Nov 6 17:38:14 UTC 2008 x86_64 GNU/Linux
root@htpc:/home/papa/vmplayer# ./VMware-Player-2.5.0-118166.x86_64.bundle
Extracting VMware Installer...done.
Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 keyThe product is ready to be installed.  Press enter to begin
installation or Ctrl-C to cancel.

You cannot install on a system with KVM enabled.
root@htpc:/home/papa/vmplayer#

what do I do next?

---

### Post by kelargo on 2008-11-13
err, never mind. I didnt realize KVM was installed..

---

### Post by mirror2m on 2008-11-17
> **kelargo said:**
> err, never mind. I didnt realize KVM was installed..

Thanks, it did help. I removed kvm ;)

---

### Post by Junkieman on 2008-11-19
> **posterberg said:**
> I tried using the bundle as this page suggests. It worked perfectly for me, good luck with it!

[http://kubuntuforums.net/forums/index.php?topic=3097965.0](http://kubuntuforums.net/forums/index.php?topic=3097965.0)

:guitar:
Thanks! This did the trick...

---

