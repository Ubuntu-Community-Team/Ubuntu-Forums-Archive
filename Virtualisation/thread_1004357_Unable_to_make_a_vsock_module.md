---
title: "Unable to make a vsock module"
date: 2008-12-07
forum: Virtualisation
---

### Post by paragkalra on 2008-12-07
Hi Friends,

I have installed VMware Server 2.0 on Ubuntu 8.10 (HOST). Today I upgraded the kernel to include the modules for the webcam.

As a result of which after the upgradeVMware server failed to start and I had to rerun "/usr/bin/vmware-config.pl". The reconfiguration process failed to build the vsock module. Here is the complete set of messages:

 > None of the pre-built vsock modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vsock module for
your system (you need to have a C compiler installed on your system)? [yes]

Extracting the sources of the vsock module.

Building the vsock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vsock-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config0/vsock-only/linux/af_vsock.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/util.o
/tmp/vmware-config0/vsock-only/linux/util.c: In function &#8216;VSockVmciLogPkt&#8217;:
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
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
cp -f vsock.ko ./../vsock.o
make: Leaving directory `/tmp/vmware-config0/vsock-only'
Unable to make a vsock module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config0/vsock.o': -1 Unknown symbol in module
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.

The VM communication interface socket family is used in conjunction with the VM
communication interface to provide a new communication path among guests and
host.  The rest of this software provided by VMware Server is designed to work
independently of this feature.  If you wish to have the VSOCK feature  you can
install the driver by running vmware-config.pl again after making sure that
gcc, binutils, make and the kernel sources for your running kernel are
installed on your machine. These packages are available on your distribution's
installation CD.
[ Press the Enter key to continue.]

 I have following questions.

1. What all components of VMware won't because of it?

2. Has any one faced same kind of problem before, If yes were you able to resolve it?

3. I restarted one of my already created VM and it seem to work fine. What are the potential issues  I might face with my already created VMs due to absence of vscok module.

---

### Post by bodhi.zazen on 2008-12-07
There is a link to a solution in the Virtualization mega thread.

There is a reason it is a sticky ;)

---

### Post by paragkalra on 2008-12-07
Thanks bodhi.zazen...the patched worked like a breeze...:)

---

### Post by bodhi.zazen on 2008-12-07
No problem, thank you for using the sticky.

But I can not take credit for the patch, it is a community effort, I am just trying to track and organize it all, make it easier to find and access.

---

