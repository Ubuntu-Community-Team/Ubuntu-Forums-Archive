---
title: "Installing VMWare Workstation 6.5 on 8.04.1"
date: 2008-09-13
forum: Virtualisation
---

### Post by philgenius on 2008-09-13
Hi all,

I installed the VMWare Workstation using steps from here: [http://blog.zmang.com/installing-vmware-workstation-65-beta-on-ubuntu-hardy-heron-804-faqs/](http://blog.zmang.com/installing-vmware-workstation-65-beta-on-ubuntu-hardy-heron-804-faqs/)

And then upon running```
$ /usr/bin/vmware
``` I get an error message saying that VMware was improperly configured. So this is what I did:

```
philip@1951-44U:~$ /usr/bin/vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

philip@1951-44U:~$ /usr/bin/vmware-config.pl
Please re-run this program as the super user.

Execution aborted.

philip@1951-44U:~$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Blocking file system:                                               done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   Bridged networking on /dev/vmnet2                                   done
   DHCP server on /dev/vmnet3                                          done
   NAT service on /dev/vmnet3                                          done
   Host-only networking on /dev/vmnet3                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the theme icons? 
[/usr/share/icons] /usr/share/icons

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] /usr/share/applications

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] /usr/share/pixmaps

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-19-generic/build/include] /lib/modules/2.6.24-19-generic/build/include

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciContext.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDs.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciGroup.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciProcess.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciResource.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciSharedMem.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

/dev is dynamic:
Trying to find a suitable vmblock module for your running kernel.

None of the pre-built vmblock modules for VMware Workstation is suitable for 
your running kernel.  Do you want this program to try to build the vmblock 
module for your system (you need to have a C compiler installed on your 
system)? [yes] yes

Extracting the sources of the vmblock module.

Building the vmblock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmblock-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/block.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/control.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/dbllnklst.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/dentry.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/file.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/filesystem.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/inode.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/module.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/stubs.o
  CC [M]  /tmp/vmware-config0/vmblock-only/linux/super.o
  LD [M]  /tmp/vmware-config0/vmblock-only/vmblock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmblock-only/vmblock.mod.o
  LD [M]  /tmp/vmware-config0/vmblock-only/vmblock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
cp -f vmblock.ko ./../vmblock.o
make: Leaving directory `/tmp/vmware-config0/vmblock-only'
The module loads perfectly in the running kernel.

/dev is dynamic:
You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] yes

Trying to find a suitable vmnet module for your running kernel.

None of the pre-built vmnet modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmnet module for 
your system (you need to have a C compiler installed on your system)? [yes] yes

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.24-19-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/filter.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Do you want to install the Eclipse Integrated Virtual Debugger? You must have 
the Eclipse IDE installed. [no] no

Starting VMware services:
   Virtual machine monitor                                             done
   Blocking file system:                                               done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   Host-only networking on /dev/vmnet1 (background)                    done
   DHCP server on /dev/vmnet1                                          done
   Bridged networking on /dev/vmnet2                                   done
   Host-only networking on /dev/vmnet3 (background)                    done
   DHCP server on /dev/vmnet3                                          done
   NAT service on /dev/vmnet3                                          done
   Host-only networking on /dev/vmnet8 (background)                    done
   DHCP server on /dev/vmnet8                                         failed
   NAT service on /dev/vmnet8                                         failed

The configuration of VMware Workstation 6.0.5 build-109488 for Linux for this 
running kernel completed successfully.

You can now run VMware Workstation by invoking the following command: 
"/usr/bin/vmware".

Enjoy,

--the VMware team

philip@1951-44U:~$ /usr/bin/vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

philip@1951-44U:~$ 

```

Any idea why?

---

### Post by philgenius on 2008-10-12
Ummm....bump?

I think 4 weeks is a good enough time to let this topic simmer before bumping.

---

### Post by bodhi.zazen on 2008-10-12
Ouch ....

The only advice I can offer is :

1. A link to this thread :

[How to VMWare in Ubuntu 8.04 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=779934") 

I do not have any experience with workstation , but others haev reported success.

2. Did you try the vmware forums ?

---

### Post by mcativa on 2008-12-03
I had the same probleam after updating the Kernel.
Can't make the files with kernel version 2.6.24-22-generic

If I boot with version 2.6.24-21-generic works OK.

I see you were using version 2.6.24-19. So I may suggest changing the kernel version.
I know it's not a real solution, but it works for me.

---

### Post by F650 on 2008-12-05
Your config-pl errors is related with your DHCP and NAT settings. But i saw that when you were in second configuration attempt you did not done anything:

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] yes

I wonder about why did you choose yes for this? I also want to install wmware, so please write here the next results.

Thank you.

---

