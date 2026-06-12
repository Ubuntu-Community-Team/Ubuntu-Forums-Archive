---
title: "VM layout for QEMU+LVM"
date: 2013-03-02
forum: Virtualisation
---

### Post by leonty on 2013-03-02
Hi all,

I'm deploying a sever (ubuntu 12.10+kvm+qemu) for a developers team carrying VMs (ubuntu 12.10) for DB, application server, build bot etc. As far as I understand, a VM has the usual process of booting, i.e. bootloader from the 1st sector, then 2nd stage loader, then kernel. So I'm thinking of a layout with 2 LVM volumes for each VM:
first - is a block device, having a partition table, loader (GRUB), partition for /boot, partition for swap.
second - raw with the root filesystem.

First is not changing much. Second can be resized easily because it's not tied with the classic partition table (LVM volume, then fs).

I'd like to know what the comunity thinks about this layout? Maybe it's possible to have just one LVM volume, but without partition table?


Thanks.

---

### Post by leonty on 2013-03-09
OK, maybe my experience would be useful for somebody.

So, we have a sever: &#1045;5-2407(2 slots), 16&#1043;&#1073; RAM, 2&#1093;1Tb as RAID1.

Goal: deploy a server with VM for a developer team.
Ubuntu Server 12.10 is chosen for both hypervisor and VMs because the author's most experience connected with Ubuntu and the author is not a system administrator.
Virtualisation technologies: those considered as "default" in Ubuntu, i.e. kvm+qemu+libvirt.

The hypervisor is installed on a 5Gb volume in LVM (all disk).
For VMs decided to avoid making boot disks with grub, partition table etc, because it makes harder to deal with VM size (lvm->VM partition table->VM FS). So the choice is to have one volume per VM with its root filesystem and skip VM BIOS loader.
LVM thin-provisioning is not supported well in Ubuntu though it allows to take first steps (no required packages, I had to retreat with shame replacing not existent /usr/sbint/thin_check with /bin/true), so we create standard LVM volumes. Volumes get formatted as EXT4.

There are VMs' kernels and initrd in hypervisor's /vmboot/vmX.
In the libvirt VM definition we set the paths to the kernel and initrd, set an LVM volume as hda/sda/vda and set the root filesystem in the kernel parameters (root=UUID=abcd-abcd-1234...).
Also we pass /vmboot/vmX to the VM as en exported filesystem. The VM mounts it to /boot (static fstab record). That's done for the case when a VM updates its kernel, so that the hypervisor could keep the track and boot this VM with its new kernel.

All /vmboot/* lie in a separate LVM volume. 

So all this makes a modular environment (hypervisor volume, VMs kernel volume, VMs root fs volumes) that is easy to update/backup etc. The VMs size can be changed easily too.

Some details:
LVM of hypervisor:
```
$ sudo lvs
  LV        VG     Attr     LSize   Pool Origin Data%  Move Log Copy%  Convert
  host_root system -wi-ao--   5.00g
  host_swap system -wi-ao--   4.66g
  vmboot    system -wi-ao-- 500.00m
  appsrv    system -wi-a---   5.00g
  jira      system -wi-a---   5.00g
  oracle    system -wi-a---   5.00g
  template  system -wi-a---   1.00g

```

LVM volumes contents:
```
$ sudo file -sL /dev/system/*
/dev/system/appsrv:    data
/dev/system/host_root: Linux rev 1.0 ext4 filesystem data, UUID=f6ac67b1-c6b0-4fba-8808-1946951a166f, volume name "root_host" (needs journal recovery) (extents) (large files) (huge files)
/dev/system/host_swap: Linux/i386 swap file (new style), version 1 (4K pages), size 1220607 pages, no label, UUID=b132bf9d-325c-4ed5-94eb-36ddf4fb3e78
/dev/system/jira:      Linux rev 1.0 ext4 filesystem data, UUID=90ef6a3f-0ac9-4d73-ae9e-6c2cb3a569a1 (extents) (large files) (huge files)
/dev/system/oracle:    data
/dev/system/template:  Linux rev 1.0 ext4 filesystem data, UUID=33ceecbc-80a6-41f0-9f26-58a8ce9a3912 (extents) (large files) (huge files)
/dev/system/vmboot:    Linux rev 1.0 ext4 filesystem data, UUID=3726d98c-580e-45df-8dc4-6179b2d21070 (needs journal recovery) (extents) (huge files)

```

VM definition in libvirt (cut a little bit):
```
$ sudo cat /etc/libvirt/qemu/jira.xml
<domain type='kvm'>
...
  <os>
    <type arch='x86_64' machine='pc-1.2'>hvm</type>
    <kernel>/vmboot/jira/vmlinuz-3.5.0-23-generic</kernel>
    <initrd>/vmboot/jira/initrd.img-3.5.0-23-generic</initrd>
    <cmdline>root=UUID=90ef6a3f-0ac9-4d73-ae9e-6c2cb3a569a1</cmdline>
    <boot dev='hd'/>
  </os>
  <devices>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/system/jira'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </disk>
    <filesystem type='mount' accessmode='mapped'>
      <driver type='path' wrpolicy='immediate'/>
      <source dir='/vmboot/jira'/>
      <target dir='boot'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </filesystem>
...
</domain>

```

Hypervisor (cut):
```
$ cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
...
UUID=3726d98c-580e-45df-8dc4-6179b2d21070 /vmboot         ext4    defaults        0       0

```

VMs (cut):
```
$ cat /etc/fstab
# <file system>                                 <mount point>   <type>  <options>       <dump>  <pass>
...
#/boot                                          boot           9p      trans=virtio,version=9p2000.L   0  0

```

Ask if you have questions! Good luck.

---

