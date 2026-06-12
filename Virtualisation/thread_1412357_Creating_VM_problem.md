---
title: "Creating VM problem"
date: 2010-02-21
forum: Virtualisation
---

### Post by satimis on 2010-02-21
Hi folks,


Host - Fedora 12 64bit
VirtualBox-3.1-3.1.4_57640_fedora12-1.x86_64 - virtualizer


I'm prepared to run following command to create a Debian VM
```

$ VBoxManage createvm -name "Debian Lenny Server" -register
$ VBoxManage modifyvm "Debian Lenny Server" -memory "512MB" -acpi on -boot1 dvd -nic1 nat
$ VBoxManage createvdi -filename "Debian_Lenny_Server.vdi" -size 10000 -register
$ VBoxManage modifyvm "Debian Lenny Server" -hda "Debian_Lenny_Server.vdi"
$ VBoxManage registerimage dvd /home/debian-500-i386-netinst.iso
$ VBoxManage modifyvm "Debian Lenny Server" -dvd /download/debian-500-i386-netinst.iso

```

Netinstall iso image is in /home/satimis/Download/debian-504-amd64-netinst.iso

On running
$ VBoxManage modifyvm "Debian Lenny Server" --hda "Debian_Lenny_Server.vdi"```

Sun VirtualBox Command Line Management Interface Version 3.1.4
(C) 2005-2010 Sun Microsystems, Inc.
All rights reserved.

ERROR: Could not find a storage controller named 'IDE Controller'
Details: code VBOX_E_OBJECT_NOT_FOUND (0x80bb0001), component Machine, interface IMachine, callee nsISupports
Context: "AttachDevice(Bstr("IDE Controller"), 0, 0, DeviceType_HardDisk, uuid)" at line 556 of file VBoxManageModifyVM.cpp

```


This is a SATA HD

$ sudo fdisk -l```

[sudo] password for satimis: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003a4bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              26      121601   976555201   8e  Linux LVM

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0883bef2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4867    39086080    7  HPFS/NTFS

Disk /dev/dm-0: 989.7 GB, 989704749056 bytes
255 heads, 63 sectors/track, 120324 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 10.3 GB, 10284433408 bytes
255 heads, 63 sectors/track, 1250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

```


Replace --hda with --sdb ?

Please advice.  TIA

B.R.
satimis

---

### Post by dcstar on 2010-02-24
> **satimis said:**
> Hi folks,

**Host - Fedora 12 64bit**
VirtualBox-3.1-3.1.4_57640_fedora12-1.x86_64 - virtualizer
........

Why do you think that people in this **UBUNTU** Linux forum have any idea about your **FEDORA** questions?

This is not a general "any flavour" Linux forum, it is for people running Ubuntu to help other people who are running VMs on their Ubuntu platforms.

You would be far better off asking your questions in a Fedora forum where people with actual systems the same as yours may have some answers for you.

---

