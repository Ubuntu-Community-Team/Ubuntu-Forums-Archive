---
title: "Custom xenified Ubuntu kernel"
date: 2008-02-04
forum: Virtualisation
---

### Post by Fubarovic on 2008-02-04
I need to recompile the custom Ubuntu kernel with Xen support (currently 2.6.22-14-xen, linux-image-2.6.22-14-xen). I'd like to enable support for scaling the speed of my Athlon X2 CPU (powernow-k8 module).

The trouble is, I can't figure out how to recompile the kernel. I have followed the guides on "how to compile a custom Linux kernel the Ubuntu / Debian way", but the linux-source package ([linux-source-2.6.22, version 2.6.22-14.47](http://packages.ubuntu.com/gutsy/base/linux-image-2.6.22-14-xen)) I download doesn't seem to have the Xen patches applied to it.

When I download the patch that's supposedly applied by the Ubuntu team to the vanilla kernel ([http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-source-2.6.22_2.6.22-14.47.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-source-2.6.22_2.6.22-14.47.diff.gz)), I do see specific Xen patches in there. However, when I try to apply this patch to the vanilla kernel ([http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-source-2.6.22_2.6.22.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-source-2.6.22_2.6.22.orig.tar.gz)), the patch tool warns me about previously applied patches.

What do I have to do to start with a patched kernel source tree that I can configure to my liking?

---

### Post by Fubarovic on 2008-02-05
I just pulled in the kernel source using "apt-get source linux-image-..." and I got the same files I already downloaded manually. Only this time, the patches were applied by dpkg-source. 

I ran "make menuconfig" and I saw a lot of warnings:

```

angrypirate:/tmp/linux-source-2.6.22-2.6.22# make menuconfig
scripts/kconfig/mconf arch/x86_64/Kconfig
#
# using defaults found in /boot/config-2.6.22-14-xen
#
/boot/config-2.6.22-14-xen:131:warning: trying to assign nonexistent symbol X86_64_XEN
/boot/config-2.6.22-14-xen:132:warning: trying to assign nonexistent symbol X86_NO_TSS
/boot/config-2.6.22-14-xen:133:warning: trying to assign nonexistent symbol X86_NO_IDT
/boot/config-2.6.22-14-xen:143:warning: trying to assign nonexistent symbol X86_XEN_GENAPIC
/boot/config-2.6.22-14-xen:218:warning: trying to assign nonexistent symbol XEN_PCIDEV_FRONTEND
/boot/config-2.6.22-14-xen:219:warning: trying to assign nonexistent symbol XEN_PCIDEV_FE_DEBUG
/boot/config-2.6.22-14-xen:2063:warning: trying to assign nonexistent symbol TCG_XEN
/boot/config-2.6.22-14-xen:3498:warning: trying to assign nonexistent symbol XEN
/boot/config-2.6.22-14-xen:3499:warning: trying to assign nonexistent symbol XEN_INTERFACE_VERSION
/boot/config-2.6.22-14-xen:3504:warning: trying to assign nonexistent symbol XEN_PRIVILEGED_GUEST
/boot/config-2.6.22-14-xen:3505:warning: trying to assign nonexistent symbol XEN_UNPRIVILEGED_GUEST
/boot/config-2.6.22-14-xen:3506:warning: trying to assign nonexistent symbol XEN_PRIVCMD
/boot/config-2.6.22-14-xen:3507:warning: trying to assign nonexistent symbol XEN_XENBUS_DEV
/boot/config-2.6.22-14-xen:3508:warning: trying to assign nonexistent symbol XEN_BACKEND
/boot/config-2.6.22-14-xen:3509:warning: trying to assign nonexistent symbol XEN_BLKDEV_BACKEND
/boot/config-2.6.22-14-xen:3510:warning: trying to assign nonexistent symbol XEN_BLKDEV_TAP
/boot/config-2.6.22-14-xen:3511:warning: trying to assign nonexistent symbol XEN_NETDEV_BACKEND
/boot/config-2.6.22-14-xen:3512:warning: trying to assign nonexistent symbol XEN_NETDEV_PIPELINED_TRANSMITTER
/boot/config-2.6.22-14-xen:3513:warning: trying to assign nonexistent symbol XEN_NETDEV_LOOPBACK
/boot/config-2.6.22-14-xen:3514:warning: trying to assign nonexistent symbol XEN_PCIDEV_BACKEND
/boot/config-2.6.22-14-xen:3515:warning: trying to assign nonexistent symbol XEN_PCIDEV_BACKEND_VPCI
/boot/config-2.6.22-14-xen:3516:warning: trying to assign nonexistent symbol XEN_PCIDEV_BACKEND_PASS
/boot/config-2.6.22-14-xen:3517:warning: trying to assign nonexistent symbol XEN_PCIDEV_BACKEND_SLOT
/boot/config-2.6.22-14-xen:3518:warning: trying to assign nonexistent symbol XEN_PCIDEV_BE_DEBUG
/boot/config-2.6.22-14-xen:3519:warning: trying to assign nonexistent symbol XEN_TPMDEV_BACKEND
/boot/config-2.6.22-14-xen:3520:warning: trying to assign nonexistent symbol XEN_BLKDEV_FRONTEND
/boot/config-2.6.22-14-xen:3521:warning: trying to assign nonexistent symbol XEN_NETDEV_FRONTEND
/boot/config-2.6.22-14-xen:3522:warning: trying to assign nonexistent symbol XEN_FRAMEBUFFER
/boot/config-2.6.22-14-xen:3523:warning: trying to assign nonexistent symbol XEN_KEYBOARD
/boot/config-2.6.22-14-xen:3524:warning: trying to assign nonexistent symbol XEN_CONSOLE
/boot/config-2.6.22-14-xen:3525:warning: trying to assign nonexistent symbol XEN_SCRUB_PAGES
/boot/config-2.6.22-14-xen:3526:warning: trying to assign nonexistent symbol XEN_DISABLE_SERIAL
/boot/config-2.6.22-14-xen:3527:warning: trying to assign nonexistent symbol XEN_SYSFS
/boot/config-2.6.22-14-xen:3528:warning: trying to assign nonexistent symbol XEN_COMPAT_030002_AND_LATER
/boot/config-2.6.22-14-xen:3529:warning: trying to assign nonexistent symbol XEN_COMPAT_030004_AND_LATER
/boot/config-2.6.22-14-xen:3530:warning: trying to assign nonexistent symbol XEN_COMPAT_LATEST_ONLY
/boot/config-2.6.22-14-xen:3531:warning: trying to assign nonexistent symbol XEN_COMPAT
/boot/config-2.6.22-14-xen:3532:warning: trying to assign nonexistent symbol HAVE_IRQ_IGNORE_UNHANDLED
/boot/config-2.6.22-14-xen:3533:warning: trying to assign nonexistent symbol GENERIC_HARDIRQS_NO__DO_IRQ
/boot/config-2.6.22-14-xen:3534:warning: trying to assign nonexistent symbol NO_IDLE_HZ
/boot/config-2.6.22-14-xen:3535:warning: trying to assign nonexistent symbol XEN_SMPBOOT

```

So the Xen patches weren't included in the .diff file. What magic voodoo do the Ubuntu kernel packagers use to create the Xen kernel?

---

