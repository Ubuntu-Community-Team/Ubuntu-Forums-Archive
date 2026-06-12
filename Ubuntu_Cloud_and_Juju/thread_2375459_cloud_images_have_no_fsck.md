---
title: "cloud images have no fsck"
date: 2017-10-24
forum: Ubuntu Cloud and Juju
---

### Post by robkooper on 2017-10-24
We create our machines using volumes to boot and copy the ubuntu 16.04 image. We now have some systems that have errors in the root file system. While booting I see the following message:

[    4.119396] md: raid10 personality registered for level 10
done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... [    4.156168] Btrfs loaded
Scanning for Btrfs filesystems
done.
Warning: fsck not present, so skipping root file system
[    4.188359] EXT4-fs (vda1): mounted filesystem with ordered data mode. Opts: (null)
I looked at the initrd file (using cpio) and noticed that there is no fsck in the initrd. I checked another server that is a VM on a normal hypervisor and this does have the fsck in initrd.

Is this intended? How can I check a root filesystem? (touch /forcefsck does not work since it does not have fsck installed)

---

