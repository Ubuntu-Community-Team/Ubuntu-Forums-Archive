---
title: "VMWare Workstation 8.0.3 on Ubuntu 12.10"
date: 2013-01-31
forum: Virtualisation
---

### Post by 0xygen on 2013-01-31
Hello everyone,

Sorry if this has been asked already but have searched and searched to no avail. Basically, I installed VMWare Workstation 8.0.3 from a bundle and that all went fine. It then said it needed to install some kernel updates (or something like that) and I clicked "ok". Anyone who has used this software will know that it then goes through 5 processes, hopefully ending up with green ticks next to everything. However, I get a red exclamation mark next to "Virtual Network Device" & "VMWare Blocking Filesystem". I then get an error message to check log file /tmp/vmware-root/modconfig-18304.log for details. I should have noted at the beginning that I am using Ubuntu 12.10 (32bit). This is what the log says:

                                     2013-02-01T01:16:46.425Z| vthread-3| I120: Log for VMware Workstation pid=18304 version=8.0.3 build=build-703057 option=Release
 2013-02-01T01:16:46.425Z| vthread-3| I120: The process is 32-bit.
 2013-02-01T01:16:46.425Z| vthread-3| I120: Host codepage=UTF-8 encoding=UTF-8
 2013-02-01T01:16:46.425Z| vthread-3| I120: Host is Linux 3.5.0-22-generic Ubuntu 12.10
 2013-02-01T01:16:46.424Z| vthread-3| I120: Msg_Reset:
 2013-02-01T01:16:46.424Z| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
 2013-02-01T01:16:46.424Z| vthread-3| I120: ----------------------------------------
 2013-02-01T01:16:46.424Z| vthread-3| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
 2013-02-01T01:16:46.425Z| vthread-3| I120: Msg_Reset:
 2013-02-01T01:16:46.425Z| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
 2013-02-01T01:16:46.425Z| vthread-3| I120: ----------------------------------------
 2013-02-01T01:16:46.425Z| vthread-3| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
 2013-02-01T01:16:46.425Z| vthread-3| I120: Msg_Reset:
 2013-02-01T01:16:46.425Z| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
 2013-02-01T01:16:46.425Z| vthread-3| I120: ----------------------------------------
 2013-02-01T01:16:46.425Z| vthread-3| I120: PREF Failed to load user preferences.
 2013-02-01T01:16:46.425Z| vthread-3| W110: Logging to /tmp/vmware-root/modconfig-18304.log
 2013-02-01T01:16:46.600Z| vthread-3| I120: modconf query interface initialized
 2013-02-01T01:16:46.601Z| vthread-3| I120: modconf library initialized
 2013-02-01T01:16:46.640Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:46.645Z| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.5.0-22-generic
 2013-02-01T01:16:46.645Z| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
 2013-02-01T01:16:46.645Z| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
 2013-02-01T01:16:46.645Z| vthread-3| I120: Validating path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic
 2013-02-01T01:16:46.648Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:46.658Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:46.672Z| vthread-3| I120: Header path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic is valid.
 2013-02-01T01:16:46.672Z| vthread-3| I120: Validating path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic
 2013-02-01T01:16:46.675Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:46.685Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:46.699Z| vthread-3| I120: Header path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic is valid.
 2013-02-01T01:16:46.722Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.726Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.729Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.733Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.736Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.758Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.761Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.765Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.768Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.772Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.775Z| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.5.0-22-generic
 2013-02-01T01:16:46.775Z| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
 2013-02-01T01:16:46.775Z| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
 2013-02-01T01:16:46.775Z| vthread-3| I120: Validating path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic
 2013-02-01T01:16:46.777Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:46.788Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:46.802Z| vthread-3| I120: Header path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic is valid.
 2013-02-01T01:16:46.832Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.836Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.839Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.843Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.846Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.849Z| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.5.0-22-generic
 2013-02-01T01:16:46.849Z| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
 2013-02-01T01:16:46.849Z| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
 2013-02-01T01:16:46.849Z| vthread-3| I120: Validating path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic
 2013-02-01T01:16:46.852Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:46.862Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:46.876Z| vthread-3| I120: Header path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic is valid.
 2013-02-01T01:16:46.916Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.920Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.923Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.927Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:46.930Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:47.242Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:47.243Z| vthread-3| I120: Validating path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic
 2013-02-01T01:16:47.246Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:47.258Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:47.273Z| vthread-3| I120: Header path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic is valid.
 2013-02-01T01:16:47.273Z| vthread-3| I120: Building module vmmon.
 2013-02-01T01:16:47.273Z| vthread-3| I120: Extracting the sources of the vmmon module.
 2013-02-01T01:16:47.290Z| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.5.0-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.7
 2013-02-01T01:16:51.069Z| vthread-3| I120: Installing module vmmon from /tmp/vmware-root/modules/vmmon.o to /lib/modules/3.5.0-22-generic/misc.
 2013-02-01T01:16:51.070Z| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.5.0-22-generic/misc/vmmon.ko
 2013-02-01T01:16:52.690Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:52.690Z| vthread-3| I120: Validating path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic
 2013-02-01T01:16:52.693Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:52.704Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:52.719Z| vthread-3| I120: Header path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic is valid.
 2013-02-01T01:16:52.719Z| vthread-3| I120: Building module vmnet.
 2013-02-01T01:16:52.719Z| vthread-3| I120: Extracting the sources of the vmnet module.
 2013-02-01T01:16:52.729Z| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.5.0-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.7
 2013-02-01T01:16:57.078Z| vthread-3| I120: Failed to compile module vmnet!
 2013-02-01T01:16:57.085Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:57.085Z| vthread-3| I120: Validating path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic
 2013-02-01T01:16:57.088Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:57.100Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:57.114Z| vthread-3| I120: Header path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic is valid.
 2013-02-01T01:16:57.114Z| vthread-3| I120: Building module vmblock.
 2013-02-01T01:16:57.114Z| vthread-3| I120: Extracting the sources of the vmblock module.
 2013-02-01T01:16:57.126Z| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.5.0-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.7
 2013-02-01T01:16:59.775Z| vthread-3| I120: Failed to compile module vmblock!
 2013-02-01T01:16:59.781Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:16:59.782Z| vthread-3| I120: Validating path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic
 2013-02-01T01:16:59.785Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:59.796Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:16:59.811Z| vthread-3| I120: Header path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic is valid.
 2013-02-01T01:16:59.811Z| vthread-3| I120: Building module vmci.
 2013-02-01T01:16:59.811Z| vthread-3| I120: Extracting the sources of the vmci module.
 2013-02-01T01:16:59.824Z| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.5.0-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.7
 2013-02-01T01:17:04.955Z| vthread-3| I120: Installing module vmci from /tmp/vmware-root/modules/vmci.o to /lib/modules/3.5.0-22-generic/misc.
 2013-02-01T01:17:04.955Z| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.5.0-22-generic/misc/vmci.ko
 2013-02-01T01:17:06.572Z| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.5.0-22-generic.
 2013-02-01T01:17:06.572Z| vthread-3| I120: Validating path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic
 2013-02-01T01:17:06.576Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:17:06.587Z| vthread-3| I120: Your GCC version: 4.7
 2013-02-01T01:17:06.601Z| vthread-3| I120: Header path /lib/modules/3.5.0-22-generic/build/include for kernel release 3.5.0-22-generic is valid.
 2013-02-01T01:17:06.601Z| vthread-3| I120: Building module vmci.
 2013-02-01T01:17:06.601Z| vthread-3| I120: Extracting the sources of the vmci module.
 2013-02-01T01:17:06.616Z| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.5.0-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.7
 2013-02-01T01:17:07.475Z| vthread-3| I120: Building module vsock.
 2013-02-01T01:17:07.476Z| vthread-3| I120: Extracting the sources of the vsock module.
 2013-02-01T01:17:07.489Z| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vsock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.5.0-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.7
 2013-02-01T01:17:11.827Z| vthread-3| I120: Installing module vsock from /tmp/vmware-root/modules/vsock.o to /lib/modules/3.5.0-22-generic/misc.
 2013-02-01T01:17:11.827Z| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.5.0-22-generic/misc/vsock.ko


I'll be honest and say that I have absolutely no idea what any of this means. Can anyone please help? I'd really appreciate it as have search high and low over the past few nights and have found "fixes" but don't really understand what they mean or how to apply them.


Thank you :),


0xy

---

### Post by meteorrock on 2013-01-31
WMware workstation 9.0 has tons of bug fixes and other problems worked out of that. Why not just upgrade? 

My hypervisor VMware workstation 9.0  using Ubuntu 12.10 with a Windows 7 host has been working fine. I do an update and see first if that will take care of the problem before going on a witchhunt through logs. You never know, it might of been taken care of already by the VMware team. Their logs of bug fixes just from VMware 8 to VMware 9 is a mile long on their site. :)

---

### Post by 0xygen on 2013-01-31
Because upgrading will cost me money and as it cost me a lot in the first place, I would like to use this one :-)

-0xy

---

### Post by heiko_s on 2013-02-01
I there a reason you use Ubuntu 32 bit? I would try the 64 bit version and see if that works with VMware. You may want to check the VMware specs to see if there are any limitations with regard to 32 bit systems.

---

### Post by SlugSlug on 2013-02-01
I've had this. You need patch files from here

[http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/](http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/)

---

### Post by 0xygen on 2013-02-01
Thank you very much for the link - did give it a go but no joy :-( . I'm probably doing something wrong and must confess I'm a bit of a n00b to linux. I will keep persevering though - any other pointers are most welcome :-)

-0xy

---

### Post by SlugSlug on 2013-02-02
whats the output?

The files I used:

patch-modules_3.2.0.sh

```
#! /bin/bash
# VMWare Workstation/Player _host kernel modules_ patcher v0.6.2 by ©2010 Artem S. Tashkinov
# Tailored and fixed vmblock patching for the 2.6.39 patch by Stefano Angeleri (weltall)
# Use at your own risk.

fpatch=vmware3.2.0.patch
vmreqver=8.0.4
plreqver=4.0.2


error()
{
    echo "$*. Exiting"
    exit
}

curdir=`pwd`
bdate=`date "+%F-%H:%M:%S"` || error "date utility didn't quite work. Hm"
vmver=`vmware-installer -l 2>/dev/null | awk '/vmware-/{print $1substr($2,1,5)}'`
vmver="${vmver#vmware-}"
basedir=/usr/lib/vmware/modules/source
ptoken="$basedir/.patched"
bkupdir="$basedir-$vmver-$bdate-backup"

unset product
[ -z "$vmver" ] && error "VMWare is not installed (properly) on this PC"
[ "$vmver" == "workstation$vmreqver" ] && product="VMWare WorkStation"
[ "$vmver" == "player$plreqver" ] && product="VMWare Player"
[ -z "$product" ] && error "Sorry, this script is only for VMWare WorkStation $vmreqver or VMWare Player $plreqver"

[ "`id -u`" != "0" ] && error "You must be root to run this script"
[ -f "$ptoken" ] && error "$ptoken found. You have already patched your sources"
[ ! -d "$basedir" ] && error "Source '$basedir' directory not found, reinstall $product"
[ ! -f "$fpatch" ] && error "'$fpatch' not found. Please, copy it to the current '$curdir' directory"

tmpdir=`mktemp -d` || exit 1
cp -an "$basedir" "$bkupdir" || exit 2

cd "$tmpdir" || exit 3
find "$basedir" -name "*.tar" -exec tar xf '{}' \; || exit 4

patch -p1 < "$curdir/$fpatch" || exit 5
tar cf  vmci.tar  vmci-only || exit 6
tar cf vsock.tar vsock-only || exit 7
tar cf vmnet.tar vmnet-only || exit 8
tar cf vmmon.tar vmmon-only || exit 9
tar cf vmblock.tar vmblock-only || exit 10

cp -a *.tar "$basedir" || exit 11
rm -rf "$tmpdir" || exit 12
touch "$ptoken" || exit 13
cd "$curdir" || exit 14

vmware-modconfig --console --install-all

echo -e "\n"
echo "All done, you can now run $product."
echo "Modules sources backup can be found in the '$bkupdir' directory"
```


vmware3.2.0.patch
```
diff -u -r source802//vmnet-only/filter.c source/vmnet-only/filter.c
--- source802//vmnet-only/filter.c    2012-01-18 23:22:02.000000000 +0100
+++ source/vmnet-only/filter.c    2012-01-26 18:07:13.000000000 +0100
@@ -40,6 +40,10 @@
 #include "vnetInt.h"
 #include "vmnetInt.h"
 
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(3, 2, 0)
+#include <linux/export.h>
+#endif
+
 // VNet_FilterLogPacket.action for dropped packets
 #define VNET_FILTER_ACTION_DRP         (1)
 #define VNET_FILTER_ACTION_DRP_SHORT   (2)
diff -u -r source802//vmnet-only/netif.c source/vmnet-only/netif.c
--- source802//vmnet-only/netif.c    2012-01-18 23:22:02.000000000 +0100
+++ source/vmnet-only/netif.c    2012-01-26 13:41:18.000000000 +0100
@@ -62,7 +62,9 @@
 static int  VNetNetifStartXmit(struct sk_buff *skb, struct net_device *dev);
 static struct net_device_stats *VNetNetifGetStats(struct net_device *dev);
 static int  VNetNetifSetMAC(struct net_device *dev, void *addr);
+#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 42, 0) || (LINUX_VERSION_CODE < KERNEL_VERSION(3, 2, 0) && LINUX_VERSION_CODE >= KERNEL_VERSION(3, 0, 0))
 static void VNetNetifSetMulticast(struct net_device *dev);
+#endif
 #if 0
 static void VNetNetifTxTimeout(struct net_device *dev);
 #endif
@@ -131,7 +133,9 @@
       .ndo_stop = VNetNetifClose,
       .ndo_get_stats = VNetNetifGetStats,
       .ndo_set_mac_address = VNetNetifSetMAC,
+#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 42, 0) || (LINUX_VERSION_CODE < KERNEL_VERSION(3, 2, 0) && LINUX_VERSION_CODE >= KERNEL_VERSION(3, 0, 0))
       .ndo_set_multicast_list = VNetNetifSetMulticast,
+#endif
       /*
        * We cannot stuck... If someone will report problems under
        * low memory conditions or some such, we should enable it.
@@ -611,12 +615,12 @@
  *
  *----------------------------------------------------------------------
  */
-
+#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 42, 0) || (LINUX_VERSION_CODE < KERNEL_VERSION(3, 2, 0) && LINUX_VERSION_CODE >= KERNEL_VERSION(3, 0, 0))
 void
 VNetNetifSetMulticast(struct net_device *dev) // IN: unused
 {
 }
-
+#endif
 
 /*
  *----------------------------------------------------------------------
diff -u -r source802//vmnet-only/userif.c source/vmnet-only/userif.c
--- source802//vmnet-only/userif.c    2012-01-18 23:22:02.000000000 +0100
+++ source/vmnet-only/userif.c    2012-01-26 13:28:48.000000000 +0100
@@ -517,10 +517,18 @@
      unsigned int tmpCsum;
      const void *vaddr;
 
+#if (LINUX_VERSION_CODE >= KERNEL_VERSION(2, 42, 0) && LINUX_VERSION_CODE < KERNEL_VERSION(3, 0, 0)) || LINUX_VERSION_CODE >= KERNEL_VERSION(3, 2, 0)
+         vaddr = kmap(skb_frag_page(frag));
+#else
      vaddr = kmap(frag->page);
+#endif
      tmpCsum = csum_and_copy_to_user(vaddr + frag->page_offset,
                      curr, frag->size, 0, &err);
+#if (LINUX_VERSION_CODE >= KERNEL_VERSION(2, 42, 0) && LINUX_VERSION_CODE < KERNEL_VERSION(3, 0, 0)) || LINUX_VERSION_CODE >= KERNEL_VERSION(3, 2, 0)
+         kunmap(skb_frag_page(frag));
+#else
      kunmap(frag->page);
+#endif
      if (err) {
         return err;
      }
```

save them & I think you just run

```
sudo ./patch-modules_3.2.0.sh
```

---

### Post by 0xygen on 2013-02-02
Thanks again SlugSlug :-) Which directory should the files be saved to or does it not matter?

Regards,

0xy

---

### Post by SlugSlug on 2013-02-02
don't matter as long as they are both in same directory

---

### Post by 0xygen on 2013-02-06
It worked!! Thank you SlugSlug - I don't really understand what I did but somehow it's up and working so kudos to you! :-)

To whoever was asking why I'm using 32 bit - simple, I'm using a very old laptop ;-)

Thanks again!

-0xy

---

### Post by SlugSlug on 2013-02-07
cool 

sometimes you just need to edit 

```
vmreqver=8.0.4
```

to match output of

```
sudo vmware-installer -l
```

---

