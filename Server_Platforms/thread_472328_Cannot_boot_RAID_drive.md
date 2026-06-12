---
title: "Cannot boot RAID drive?"
date: 2007-06-12
forum: Server Platforms
---

### Post by Ventajou on 2007-06-12
Hi,

I'm having trouble setting up feisty server. I have added a PCI IDE controller to an older system and slapped a CD drive, two 20GB disks and three 40GB disks in the box. 

During setup, I manually configured the partitions as such:

2x 20GB drives:
- 18GB RAID1 volume, bootable, ReiserFS, mounted as /
- 2GB RAID1 volume, mounted as swap

3x40GB drives:
- 80GB RAID5 volume, ReiserFS, mounted as /var

The installation went just fine until it was time to reboot. Then I get a no system found message...
Am I missing something?

---

