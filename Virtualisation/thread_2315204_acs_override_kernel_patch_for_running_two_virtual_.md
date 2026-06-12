---
title: "acs override kernel patch for running two virtual vms at the same time both with..."
date: 2016-02-26
forum: Virtualisation
---

### Post by fredwntr1 on 2016-02-26
so im running kvm through virt-manager on debian 8 with pci passthrough on two different machines. the first vm is steamos using a gtx 760 and my second vm is windows 8.1 using my r9 390. im trying to find a way to run them both at the same time for im using a network bridge for both vm's this way i can use in home streaming from my pc to my living room tv using wireless hdmi. The problem is the two graphics cards are part of the same iommu group as shown here they are part of group 1. 01:00.0 is my nvidia and :02:00.0 is the amd card.  my question is will the acs override patch allow me to run both vm's at the same time? and if yes how do i even do the patch? i would like to use kernel 4.1.18 and theres a link on the forum to a kernel patch for 3.18 will that work?/sys/kernel/iommu_groups/0/devices/0000:00:00.0/sys/kernel/iommu_groups/1/devices/0000:00:01.0/sys/kernel/iommu_groups/1/devices/0000:00:01.1/sys/kernel/iommu_groups/1/devices/0000:01:00.0/sys/kernel/iommu_groups/1/devices/0000:01:00.1/sys/kernel/iommu_groups/1/devices/0000:02:00.0/sys/kernel/iommu_groups/1/devices/0000:02:00.1/sys/kernel/iommu_groups/2/devices/0000:00:02.0/sys/kernel/iommu_groups/3/devices/0000:00:03.0/sys/kernel/iommu_groups/4/devices/0000:00:14.0/sys/kernel/iommu_groups/5/devices/0000:00:16.0/sys/kernel/iommu_groups/6/devices/0000:00:19.0/sys/kernel/iommu_groups/7/devices/0000:00:1a.0/sys/kernel/iommu_groups/8/devices/0000:00:1b.0/sys/kernel/iommu_groups/9/devices/0000:00:1c.0/sys/kernel/iommu_groups/9/devices/0000:00:1c.3/sys/kernel/iommu_groups/9/devices/0000:04:00.0/sys/kernel/iommu_groups/10/devices/0000:00:1d.0/sys/kernel/iommu_groups/11/devices/0000:00:1f.0/sys/kernel/iommu_groups/11/devices/0000:00:1f.2/sys/kernel/iommu_groups/11/devices/0000:00:1f.3

---

