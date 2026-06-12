---
title: "Can't boot raw WinXP in VirtualBox (can't safely limit partitions; boot stalls)"
date: 2012-12-08
forum: Virtualisation
---

### Post by mjjj on 2012-12-08
(I tried to post this to the VirtualBox forums but their registration page appears to be broken. And part of it may be an issue with install-mbr .)

I'm having trouble booting Windows XP from a raw vdmk partition inside VirtualBox. (I'm doing this because I still need the  option of booting natively, not in a VM.) I followed the steps described on the following site, which seems to agree with what other sites/forums and section 9.10 of the VirtualBox manual say as well:
[http://geekery.amhill.net/2010/01/27/virtualbox-with-existing-windows-partition/](http://geekery.amhill.net/2010/01/27/virtualbox-with-existing-windows-partition/)

My laptop is a Lenovo T61 with 3GB RAM with WinXP Pro SP3 32-bit installed on C: and most of its data on D: . Those two correspond to sda1 and sda6 below. There's also a FAT32 partition just in case (sda5).

I left some free space next to the logical volume and installed Ubuntu 12.04.1 Desktop 32-bit using default options, so it automatically placed itself and its swap inside that logical volume (sda7 and sda8 below). I installed the latest full VirtualBox (4.1.12) in the Ubuntu host.

```

(parted) print all                                                        
Model: ATA ST9500420AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      7774kB  57.7GB  57.7GB  primary   ntfs            boot
 2      57.7GB  500GB   442GB   extended                  lba
 7      57.7GB  80.7GB  23.0GB  logical   ext4
 8      80.7GB  83.9GB  3199MB  logical   linux-swap(v1)
 5      83.9GB  89.1GB  5239MB  logical   fat32
 6      89.1GB  500GB   411GB   logical   ntfs

install-mbr --f ~/.VirtualBox/FAKE.mbr

```Setting the permissions and creating the vmdk file seemed to go smoothly, but trying to limit the VM's access to specific partitions (whether 3 partitions or just the one crucial one) didn't seem to actually work once attached to my vm. All I see upon booting is "MBR" on a black screen, indefinitely. (Each vmdk I make shows a size of 465.76GB, but I'm guessing that's fine. I get a VERR_NOT_SUPPORTED error if I try to attach one of the "-pt.vmdk" files instead, but I'm guessing those shouldn't be mapped anyway.)

If I instead give the vm access to the full disk, it starts to work. I then get a functioning GRUB boot menu, but when I select WinXP it's goes to a permanent black screen, rather than to my WinXP screen for choosing a hardware profile. I get the same stalled black screen whether I attach the vmdk to the IDE or the ATA controller (with "Use host I/O cache" checked or unchecked). I've tried with and without VT-x enabled; ditto for graphics acceleration. "Enable IO APIC" is checked, and "Enable absolute pointing device" is unchecked. Medium values selected for RAM (512MB or 1024MB) and video (64MB).

```

user57@tpadt61:~/.VirtualBox$ sudo chmod 666 /dev/sda
user57@tpadt61:~/.VirtualBox$ ll /dev/sd*
brw-rw-rw- 1 root disk 8, 0 Dec  9 07:02 /dev/sda
brw-rw---- 1 root disk 8, 1 Dec  9 05:41 /dev/sda1
brw-rw---- 1 root disk 8, 2 Dec  9 04:36 /dev/sda2
brw-rw---- 1 root disk 8, 5 Dec  9 05:41 /dev/sda5
brw-rw---- 1 root disk 8, 6 Dec  9 05:41 /dev/sda6
brw-rw---- 1 root disk 8, 7 Dec  9 04:36 /dev/sda7
brw-rw---- 1 root disk 8, 8 Dec  9 04:36 /dev/sda8
user57@tpadt61:~/.VirtualBox$ VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/winxp3.vmdk -rawdisk /dev/sda -partitions 1,5,6 -mbr ~/.VirtualBox/FAKE.mbr
RAW host disk access VMDK file /home/user57/.VirtualBox/winxp3.vmdk created successfully.
user57@tpadt61:~/.VirtualBox$ VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/winxp1.vmdk -rawdisk /dev/sda -partitions 1 -mbr ~/.VirtualBox/FAKE.mbr
RAW host disk access VMDK file /home/user57/.VirtualBox/winxp1.vmdk created successfully.
user57@tpadt61:~/.VirtualBox$ VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/winxpall.vmdk -rawdisk /dev/sda
RAW host disk access VMDK file /home/user57/.VirtualBox/winxpall.vmdk created successfully.
user57@tpadt61:~/.VirtualBox$ ls
compreg.dat    VBoxSVC.log.10  VBoxSVC.log.5  VBoxSVC.log.9        winxp1.vmdk     xpti.dat
FAKE.mbr       VBoxSVC.log.2   VBoxSVC.log.6  VirtualBox.xml       winxp3-pt.vmdk
VBoxSVC.log    VBoxSVC.log.3   VBoxSVC.log.7  VirtualBox.xml-prev  winxp3.vmdk
VBoxSVC.log.1  VBoxSVC.log.4   VBoxSVC.log.8  winxp1-pt.vmdk       winxpall.vmdk
user57@tpadt61:~/.VirtualBox$ 

```Any pointers you might have would be appreciated.

---

