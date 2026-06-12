---
title: "VMWare requires c header files"
date: 2009-03-23
forum: Server Platforms
---

### Post by BradleyAtkins on 2009-03-23
Hi

Seems I have the wrong header files for installing VMWare on 64 bit Ubuntu Server 8.10. Can anyone tell me how to get them? Here is the error message: -

[B]Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vsock-only'
make -C /lib/modules/2.6.27-7-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-server'
  CC [M]  /tmp/vmware-config0/vsock-only/linux/af_vsock.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/util.o
/tmp/vmware-config0/vsock-only/linux/util.c: In function â&#8364;&#732;VSockVmciLogPktâ&#8364;&#8482;:
/tmp/vmware-config0/vsock-only/linux/util.c:157: warning: format not a string literal and no format arguments
  CC [M]  /tmp/vmware-config0/vsock-only/linux/vsockAddr.o
  LD [M]  /tmp/vmware-config0/vsock-only/vsock.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "VMCIDatagram_CreateHnd" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_DestroyHnd" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCI_GetContextID" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_Send" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
  CC      /tmp/vmware-config0/vsock-only/vsock.mod.o
  LD [M]  /tmp/vmware-config0/vsock-only/vsock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-server'
cp -f vsock.ko ./../vsock.o
make: Leaving directory `/tmp/vmware-config0/vsock-only'
Unable to make a vsock module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config0/vsock.o': -1 Unknown symbol in module There is probably a slight difference in the kernel configuration between the set of C header files you specified and your running kernel.  You may want to rebuild a kernel based on that directory, or specify another directory.

The VM communication interface socket family is used in conjunction with the VM communication interface to provide a new communication path among guests and host.  The rest of this software provided by VMware Server is designed to work independently of this feature.  If you wish to have the VSOCK feature  you can install the driver by running vmware-config.pl again after making sure that gcc, binutils, make and the kernel sources for your running kernel are installed on your machine. These packages are available on your distribution's installation CD.[/B]

I do have the installation CD but don't know how to get them off it....

Cheers

Brad

BTW

This may not be as it seems, perhaps I do have the correct versions of C headers: -

root@poweredge:/tmp/vmware-server-distrib# apt-get install xinetd linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xinetd is already the newest version.
linux-headers-2.6.27-7-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 67 not upgraded.

Can anyone tell me the reason for the error message?

Thanks

---

### Post by netztier on 2009-03-23
> **BradleyAtkins said:**
> 
Seems I have the wrong header files for installing VMWare on 64 bit Ubuntu Server 8.10.

*gentle nudge*

You've already spotted the Virtualization sub-forum here, haven't you?

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

regards

Marc

---

### Post by BradleyAtkins on 2009-03-23
Cheers :D

---

### Post by windependence on 2009-03-23
A lot less trouble to install ESXi on the bare metal and then run your VMs on top of that including your Ubuntu install. You can convert your physical Ubuntu machine to a VM with the free VMware Converter.

-Tim

---

### Post by netztier on 2009-03-23
> **windependence said:**
> A lot less trouble to install ESXi on the bare metal and then run your VMs on top of that including your Ubuntu install. 

I'd agree. Tried. Failed.

ESXi didn't like my (new) hardware at all :-( .

Thats back to VMware Server 2.0 on Ubuntu, then. And I hope it'll accept Ubuntu's subinterfaces on a dot1q trunk as "host interfaces" to connect it's VMnetXs to. Too bad it doesn't seem to have the vSwitch concept that ESX(i) has - I've been working with that in the office.

regards

Marc

---

### Post by BradleyAtkins on 2009-03-24
Hi sorry, that reply assumes a lot of knowledge on my part :)

I have found the converter on the web but I don't really understand what you mean by converting the physical machine into a virtual one.

I have just bought a server and have installed Ubuntu server on it. Now I am trying to install VMWare on top of that. I am a real novice at this so if I am doing things in the wrong order please let me now.

Are you saying that if I run this converter my Ubuntu Server will then be running on top of VMWare or something?

Sorry for sounding so dense but I have no experience of this technology.

Cheers

Brad

---

