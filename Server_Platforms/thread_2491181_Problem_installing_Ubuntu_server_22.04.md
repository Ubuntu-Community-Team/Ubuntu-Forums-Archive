---
title: "Problem installing Ubuntu server 22.04"
date: 2023-09-28
forum: Server Platforms
---

### Post by Minny on 2023-09-28
I'm trying to install Ubuntu server 22.04 to a partition on a hard drive and I'm having a problem. The problem arises when I come to the screen shown in the picture.

[IMG]https://lh3.googleusercontent.com/pw/ADCreHc-dW3XxeoxnmkqP-W7FI4b5-ZdKE4_8Yh8BmjrjHKTyXKo9gEBYEJnWDtq1kRgKS3FQAu4Ajj5Nz7QUiFVNFwNnSIB_gTHam84PzQzfzU80hcJY1UsWKXQ_kMWOqVsuU9Pi3jVbrKcbT6Yvz6ViXs9AXo1b8VdBsADxq47cniCMYwzu3XD9GwRxPGT4zH1FDnEVerz31jGAje3t5l3Hov0SRJ52Qgewge85Q38vjo2zlDT6y4RDadW5BnhhOnepgfmOFb3ZGt7pn1056HdYnw9tPnwWNG4NTA6o0qD7jdPkRLK81nPmjU3Ta9s6nYSKYfOyzRu87u8EGxZ75F0u4s3smv8lKtqcup7WEIRQ1KwHOe2AcH7Wqv0P5jZJQPaQERAuGkJGm3vhRWLBC34Nh0IDM2SWL11VNwUECxe0eT_Chk8rvhWHBBAqkVk3HFStHNi5YDn4J9VJI7g0p0E_fMj4rZhriNrLGkaGz6ygYuU8JKHJqNX_dHoQ30oHeAAM066EGNTYFoQjbKbCsyGpPC7xHDebfyZ93E_NLFbBNDfNc8E7ZyscMHrfXVTcedRk22C9NjNHXikgkUxndybJbs7InfUfSQgsm6tmA63sP3vMeQQ_Jh51jm2J05iGYL1pSVcntyEvNxdQN8SDKma2C5Nn7hHurulp2K0j4ohUN2j9xQNXtFow6fm0Zphuq1y-GfE63-kMp-5XmrAs-qrv_L7je8LpyKV3cuhfudOJH1A3qysJbsGE0NHEmZSKlFU2_klaxouFuG4-1Sr4qWi-4CEO08gZjM0LcUaXRNPSTWEZHtJENFemhgWINwy8DDNgeiDcmUm8-rowCGxtnLXXOf2EpFXuqMDqo2jLIbjgecj8Cv1Dczsi9idPE943XNloCwgPVd_aJcx3_GlkxAIh5KUVFh_01si9C5PXLXWlU8eIBZSMFG4wK5AK2QUnYL595qspKJ1yTmuV8MQHXla7HTkGTB-QMJsEx0=w724-h965-s-no?authuser=0[/IMG]
[IMG]https://lh3.googleusercontent.com/pw/ADCreHfPgYrlucK3Nx8AOgC_7dYYiArKs2h9IZgd4hOxHMYFAssGAh1ER2UcSJt7L3WR0n6c0d9bi3todwMOfP2PQRG2kaTv7KBBeSzn8jX6EOCba40hFJ1NCdEEuBCT9-KBcn1bfyTIpl7lYArq6BGyh4fYEA=w726-h969-s-no?authuser=0[/IMG]
At this screen I need to select a drive to be the boot drive. I want it to the first one in the list of available devices, the WDS100 which is a 1TB SSD internal drive. I have already selected partition 2 of this drive to be the installation partition for the Ubuntu server install.

The problem is that when I click on the WDS100 drive the option to select it as the boot drive is grayed out. I can't figure out why. I'm a bit of a noob with Ubuntu server but have installed Ubuntu desktop before, which I found pretty straightforward.

The WDS already has 2 installations of Windows (which are the partitions 4 and 5) that I don't want to delete. Could those be somehow causing the problem? Maybe I need to do something to the boot partition (partition 1 of WDS100) before I start the installation?

Since I cannot select a boot drive I cannot get past this screen and continue with the installation.

Any help would be appreciated.

---

### Post by TheFu on 2023-09-28
Dual boot.  That's a very, very, important distinction. I cannot help. Sorry.

I've been setting up storage for my installs manually for a few years. In general, I have a script the creates a partition table, creates 3 partitions on the device, connects one of the partitions as a PV for LVM, creates a Volume Group using the PV, then creates about 5 LVs.  This all happens BEFORE I get to the screen you've posted.  All I need to do is to connect the specific LVs with the specific mount locations and file system types.  I do remember that for some of those partition, formatting was required.  Took me a bit to figure that requirement out. Sorry, I don't recall which partitions required formatting, but it wasn't the those inside LVM.  That just leaves the EFI and /boot/ areas ... which could be really bad for a dual boot attempt.

---

### Post by darkod on 2023-09-28
Is there really a point in installing a server as dual boot?

I have done it with desktop, but with ubuntu server I am not even sure the bootloader can correctly detect and boot your windows. Especially when EFI boot is involved.

If you insist to try and install this way, did you try to select the WDS100 disk as boot device first, before selecting which partition to use as root? Maybe in that order it will accept it.

Also when selecting a boot device remember that you need to select the disk itself, not any partition on it. Or for EFI boots what you needed to select was the ESP partition as boot device? I don't remember now, I usually use legacy boot myself.

---

### Post by Rubi1200 on 2023-09-28
I also wonder what the point of it would be.

In any event, it might be helpful if you run the boot info script from a live medium and post the link to the results so we can see what is going on.

No repair, just the results please.

---

### Post by Rubi1200 on 2023-09-28
> **darkod said:**
> Is there really a point in installing a server as dual boot?

I must admit I also don't see the point.

In any event, so we can try and get a better picture of how things look please post the results of the boot info script from my signature. No repair, just the results please.

---

### Post by TheFu on 2023-09-28
> **darkod said:**
> Is there really a point in installing a server as dual boot?

I have done it with desktop, but with ubuntu server I am not even sure the bootloader can correctly detect and boot your windows. Especially when EFI boot is involved.

If you insist to try and install this way, did you try to select the WDS100 disk as boot device first, before selecting which partition to use as root? Maybe in that order it will accept it.

Also when selecting a boot device remember that you need to select the disk itself, not any partition on it. Or for EFI boots what you needed to select was the ESP partition as boot device? I don't remember now, I usually use legacy boot myself.

This is for a 20.04 EFI boot, Ubuntu Server.  No dual boot:

```
$ sudo fdisk -l /dev/nvme0n1
Disk /dev/nvme0n1: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: Samsung SSD 980 1TB                     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 16384 bytes / 131072 bytes
Disklabel type: gpt
Disk identifier: AA2A1763-553C-4097-9CFD-D3621DFC2FE5

Device           Start        End    Sectors   Size Type
/dev/nvme0n1p1    2048       4095       2048     1M BIOS boot
/dev/nvme0n1p2    4096     106495     102400    50M EFI System
/dev/nvme0n1p3  106496    1540095    1433600   700M Linux filesystem
/dev/nvme0n1p4 1540096 1953525134 1951985039 930.8G Linux LVM

```
nvme0n1p1 isn't mounted anywhere. Might be excess, but I just wanted something that worked.
```
nvme0n1                          disk                    931.5G                               
&#9500;&#9472;nvme0n1p1                      part  ext2                  1M                               
&#9500;&#9472;nvme0n1p2                      part  vfat                 50M   43.9M    12%                /boot/efi
&#9500;&#9472;nvme0n1p3                      part  ext4                700M    340M    42%                /boot
&#9492;&#9472;nvme0n1p4                      part  LVM2_member       930.8G                               
  &#9500;&#9472;vg01-swap01                  lvm   swap                4.1G                               [SWAP]
  &#9500;&#9472;vg01-root01                  lvm   ext4                 35G   25.4G    20%                /
  &#9500;&#9472;vg01-var01                   lvm   ext4                 20G   15.6G    15%                /var
  &#9500;&#9472;vg01-tmp01                   lvm   ext4                  4G    3.4G     6% tmp01          /tmp
  &#9500;&#9472;vg01-home01                  lvm   ext4                 10G    2.9G    65% home01         /home

```

I think nvme0n1p2 for a dual boot probably needs to be larger.  My single-boot systems have never used more than 8MB, but I've seen where people recommend 500MB. 

/boot in Linux is expanding due to all the built-in-at-boot modules, so 500MB isn't sufficient to have 3+ kernels anymore. I suspect the recommendation is 1G now - a new high in "bloat" to my mind. As you can see, I chose 700MB and have plenty of comfort room, unless I get 2 kernel-lines installed, which can happen if you aren't careful.  Updates fail when /boot/ is near full and fixing those can become challenging. Best to never allow it. I get this is jumping ahead.

If you don't use LVM, fewer partitions can be made to work.

I suppose someone should say this.
Have you considered running Ubuntu in a virtual machine under MS-Windows?  Then the partition limits would go away, since you could setup GPT inside the VM. Just depends on what you intend this server to handle if that's a good idea or not.

---

### Post by MAFoElffen on 2023-09-28
There are a few caveats with the Server Edition Installer. For installing on a system that already has something installed (such as another OS) it has some built in limitations, and tricks to get around them. Some you have to do things to get around.

Easiest for you, for what you described, and the challenges you are facing:
You say you want to install it on another blank drive, and to create it's own EFI partition, with it as the only OS on that drive. You said that is your goal, correct?

Open the case and disconnect all drives except that drive.

Boot from the Server Edition Live Installer media. Use the 'Help' button in the upper right to get to Command Prompt. Zero the drive, by using gdisk to create a new GPT partition table. Exit the command prompt to get back to the Installer. 

Note that will make anything that was there on that drive disappear, but that is what you described as what you wanted. If that is not what you meant, stop before doing that and tell us what you want differently.

Install as you desire. After the install, shutdown the computer.

Reconnect all the drives.

On first boot, enter your UEFI BIOS setting and set that drive as the primary boot drive. Continue the boot.

After boot, log in with your credentials.
```

sudo vi /etc/default/grub

```
In the editor, remove the comment character before the line "GRUB_OSPROBER_DISABLE=false". Save and exit.
```

sudo update-grub

```
Watch the output to ensure the other OS'es are picked up by Grub. Reboot to test.

If anywhere in that, something unexpected happens or you have a question, stop and ask.

---

### Post by darkod on 2023-09-28
> You say you want to install it on another blank drive, and to create it's own EFI partition, with it as the only OS on that drive. You said that is your goal, correct?

On the contrary. Partitions 4 and 5 on the same disk hold windows installation and the OP doesn't want to remove it. Ubuntu will not be the only OS on the disk. Neither the EFI partition since it will be shared (??) with windows.

---

### Post by Minny on 2023-09-28
The purpose is to install docker as I'm interested in playing around with containers and learning more about that technology & what I can do with it. I ran into problems trying to install docker under Windows and wanted to try this.

The boot info is below:

```
boot-info-4ppa203                                              [20230928_1943]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => No boot loader is installed in the MBR of /dev/sda.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/fwupx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

nvme0n1p2: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

nvme0n1p3: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

nvme0n1p4: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe

nvme0n1p5: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       3518998527 sectors, but according to the info from 
                       fdisk, it has 7813965823 sectors.
    Operating System:  
    Boot files:        

sdf: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg


================================ 3 OS detected =================================

OS#1:   Ubuntu 18.04.3 LTS on nvme0n1p2
OS#2:   Windows 10 or 11 on nvme0n1p4
OS#3:   Windows 10 or 11 on nvme0n1p5

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GV102 from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 18.04.3 LTS, bionic, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 1.C0 from American Megatrends Inc.
The firmware is EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).


f7a57b08bc7c1c85417ae4cea582d1d4   nvme0n1p1/BOOT/bkpbootx64.efi
f7a57b08bc7c1c85417ae4cea582d1d4   nvme0n1p1/BOOT/bootx64.efi
bed45d1c9554cea09924d3814cb7c446   nvme0n1p1/BOOT/fbx64.efi
4487628005555bfd4a4c0a47211e0700   nvme0n1p1/BOOT/mmx64.efi
256fe27540b54b71cf38110338247688   nvme0n1p1/ubuntu/fwupx64.efi
b6e92eeb44c28043967df78682083d85   nvme0n1p1/ubuntu/grubx64.efi
4487628005555bfd4a4c0a47211e0700   nvme0n1p1/ubuntu/mmx64.efi
f7a57b08bc7c1c85417ae4cea582d1d4   nvme0n1p1/ubuntu/shimx64.efi
428af1f61d3b409a787f731380659cf3   nvme0n1p1/Microsoft/Boot/bootmgfw.efi
4d2e91c14e27a7643e0601544f14fc9e   nvme0n1p1/Microsoft/Boot/bootmgr.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
sda    : is-GPT,    no-BIOSboot,    has-noESP,     usb-disk,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
nvme0n1p4    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p5    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p5    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1
nvme0n1p4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 1E55E181-C015-4434-AD3F-181686668A35
               Start        End    Sectors   Size Type
nvme0n1p1       2048    1050623    1048576   512M EFI System
nvme0n1p2    1050624 1172926463 1171875840 558.8G Linux filesystem
nvme0n1p3 1563551744 1563584511      32768    16M Microsoft reserved
nvme0n1p4 1563584512 1953523711  389939200   186G Microsoft basic data
nvme0n1p5 1172926464 1563551743  390625280 186.3G Microsoft basic data
Partition table entries are not in disk order.
Disk sda: 3.7 TiB, 4000752599040 bytes, 7813969920 sectors
Disk identifier: 75B3A371-73B9-4416-92A8-9BCAB951863C
      Start        End    Sectors  Size Type
sda1   2048 7813967871 7813965824  3.7T Microsoft basic data
Disk sdf: 3.7 GiB, 4005560320 bytes, 7823360 sectors
Disk identifier: 0x5092863d
      Boot   Start     End Sectors  Size Id Type
sdf1  *          0 4067999 4068000    2G  0 Empty
sdf2       3989132 3994059    4928  2.4M  e W95 FAT16 (LBA)

parted -lm (filtered): _________________________________________________________

sda:4001GB:scsi:512:4096:gpt:WD My Book 1235:;
1:1049kB:4001GB:4001GB:ntfs:My Book:msftdata;
sdf:4006MB:scsi:512:512:unknown:Kingston DataTraveler 2.0:;
nvme0n1:1000GB:nvme:512:512:gpt:WDS100T2X0C-00L350:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:601GB:600GB:ext4::;
5:601GB:801GB:200GB:ntfs::msftdata;
3:801GB:801GB:16.8MB::Microsoft reserved partition:msftres;
4:801GB:1000GB:200GB:ntfs:Basic data partition:msftdata;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                     
&#9492;&#9472;sda1      ntfs     4A06CAD506CAC165                     f3532e87-6f1f-487a-8f79-d6303ee6018b My Book                  My Book
sdf         iso9660  2019-08-05-19-29-01-00                                                    Ubuntu 18.04.3 LTS amd64 
&#9500;&#9472;sdf1      iso9660  2019-08-05-19-29-01-00               5092863d-01                          Ubuntu 18.04.3 LTS amd64 
&#9492;&#9472;sdf2      vfat     74B7-E2BB                            5092863d-02                          Ubuntu 18.04.3 LTS amd64 
nvme0n1                                                                                                                 
&#9500;&#9472;nvme0n1p1 vfat     8A08-AD80                            f02f28d7-53b7-4e2a-b13a-4e653a9e3629                          EFI System Partition
&#9500;&#9472;nvme0n1p2 ext4     e9068161-f6bc-4fa6-b223-98f418e539aa 2823bded-0d5c-4dd9-9d01-c1c562f0006c                          
&#9500;&#9472;nvme0n1p3                                               fc5c2f72-b421-48d3-8f47-0f711214538b                          Microsoft reserved partition
&#9500;&#9472;nvme0n1p4 ntfs     3880FE5980FE1CD6                     4d01c3e5-05bd-4732-8f5f-65baac157ea3                          Basic data partition
&#9492;&#9472;nvme0n1p5 ntfs     156D614171F6B56C                     fbb7e2ce-b406-416d-a377-8dd3fd3311c6 Win2                     

Mount points (filtered): _______________________________________________________

                Avail Use% Mounted on
/dev/nvme0n1p1 473.2M   7% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p2 446.8G  14% /mnt/boot-sav/nvme0n1p2
/dev/nvme0n1p4   7.8G  96% /mnt/boot-sav/nvme0n1p4
/dev/nvme0n1p5  18.8G  90% /mnt/boot-sav/nvme0n1p5
/dev/sda1        1.3T  65% /mnt/boot-sav/sda1
/dev/sdf            0 100% /cdrom

Mount options (filtered): ______________________________________________________


=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid e9068161-f6bc-4fa6-b223-98f418e539aa root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

=================== nvme0n1p2/boot/grub/grub.cfg (filtered) ====================

Ubuntu   e9068161-f6bc-4fa6-b223-98f418e539aa
Ubuntu, with Linux 5.4.0-47-generic   e9068161-f6bc-4fa6-b223-98f418e539aa
Ubuntu, with Linux 5.4.0-45-generic   e9068161-f6bc-4fa6-b223-98f418e539aa
Ubuntu, with Linux 4.15.0-117-generic   e9068161-f6bc-4fa6-b223-98f418e539aa
Windows Boot Manager (on nvme0n1p1)   osprober-efi-8A08-AD80
### END /etc/grub.d/30_os-prober ###
System setup   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme0n1p2/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=e9068161-f6bc-4fa6-b223-98f418e539aa /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=8A08-AD80  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
//192.168.1.1/Myb1  /media/mybookshare  cifs  vers=1.0,guest,uid=1000,iocharset=utf8  0  0

==================== nvme0n1p2/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

================= nvme0n1p2: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
   3.346691132 = 3.593482240    boot/grub/grub.cfg                             2
  52.647483826 = 56.529805312   boot/grub/i386-pc/core.img                     1
  90.297847748 = 96.956575744   boot/vmlinuz-4.15.0-117-generic                1
  88.251899719 = 94.759755776   boot/vmlinuz-5.4.0-45-generic                  1
  90.720649719 = 97.410555904   boot/vmlinuz-5.4.0-47-generic                  1
  90.720649719 = 97.410555904   vmlinuz                                        1
  90.297847748 = 96.956575744   vmlinuz.old                                    1
  90.579681396 = 97.259192320   boot/initrd.img-4.15.0-117-generic             2
  89.601455688 = 96.208830464   boot/initrd.img-5.4.0-45-generic               4
  90.590061188 = 97.270337536   boot/initrd.img-5.4.0-47-generic               5
  90.590061188 = 97.270337536   initrd.img                                     5
  90.579681396 = 97.259192320   initrd.img.old                                 2

=================== nvme0n1p2: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 12693 Mar 18  2019 10_linux
-rwxr-xr-x 1 root root 11298 Mar 18  2019 20_linux_xen
-rwxr-xr-x 1 root root 12059 Mar 18  2019 30_os-prober
-rwxr-xr-x 1 root root  1418 Mar 18  2019 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Mar 18  2019 40_custom
-rwxr-xr-x 1 root root   216 Mar 18  2019 41_custom

====================== sdf/boot/grub/grub.cfg (filtered) =======================

Try Ubuntu without installing
Install Ubuntu
OEM install (for manufacturers)
Check disc for defects

==================== sdf: Location of files loaded by Grub =====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
nvme0n1p2,
using the following options:  nvme0n1p1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups

Blockers in case of suggested repair: __________________________________________

The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode. 

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 18.04.3 LTS entry (nvme0n1p1/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)
The boot of your PC is in BIOS-compatibility/CSM/Legacy mode. You may want to retry after changing it to UEFI mode.
```

---

### Post by MAFoElffen on 2023-09-29
@Minny -- 

It is a Forum policy to only post commands ad raw  output wrapped within CODE tags. Beside making it very hard for us Users  to read an interpret something in a post, it does strange things to the  Forums Software. (This may be why no one has answered you further.)

Please  go back to your post #9, and select Edit Post > Advanced Edit.  Select the output from your boot-info Report > Select the "#" Icon  from the extended edit menu bar to wrap the selected text with CODE  Tags. Save the edited post.

If you are creating a post and are  inserting commands or output, use "Advanced Reply" or "Advanced Editor"  to get the extended edit menu bar to be able to insert your CODE Tags,  and paste them between the Tags.

---

### Post by SeijiSensei on 2023-09-29
Servers should be running all the time. Dual-booting makes little sense.

Your best bet is probably installing VirtualBox on Windows then creating a virtual machine to use as the Linux server. Then it will be available whenever the machine is booted into Windows.

---

### Post by MAFoElffen on 2023-09-29
@SeijiSensei

+1 Traditionally.

But: To each, their own.

I have answered at least 4 threads this month for people installing Desktops to Server Edition servers, and then installing xdrp-server onto them. (or VNC, or x2go, etc) I always remind them (first) that Server Edition is "Console" and they can just connect to them remotely from ssh. 

GUI's add load. Desktops install "power plans" that want to put machines to sleep and/or hibernate to save power. Those Users cause themselves extra work and open up  vulnerabilities that they then need to deal with. The priority for a Desktop is the presentation layer. Priorities on Server are server services.

When I had to go through Windows Server Administration courses... and around 2016, when MS changed their server focus to Server-Core... And MS'es marketing hype machine was spinning that there was better security and less resources used on a server without a GUI... I said, SEE!?! What have we been saying for years.

I don't get it, but I also don't judge. I do make them aware... But in the end, I support people to get to their goals. I support Ubuntu in all it's forms.

And the other hand-- Server Edition (besides being a full-function production grade server system) is a good learning tool for someone starting out for someone who wants to learn. It's lightweight. It's scalable to much more than they can imagine. It will cause them to learn commandline. And we are here to support them if they need help.

---

### Post by Minny on 2023-10-01
I found a solution for this.

The last line of the boot-info I posted has this line:

```
The boot of your PC is in BIOS-compatibility/CSM/Legacy mode. You may want to retry after changing it to UEFI mode.
```

I tried doing that and it solved my problem. When I tried doing the ubuntu server installation again I was able to select the boot disk and continue with the ubuntu server installation. In fact, once I did that the boot disk was automatically selected after I selected the installation partition.

I changed from 'legacy' to UEFI mode by going into my BIOS settings during boot and making the change.

Anyone else having this problem might find additional help in the comments section under [this youtube]("https://www.youtube.com/watch?v=yJeDV34GzqI&ab_channel=SavvyNik") or on [this help page]("https://neosmart.net/wiki/enable-uefi-boot/").

I'm now able to boot into Windows or Ubuntu Server as I please.

---

### Post by MAFoElffen on 2023-10-01
Congratulations. Thank you for sharing this with us.

If solved to your satisfaction, please select the "Thread Tools" link in the upper right of this thread, and mark your threas as "Sovled". That will help other users to be able to find your solution.

---

### Post by Minny on 2023-10-01
Thanks for your help with the forum protocols MAFoElffen!

---

### Post by MAFoElffen on 2023-10-03
My pleasure to keep you having fun, and enjoying yourself... Instead of being scolded by the Moderators and Admins. (They are busy enough having to do many other things. LOL)

---

### Post by worldomkar on 2024-01-25
I was able to work around by changing the type of the allocated partition to 1 (EFI System) from another console.
I had /dev/sda disk for Ubuntu to be installed, and dvd-image was booted from another disk.

[TABLE="width: 500, align: left"]
[TR]
[TD]```
Ctrl+Alt+F2
```[/TD]
[TD]Opens another console[/TD]
[/TR]
[TR]
[TD]```
sudo fdisk /dev/sda
```[/TD]
[TD]Change the disk device to the appropriate device you have[/TD]
[/TR]
[TR]
[TD]```
t
```[/TD]
[TD]Change partition type[/TD]
[/TR]
[TR]
[TD]```
2
```[/TD]
[TD]Change the partition number to the appropriate partition you have.
2 was the partition I created for boot (1GB)[/TD]
[/TR]
[TR]
[TD]```
1
```[/TD]
[TD]"EFI System"[/TD]
[/TR]
[TR]
[TD]Reboot[/TD]
[TD]After Reboot, the installer recognises this partition as /boot/efi and the installer should be unblocked.[/TD]
[/TR]
[TR]
[TD]```
update-grub
```[/TD]
[TD]Run Update grub from the disk to detect new installation; for some reason disk was not able to boot, but grub from another disk was able to detect this installation.[/TD]
[/TR]
[TR]
[TD]```
grub-install /dev/sda2
```[/TD]
[TD]Change to "EFI System" partition used in earlier steps.[/TD]
[/TR]
[/TABLE]
Hope this helps.

---

