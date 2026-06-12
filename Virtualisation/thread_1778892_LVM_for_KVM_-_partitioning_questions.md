---
title: "LVM for KVM - partitioning questions"
date: 2011-06-09
forum: Virtualisation
---

### Post by Evaderx on 2011-06-09
Hi, dear forum members!

This is my first post here. I am much more a reader than a writer, but this time I completely ran out of ideas and couldn't find the solution to the problem I encountered.

I will try to describe the situation. So, at the moment I'm trying to build an infrastructure of virtual machines using KVM+libvirt+some custom scripts. I decided to go for virtio+LVM. After lots of hours of researching, I found out that the most convenient way of creating a VM (I am not talking about cloning and so on now), is:

[LIST]
[*]create an LV in my host system,
[*]mkfs.ext4 on it,
[*]in the process of installing the guest OS (e.g., server Lucid LTS), give the installer this pre-made LV with ext4 fs on it as a single drive (no formatting, just use of the volume as a place for root FS).
[/LIST]
The two main reasons for this way are:

[LIST]
[*]no need for additional partition table, so I just do lvresize and resize2fs in case of space changes,
[*]I can mount this LV directly to my host machine without loop devices, offsets, kpartx maps and so on.
[/LIST]
But the great problem with such approach is that... *hmmm, how to describe it correctly* ... it works only for the first time!

Let me explain.

[LIST=1]
[*]I make an LV in the host system, mkfs.ext4 on it.
[*]This LV with an existing partition table and ext4 volume is seen perfectly well in an installer as a VirtIO Block Device with ext4 partition.
[*]I install the system. Everything goes superb, it boots, mounts to host without any questions. BUT...
[*]If I want to see this root partition from an installer once more (e.g., I broke GRUB2 and I want to fix it, booting from CD image), it just shows me that the VirtIO Block Device is FREE. It doesn't see the existing partition table, nor the info on it.
[/LIST]
This occurs always, regarding the distro version (10.04, 11.04, server, desktop, alternate, in debian everything is the same as well). The funniest thing is though the installer can't understand the partition table on this VirtIO Block Device, I can open the second console via Alt+F2, mount the existing /dev/vda somewhere, and access all the files and even chroot there! But nevertheless GRUB2 doesn't understand that there is a block device where it has to install to.

I would really appreciate if you could help me and point to what am I doing wrong!
It would also be great to get a piece of advice, taking into account that I want to preserve the existing scheme of 1 LV = root partition, created from host, if that is possible.

Thank you very much in advance! :redface:

---

