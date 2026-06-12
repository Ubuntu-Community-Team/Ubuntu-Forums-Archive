---
title: "LVM guest disk access from host"
date: 2009-09-09
forum: Virtualisation
---

### Post by it-fits on 2009-09-09
Hello,

I'm trying to understand how I can access raw disks (on LVM logical volumes) from KVM guest. Purpose is to resize (extend) the filesystem of the guest. Both are running Jaunty AMD64.

Now I'm stumbling upon something I can't explain, maybe a bug, or maybe something I don't understand. 

When I access an existing filesystem (that I setup as described below) from the guest, then an fsck tells me the filesystem is corrupt. If I do the same from the host, nothing is wrong. It looks like the raw disk is mapped differently by kvm compared to when mapped by kpartx. 

Reproduction is easy as follows:

root@host:

```

root@server1:~# lvcreate -n ltspsys -L15G SAS
root@server1:~# fdisk /dev/SAS/ltspsys (n, p, 1, default, default, w)
root@server1:~# fdisk -l /dev/mapper/SAS-ltspsys

    Disk /dev/mapper/SAS-ltspsys: 16.1 GB, 16106127360 bytes
    255 heads, 63 sectors/track, 1958 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Disk identifier: 0xaeeda491

                      Device Boot      Start         End      Blocks   Id  System
    /dev/mapper/SAS-ltspsys1               1        1958    15727603+  83  Linux


root@server1:~# kpartx -av /dev/mapper/SAS-ltspsys
root@server1:~# mke2fs -j /dev/mapper/SAS-ltspsys1
root@server1:~# e2fsck -f /dev/mapper/SAS-ltspsys1

```

... returns no errors.

Then boot guest from rescue ISO using /dev/mapper/SAS-ltspsys (LVM Logical Volume) as /dev/hda. 

root@rescue:

Now fs returns errors on e2fsck from guest while nothing is modified since last check from host... So apparently, when the partition is accessed from host, it's seen differently as when used from guest? (though fdisk -l /dev/mapper/SAS-ltspsys on host is identical to fdisk -l /dev/sda1 on guest). Can't find no pointers as what could be the cause for this.

Any idea's?

---

### Post by it-fits on 2009-09-11
Can somebody reproduce this?

---

### Post by it-fits on 2009-09-12
Hello,

problem is solved

Using libvirt, this was my disk config:

guest.xml
```
...
    <disk type='file' device='disk'>
      <source file='/dev/SAS/guest'/>
      <target dev='hda' bus='ide'/>
    </disk>
...
```

Actually it should be:


```

    <disk type='block' device='disk'>
      <source dev='/dev/SAS/guest'/>
      <target dev='hda' bus='ide'/>
    </disk>

```

or using virtio

```

    <disk type='block' device='disk'>
      <source dev='/dev/SAS/guest'/>
      <target dev='vda' bus='virtio'/>
    </disk>

```

I'll post some complete howto on using lvm raw devices with kvm/libvirt, access from host and resizing guest filesystems.

---

### Post by tauren on 2010-05-24
> **it-fits said:**
> Hello,

I'll post some complete howto on using lvm raw devices with kvm/libvirt, access from host and resizing guest filesystems.

Did this howto ever get posted? I'd love to see it.

---

