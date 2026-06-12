---
title: "Is this VMware patch safe?"
date: 2012-06-15
forum: Security
---

### Post by The Phone on 2012-06-15
Hi!

I'am running Ubuntu 12.04 with 3.2.0-25-generic as kernel. When I tried   to install VMware player I got an error that it could't patch the   kernel. I found this thread [http://communities.vmware.com/thread/344213](http://communities.vmware.com/thread/344213)   there they have solvd it with this patch:

[http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/](http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/)

There two files you need to download, one is named patch-modules_3.2.0.sh and one is named vmware3.2.0.patch.

Here is the code:
[U][B]
patch-modules_3.2.0.sh[/B][/U]

```

#! /bin/bash
# VMWare Workstation/Player _host kernel modules_ patcher v0.6.2 by ©2010 Artem S. Tashkinov
# Tailored and fixed vmblock patching for the 2.6.39 patch by Stefano Angeleri (weltall)
# Use at your own risk.

fpatch=vmware3.2.0.patch
vmreqver=8.0.2
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
```_**vmware3.2.0.patch**_

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
+#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 42, 0) ||  (LINUX_VERSION_CODE < KERNEL_VERSION(3, 2, 0) &&  LINUX_VERSION_CODE >= KERNEL_VERSION(3, 0, 0))
 static void VNetNetifSetMulticast(struct net_device *dev);
+#endif
 #if 0
 static void VNetNetifTxTimeout(struct net_device *dev);
 #endif
@@ -131,7 +133,9 @@
       .ndo_stop = VNetNetifClose,
       .ndo_get_stats = VNetNetifGetStats,
       .ndo_set_mac_address = VNetNetifSetMAC,
+#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 42, 0) ||  (LINUX_VERSION_CODE < KERNEL_VERSION(3, 2, 0) &&  LINUX_VERSION_CODE >= KERNEL_VERSION(3, 0, 0))
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
+#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 42, 0) ||  (LINUX_VERSION_CODE < KERNEL_VERSION(3, 2, 0) &&  LINUX_VERSION_CODE >= KERNEL_VERSION(3, 0, 0))
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
 
+#if (LINUX_VERSION_CODE >= KERNEL_VERSION(2, 42, 0) &&  LINUX_VERSION_CODE < KERNEL_VERSION(3, 0, 0)) || LINUX_VERSION_CODE  >= KERNEL_VERSION(3, 2, 0)
+         vaddr = kmap(skb_frag_page(frag));
+#else
      vaddr = kmap(frag->page);
+#endif
      tmpCsum = csum_and_copy_to_user(vaddr + frag->page_offset,
                      curr, frag->size, 0, &err);
+#if (LINUX_VERSION_CODE >= KERNEL_VERSION(2, 42, 0) &&  LINUX_VERSION_CODE < KERNEL_VERSION(3, 0, 0)) || LINUX_VERSION_CODE  >= KERNEL_VERSION(3, 2, 0)
+         kunmap(skb_frag_page(frag));
+#else
      kunmap(frag->page);
+#endif
      if (err) {
         return err;
      }


```If the code looks like a mess I have attached the tar.gz with the original files.

Is there some weird code that could be a virus?


Thanks!

---

### Post by JuhazOne on 2012-06-28
I used the patch today. I read it briefly before using it but I didn't think it looks suspicious. But I don't know for sure.

---

### Post by CharlesA on 2012-06-28
It looks like the same patch I had to use on 10.04 a long, long time ago. It just adds support for the newer kernels.

---

