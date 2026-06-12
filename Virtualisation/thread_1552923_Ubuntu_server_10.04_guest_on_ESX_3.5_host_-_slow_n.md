---
title: "Ubuntu server 10.04 guest on ESX 3.5 host - slow network"
date: 2010-08-14
forum: Virtualisation
---

### Post by vyruz18 on 2010-08-14
Hi,

I'm running Ubuntu 10.04 LTS server inside a virtual machine hosted on a ESX 3.5 host. The problem I'm having is poor network performance.
I'm testing using iperf with the ubuntu guest being the iperf client and a physical windows XP machine being the iperf server.
Max speed i'm getting is about 30Mbit/s.
Windows guests on the same ESX 3.5 hosts are all getting 90~100Mbit/s speeds using the same testing method.

My assumption is that this is related to the Ubuntu server not using the correct NIC drivers, I've found [this guide]("http://flux.org.uk/howto/linux/ubuntu_vmware_tools") on how to install vmware tools on ubuntu server, however when I'm running the installer I'm always asked whether I want to build drivers for which no precompiled drivers exist for my system. When choosing yes I get the following error:
```
Trying to find a suitable vmxnet module for your running kernel.

None of the pre-built vmxnet modules for VMware Tools is suitable for your
running kernel.  Do you want this program to try to build the vmxnet module for
your system (you need to have a C compiler installed on your system)? [yes]

Extracting the sources of the vmxnet module.

Building the vmxnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmxnet-only'
make -C /lib/modules/2.6.32-24-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic-pae'
  CC [M]  /tmp/vmware-config2/vmxnet-only/vmxnet.o
In file included from /tmp/vmware-config2/vmxnet-only/vmxnet.c:50:
/tmp/vmware-config2/vmxnet-only/vm_basic_types.h:119:7: warning: "__FreeBSD__" is not defined
/tmp/vmware-config2/vmxnet-only/vmxnet.c: In function âvmxnet_change_mtuâ:
/tmp/vmware-config2/vmxnet-only/vmxnet.c:190: error: âstruct net_deviceâ has no member named âprivâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c: In function âvmxnet_get_drvinfoâ:
/tmp/vmware-config2/vmxnet-only/vmxnet.c:264: error: âstruct net_deviceâ has no member named âprivâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c: In function âvmxnet_set_tsoâ:
/tmp/vmware-config2/vmxnet-only/vmxnet.c:302: error: âstruct net_deviceâ has no member named âprivâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c: In function âvmxnet_link_checkâ:
/tmp/vmware-config2/vmxnet-only/vmxnet.c:656: error: âstruct net_deviceâ has no member named âprivâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c: In function âvmxnet_probe_deviceâ:
/tmp/vmware-config2/vmxnet-only/vmxnet.c:838: error: âstruct net_deviceâ has no member named âprivâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c:980: warning: cast to pointer from integer of different size
/tmp/vmware-config2/vmxnet-only/vmxnet.c:1045: error: âstruct net_deviceâ has no member named âopenâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c:1046: error: âstruct net_deviceâ has no member named âhard_start_xmitâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c:1047: error: âstruct net_deviceâ has no member named âstopâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c:1048: error: âstruct net_deviceâ has no member named âget_statsâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c:1049: error: âstruct net_deviceâ has no member named âset_multicast_listâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c:1051: error: âstruct net_deviceâ has no member named âchange_mtuâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c:1054: error: âstruct net_deviceâ has no member named âtx_timeoutâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c:1058: error: âstruct net_deviceâ has no member named âpoll_controllerâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c:1062: error: âstruct net_deviceâ has no member named âset_mac_addressâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c: In function âvmxnet_remove_deviceâ:
/tmp/vmware-config2/vmxnet-only/vmxnet.c:1129: error: âstruct net_deviceâ has no member named âprivâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c: In function âvmxnet_init_ringâ:
/tmp/vmware-config2/vmxnet-only/vmxnet.c:1200: error: âstruct net_deviceâ has no member named âprivâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c: In function âvmxnet_openâ:
/tmp/vmware-config2/vmxnet-only/vmxnet.c:1325: error: âstruct net_deviceâ has no member named âprivâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c: In function âcheck_tx_queueâ:
/tmp/vmware-config2/vmxnet-only/vmxnet.c:1581: error: âstruct net_deviceâ has no member named âprivâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c: In function âvmxnet_txâ:
/tmp/vmware-config2/vmxnet-only/vmxnet.c:1645: error: âstruct net_deviceâ has no member named âprivâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c: In function âvmxnet_rxâ:
/tmp/vmware-config2/vmxnet-only/vmxnet.c:2044: error: âstruct net_deviceâ has no member named âprivâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c: In function âvmxnet_interruptâ:
/tmp/vmware-config2/vmxnet-only/vmxnet.c:2169: error: âstruct net_deviceâ has no member named âprivâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c: In function âvmxnet_closeâ:
/tmp/vmware-config2/vmxnet-only/vmxnet.c:2251: error: âstruct net_deviceâ has no member named âprivâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c: In function âvmxnet_load_multicastâ:
/tmp/vmware-config2/vmxnet-only/vmxnet.c:2341: error: âstruct net_deviceâ has no member named âprivâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c: In function âvmxnet_set_multicast_listâ:
/tmp/vmware-config2/vmxnet-only/vmxnet.c:2402: error: âstruct net_deviceâ has no member named âprivâ
/tmp/vmware-config2/vmxnet-only/vmxnet.c: In function âvmxnet_get_statsâ:
/tmp/vmware-config2/vmxnet-only/vmxnet.c:2482: error: âstruct net_deviceâ has no member named âprivâ
make[2]: *** [/tmp/vmware-config2/vmxnet-only/vmxnet.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmxnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic-pae'
make: *** [vmxnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmxnet-only'
Unable to build the vmxnet module.

```

Thanks in advance for helping out!

---

### Post by Wloxen on 2010-11-06
I'm having the same problem right now with Kubuntu 10.10... Don't know a solution yet.

---

### Post by ro8inmorgan on 2011-02-28
Try this

[http://wiltonsoftware.com/posts/view/install-vmxnet-network-driver-on-your-debian-vm](http://wiltonsoftware.com/posts/view/install-vmxnet-network-driver-on-your-debian-vm)

With this tutorial i got the vmxnet driver running and now get normal speeds.

---

### Post by vyruz18 on 2011-02-28
I'm not going to try this because in the meantime I've moved to ESXi 4.0 and thus can use the VMXNET3 driver (opposed to VMXNET1 in 3.5) which is natively supported in Ubuntu.

Alltough I did have problems with VMXNET3 and sabnzbd, the driver would somehow crash/stop working after a few days of heavy downloading. So I moved to the E1000 driver (also new in ESXi 4.0) which solved that problem.

Thanks for this post though, it might be helpfull to other people stuck on older hardware which cannot run ESXi 4.0.

---

