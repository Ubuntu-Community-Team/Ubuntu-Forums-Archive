---
title: "VMWare install error"
date: 2009-01-20
forum: Virtualisation
---

### Post by Kerel on 2009-01-20
I've seen many others around but I'm not sure if it matches mine. 
Still new @ ubuntu, about one week or so. 

```
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
kernel? [/lib/modules/2.6.27-9-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Map '/tmp/vmware-config2/vmmon-only' wordt binnengegaan
make -C /lib/modules/2.6.27-9-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Map '/usr/src/linux-headers-2.6.27-9-generic' wordt binnengegaan
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
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
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:71:
/tmp/vmware-config2/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: Bestand of map bestaat niet
/tmp/vmware-config2/vmmon-only/linux/driver.c:146: fout: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config2/vmmon-only/linux/driver.c:147: let op: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c:150: fout: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config2/vmmon-only/linux/driver.c:151: let op: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c: In functie ‘LinuxDriver_Ioctl’:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1670: fout: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Fout 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Fout 2
make[1]: Map '/usr/src/linux-headers-2.6.27-9-generic' wordt verlaten
make: *** [vmmon.ko] Fout 2
make: Map '/tmp/vmware-config2/vmmon-only' wordt verlaten
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

Exactly what I did, everything else went fine.
Thx in advance

---

### Post by HermanAB on 2009-01-20
The way I avoid this kind of grief, is by first compiling and installing the kernel and doing a reboot.  If that works, then installing VMware always works.  If the kernel won't compile and install, then VMware won't either, since it has to modify the kernel.

Also remember that once you installed VMware, don't upgrade your kernel, unless you want to re-install VMware all over again too...

Hope that helps!

Herman

---

### Post by veloce on 2009-01-20
> **Kerel said:**
> I've seen many others around but I'm not sure if it matches mine. 
Still new @ ubuntu, about one week or so. 

(snip)

Exactly what I did, everything else went fine.
Thx in advance

Personally, I've never (re)built a linux kernel.  (I guess that means I'm still on the non-linux-guru side of the fence.)  So if rebuilding the kernel scares you ...

My guess is that you need a patch for vmware-config. Which one depends on what versions of everything you are using. So:

What versions of Ubuntu and vmware are you using?

---

### Post by dcstar on 2009-01-20
> **Kerel said:**
> I've seen many others around but I'm not sure if it matches mine. 
Still new @ ubuntu, about one week or so. 
.........
Exactly what I did, everything else went fine.
Thx in advance

Check that you have the **build-essential** and **linux-headers-generic** (assuming you are using the generic kernel) packages installed.

---

### Post by Kerel on 2009-02-06
> **HermanAB said:**
> The way I avoid this kind of grief, is by first compiling and installing the kernel and doing a reboot.  If that works, then installing VMware always works.  If the kernel won't compile and install, then VMware won't either, since it has to modify the kernel.

Also remember that once you installed VMware, don't upgrade your kernel, unless you want to re-install VMware all over again too...

Hope that helps!

Herman

Can you give me some info then about compiling a kernel? Still fresh in Ubuntu.

[QUOTE="veloce"]
My guess is that you need a patch for vmware-config. Which one depends on what versions of everything you are using. So:

What versions of Ubuntu and vmware are you using? [/QUOTE]
ubuntu = 8.10 intrepid

VMware Server 2.0
Latest Version: 2.0 | 2008/10/29 | Build: 122956

[QUOTE="dcstar"]Check that you have the build-essential and linux-headers-generic (assuming you are using the generic kernel) packages installed. [/QUOTE]

I think I have them, but can you guide me through finding them? Where are they located, or is it custom? I followed the setup from VMware with everything on default. 



Thx for the help so far guys.

---

### Post by RealG187 on 2009-02-09
I have VMware-server-1.0.6-91891 and it doesn't work, I think I need to patch it

---

