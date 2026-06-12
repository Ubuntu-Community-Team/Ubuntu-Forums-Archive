---
title: "VMWare problems after upgrading to Heron."
date: 2008-07-08
forum: Virtualisation
---

### Post by namich2007 on 2008-07-08
Hi everyone,

As everyone, my VMware  set-up was broken when I upgrades to Hardy Heron. I had VMware server 1.0.4 build-56528 installed on Gutsy.....worked beautifully.

I have been trying to get my VM going again and was wondering if Hardy Heron supports VMware server 1.0.4 ( I have serials for that).

If this version is supported, do I have to completely re-install, or can I just repair this by installing the appropriate modules.

Thanks namich

---

### Post by fjgaude on 2008-07-08
Say, did you run

```
sudo /usr/bin/vmware-config.pl
```

to see if that worked?

---

### Post by namich2007 on 2008-07-08
fjgaude'


I ran that code as you provided and here are the errors I receive:

namich@michtop:~/vmware-server-distrib$ sudo /usr/bin/vmware-config.pl
[sudo] password for namich: 
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
kernel? [/lib/modules/2.6.24-19-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:48:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config1/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

any help would be appreciated

Namich

---

### Post by fjgaude on 2008-07-08
I would suggest you delete the present install and use the 1.0.6 version from vmware.com. With 8.04 it should install easily.

Make sure you keep your VM WinXP as is. It will work with the new install. The .vmx files are usually in /var/liv/vmware/Virtual Machines folder.

The easy way to re-install is to either delete or rename /etc/vmware, then do the new install. Rename vmware to say, vmwarebak. Leave everything else the way it is. After the new install you can delete /vmwarebak, since no longer used.

---

### Post by namich2007 on 2008-07-08
I would like to completely remove the old VMware  and start fresh. What would you recommend I do first.

Thanks

---

### Post by forger on 2008-07-08
Do you have or did you have (say the last 3 months) any other virtual machine applications, virtualbox or kvm or qemu? Their leftovers could be causing problems.

Have you tried the solution at [https://help.ubuntu.com/community/VMware](https://help.ubuntu.com/community/VMware) ?

Is this ubuntu architecture amd64 or i386? 
[http://ubuntuforums.org/showthread.php?t=826626](http://ubuntuforums.org/showthread.php?t=826626)
[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

---

### Post by fjgaude on 2008-07-08
> **namich2007 said:**
> I would like to completely remove the old VMware  and start fresh. What would you recommend I do first.

Thanks

Just do as suggested in the previous post... if you delete /etc/vmware file and re-install the server using the .tar.gz from vmware.com, all the old stuff will be overwritten. There are many, many files associated with vmware so this is really the only way to go, trust me.

---

### Post by namich2007 on 2008-07-09
> **fjgaude said:**
> Just do as suggested in the previous post... if you delete /etc/vmware file and re-install the server using the .tar.gz from vmware.com, all the old stuff will be overwritten. There are many, many files associated with vmware so this is really the only way to go, trust me.

 Thanks Fjgaude.... my VM is up and running.

However I have another issue. When I connect my USB stick (pen drive) to the guest OS (XP pro) , it is not detected by the guest OS. Instead it opens up on my Host OS. (Heron)

Is there some settings that I may have overlooked.


Thanks
Namich

---

### Post by fjgaude on 2008-07-09
I suppose you need to fix Hardy this way:

Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Like so:
```

       mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Then place in the fstab file this line:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Let us know if this works... I had thought that Hardy didn't need these changes but maybe it does.

---

