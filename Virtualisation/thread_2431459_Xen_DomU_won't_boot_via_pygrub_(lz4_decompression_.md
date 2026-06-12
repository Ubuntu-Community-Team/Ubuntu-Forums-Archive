---
title: "Xen DomU won't boot via pygrub (lz4 decompression fails)"
date: 2019-11-16
forum: Virtualisation
---

### Post by kshots on 2019-11-16
Hello,

I recently performed a system upgrade on one of my guest machines (Ubuntu) and found it was unable to boot. I get my pygrub menu showing kernel versions 5.3.0-23-generic (which fails) and 5.0.0.-36-generic (which still works):
```
xc: error: panic: xc_dom_bzimageloader.c:768: xc_dom_probe_bzimage_kernel unable to LZ4 decompress kernel                         : Invalid kernel
                                         xc: error: panic: xc_dom_core.c:692: xc_dom_find_loader: no loader found: Invalid kernel
                                                 libxl: error: libxl_dom.c:722:libxl__build_dom: xc_dom_parse_image failed
                                          libxl: error: libxl_create.c:1267:domcreate_rebuild_done: Domain 9:cannot (re-)build domain: -3
                                                         libxl: error: libxl_domain.c:1034:libxl__destroy_domid: Domain 9:Non-existant domain
libxl: error: libxl_domain.c:993:domain_destroy_callback: Domain 9:Unable to destroy guest
libxl: error: libxl_domain.c:920:domain_destroy_cb: Domain 9:Destruction of domain failed
```
The host is running gentoo linux with xen 4.11.2. My best guess is that the 5.0.0-36 kernel was not LZ4 compressed, and 5.3.0-23 is... and pygrub doesn't know how to decompress it. I'd take the easier of:

1. Disabling LZ4 compression for the kernel under Ubuntu
or
2. Enabling LZ4 compression on pygrub under Gentoo (located under the xen-tools package for version 4.11.2).

How should I proceed? I'd actually prefer option 2, but I don't see any convenient Gentoo USE flags enabling LZ4 compression.

---

### Post by kshots on 2019-11-24
bump - still an issue, and continued research has shown me nothing :(

---

### Post by kshots on 2019-12-01
Does no one know how to disable compresson on the kernel in ubuntu?? :(

---

### Post by kevdog on 2019-12-02
Hmm -- did some reading about this topic as I didn't know about it either.  I'm running xcp-ng which runs on top of centos. Is it the initramfs or kernel that is lz4 compressed or both?  This article seems to suggest both: [https://www.phoronix.com/scan.php?page=news_item&px=LZ4-Initramfs-Ubuntu-Go-Ahead](https://www.phoronix.com/scan.php?page=news_item&px=LZ4-Initramfs-Ubuntu-Go-Ahead)

---

### Post by kshots on 2019-12-02
I believe it's both, but it's the kernel that decompresses the initrd (otherwise the EFI stub loading I'm using on other systems couldn't work as they don't use GRUB or any other bootloaders). So I just need to either decompress the kernel or compress it with something that pygrub knows how to deal with (bz2, maybe? What was ubuntu running prior to LZ4?)

EDIT: Come to think of it, a compressed kernel should act the same way - even with an EFI stub, a compressed kernel knows how to decompress itself. Something else is going on here :/ I'm not sure how to attack it at this point.

---

### Post by kshots on 2019-12-02
Looks like someone just posted a bug report ([https://bugs.launchpad.net/ubuntu/+source/xen/+bug/1854575](https://bugs.launchpad.net/ubuntu/+source/xen/+bug/1854575)) about this issue... I'm also running a PV with a similar setup. Hopefully that gets some attention

---

### Post by kevdog on 2019-12-02
Interesting to see where this goes.  Just curious -- why Pygrub?

---

### Post by Doug S on 2019-12-03
I got hit by this some time ago with the mainline kernels, when Ubuntu switched to L4Z compression in the kernel configuration. I had to do this:

```
scripts/config --disable KERNEL_LZ4
scripts/config --enable KERNEL_GZIP
``` after stealing the Ubuntu kernel configuration, and before compiling the kernel myself.

i was still using Ubuntu 16.04 on my main test server, for which L4Z was not available.
For other reasons, I have now been forced to upgrade, and am in the middle of that saga now.

EDIT: Reference: [https://ubuntuforums.org/showthread.php?t=2423441&p=13884993#post13884993](https://ubuntuforums.org/showthread.php?t=2423441&p=13884993#post13884993)

---

### Post by kshots on 2019-12-03
I use pygrub because it looks into the VM disk image for the kernel and initrd automatically without having to extract them to the host to be executed outside of the VM. This allows the guest to update transparently (usually) to the host. One or the other is required for a PV VM, but a PVH or an HVM would just boot the image like a normal machine (without having the kernel fed directly into xen's hypervisor).

---

### Post by kevdog on 2019-12-03
Which systems are you running as PV VMs?  I looked at all my VMs I've installed inside xcp-ng and they are all PVH VMs -- however all my VMs are either linux/bsd types.

---

### Post by kshots on 2019-12-04
Just ubuntu - as far as I know, only linux guests are supported as PV's

---

