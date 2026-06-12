---
title: "VMWare Player wont build vmnet module"
date: 2008-01-23
forum: Virtualisation
---

### Post by martibs on 2008-01-23
I've installed VMWare Player, and it runs and loads .vmx-files, but the networking doesn't work. It seems like there's some module it isn't able to build. Output from the vmware-config.pl script:

```
Do you want networking for your virtual machines? (yes/no/help) [yes] 

Configuring a bridged network for vmnet0.

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] 

Configuring a NAT network for vmnet8.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.16.0/255.255.255.0 appears to be unused.

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 172.16.16.0.

Do you wish to configure another NAT network? (yes/no) [no] 

Do you want to be able to use host-only networking in your virtual machines? 
[yes] no

Trying to find a suitable vmnet module for your running kernel.

None of the pre-built vmnet modules for VMware Player is suitable for your 
running kernel.  Do you want this program to try to build the vmnet module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmnet-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config1/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config1/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config1/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config1/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config1/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config1/vmnet-only/filter.o
  CC [M]  /tmp/vmware-config1/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config1/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config1/vmnet-only/smac_linux.x86_64.o
  LD [M]  /tmp/vmware-config1/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /tmp/vmware-config1/vmnet-only/.smac_linux.x86_64.o.cmd for /tmp/vmware-config1/vmnet-only/smac_linux.x86_64.o
  CC      /tmp/vmware-config1/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config1/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config1/vmnet-only'
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config1/vmnet.o': -1 File exists
There is probably a slight difference in the kernel configuration between the 
set of C header files you specified and your running kernel.  You may want to 
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

I did also have some problems building the vmblock module, but it didn't seem relevant.

---

### Post by joechiang on 2008-02-25
I've also met this problem 

VMware workstation v6.0.0.45731 and Ubuntu 7.10 2.6.22.14

---

### Post by HermanAB on 2008-02-25
Install the kernel source and compile and install the kernel then reboot with the newly compiled kernel.  Thereafter, VMware should also be able to compile.

---

