---
title: "[ubuntu 8.04] vmware-tools-7.6.3"
date: 2008-04-25
forum: Virtualisation
---

### Post by thefinest on 2008-04-25
Hello,

I just installed ubuntu 8.04 via Vmware Fusion on my Mac. Everything worked fine so far but the installation of vmware-tools. 

I followed some Howto's and already installed the build-essentials, linux-headers and linux-source for the current kernel.

The installation of vmware-tools works fine, however, fails on compiling modules with some warnings:

In file included from /tmp/vmware-config8/vmblock-only/linux/os.h:35,
                 from /tmp/vmware-config8/vmblock-only/linux/block.c:26:
/tmp/vmware-config8/vmblock-only/./include/compat_wait.h:55:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config8/vmblock-only/./include/compat_wait.h:61:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config8/vmblock-only/linux/os.h:35,
                 from /tmp/vmware-config8/vmblock-only/linux/block.c:26:
/tmp/vmware-config8/vmblock-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config8/vmblock-only/linux/vmblockInt.h:40,
                 from /tmp/vmware-config8/vmblock-only/linux/block.c:29:
/tmp/vmware-config8/vmblock-only/./include/vm_basic_types.h:184: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/tmp/vmware-config8/vmblock-only/linux/block.o] Error 1
make[1]: *** [_module_/tmp/vmware-config8/vmblock-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmblock.ko] Error 2
make: Leaving directory `/tmp/vmware-config8/vmblock-only'
Unable to build the vmblock module.

This "Error 2" happens everytime the vmware script is trying to build a module.

**Update:** I just tried the fix mentioned [here]("http://blog.gnu-designs.com/fix-vmware-vmw_have_epoll-error-message-with-current-distributions"), it does not apply because the specified line is already there.

**Update 2:**

I just installed vmware-any-any-update and vmblock builds now but the other modules are still throwing the same error.

Here's the complete error output:

```
Updating /usr/bin/vmware ... failed
Cannot open /usr/bin/vmware: No such file or directory
Updating /usr/bin/vmnet-bridge ... failed
Cannot open /usr/bin/vmnet-bridge: No such file or directory
Updating /usr/lib/vmware-tools/bin/vmware-vmx ... failed
Cannot open /usr/lib/vmware-tools/bin/vmware-vmx: No such file or directory
Updating /usr/lib/vmware-tools/bin-debug/vmware-vmx ... failed
Cannot open /usr/lib/vmware-tools/bin-debug/vmware-vmx: No such file or directory
VMware modules in "/usr/lib/vmware-tools/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config-tools.pl". Do you want this script to invoke the command
for you now? [yes] 


Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:                                      done
   Blocking file system:                                               done
Trying to find a suitable vmmemctl module for your running kernel.

None of the pre-built vmmemctl modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmmemctl module 
for your system (you need to have a C compiler installed on your system)? 
[yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmemctl module.

Building the vmmemctl module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config10/vmmemctl-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config10/vmmemctl-only/backdoorGcc32.o
  CC [M]  /tmp/vmware-config10/vmmemctl-only/os.o
In file included from /tmp/vmware-config10/vmmemctl-only/os.c:51:
/tmp/vmware-config10/vmmemctl-only/compat_wait.h:55:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config10/vmmemctl-only/compat_wait.h:61:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config10/vmmemctl-only/os.c:51:
/tmp/vmware-config10/vmmemctl-only/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
make[2]: *** [/tmp/vmware-config10/vmmemctl-only/os.o] Error 1
make[1]: *** [_module_/tmp/vmware-config10/vmmemctl-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmemctl.ko] Error 2
make: Leaving directory `/tmp/vmware-config10/vmmemctl-only'
Unable to build the vmmemctl module.

The memory manager driver (vmmemctl module) is used by VMware host software to 
efficiently reclaim memory from a virtual machine.
If the driver is not available, VMware host software may instead need to swap 
guest memory to disk, which may reduce performance.
The rest of the software provided by VMware Tools is designed to work 
independently of this feature.
If you want the memory management feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 

Trying to find a suitable vmhgfs module for your running kernel.

None of the pre-built vmhgfs modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmhgfs module.

Building the vmhgfs module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config11/vmhgfs-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config11/vmhgfs-only/backdoor.o
  CC [M]  /tmp/vmware-config11/vmhgfs-only/backdoorGcc32.o
  CC [M]  /tmp/vmware-config11/vmhgfs-only/bdhandler.o
In file included from /tmp/vmware-config11/vmhgfs-only/rpcout.h:30,
                 from /tmp/vmware-config11/vmhgfs-only/hgfsBd.h:28,
                 from /tmp/vmware-config11/vmhgfs-only/bdhandler.c:43:
/tmp/vmware-config11/vmhgfs-only/vm_basic_types.h:184: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config11/vmhgfs-only/request.h:35,
                 from /tmp/vmware-config11/vmhgfs-only/bdhandler.c:48:
/tmp/vmware-config11/vmhgfs-only/compat_wait.h:55:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config11/vmhgfs-only/compat_wait.h:61:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config11/vmhgfs-only/request.h:35,
                 from /tmp/vmware-config11/vmhgfs-only/bdhandler.c:48:
/tmp/vmware-config11/vmhgfs-only/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
make[2]: *** [/tmp/vmware-config11/vmhgfs-only/bdhandler.o] Error 1
make[1]: *** [_module_/tmp/vmware-config11/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-config11/vmhgfs-only'
Unable to build the vmhgfs module.

The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.
If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 

Trying to find a suitable vmxnet module for your running kernel.

None of the pre-built vmxnet modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmxnet module for
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmxnet module.

Building the vmxnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config12/vmxnet-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config12/vmxnet-only/vmxnet.o
In file included from /tmp/vmware-config12/vmxnet-only/vmxnet.c:49:
/tmp/vmware-config12/vmxnet-only/vm_basic_types.h:184: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
/tmp/vmware-config12/vmxnet-only/vmxnet.c: In function ‘vmxnet_probe_device’:
/tmp/vmware-config12/vmxnet-only/vmxnet.c:866: error: implicit declaration of function ‘SET_MODULE_OWNER’
make[2]: *** [/tmp/vmware-config12/vmxnet-only/vmxnet.o] Error 1
make[1]: *** [_module_/tmp/vmware-config12/vmxnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmxnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config12/vmxnet-only'
Unable to build the vmxnet module.

The fast network device driver (vmxnet module) is used only for our fast 
networking interface. The rest of the software provided by VMware Tools is 
designed to work independently of this feature.
If you wish to have the fast network driver enabled, you can install the driver
by running vmware-config-tools.pl again after making sure that gcc, binutils, 
make and the kernel sources for your running kernel are installed on your 
machine. These packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 

Trying to find a suitable vmblock module for your running kernel.

None of the pre-built vmblock modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmblock module 
for your system (you need to have a C compiler installed on your system)? 
[yes] 

Extracting the sources of the vmblock module.

Building the vmblock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config13/vmblock-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config13/vmblock-only/linux/block.o
  CC [M]  /tmp/vmware-config13/vmblock-only/linux/control.o
  CC [M]  /tmp/vmware-config13/vmblock-only/linux/dbllnklst.o
  CC [M]  /tmp/vmware-config13/vmblock-only/linux/dentry.o
  CC [M]  /tmp/vmware-config13/vmblock-only/linux/file.o
  CC [M]  /tmp/vmware-config13/vmblock-only/linux/filesystem.o
  CC [M]  /tmp/vmware-config13/vmblock-only/linux/inode.o
  CC [M]  /tmp/vmware-config13/vmblock-only/linux/module.o
  CC [M]  /tmp/vmware-config13/vmblock-only/linux/stubs.o
  CC [M]  /tmp/vmware-config13/vmblock-only/linux/super.o
  LD [M]  /tmp/vmware-config13/vmblock-only/vmblock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config13/vmblock-only/vmblock.mod.o
  LD [M]  /tmp/vmware-config13/vmblock-only/vmblock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
cp -f vmblock.ko ./../vmblock.o
make: Leaving directory `/tmp/vmware-config13/vmblock-only'
The module loads perfectly in the running kernel.

[EXPERIMENTAL] The Virtual Machine Communication Interface (VMCI) service 
provides a new communication capability with the Host, primarily for 
development at the moment.  Would you like to enable this feature? [no] 



Detected X.org version 
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)

Current Operating System: Linux thefinest-desktop 2.6.24-16-generic #1 SMP Thu Apr
10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM

	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
.



No drivers for X.org version: 
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)

Current Operating System: Linux thefinest-desktop 2.6.24-16-generic #1 SMP Thu Apr
10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM

	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
.



Do you want to change the display size that X starts with? (yes/no) [no] 

Starting VMware Tools services in the virtual machine:
   Switching to guest configuration:                                   done
   Blocking file system:                                               done
   DMA setup:                                                          done
   Guest operating system daemon:                                      done

The configuration of VMware Tools 7.6.3 build-87978 for Linux for this running 
kernel completed successfully.

You must restart your X session before any mouse or graphics changes take 
effect.

You can now run VMware Tools by invoking the following command: 
"/usr/bin/vmware-toolbox" during an X server session.

To make use of the virtual printer, you will need to restart the CUPS service

If you wish to configure any experimental features, please run the following 
command: "vmware-config-tools.pl --experimental".

Enjoy,

--the VMware team
```

---

### Post by spaceballl on 2008-04-25
I'm in the exact same situation as you - Downloaded the most recent Ubuntu and I can't get vmware-tools to install properly. Very annoying. Any help would be appreciated!

On a side note, the scroll bar isn't working w/ my USB mouse... but maybe that has something to do w/ vmware-tools... I await a wise one's advice!

---

### Post by maddojf on 2008-04-25
I don't have much of a fix for you, but this may help a little.  I am running Ubuntu 8.04 inside VMWare Fusion on a MacBook Pro(4,1).  I read on the VMWare Fusion forums that the VMWare tools does not yet support the Kernel used in Ubuntu 8.04.  It seems that the only fix for this is to wait until VMWare provides an update.

Having said that, I went ahead and tried to install vmware-tools anyway and in the install process most of the components failed, but after it finished, I was able to get the drag and drop between the host and guest functionality which hadn't worked previously.  I don't know if any other components were installed, but I haven't really tried to find out either.  

As for the mouse, my scroll wheel didn't work at first either.  I followed the direction in a few other posts (for instance [http://ubuntuforums.org/showthread.php?t=301616&highlight=vmware+scroll+wheel](http://ubuntuforums.org/showthread.php?t=301616&highlight=vmware+scroll+wheel)).  Basically you need to edit you /etc/X11/xorg.conf.  I found that replacing: "vmmouse" with "mouse", and "ps/2" with "imps/2" gave me the best results of the solutions that were offered.  I do have the problem now that my mouse doesn't move as smooth as it used to, but it is worth it to get the scroll wheel working.  

Also, for VMWare Fusion, you can get USBOverdrive, Steermouse, or ControllerMate to program the extra buttons on your mouse from the mac side.  I use a Logitech MXRevolution which comes with a preference pane for the Mac that allows it to be programmed differently for each application.  I programmed it for the application VMWare Fusion to have the keyboard shortcuts assigned to it that I want to have work on the Linux side. So now I have a fully working multi-function mouse with scrolling.  Note: I prefer to have the horizontal scroll assigned to change tabs so I don't know whether or not horizontal scrolling will be enabled with this method.  Also, I noticed while writing this that the trackpad scrolling is now working too.

Hope this helps.

---

### Post by thefinest on 2008-04-26
I just got a private message from petercooper saying:

> For some stupid reason ubuntuforums.org won't let post a reply to your message, but this will solve your problem (I had it too):

[http://peterc.org/2008/62-how-to-install-vmware-tools-on-ubuntu-hardy-804-under-vmware-fusion.html]("http://peterc.org/2008/62-how-to-install-vmware-tools-on-ubuntu-hardy-804-under-vmware-fusion.html")

I just tried it and it works perfectly. He also mentions how to fix the scrolling problem in his blog.

---

### Post by petercooper on 2008-04-27
Appears I can post now. Sorry for calling the forums stupid, but it seemed a rather arbitrary amount of time before being activated. I guess this does cut down on the spam though, so perhaps it's worth it!

Thanks for sharing the link. A lot of people seem to have found it useful.

---

### Post by PabloCardoso on 2008-04-29
> **thefinest said:**
> I just tried it and it works perfectly. He also mentions how to fix the scrolling problem in his blog.

Yeap, I've just installed the latest version of VMware-Tools on my Ubuntu 8.04 virtual machine running the latest kernel (2.6.24-16-generic). The link [http://peterc.org/2008/62-how-to-install-vmware-tools-on-ubuntu-hardy-804-under-vmware-fusion.html]("http://peterc.org/2008/62-how-to-install-vmware-tools-on-ubuntu-hardy-804-under-vmware-fusion.html") works like a charm!

The mouse thing, I had to change back the driver from vmmouse to mouse and add the protocol line to imps/2 (note that the line "protocol ps/2" didn't exist on my xorg.conf)...

My section looks like this and it's working right now:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Protocol"      "IMPS/2"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
EndSection

```

EDIT: I'm running a VMware Server 1.0.5 on a Fedora Core 6 host with a Ubuntu 8.04 Virtual Machine...

---

### Post by ubusarah on 2008-04-29
Thanks for the detailed blog post, Peter! 

The instructions worked fine for me; Ubuntu 8.0.4 installed on VMWare Fusion 1.1.2 running on MacOS 10.5.2.

I did get one weird looking error message; it looked like maybe there was a broken package in one of the dependencies. I think it was ScrollKeeper or something like that. It seemed to be complaining about the syntax of an xml file. I ignored it, and everything else went smoothly.

And the VMWare tools all seem to be working now!

---

