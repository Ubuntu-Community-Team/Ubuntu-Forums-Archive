---
title: "Virtualbox install broken (12.04.2 x86)"
date: 2013-02-25
forum: Virtualisation
---

### Post by Objekt on 2013-02-25
This must be the umpteenth thread on this topic, but none of the "fixes" posted elsewhere have worked.

I need to create a virtualized Windows XP machine on my new Ubuntu 12.04.2 install (not *totally* new, I have all updates as of this writing), but I can't get it to work.  The installation (through Software Center) always generates an error message with a non-working "fake" Virtualbox install.

During installation, I get an error dialog which says in part:
> Sorry, a problem occurred while installing software.  Package: virtualbox-dkms
If I click "Details" it says the problem is "virtualbox kernel module failed to build."

Here's the error dialog I get when attempting to start up a virtual machine in the non-working Virtualbox install:

> Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

Executing that command as instructed does not fix the problem, and I do have the DKMS package installed before I install Virtualbox.

Simultaneously, I get another error dialog stating:
> Failed to open a session for the virtual machine XP In Linux (x86).

The virtual machine 'XP In Linux (x86)' has terminated unexpectedly during startup with exit code 1.

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Machine
Interface: IMachine {5eaa9319-62fc-4b0a-843c-0cb1940f8a91}
Details:
Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {5eaa9319-62fc-4b0a-843c-0cb1940f8a91}

I also have the generic kernel headers installed, so I have no idea how to fix this.  I have reinstalled dkms as well.  Still have the problem noted.

The system is a Samsung Series 3 notebook (model NP300-V5A-A02US), which I dual-boot with Windows 7 Home Premium.  Under Windows 7, I have no trouble whatsoever using Virtualbox.

---

### Post by varunendra on 2013-02-26
> **Objekt said:**
> If I click "Details" it says the problem is "virtualbox kernel module failed to build."
This error doesn't make much sense other than indicating that either headers and/or gcc packages are not installed, or are incompatible.

Are you using the default Ubuntu repositories or the one from VBox website?

Make sure you are added to the vboxusers group. To check that -
```
groups
```
If it shows "vboxusers" among other groups, then double-check other possibilities.

Please try-
```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install --reinstall linux-headers-generic build-essential
```
Then run-
```
sudo /etc/init.d/vboxdrv setup
```
If it doesn't work or returns errors, then also reinstall VBox-
```
sudo apt-get install --reinstall virtualbox
```
..or whatever package you are using for it.

Please confirm these and post back errors, if any.

---

### Post by Objekt on 2013-02-26
Groups does *not* show "vboxusers."  So I think you are on to something.  I'll try the reinstall from console.  

Okay, I tried it and there's an error:
> No suitable module for running kernel found
This is probably the root of the problem - but, again, I don't know how to fix this.

For what it's worth, here's the make.log file (found in /var/lib/dkms/virtualbox/4.1.12/build) from where the installation process tries to build the kernel module:
> DKMS make.log for virtualbox-4.1.12 for kernel 3.5.0-25-generic (i686)
Tue Feb 26 10:58:29 MST 2013
make: Entering directory `/usr/src/linux-headers-3.5.0-25-generic'
  LD      /var/lib/dkms/virtualbox/4.1.12/build/built-in.o
  LD      /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/built-in.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/linux/SUPDrv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/SUPDrv.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/SUPDrvSem.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/alloc-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/initterm-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/memobj-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/mpnotification-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/powernotification-r0drv.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/linux/assert-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/linux/alloc-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/linux/initterm-r0drv-linux.o
  CC [M]  /var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.o
/var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.c: In function &#8216;rtR0MemObjLinuxDoMmap&#8217;:
/var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.c:1150:9: error: implicit declaration of function &#8216;do_mmap&#8217; [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/var/lib/dkms/virtualbox/4.1.12/build/vboxdrv/r0drv/linux/memobj-r0drv-linux.o] Error 1
make[1]: *** [/var/lib/dkms/virtualbox/4.1.12/build/vboxdrv] Error 2
make: *** [_module_/var/lib/dkms/virtualbox/4.1.12/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'

---

### Post by varunendra on 2013-02-26
Didn't look at the output but first things first. To add yourself to vboxusers group, please run -
```
sudo adduser <your user id> vboxusers
```

---

### Post by pfeiffep on 2013-02-27
> **Objekt said:**
> This must be the umpteenth thread on this topic, but none of the "fixes" posted elsewhere have worked.

I need to create a virtualized Windows XP machine on my new Ubuntu 12.04.2 install (not *totally* new, I have all updates as of this writing), but I can't get it to work.  The installation (through Software Center) always generates an error message with a non-working "fake" Virtualbox install.

During installation, I get an error dialog which says in part:

If I click "Details" it says the problem is "virtualbox kernel module failed to build."

Here's the error dialog I get when attempting to start up a virtual machine in the non-working Virtualbox install:



Executing that command as instructed does not fix the problem, and I do have the DKMS package installed before I install Virtualbox.

Simultaneously, I get another error dialog stating:


I also have the generic kernel headers installed, so I have no idea how to fix this.  I have reinstalled dkms as well.  Still have the problem noted.

The system is a Samsung Series 3 notebook (model NP300-V5A-A02US), which I dual-boot with Windows 7 Home Premium.  Under Windows 7, I have no trouble whatsoever using Virtualbox.

I had a VERY similar situation:
[LIST]
[*]Installed VirtualBox using Synaptic (Ubuntu 12.10)
[*]VirtualBox started and led me through GUI set up, when attempting to start the instance I received the same messages.
[*]Completely removed, rebooted , refreshed Synaptic then reinstalled - same results.
[*]Navigated to /etc/init.d and did NOT find [COLOR="Red"]**vboxdrv**[/COLOR]
[*]Did find ***virtualbox*** and after I executed " _sudo /etc/init.d/virtualbox setup_ " everything worked):P
[/LIST]

---

### Post by Objekt on 2013-02-27
When I execute 'sudo /etc/init.d/virtualbox setup' this is what I get:
```
objekt@objekt_lappy:~$ sudo /etc/init.d/virtualbox setup
[sudo] password for rrece440user: 
Usage: /etc/init.d/virtualbox {start|stop|stop_vms|restart|force-reload|status}
```
and Virtualbox is still broken.

---

### Post by pfeiffep on 2013-02-27
> **Objekt said:**
> When I execute 'sudo /etc/init.d/virtualbox setup' this is what I get:
```
objekt@objekt_lappy:~$ sudo /etc/init.d/virtualbox setup
[sudo] password for rrece440user: 
Usage: /etc/init.d/virtualbox {start|stop|stop_vms|restart|force-reload|status}
```
and Virtualbox is still broken.

date stamp on my installation of Virtual box

 ls -al /etc/init.d/v*
-rwxr-xr-x 1 root root 6138 Apr  5  2012 /etc/init.d/virtualbox

I did state in first response this was a SIMILAR;) situation
you have a different version (12.04) and are using software center for installation.

what does this command produce 
[INDENT]sudo /etc/init.d/virtualbox start[/INDENT] 

possibly you can try this command to learn more about virtual box
[INDENT]man virtualbox[/INDENT]

If this doesn't help possibly a MOD :popcorn:will have more complete suggestions or an actual solution that works for you

---

### Post by varunendra on 2013-02-27
Mods are just common users like everyone else here :P

Btw, it's past midnight here and I'm too tired now to play brain games, so please confirm if you are now successfully added to the vboxusers group -
```
groups
```

---

### Post by Objekt on 2013-02-27
Yes, I am now part of 'vboxusers'.

---

### Post by Objekt on 2013-02-27
Rather than continue using the Software Center method which doesn't work, I downloaded a .deb package for Virtualbox from the Virtualbox website (virtualbox-4.2_4.2.6-82870~Ubuntu~precise_i386.deb) and installed it that way.  

So far, it's working.  So I'm calling this one tentatively "solved."

It would have been nice if the Software Center method worked, but eh, what are you going to do?

---

### Post by nicolas1390 on 2013-06-19
Hello.
I have a problem like this !
I have installed Ubuntu 12.04.2 and I have Virtualbox on ubuntu , but it doesn't work properly !
when I want to power on the virtual machine , Virtualbox stop and give error :

 ```
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```

help me please ! (I have Samsung Series 3 notebook)

---

### Post by varunendra on 2013-06-20
Welcome to the forums Nicolas !

Please run the following commands in a terminal (Ctrl + Alt + T) and show us their outputs :
```
dpkg --get-selections | grep virtualbox
groups
```

---

