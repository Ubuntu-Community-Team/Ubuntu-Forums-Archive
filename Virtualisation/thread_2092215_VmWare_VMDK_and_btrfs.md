---
title: "VmWare VMDK and btrfs"
date: 2012-12-07
forum: Virtualisation
---

### Post by phoogkamer on 2012-12-07
Hello,

I am experimenting with btrfs on virualized servers running on Vmware. If I have a single VMDK disk and partitioned with btrfs I can do online resizing of my partitions when downsizing. When extending my VMDK from original 10Gb to 20Gb in Vmware I would like to online resize my btrfs partition to 20Gb. However this is not possible, because btrfs does not see the extra space. Is it possible to let btrfs or the OS be aware of the extra diskspace so I can grow my btrfs partition to 20Gb?

Regards,

Tux

---

