---
title: "VMWare requires c header files"
date: 2009-03-23
forum: Virtualisation
---

### Post by BradleyAtkins on 2009-03-23
Hi

Seems I have the wrong header files for installing VMWare on 64 bit Ubuntu Server 8.10. Can anyone tell me how to get them? Here is the error message: -

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vsock-only'
make -C /lib/modules/2.6.27-7-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-server'
CC [M] /tmp/vmware-config0/vsock-only/linux/af_vsock.o
CC [M] /tmp/vmware-config0/vsock-only/linux/driverLog.o
CC [M] /tmp/vmware-config0/vsock-only/linux/util.o
/tmp/vmware-config0/vsock-only/linux/util.c: In function â€˜VSockVmciLogPktâ€™:
/tmp/vmware-config0/vsock-only/linux/util.c:157: warning: format not a string literal and no format arguments
CC [M] /tmp/vmware-config0/vsock-only/linux/vsockAddr.o
LD [M] /tmp/vmware-config0/vsock-only/vsock.o
Building modules, stage 2.
MODPOST 1 modules
WARNING: "VMCIDatagram_CreateHnd" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_DestroyHnd" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCI_GetContextID" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_Send" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
CC /tmp/vmware-config0/vsock-only/vsock.mod.o
LD [M] /tmp/vmware-config0/vsock-only/vsock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-server'
cp -f vsock.ko ./../vsock.o
make: Leaving directory `/tmp/vmware-config0/vsock-only'
Unable to make a vsock module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config0/vsock.o': -1 Unknown symbol in module There is probably a slight difference in the kernel configuration between the set of C header files you specified and your running kernel. You may want to rebuild a kernel based on that directory, or specify another directory.

The VM communication interface socket family is used in conjunction with the VM communication interface to provide a new communication path among guests and host. The rest of this software provided by VMware Server is designed to work independently of this feature. If you wish to have the VSOCK feature you can install the driver by running vmware-config.pl again after making sure that gcc, binutils, make and the kernel sources for your running kernel are installed on your machine. These packages are available on your distribution's installation CD.

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

