---
title: "Ubuntu 14.04 LTS network performance problem on vmware ESXi 5.5"
date: 2015-04-09
forum: Virtualisation
---

### Post by mr_cygi on 2015-04-09
Hello,
 
I have problem with Ubuntu 14.04 LTS and network performance (ESXi 5.5). After starting downloading file (http/scp etc.) transfer is ok but after next 2-3s transfer is going down to 0. I checked everything with virtual eth adapters (e1000 and vxnet3) and with vmware tools (vmware-tools and open-vm-tools).
 
This problem exists with transfer file to Internet, when I transfer file inside our network everything is ok. From other OS on physical server transfer is ok.


Who can help me?

BR

---

### Post by mr_cygi on 2015-04-11
This problem exists only on vmware 5.5 with ubuntu 14.04 as guest OS so this is ubuntu problem.

Any idea?

---

### Post by mr_cygi on 2015-04-12
This same problem exists on ubuntu 12.04. Maybe this is driver isue? On debian 6/7 this problem doesn't exist.

---

### Post by TheFu on 2015-04-12
Perhaps if you posted some detailed information? 

We stopped using ESXi years ago (license changes scared us). Been happy on KVM ever sense.  Don't recall ever having performance issues with the stock e1000 drivers. These days, most hypervisors prefer virtio drivers - is that not an option for ESXi?

---

### Post by mr_cygi on 2015-04-13
Which kind of info do you need?

license changes?

---

### Post by mr_cygi on 2015-04-13
[COLOR=#666666][FONT=proxima-nova]I found something interesting.[/FONT][/COLOR]
[COLOR=#666666][FONT=proxima-nova]Debian and ubuntu uses e1000 driver version 7.3.21-k8-NAPI but has different kernel version:[/FONT][/COLOR]
[COLOR=#666666][FONT=proxima-nova] [/FONT][/COLOR]
[COLOR=#666666][FONT=proxima-nova]debian: 3.2.65-1+deb7u2[/FONT][/COLOR]
[COLOR=#666666][FONT=proxima-nova]ubuntu: 3.16.0-30-generic

I changed ubuntu kernel to debian kernel (3.2.65-1+deb7u2) and everything is ok, so this is ubuntu kernel problem.
Is possible to fix this problem by ubuntu dev?

[/FONT][/COLOR]

---

### Post by TheFu on 2015-04-13
Don't think that matters, but feel free to submit a bug on launchpad with the data.  I'm running e1000 drivers in a few boxes here.

 ```
$ sudo lshw -C network
 *-network DISABLED
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: p135p1
       version: 00
       serial: 00:1b:21:84:50:7c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=**e1000e** driverversion=**2.3.2-k** firmware=1.8-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:19 memory:fbee0000-fbefffff memory:fbe00000-fbe7ffff ioport:dc00(size=32) memory:fbedc000-fbedffff memory:fbe80000-fbebffff
```
and don't see any performance issues.  
Kernel is:  3.13.0-48-generic #80-Ubuntu SMP Thu Mar 12 11:16:15 UTC 2015 x86_64  (yes, I have a newer kerne, just waiting for a maintenance window to reboot)

```
$ more /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS"

```
Of course, none of the VMs use e1000 drivers - all use virtio drivers for NIC and storage, per best practices, even on Windows VMs.

My server is a fully patched 14.04 x64 system - don't know how you got a different kernel, unless you loaded the HW compatibility kernels ... 
Looking here [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) - looks like your system gets 18 months of support, not 5 yrs based on having that kernel. Looks like it is automatic for new 14.04.2 installs. Don't have any of those here.

BTW, the ESXi 5.5 Performance Best Practices Guide (pg 47-48) says to use VMXNET3 drivers instead of E1000e drivers. At least that is my interpretation.

---

### Post by mr_cygi on 2015-04-13
The most important question is that your boxes are based on vmware esxi 5.5u2? In this version is problem with ubuntu, for example in 5.1 everything is ok.
Kernel was installed from debian packages.

Regarding ESXi5.5 Performance Best Practices Guide - vmxnet3 instead e1000e (I told about e1000 not e1000e) and I told earlier that vmxnet3 doesn't work properly also on this ubuntu kernel. For example on others platforms (debian, windows etc.) this problem doesn't exist.

Thx for suggestions.

---

### Post by mr_cygi on 2015-04-17
[COLOR=#666666][FONT=proxima-nova]This same problem exists on debian with kernel 3.13 and 3.16. So it looks like kernel issue.[/FONT][/COLOR]

---

