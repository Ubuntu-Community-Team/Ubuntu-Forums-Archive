---
title: "Vmware Tools Setup on Ubuntu 8.10 running on x86 (vista)"
date: 2008-12-19
forum: Virtualisation
---

### Post by btaz on 2008-12-19
After searching and searching for options of how to get VMware tools working on my system I finally came up with a small sequence of steps to follow that acutally works (for me).  As the title suggests, I'm running Ubuntu 8.10 (Intrepid) on VMware workstation 6.5 on Windows Vista

My issues when installing was vsock and then no copy/paste

Here is the Vsock error:
----------------------------------------------------
----------------------------------------------------
[SIZE="1"]Extracting the sources of the vsock module.

Building the vsock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vsock-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config0/vsock-only/linux/af_vsock.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/util.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/vsockAddr.o
  LD [M]  /tmp/vmware-config0/vsock-only/vsock.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "VMCIDatagram_CreateHnd" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_DestroyHnd" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIEvent_Subscribe" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCI_DeviceGet" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIMemcpyFromQueueV" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIQueuePair_Detach" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCI_GetContextID" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_Send" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIQueuePair_Alloc" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIEvent_Unsubscribe" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIMemcpyToQueueV" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
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
[/SIZE]
----------------------------------------------------
----------------------------------------------------



Here is the  copy and paste error:
--------------------------------------------------
--------------------------------------------------
[SIZE="1"]vmware-user failed to initialize blocking driver.  vmware workstation[/SIZE]
--------------------------------------------------
--------------------------------------------------

Now here are the steps.  (Note: I didn't create these, I just put the pieces together.  I'll give credit to where I found them)


1) Get the latest [VMware Tools]("http://open-vm-tools.sourceforge.net/") ( last test 11-08-2008 )
2) Install, but don't configure.  It is also a good idea to turn off the automatic updates in the VMware setting in windows.
3) Run the patch (Attached)  to fix the vsock error 
   [INDENT][INDENT]a.) remove the .txt extension to the patch
   b.) make it executable 
       >> chmod 711 /path-to-patch/vmware-config.pl.patch
   c.) run patch
       >>  sudo patch /usr/bin/vmware-config.pl /path-to-patch/vmware-config.pl.patch

   Source([delgurth]("http://ubuntuforums.org/member.php?u=419937") post: [http://ubuntuforums.org/showthread.php?p=6267637](http://ubuntuforums.org/showthread.php?p=6267637))[/INDENT][/INDENT]

4) Now add to the startup programs to fix (or more accurately start correctly) the copy/paste
[INDENT][INDENT]   a.) Go to System->Preferences->Startup
   b.) add the command "vmware-user >/dev/null 2>&1 -blockFd 11"
       
   Source(asif_is_me post: [http://www.howtogeek.com/howto/ubuntu/enable-copy-and-paste-from-ubuntu-vmware-guest/](http://www.howtogeek.com/howto/ubuntu/enable-copy-and-paste-from-ubuntu-vmware-guest/)[/INDENT][/INDENT]


That should do it.  Hope this helps and I enjoyed making my first post ever to any forum :)

--btaz

---

