---
title: "Ubuntu 14.04 Trusty Tahr Only boots after a fresh install, then no boot device"
date: 2014-03-11
forum: Ubuntu Development Version
---

### Post by Trentin_Shaun_Fred on 2014-03-11
I have been at this for a about a week, I am attempting to perform a  fresh install on a TOSHIBA Satellite NB15T-A1302 laptop of Ubuntu 14.04  Trusty Tahr.

**Problem:**
[LIST]
[*]Installing Ubuntu 14.04 Trusty Tahr on a UEFI machine, no CSM/Legacy support to my knowledge. 
[/LIST]
**HDD Partition Info:**
```

##### GPT fdisk #####
##### Initial Scan #####
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

##### Partition Table #####
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 325C463C-D152-46AF-B063-795B786AFAFB
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 4077 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          999423   487.0 MiB   EF00  
   2          999424         1499135   244.0 MiB   8300  
   3         1499136       976771071   465.0 GiB   8E00  

##### Partition 1 #####
Partition GUID code: C12A7328-F81F-11D2-BA4B-00A0C93EC93B (EFI System)
Partition unique GUID: A69C9291-206C-47CE-8AD0-305D745B9AE5
First sector: 2048 (at 1024.0 KiB)
Last sector: 999423 (at 488.0 MiB)
Partition size: 997376 sectors (487.0 MiB)
Attribute flags: 0000000000000000
Partition name: ''

##### Partition 2 #####
Partition number (1-3): 2
Partition GUID code: 0FC63DAF-8483-4772-8E79-3D69D8477DE4 (Linux filesystem)
Partition unique GUID: 01C7E548-198C-437A-A3BF-766C0A542272
First sector: 999424 (at 488.0 MiB)
Last sector: 1499135 (at 732.0 MiB)
Partition size: 499712 sectors (244.0 MiB)
Attribute flags: 0000000000000000
Partition name: ''

##### Partition 3 #####
Partition number (1-3): 3
Partition GUID code: E6D6D379-F507-44C2-A23C-238F2A3DF928 (Linux LVM)
Partition unique GUID: F6440B88-8E13-4679-8D37-9E91CB35779F
First sector: 1499136 (at 732.0 MiB)
Last sector: 976771071 (at 465.8 GiB)
Partition size: 975271936 sectors (465.0 GiB)
Attribute flags: 0000000000000000
Partition name: ''
```
**Basic Hardware Info:**
```

Intel Celeron Processor N2810
4GB DDR3L 1600MHz memory
500GB HDD (5400rpm, Serial ATA)
Intel Dual Band Wireless-AC 3160 1x1 AC (433Mbps)
Bluetooth V4.0
10/100 Ethernet LAN
1-USB (3.0) port
2-USB (2.0) ports

Host bridge: Intel Corporation ValleyView SSA-CUnit (rev 0a)
VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0a)
SATA controller: Intel Corporation ValleyView 6-Port SATA AHCI Controller (rev 0a)
USB controller: Intel Corporation ValleyView USB xHCI Host Controller (rev 0a)
Encryption controller: Intel Corporation ValleyView SEC (rev 0a)
Audio device: Intel Corporation ValleyView High Definition Audio Controller (rev 0a)
PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0a)
PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0a)
PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0a)
ISA bridge: Intel Corporation ValleyView Power Control Unit (rev 0a)
SMBus: Intel Corporation ValleyView SMBus Controller (rev 0a)
Network controller: Intel Corporation Wireless 3160 (rev 83)
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)

BIOS: ACPI Flash BIOS version 1.00 for Satellite NB10/NB10t/NB15/NB15t
```[B]
Symptoms:[/B]
[LIST]
[*]No boot device detected; Insert boot device and press any button to continue. 
[/LIST]
[INDENT=2]This occures after I restart the  machine from Ubuntu immediatly after a fresh install, I am able to  consistently boot into Ubuntu after the install but not consecutively, This is leading me to  believe it is a GRUB2 issue or a conflict with whatever happens to the  MBR and/or EFI partition after Ubuntu loads the first time.
[/INDENT]
 **Notes:**
[LIST]
[*]I come from a windows background, this machine  had windows 8 installed on it and was upgrades to windows 8.1, I since  then wiped the hardrive with: 
[/LIST]
[INDENT]*dd if=/dev/zero of=/dev/sda bs=512*

And  reinstalled onto the 'fresh' drive, I am planning to become a full time Linux user with eyes currently on Ubuntu and Fedora.
[/INDENT]

[LIST]
[*]My UEFI BIOS (referred to as much) detects my HDD and it is in the proper boot order. 
[*]I have yet to tamper with the grub boot settings manually.
[*]Trusty Tahr seems to detect all my hardware, older builds not so much, nomodeset does not seem to offer a consistent solution. 
[*]I  have said that this laptop may be strictly UEFI, I base this assumption  on the fact that there is no Legacy or CSM option in the BIOS, but it  may be possible that the BIOS does this automatically based on HDD  format. 
[*]I have removed windows 8 from his machine all together, currently I am running in a live session. 
[*]Secure Boot is disabled. 
[*]I will update this post with a solution as soon as I find one. 
[/LIST]

---

### Post by Bucky Ball on 2014-03-12
*Thread moved to **Ubuntu +1**.*

Welcome. Any and all threads regarding the unreleased 14.04 go here. 

Unless you know what you're doing and/or want to test and help troubleshoot bugs and issues, 14.04 is NOT a good place to start. Expect breakages. 

Unless you fit into the above category, I strongly advise you install 12.04 or 13.10, both directly upgradeable to 14.04.

PS: Having said this, reporting any issues with 14.04 and giving the community a chance to troubleshoot them is a good thing.

---

### Post by sdowney717 on 2014-03-12
try this if its grub issue.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I had to download the iso and make a boot flash drive with unetbootin.
14.04 even with the ppa added could not install the package.

Why a grub issue if it does boot into ubuntu?

---

### Post by strowger2 on 2014-04-04
> **Trentin_Shaun_Fred said:**
> 

[LIST]
[*]I  have said that this laptop may be strictly UEFI, I base this assumption  on the fact that there is no Legacy or CSM option in the BIOS, but it  may be possible that the BIOS does this automatically based on HDD  format.
[*]I have removed windows 8 from his machine all together, currently I am running in a live session.
[*]Secure Boot is disabled.
[*]I will update this post with a solution as soon as I find one.
[/LIST]


I have the NB10, which is a close relative of the NB15. There's not enough information about these machines online - I've started a site at [http://unofficialnb10.wordpress.com/](http://unofficialnb10.wordpress.com/) but it's still sparse.

A few comments which might help:

1 - There's a BIOS 1.20 out now. Unfortunately you need Windows to install it! I think you should probably install that before you do anything else, it seems to fix a lot of bugs. Power consumption is noticeably lower with the latest BIOS too.

2 - Even with the latest BIOS, UEFI booting is still quite broken. It can be done though! A big problem I had is that the NB10/15 BIOS will only boot a file (from the EFI partition which is normally mounted on /boot/efi) called boot/bootx64.efi.  If you've got the standard "ubuntu/grubx64.efi" try copying it to boot/bootx64.efi. 

This issue explains why the installer, and the livecd, will boot (as they have files named boot/bootx64.efi on their EFI partitions), but your installed system will not.

This occurs because at the end of the install process, the installer tries to tell the BIOS the name and location of the file to boot from - but the Toshiba BIOS could most politely be described as "not very good".

3 - Any kernel before 3.14 has various problems. It doesn't sound like you're getting as far as a kernel being loaded, though.

I'm happy to help further if you're still stuck.

Cheers

---

