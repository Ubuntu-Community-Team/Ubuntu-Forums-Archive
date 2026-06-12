---
title: "KVM module doesn't get loaded automatically"
date: 2010-03-08
forum: Virtualisation
---

### Post by CHaoSlayeR on 2010-03-08
Hi *,

I've got a new machine for using Ubuntu:

MB: Gigabyte GA-790XTA-UD4
CPU: AMD Phenom II X4 955 @ 3.2GHz
GPU: AMD Radeon HD4770 (RV740)
RAM: 2x 2 GB Non-ECC DDR3 @ 1,333 MHz
HDD: 2x 500 GB S-ATA

As I'm using a RV740 GPU here I have to use the 2.6.33 kernel from mainline which includes the proper initialization fixes in its kernel code from radeon. This didn't work for Karmic so I'm forced to use Lucid (currently Alpha 3) as a base.

The problem is now that it doesn't load the kvm and kvm-amd modules on startup. Even putting them in /etc/modules doesn't do the trick. A ```
dmesg | grep -i kvm
``` doesn't reveal anything directly after startup and virtualization is enabled in the BIOS.

When I load those modules manually 
```
sudo modprobe kvm
sudo modprobe kvm-amd
```

All is fine and I can use the VM's as usual without any other issues. When I try to start a VM before that I get this:
```
open /dev/kvm: No such file or directory
Could not initialize KVM, will disable KVM support
```

This prevents other people to actually use the VM's that are provided by this machine before manual intervention after startup.

I don't know if this is somehow related but I found these entries in /var/log/messages:
```
...
Mar  7 21:33:02 ladydeath libvirtd: 21:33:02.228: warning : virEventUpdateHandleImpl:149 : Ignoring invalid update watch -1
Mar  7 21:35:47 ladydeath libvirtd: 21:35:47.324: warning : qemudDispatchSignalEvent:385 : Shutting down on signal 15
...
Mar  7 21:36:51 ladydeath libvirtd: 21:36:51.347: warning : qemudStartup:1076 : Unable to create cgroup for driver: No such device or address
Mar  7 21:36:53 ladydeath libvirtd: 21:36:53.996: warning : lxcStartup:1755 : Unable to create cgroup for driver: No such device or address
...
```

Is this some incompatibility between the user-mode stuff provided through the Lucid repositories and the 2.6.33 mainline kernel I use?


Thanx for any hints,

C]-[aoZ

---

### Post by CHaoSlayeR on 2010-03-11
I've updated the BIOS of the motherboard to the latest version and now (or because of some software updates in Lucid) I get in dmesg:
```
[   12.817985] kvm: Nested Virtualization enabled
[   12.817988] kvm: Nested Paging enabled
```

Well, but the main problem remains the same and I found out why:

The "pre-start" script for qemu-kvm for upstart requires KSM (Kernel Samepage Merging) being enabled:

```

        if [ "$KSM_ENABLED" = "1" ]; then
                [ -w /sys/kernel/mm/ksm/run ] && echo 1 > /sys/kernel/mm/ksm/run
        else
                [ -w /sys/kernel/mm/ksm/run ] && echo 0 > /sys/kernel/mm/ksm/run
        fi

```

These lines return with code "1" because KSM is not enable in the 2.6.33 mainline kernel (and therefore "/sys/kernel/mm/ksm/run" is just not there):

```
$ grep 'KSM' /boot/config-2.6.33-020633-generic
# CONFIG_KSM is not set
```

And as k10temp is not enabled either I guess I'll have to compile it myself.

---

### Post by CHaoSlayeR on 2010-03-11
I just noticed that the RV740 initialization fix has been backported into 2.6.32 kernel for lucid.

With that kernel the KVM module problems are gone.

---

