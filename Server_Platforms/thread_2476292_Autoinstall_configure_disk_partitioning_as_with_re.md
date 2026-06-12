---
title: "Autoinstall: configure disk partitioning as with relative values"
date: 2022-06-22
forum: Server Platforms
---

### Post by conre on 2022-06-22
Hi,

I would like to get Ansible automation for my server install from scratch, including bare metal installation (via KVM).

Ubuntu uses autoinstall since 2020 and I have not found a way how to combine absolute and relative sizes of partitions (like boot: absolute, efs: absolute, / (root): remaining space).

P.S. The actual target is to create a single LVM logical volume accross any available unpartitioned disks during bare metal installation. Only efs and boot would have a direct disk partition.

[FONT=monospace][COLOR=#800080]Any idea if it is possible to define relative sizes (e.g. "all available space" or "90 % of available space" in autoinstall.
[/COLOR][COLOR=#d0d0d0]
[/COLOR][/FONT]```
autoinstall:
  storage:
    config:
    - ptable: gpt
      serial: ADATA_SP310_2F1120000320
      wwn: '0x5000000000000000'
      path: /dev/sda
      wipe: superblock
      preserve: false
      name: ''
      grub_device: false
      type: disk
      id: disk-sda

... cut on purpose ...

    - device: disk-sda
      size: 28739371008
      wipe: superblock
      flag: ''
      number: 3
      preserve: false
      grub_device: false
      type: partition
      id: partition-2

... cut on purpose ...

    - name: ubuntu-lv
      volgroup: lvm_volgroup-0
      size: 14357102592B
      wipe: superblock
      preserve: false
      type: lvm_partition
      id: lvm_partition-0

... cut on purpose ...

```[FONT=monospace]
[/FONT]

---

### Post by conre on 2022-06-22
Ah, I have overlooked that on top of [Curtin]("https://curtin.readthedocs.io/en/latest/topics/storage.html#") there is a superset by [autoinstaller]("https://ubuntu.com/server/docs/install/autoinstall-reference") (Disk selection extensions) allowing to use what I am looking for. I will try and get back if I fail.

---

