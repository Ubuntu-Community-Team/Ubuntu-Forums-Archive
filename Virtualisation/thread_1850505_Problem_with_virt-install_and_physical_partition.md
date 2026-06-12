---
title: "Problem with virt-install and physical partition"
date: 2011-09-26
forum: Virtualisation
---

### Post by i.sinister on 2011-09-26
Good morining/day/evening,

I'm trying to install windows7 on a physical drive on my xubuntu box. Kvm/qemu are installed and working fine, but I am unable to hook physical partition I prepared for windows. Here is the command I'm using to start vm:

```

sudo virt-install --name W7x64 --ram 1024 --disk /dev/sda7,bus=virtio,sparse=false,device=disk --disk /tmp/virtio/virtio-win-1.1.16.vfd,device=floppy --os-variant win7 --cdrom /home/tmp/win7.iso --debug

```All paths are correct, /dev/sda7 has following permissions:
```

brw-rw---- 1 libvirt-qemu kvm /dev/sda7

```Vm is started from the disk, I am able to choose driver for the disk from the virtual floppy drive, but even after driver is installed no drives are found. 

Can anybody think of what could be the problem?

Thanks for assistance

---

### Post by i.sinister on 2011-09-30
Ok, i managed to hook up my drive - if i write "--disk /dev/sda,bus=virtio" instead of "--disk /dev/sda[COLOR=Red]**7**[/COLOR],bus=virtio" windows installer sees the drive and partitions but this time it tells that it can not install windows on this partition, even though its formatted to ntfs and permissions on that partitions are set.

Any ideas?

---

