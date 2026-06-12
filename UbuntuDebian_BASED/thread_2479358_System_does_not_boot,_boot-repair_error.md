---
title: "System does not boot, boot-repair error"
date: 2022-09-22
forum: Ubuntu/Debian BASED
---

### Post by chunkypuding on 2022-09-22
Hello
I have issues with pop os booting the boot loader is not visible in bios.
When i try to run boot-repair I get an error.
Boot info report
```
boot-repair-4ppa200                                              [20220922_1645]

============================== Boot Info Summary ===============================

 => libparted MBR boot code is installed in the MBR of /dev/sda.
 => Windows 7/8/10/11/2012 is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Windows 7/8/10/11/2012 is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/Pop_OS-21546503-6099-4165-ba45-1cc1c5f0ece6/vmlinu
                       z-previous.efi 
                       /efi/Pop_OS-21546503-6099-4165-ba45-1cc1c5f0ece6/vmlinu
                       z.efi /efi/Recovery-AE83-3AB9/vmlinuz.efi 
                       /efi/pop/grubx64.efi /efi/systemd/systemd-bootx64.efi 
                       /efi/pop/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

sdc2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 

sdc4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdd3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sde: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sde: /dev/sde already mounted or mount point busy.


================================ 1 OS detected =================================

OS#1:   Pop!_OS 22.04 LTS (22.04) on mapper/data-root

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GA102 [GeForce RTX 3090] EFI VGA from NVIDIA Corporation
Live-session OS is Pop 64-bit (Pop!_OS 22.04 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 5602(5.13) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled - SecureBoot disabled - Please report this message to boot.repair@gmail.com.
BootCurrent: 0003
Timeout: 1 seconds
BootOrder: 0003,0004,0005,0002,0001
Boot0001* Hard Drive    BBS(HD,,0x0)..GO..NO........u.P.L.E.X.T.O.R. .P.X.-.1.2.8.M.5.S....................A.................................>..Gd-.;.A..MQ..L.0.P.3.2.9.3.0.1.6.3.4.7. . . . . . . . ........BO..NO........u.S.T.4.0.0.0.D.M.0.0.5.-.2.D.P.1.6.6....................A.................................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .D.Z.2.H.4.S.D.J........BO..NO........u.S.a.m.s.u.n.g. .S.S.D. .8.6.0. .E.V.O. .5.0.0.G.B....................A.................................>..Gd-.;.A..MQ..L.3.S.2.Z.B.N.K.0.9.1.9.2.2.7. .F. . . . ........BO..NO........u.S.a.m.s.u.n.g. .S.S.D. .8.6.0. .E.V.O. .1.T.B....................A.................................>..Gd-.;.A..MQ..L.3.S.9.Z.X.N.N.0.0.3.0.5.4.8. .E. . . . ........BO
Boot0002* Windows Boot Manager    HD(1,GPT,3b8cc85a-6473-42cc-9c16-7c1bf5d9537c,0x1000,0xf8fff)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)..BO
Boot0003* UEFI: SMI USB DISK 1100    PciRoot(0x0)/Pci(0x1,0x3)/Pci(0x0,0x0)/USB(2,0)/CDROM(1,0x1e4,0x8000)..BO
Boot0004* UEFI: SMI USB DISK 1100, Partition 2    PciRoot(0x0)/Pci(0x1,0x3)/Pci(0x0,0x0)/USB(2,0)/HD(2,MBR,0x58d50179,0x1e4,0x2000)..BO
Boot0005* USB    BBS(HD,,0x0)..GO..NO........q.S.M.I. .U.S.B. .D.I.S.K. .1.1.0.0....................A.............................>..Gd-.;.A..MQ..L.C.C.Y.Y.M.M.D.D.H.H.m.m.S.S.T.1.7.6.J.I........BO

f62c28d9b477b6a1a7b1c991b2b6637d   sdc1/BOOT/bkpbootx64.efi
f62c28d9b477b6a1a7b1c991b2b6637d   sdc1/BOOT/bootx64.efi
72499c6e5ffb05fcef2bcb75d1a6c15d   sdc1/Pop_OS-21546503-6099-4165-ba45-1cc1c5f0ece6/vmlinuz-previous.efi
76b642d1f9dd193d7ab09d2a299d1c96   sdc1/Pop_OS-21546503-6099-4165-ba45-1cc1c5f0ece6/vmlinuz.efi
d32b1a522d11d5680bfc6d9956d770a6   sdc1/Recovery-AE83-3AB9/vmlinuz.efi
f62c28d9b477b6a1a7b1c991b2b6637d   sdc1/pop/grubx64.efi
ef9a21484cc40834aeb42f88f2c6c4e0   sdc1/systemd/systemd-bootx64.efi
3ff213addd49e6515922de34952223ad   sdc1/Microsoft/Boot/bootmgfw.efi
b8736f6dbf1baf951d389be5a519fb32   sdc1/Microsoft/Boot/bootmgr.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
sdb    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    34 sectors * 512 bytes
sdc    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes
sdd    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdb2    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdb3    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdc1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdc2    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdd3    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
mapper/data-root    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    not-far

Partitions info (2/3): _________________________________________________________

sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdd3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
mapper/data-root    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sdb2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdb3    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdc1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdd3    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdd
mapper/data-root    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 119.24 GiB, 128035676160 bytes, 250069680 sectors
Disk identifier: 0x03c6ce02
      Boot Start       End   Sectors   Size Id Type
sda1  *     2048 250068991 250066944 119.2G  7 HPFS/NTFS/exFAT
Disk sdb: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors
Disk identifier: F6BA9AF6-82A9-4698-BA52-23B5B609D558
           Start        End    Sectors  Size Type
sdb1          34      32767      32734   16M Microsoft reserved
sdb2       32768 2434574335 2434541568  1.1T Microsoft basic data
sdb3  2434574336 7814035455 5379461120  2.5T Linux filesystem
Disk sdc: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 237DDB54-C5CE-464F-BC17-0B47DEE71B2F
          Start       End   Sectors   Size Type
sdc1       4096   1023998   1019903   498M EFI System
sdc2    1024000   9412606   8388607     4G Microsoft basic data
sdc3    9412608 968380460 958967853 457.3G Linux filesystem
sdc4  968380464 976769070   8388607     4G Linux swap
Disk sdd: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 08606813-0580-4F9D-A09A-DE028C5490E5
      Start        End    Sectors   Size Type
sdd3   2048 1953521663 1953519616 931.5G Linux filesystem
Disk sde: 29.44 GiB, 31611420672 bytes, 61741056 sectors
Disk identifier: 0x58d50179
      Boot   Start      End  Sectors  Size Id Type
sde1  *          0  6991807  6991808  3.3G  0 Empty
sde2           484     8675     8192    4M ef EFI (FAT-12/16/32)
sde3       6991872 61741055 54749184 26.1G 83 Linux
Disk mapper/myvolume: 457.26 GiB, 490974763520 bytes, 958935085 sectors
Disk mapper/data-root: 457.25 GiB, 490972643328 bytes, 958930944 sectors

parted -lm (filtered): _________________________________________________________

sda:128GB:scsi:512:512:msdos:ATA PLEXTOR PX-128M5:;
1:1049kB:128GB:128GB:ntfs::boot;
sdb:4001GB:scsi:512:4096:gpt:ATA ST4000DM005-2DP1:;
1:17.4kB:16.8MB:16.8MB::Microsoft reserved partition:msftres;
2:16.8MB:1247GB:1246GB:ntfs:Basic data partition:msftdata;
3:1247GB:4001GB:2754GB:ext4:Storage:;
sdc:500GB:scsi:512:512:gpt:ATA Samsung SSD 860:;
1:2097kB:524MB:522MB:fat32::boot, esp;
2:524MB:4819MB:4295MB:fat32:recovery:msftdata;
3:4819MB:496GB:491GB:::;
4:496GB:500GB:4295MB:linux-swap(v1)::swap;
sdd:1000GB:scsi:512:512:gpt:ATA Samsung SSD 860:;
3:1049kB:1000GB:1000GB:ext4:Games:;
sde:31.6GB:scsi:512:512:msdos:SMI USB DISK:;
2:248kB:4442kB:4194kB:::esp;
3:3580MB:31.6GB:28.0GB:ext4::;
mapper/data-root:491GB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:491GB:491GB:ext4::;
mapper/myvolume:491GB:dm:512:512:unknown:Linux device-mapper (crypt):;

Free space >10MiB: ______________________________________________________________

sde: 4.24MiB:3414MiB:3410MiB

blkid (filtered): ______________________________________________________________

NAME            FSTYPE      UUID                                   PARTUUID                             LABEL                     PARTLABEL
sda                                                                                                                               
&#9492;&#9472;sda1          ntfs        197BF7E21A658BBB                       03c6ce02-01                          Windows                   
sdb                                                                                                                               
&#9500;&#9472;sdb1                                                             855b799e-7550-4f98-a707-de3bc719be1f                           Microsoft reserved partition
&#9500;&#9472;sdb2          ntfs        6A47CD4E5645470A                       757ba89e-b860-48a2-a1cf-8d27014a604c windows files             Basic data partition
&#9492;&#9472;sdb3          ext4        1fa3f0ff-92e2-4900-9bb5-45e5950b9b48   e1c1de8a-ae40-452e-b360-7205e269358a D                         Storage
sdc                                                                                                                               
&#9500;&#9472;sdc1          vfat        AE83-39F2                              3b8cc85a-6473-42cc-9c16-7c1bf5d9537c                           
&#9500;&#9472;sdc2          vfat        AE83-3AB9                              4023464c-9330-4d81-b6ee-636718e674e8                           recovery
&#9500;&#9472;sdc3          crypto_LUKS 4258a38c-cac3-4cc2-8b31-460f6b494270   0fd9b9dd-b27b-4d93-864e-3c432f888ae9                           
&#9474; &#9492;&#9472;myvolume    LVM2_member p37m3i-j9oz-gZOQ-2KKN-w931-JtYA-8ExZ1d                                                                
&#9474;   &#9492;&#9472;data-root ext4        21546503-6099-4165-ba45-1cc1c5f0ece6                                                                  
&#9492;&#9472;sdc4          swap        366d2418-6b3f-4307-9808-364ba9ec0af6   fab0371d-2447-4d16-84b3-21dc5bb6c9cd                           
sdd                                                                                                                               
&#9492;&#9472;sdd3          ext4        9f626842-0d28-4815-906c-653ab5300f12   47944e4f-7b0f-4b41-9d73-f89180564d53 Games                     Games
sde             iso9660     2022-08-31-06-00-25-00                                                      Pop_OS 22.04 amd64 Nvidia 
&#9500;&#9472;sde1          iso9660     2022-08-31-06-00-25-00                 58d50179-01                          Pop_OS 22.04 amd64 Nvidia 
&#9500;&#9472;sde2          vfat        8F2A-97C8                              58d50179-02                                                    
&#9492;&#9472;sde3          ext4        cc70870e-9a61-4396-8513-2d6c73318cf2   58d50179-03                          writable                  

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/disk/by-label/writable[/install-logs-2022-09-22.4/crash]  24.1G   0% /var/crash
/dev/disk/by-label/writable[/install-logs-2022-09-22.4/log]    24.1G   0% /var/log
/dev/mapper/data-root                                         325.6G  22% /mnt/boot-sav/mapper/data-root
/dev/sda1                                                     119.1G   0% /mnt/boot-sav/sda1
/dev/sdb2                                                       1.1T   0% /mnt/boot-sav/sdb2
/dev/sdb3                                                       1.4T  39% /mnt/boot-sav/sdb3
/dev/sdc1                                                      98.5M  80% /mnt/boot-sav/sdc1
/dev/sdc2                                                     973.4M  76% /mnt/boot-sav/sdc2
/dev/sdd3                                                     703.7G  18% /mnt/boot-sav/sdd3
/dev/sde1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/disk/by-label/writable[/install-logs-2022-09-22.4/crash] ext4            rw,relatime
/dev/disk/by-label/writable[/install-logs-2022-09-22.4/log]   ext4            rw,relatime
/dev/mapper/data-root                                         ext4            rw,relatime
/dev/sda1                                                     fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdb2                                                     fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdb3                                                     ext4            rw,relatime
/dev/sdc1                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sdc2                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sdd3                                                     ext4            rw,relatime
/dev/sde1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8

============================== ls -R /dev/mapper/ ==============================

/dev/mapper:
control
data-root
myvolume

======================= sdc1/efi/pop/grub.cfg (filtered) =======================

search.fs_uuid 21546503-6099-4165-ba45-1cc1c5f0ece6 root lvmid/AdaPI3-9snE-3rsI-NQSi-M19S-p24X-t0mr35/bZANi6-T0eM-mulS-dl3q-0e46-CSki-hJ9m6u 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

================================= User choice ==================================

Is there RAID on this computer? no


==================== blkid (filtered) before lvm activation ====================

/dev/sda1: LABEL="Windows" BLOCK_SIZE="512" UUID="197BF7E21A658BBB" TYPE="ntfs" PARTUUID="03c6ce02-01"
/dev/sdb2: LABEL="windows files" BLOCK_SIZE="512" UUID="6A47CD4E5645470A" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="757ba89e-b860-48a2-a1cf-8d27014a604c"
/dev/sdb3: LABEL="D" UUID="1fa3f0ff-92e2-4900-9bb5-45e5950b9b48" BLOCK_SIZE="4096" TYPE="ext4" PARTLABEL="Storage" PARTUUID="e1c1de8a-ae40-452e-b360-7205e269358a"
/dev/sdc1: UUID="AE83-39F2" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="3b8cc85a-6473-42cc-9c16-7c1bf5d9537c"
/dev/sdc2: UUID="AE83-3AB9" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="recovery" PARTUUID="4023464c-9330-4d81-b6ee-636718e674e8"
/dev/sdd3: LABEL="Games" UUID="9f626842-0d28-4815-906c-653ab5300f12" BLOCK_SIZE="4096" TYPE="ext4" PARTLABEL="Games" PARTUUID="47944e4f-7b0f-4b41-9d73-f89180564d53"
/dev/sde1: BLOCK_SIZE="2048" UUID="2022-08-31-06-00-25-00" LABEL="Pop_OS 22.04 amd64 Nvidia" TYPE="iso9660" PTUUID="58d50179" PTTYPE="dos" PARTUUID="58d50179-01"
/dev/sde2: SEC_TYPE="msdos" UUID="8F2A-97C8" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="58d50179-02"
/dev/sde3: LABEL="writable" UUID="cc70870e-9a61-4396-8513-2d6c73318cf2" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="58d50179-03"
/dev/sdc3: UUID="4258a38c-cac3-4cc2-8b31-460f6b494270" TYPE="crypto_LUKS" PARTUUID="0fd9b9dd-b27b-4d93-864e-3c432f888ae9"
/dev/sdc4: UUID="366d2418-6b3f-4307-9808-364ba9ec0af6" TYPE="swap" PARTUUID="fab0371d-2447-4d16-84b3-21dc5bb6c9cd"
/dev/mapper/data-root: UUID="21546503-6099-4165-ba45-1cc1c5f0ece6" BLOCK_SIZE="4096" TYPE="ext4"
/dev/mapper/myvolume: UUID="p37m3i-j9oz-gZOQ-2KKN-w931-JtYA-8ExZ1d" TYPE="LVM2_member"
/dev/sdb1: PARTLABEL="Microsoft reserved partition" PARTUUID="855b799e-7550-4f98-a707-de3bc719be1f"


================================ LVM activation ================================

modprobe dm-mod  
vgscan --mknodes
  Found volume group "data" using metadata type lvm2
vgchange -ay
  1 logical volume(s) in volume group "data" now active
lvscan
  ACTIVE            '/dev/data/root' [457.25 GiB] inherit
blkid -g



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge (in order to enable-lvm) and reinstall the grub-efi of
mapper/data-root,
using the following options:  sdc1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups

Confirmation request before suggested repair: __________________________________

You may want to retry after mounting your encrypted partitions so that the tool can verify their contents. (sudo cryptsetup luksOpen /dev/sdc3 myvolume)
Are you sure you want to continue anyway?

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Pop!_OS 22.04 LTS (22.04) entry (sdc1/efi/****/grub****.efi (**** will be updated in the final message) file) !

```
Error that I get when i try to use Boot-repair.
```
An error occurred during the repair.
Error: NVram is locked (Pop not found in efibootmgr). 
```

---

### Post by chunkypuding on 2022-09-22
I could not post post repair summary in my first post.
So here it is.
```
boot-repair-4ppa200                                              [20220922_1656]

============================= Boot Repair Summary ==============================

User choice:

Is there RAID on this computer? no


==================== blkid (filtered) before lvm activation ====================

/dev/sda1: LABEL="Windows" BLOCK_SIZE="512" UUID="197BF7E21A658BBB" TYPE="ntfs" PARTUUID="03c6ce02-01"
/dev/sdb2: LABEL="windows files" BLOCK_SIZE="512" UUID="6A47CD4E5645470A" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="757ba89e-b860-48a2-a1cf-8d27014a604c"
/dev/sdb3: LABEL="D" UUID="1fa3f0ff-92e2-4900-9bb5-45e5950b9b48" BLOCK_SIZE="4096" TYPE="ext4" PARTLABEL="Storage" PARTUUID="e1c1de8a-ae40-452e-b360-7205e269358a"
/dev/sdc1: UUID="AE83-39F2" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="3b8cc85a-6473-42cc-9c16-7c1bf5d9537c"
/dev/sdc2: UUID="AE83-3AB9" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="recovery" PARTUUID="4023464c-9330-4d81-b6ee-636718e674e8"
/dev/sdd3: LABEL="Games" UUID="9f626842-0d28-4815-906c-653ab5300f12" BLOCK_SIZE="4096" TYPE="ext4" PARTLABEL="Games" PARTUUID="47944e4f-7b0f-4b41-9d73-f89180564d53"
/dev/sde1: BLOCK_SIZE="2048" UUID="2022-08-31-06-00-25-00" LABEL="Pop_OS 22.04 amd64 Nvidia" TYPE="iso9660" PTUUID="58d50179" PTTYPE="dos" PARTUUID="58d50179-01"
/dev/sde2: SEC_TYPE="msdos" UUID="8F2A-97C8" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="58d50179-02"
/dev/sde3: LABEL="writable" UUID="cc70870e-9a61-4396-8513-2d6c73318cf2" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="58d50179-03"
/dev/sdc3: UUID="4258a38c-cac3-4cc2-8b31-460f6b494270" TYPE="crypto_LUKS" PARTUUID="0fd9b9dd-b27b-4d93-864e-3c432f888ae9"
/dev/sdc4: UUID="366d2418-6b3f-4307-9808-364ba9ec0af6" TYPE="swap" PARTUUID="fab0371d-2447-4d16-84b3-21dc5bb6c9cd"
/dev/mapper/data-root: UUID="21546503-6099-4165-ba45-1cc1c5f0ece6" BLOCK_SIZE="4096" TYPE="ext4"
/dev/mapper/myvolume: UUID="p37m3i-j9oz-gZOQ-2KKN-w931-JtYA-8ExZ1d" TYPE="LVM2_member"
/dev/sdb1: PARTLABEL="Microsoft reserved partition" PARTUUID="855b799e-7550-4f98-a707-de3bc719be1f"


================================ LVM activation ================================

modprobe dm-mod  
vgscan --mknodes
  Found volume group "data" using metadata type lvm2
vgchange -ay
  1 logical volume(s) in volume group "data" now active
lvscan
  ACTIVE            '/dev/data/root' [457.25 GiB] inherit
blkid -g




[dmraid -sa -c] no
[dmraid -sa -c] raid
[dmraid -sa -c] disks
[dmraid -sa -c] no
[dmraid -sa -c] raid
[dmraid -sa -c] disks

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will purge (in order to enable-lvm) and reinstall the grub-efi of
mapper/data-root,
using the following options:  sdc1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups


rm /mnt/boot-sav/sdc1/efi/Boot/bootx64.efi
mv /mnt/boot-sav/sdc1/efi/Boot/bkpbootx64.efi /mnt/boot-sav/sdc1/efi/Boot/bootx64.efi
Mount sdc1 on /mnt/boot-sav/mapper/data-root/boot/efi
No mapper/data-root/boot/efi/efi/ ubuntu/mint folder
chroot /mnt/boot-sav/mapper/data-root apt-get -y update
Purge the GRUB of mapper/data-root
grub-efi available

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 21 not upgraded.
DEBCHECK debOK, grub-efi
DEBCHECK debOK
Please type: sudo chroot "/mnt/boot-sav/mapper/data-root" dpkg --configure -ansudo chroot "/mnt/boot-sav/mapper/data-root" apt-get install -fynsudo chroot "/mnt/boot-sav/mapper/data-root" apt-get install -y lvm2nsudo chroot "/mnt/boot-sav/mapper/data-root" apt-get purge --allow-remove-essential -y grub-com*nsudo chroot "/mnt/boot-sav/mapper/data-root" apt-get purge --allow-remove-essential -y grub2-com*nsudo chroot "/mnt/boot-sav/mapper/data-root" apt-get purge --allow-remove-essential -y shim-signednsudo chroot "/mnt/boot-sav/mapper/data-root" apt-get purge --allow-remove-essential -y grub-common:*nsudo chroot "/mnt/boot-sav/mapper/data-root" apt-get purge --allow-remove-essential -y grub2-common:*n
Then type: sudo chroot "/mnt/boot-sav/mapper/data-root" apt-get install -y grub-efi

Unhide GRUB boot menu in mapper/data-root/etc/default/grub

================== Reinstall the grub-efi of mapper/data-root ==================

chroot /mnt/boot-sav/mapper/data-root grub-install --version
grub-install (GRUB) 2.06-2ubuntu7
chroot /mnt/boot-sav/mapper/data-root modprobe efivars

chroot /mnt/boot-sav/mapper/data-root efibootmgr -v before grub install
BootCurrent: 0003
Timeout: 1 seconds
BootOrder: 0003,0004,0005,0002,0001
Boot0001* Hard Drive    BBS(HD,,0x0)..GO..NO........u.P.L.E.X.T.O.R. .P.X.-.1.2.8.M.5.S....................A.................................>..Gd-.;.A..MQ..L.0.P.3.2.9.3.0.1.6.3.4.7. . . . . . . . ........BO..NO........u.S.T.4.0.0.0.D.M.0.0.5.-.2.D.P.1.6.6....................A.................................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .D.Z.2.H.4.S.D.J........BO..NO........u.S.a.m.s.u.n.g. .S.S.D. .8.6.0. .E.V.O. .5.0.0.G.B....................A.................................>..Gd-.;.A..MQ..L.3.S.2.Z.B.N.K.0.9.1.9.2.2.7. .F. . . . ........BO..NO........u.S.a.m.s.u.n.g. .S.S.D. .8.6.0. .E.V.O. .1.T.B....................A.................................>..Gd-.;.A..MQ..L.3.S.9.Z.X.N.N.0.0.3.0.5.4.8. .E. . . . ........BO
Boot0002* Windows Boot Manager    HD(1,GPT,3b8cc85a-6473-42cc-9c16-7c1bf5d9537c,0x1000,0xf8fff)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)..BO
Boot0003* UEFI: SMI USB DISK 1100    PciRoot(0x0)/Pci(0x1,0x3)/Pci(0x0,0x0)/USB(2,0)/CDROM(1,0x1e4,0x8000)..BO
Boot0004* UEFI: SMI USB DISK 1100, Partition 2    PciRoot(0x0)/Pci(0x1,0x3)/Pci(0x0,0x0)/USB(2,0)/HD(2,MBR,0x58d50179,0x1e4,0x2000)..BO
Boot0005* USB    BBS(HD,,0x0)..GO..NO........q.S.M.I. .U.S.B. .D.I.S.K. .1.1.0.0....................A.............................>..Gd-.;.A..MQ..L.C.C.Y.Y.M.M.D.D.H.H.m.m.S.S.T.1.7.6.J.I........BO

chroot /mnt/boot-sav/mapper/data-root uname -r
5.19.0-76051900-generic

chroot /mnt/boot-sav/mapper/data-root grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 66972: grub-install
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 66972: grub-install
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/sdc1
mv /mnt/boot-sav/mapper/data-root/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/mapper/data-root/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/mapper/data-root/boot/efi/efi/pop/grubx64.efi /mnt/boot-sav/mapper/data-root/boot/efi/EFI/Boot/bootx64.efi

chroot /mnt/boot-sav/mapper/data-root grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67178: grub-install
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67178: grub-install
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.

chroot /mnt/boot-sav/mapper/data-root efibootmgr -v after grub install
BootCurrent: 0003
Timeout: 1 seconds
BootOrder: 0003,0004,0005,0002,0001
Boot0001* Hard Drive    BBS(HD,,0x0)..GO..NO........u.P.L.E.X.T.O.R. .P.X.-.1.2.8.M.5.S....................A.................................>..Gd-.;.A..MQ..L.0.P.3.2.9.3.0.1.6.3.4.7. . . . . . . . ........BO..NO........u.S.T.4.0.0.0.D.M.0.0.5.-.2.D.P.1.6.6....................A.................................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .D.Z.2.H.4.S.D.J........BO..NO........u.S.a.m.s.u.n.g. .S.S.D. .8.6.0. .E.V.O. .5.0.0.G.B....................A.................................>..Gd-.;.A..MQ..L.3.S.2.Z.B.N.K.0.9.1.9.2.2.7. .F. . . . ........BO..NO........u.S.a.m.s.u.n.g. .S.S.D. .8.6.0. .E.V.O. .1.T.B....................A.................................>..Gd-.;.A..MQ..L.3.S.9.Z.X.N.N.0.0.3.0.5.4.8. .E. . . . ........BO
Boot0002* Windows Boot Manager    HD(1,GPT,3b8cc85a-6473-42cc-9c16-7c1bf5d9537c,0x1000,0xf8fff)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)..BO
Boot0003* UEFI: SMI USB DISK 1100    PciRoot(0x0)/Pci(0x1,0x3)/Pci(0x0,0x0)/USB(2,0)/CDROM(1,0x1e4,0x8000)..BO
Boot0004* UEFI: SMI USB DISK 1100, Partition 2    PciRoot(0x0)/Pci(0x1,0x3)/Pci(0x0,0x0)/USB(2,0)/HD(2,MBR,0x58d50179,0x1e4,0x2000)..BO
Boot0005* USB    BBS(HD,,0x0)..GO..NO........q.S.M.I. .U.S.B. .D.I.S.K. .1.1.0.0....................A.............................>..Gd-.;.A..MQ..L.C.C.Y.Y.M.M.D.D.H.H.m.m.S.S.T.1.7.6.J.I........BO
Error: NVram is locked (Pop not found in efibootmgr). Please report this message to boot.repair@gmail.com

chroot /mnt/boot-sav/mapper/data-root update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67256: grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67256: grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67278: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67278: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67282: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67282: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67285: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67285: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67289: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67289: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67326: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67326: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-5.19.0-76051900-generic
Found initrd image: /boot/initrd.img-5.19.0-76051900-generic
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67424: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67424: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67428: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67428: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67432: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67432: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67436: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 67436: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-5.18.10-76051810-generic
Found initrd image: /boot/initrd.img-5.18.10-76051810-generic
Found linux image: /boot/vmlinuz-5.17.15-76051715-generic
Found initrd image: /boot/initrd.img-5.17.15-76051715-generic
Found linux image: /boot/vmlinuz-5.16.15-76051615-generic
Found initrd image: /boot/initrd.img-5.16.15-76051615-generic
Found linux image: /boot/vmlinuz-5.16.11-76051611-generic
Found initrd image: /boot/initrd.img-5.16.11-76051611-generic
Found linux image: /boot/vmlinuz-5.15.23-76051523-generic
Found initrd image: /boot/initrd.img-5.15.23-76051523-generic
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 68244: /usr/sbin/grub-probe
File descriptor 63 (pipe:[268481]) leaked on vgs invocation. Parent PID 68244: /usr/sbin/grub-probe
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
grub-probe: error: cannot find a GRUB drive for /dev/sde1.  Check your device.map.
Found Windows Boot Manager on /dev/sdc1@/EFI/Microsoft/Boot/bootmgfw.efi

Unhide GRUB boot menu in mapper/data-root/boot/grub/grub.cfg

An error occurred during the repair.
Error: NVram is locked (Pop not found in efibootmgr). Please report this message to boot.repair@gmail.com

Locked-NVram detected.


============================ Boot Info After Repair ============================

 => libparted MBR boot code is installed in the MBR of /dev/sda.
 => Windows 7/8/10/11/2012 is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Windows 7/8/10/11/2012 is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/Pop_OS-21546503-6099-4165-ba45-1cc1c5f0ece6/vmlinu
                       z-previous.efi 
                       /efi/Pop_OS-21546503-6099-4165-ba45-1cc1c5f0ece6/vmlinu
                       z.efi /efi/Recovery-AE83-3AB9/vmlinuz.efi 
                       /efi/pop/grubx64.efi /efi/systemd/systemd-bootx64.efi 
                       /efi/pop/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

sdc2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 

sdc4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdd3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sde: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sde: /dev/sde already mounted or mount point busy.


================================ 1 OS detected =================================

OS#1:   Pop!_OS 22.04 LTS (22.04) on mapper/data-root

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GA102 [GeForce RTX 3090] EFI VGA from NVIDIA Corporation
Live-session OS is Pop 64-bit (Pop!_OS 22.04 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 5602(5.13) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled - SecureBoot disabled - Please report this message to boot.repair@gmail.com.
BootCurrent: 0003
Timeout: 1 seconds
BootOrder: 0003,0004,0005,0002,0001
Boot0001* Hard Drive    BBS(HD,,0x0)..GO..NO........u.P.L.E.X.T.O.R. .P.X.-.1.2.8.M.5.S....................A.................................>..Gd-.;.A..MQ..L.0.P.3.2.9.3.0.1.6.3.4.7. . . . . . . . ........BO..NO........u.S.T.4.0.0.0.D.M.0.0.5.-.2.D.P.1.6.6....................A.................................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .D.Z.2.H.4.S.D.J........BO..NO........u.S.a.m.s.u.n.g. .S.S.D. .8.6.0. .E.V.O. .5.0.0.G.B....................A.................................>..Gd-.;.A..MQ..L.3.S.2.Z.B.N.K.0.9.1.9.2.2.7. .F. . . . ........BO..NO........u.S.a.m.s.u.n.g. .S.S.D. .8.6.0. .E.V.O. .1.T.B....................A.................................>..Gd-.;.A..MQ..L.3.S.9.Z.X.N.N.0.0.3.0.5.4.8. .E. . . . ........BO
Boot0002* Windows Boot Manager    HD(1,GPT,3b8cc85a-6473-42cc-9c16-7c1bf5d9537c,0x1000,0xf8fff)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)..BO
Boot0003* UEFI: SMI USB DISK 1100    PciRoot(0x0)/Pci(0x1,0x3)/Pci(0x0,0x0)/USB(2,0)/CDROM(1,0x1e4,0x8000)..BO
Boot0004* UEFI: SMI USB DISK 1100, Partition 2    PciRoot(0x0)/Pci(0x1,0x3)/Pci(0x0,0x0)/USB(2,0)/HD(2,MBR,0x58d50179,0x1e4,0x2000)..BO
Boot0005* USB    BBS(HD,,0x0)..GO..NO........q.S.M.I. .U.S.B. .D.I.S.K. .1.1.0.0....................A.............................>..Gd-.;.A..MQ..L.C.C.Y.Y.M.M.D.D.H.H.m.m.S.S.T.1.7.6.J.I........BO

f62c28d9b477b6a1a7b1c991b2b6637d   sdc1/BOOT/bkpbootx64.efi
f62c28d9b477b6a1a7b1c991b2b6637d   sdc1/BOOT/bootx64.efi
72499c6e5ffb05fcef2bcb75d1a6c15d   sdc1/Pop_OS-21546503-6099-4165-ba45-1cc1c5f0ece6/vmlinuz-previous.efi
76b642d1f9dd193d7ab09d2a299d1c96   sdc1/Pop_OS-21546503-6099-4165-ba45-1cc1c5f0ece6/vmlinuz.efi
d32b1a522d11d5680bfc6d9956d770a6   sdc1/Recovery-AE83-3AB9/vmlinuz.efi
f62c28d9b477b6a1a7b1c991b2b6637d   sdc1/pop/grubx64.efi
ef9a21484cc40834aeb42f88f2c6c4e0   sdc1/systemd/systemd-bootx64.efi
3ff213addd49e6515922de34952223ad   sdc1/Microsoft/Boot/bootmgfw.efi
b8736f6dbf1baf951d389be5a519fb32   sdc1/Microsoft/Boot/bootmgr.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
sdb    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    34 sectors * 512 bytes
sdc    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes
sdd    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdb2    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdb3    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdc1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdc2    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdd3    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
mapper/data-root    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    not-far

Partitions info (2/3): _________________________________________________________

sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdd3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
mapper/data-root    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sdb2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdb3    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdc1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdd3    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdd
mapper/data-root    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 119.24 GiB, 128035676160 bytes, 250069680 sectors
Disk identifier: 0x03c6ce02
      Boot Start       End   Sectors   Size Id Type
sda1  *     2048 250068991 250066944 119.2G  7 HPFS/NTFS/exFAT
Disk sdb: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors
Disk identifier: F6BA9AF6-82A9-4698-BA52-23B5B609D558
           Start        End    Sectors  Size Type
sdb1          34      32767      32734   16M Microsoft reserved
sdb2       32768 2434574335 2434541568  1.1T Microsoft basic data
sdb3  2434574336 7814035455 5379461120  2.5T Linux filesystem
Disk sdc: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 237DDB54-C5CE-464F-BC17-0B47DEE71B2F
          Start       End   Sectors   Size Type
sdc1       4096   1023998   1019903   498M EFI System
sdc2    1024000   9412606   8388607     4G Microsoft basic data
sdc3    9412608 968380460 958967853 457.3G Linux filesystem
sdc4  968380464 976769070   8388607     4G Linux swap
Disk sdd: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 08606813-0580-4F9D-A09A-DE028C5490E5
      Start        End    Sectors   Size Type
sdd3   2048 1953521663 1953519616 931.5G Linux filesystem
Disk sde: 29.44 GiB, 31611420672 bytes, 61741056 sectors
Disk identifier: 0x58d50179
      Boot   Start      End  Sectors  Size Id Type
sde1  *          0  6991807  6991808  3.3G  0 Empty
sde2           484     8675     8192    4M ef EFI (FAT-12/16/32)
sde3       6991872 61741055 54749184 26.1G 83 Linux
Disk mapper/myvolume: 457.26 GiB, 490974763520 bytes, 958935085 sectors
Disk mapper/data-root: 457.25 GiB, 490972643328 bytes, 958930944 sectors

parted -lm (filtered): _________________________________________________________

sda:128GB:scsi:512:512:msdos:ATA PLEXTOR PX-128M5:;
1:1049kB:128GB:128GB:ntfs::boot;
sdb:4001GB:scsi:512:4096:gpt:ATA ST4000DM005-2DP1:;
1:17.4kB:16.8MB:16.8MB::Microsoft reserved partition:msftres;
2:16.8MB:1247GB:1246GB:ntfs:Basic data partition:msftdata;
3:1247GB:4001GB:2754GB:ext4:Storage:;
sdc:500GB:scsi:512:512:gpt:ATA Samsung SSD 860:;
1:2097kB:524MB:522MB:fat32::boot, esp;
2:524MB:4819MB:4295MB:fat32:recovery:msftdata;
3:4819MB:496GB:491GB:::;
4:496GB:500GB:4295MB:linux-swap(v1)::swap;
sdd:1000GB:scsi:512:512:gpt:ATA Samsung SSD 860:;
3:1049kB:1000GB:1000GB:ext4:Games:;
sde:31.6GB:scsi:512:512:msdos:SMI USB DISK:;
2:248kB:4442kB:4194kB:::esp;
3:3580MB:31.6GB:28.0GB:ext4::;
mapper/data-root:491GB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:491GB:491GB:ext4::;
mapper/myvolume:491GB:dm:512:512:unknown:Linux device-mapper (crypt):;

Free space >10MiB: ______________________________________________________________

sde: 4.24MiB:3414MiB:3410MiB

blkid (filtered): ______________________________________________________________

NAME            FSTYPE      UUID                                   PARTUUID                             LABEL                     PARTLABEL
sda                                                                                                                               
&#9492;&#9472;sda1          ntfs        197BF7E21A658BBB                       03c6ce02-01                          Windows                   
sdb                                                                                                                               
&#9500;&#9472;sdb1                                                             855b799e-7550-4f98-a707-de3bc719be1f                           Microsoft reserved partition
&#9500;&#9472;sdb2          ntfs        6A47CD4E5645470A                       757ba89e-b860-48a2-a1cf-8d27014a604c windows files             Basic data partition
&#9492;&#9472;sdb3          ext4        1fa3f0ff-92e2-4900-9bb5-45e5950b9b48   e1c1de8a-ae40-452e-b360-7205e269358a D                         Storage
sdc                                                                                                                               
&#9500;&#9472;sdc1          vfat        AE83-39F2                              3b8cc85a-6473-42cc-9c16-7c1bf5d9537c                           
&#9500;&#9472;sdc2          vfat        AE83-3AB9                              4023464c-9330-4d81-b6ee-636718e674e8                           recovery
&#9500;&#9472;sdc3          crypto_LUKS 4258a38c-cac3-4cc2-8b31-460f6b494270   0fd9b9dd-b27b-4d93-864e-3c432f888ae9                           
&#9474; &#9492;&#9472;myvolume    LVM2_member p37m3i-j9oz-gZOQ-2KKN-w931-JtYA-8ExZ1d                                                                
&#9474;   &#9492;&#9472;data-root ext4        21546503-6099-4165-ba45-1cc1c5f0ece6                                                                  
&#9492;&#9472;sdc4          swap        366d2418-6b3f-4307-9808-364ba9ec0af6   fab0371d-2447-4d16-84b3-21dc5bb6c9cd                           
sdd                                                                                                                               
&#9492;&#9472;sdd3          ext4        9f626842-0d28-4815-906c-653ab5300f12   47944e4f-7b0f-4b41-9d73-f89180564d53 Games                     Games
sde             iso9660     2022-08-31-06-00-25-00                                                      Pop_OS 22.04 amd64 Nvidia 
&#9500;&#9472;sde1          iso9660     2022-08-31-06-00-25-00                 58d50179-01                          Pop_OS 22.04 amd64 Nvidia 
&#9500;&#9472;sde2          vfat        8F2A-97C8                              58d50179-02                                                    
&#9492;&#9472;sde3          ext4        cc70870e-9a61-4396-8513-2d6c73318cf2   58d50179-03                          writable                  

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/disk/by-label/writable[/install-logs-2022-09-22.4/crash]  24.1G   0% /var/crash
/dev/disk/by-label/writable[/install-logs-2022-09-22.4/log]    24.1G   0% /var/log
/dev/mapper/data-root                                         325.6G  22% /mnt/boot-sav/mapper/data-root
/dev/sda1                                                     119.1G   0% /mnt/boot-sav/sda1
/dev/sdb2                                                       1.1T   0% /mnt/boot-sav/sdb2
/dev/sdb3                                                       1.4T  39% /mnt/boot-sav/sdb3
/dev/sdc1                                                      98.5M  80% /mnt/boot-sav/sdc1
/dev/sdc2                                                     973.4M  76% /mnt/boot-sav/sdc2
/dev/sdd3                                                     703.7G  18% /mnt/boot-sav/sdd3
/dev/sde1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/disk/by-label/writable[/install-logs-2022-09-22.4/crash] ext4            rw,relatime
/dev/disk/by-label/writable[/install-logs-2022-09-22.4/log]   ext4            rw,relatime
/dev/mapper/data-root                                         ext4            rw,relatime
/dev/sda1                                                     fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdb2                                                     fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdb3                                                     ext4            rw,relatime
/dev/sdc1                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sdc2                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sdd3                                                     ext4            rw,relatime
/dev/sde1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8

============================== ls -R /dev/mapper/ ==============================

/dev/mapper:
control
data-root
myvolume

======================= sdc1/efi/pop/grub.cfg (filtered) =======================

search.fs_uuid 21546503-6099-4165-ba45-1cc1c5f0ece6 root lvmid/AdaPI3-9snE-3rsI-NQSi-M19S-p24X-t0mr35/bZANi6-T0eM-mulS-dl3q-0e46-CSki-hJ9m6u 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

---

### Post by howefield on 2022-09-22
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by oldfred on 2022-09-22
Forum does not like very large data posts.
You should follow Boot-Repair's suggestion of posting just the link to the Summary Report on the pastebin site.

You have to decrypt your install for Boot-Repair to work.
And may have to use advanced mode, so you can select sdc drive as drive you want UEFI boot files installed into.

Lock issue, is probably an UEFI setting, please update UEFI & review UEFI setting.
what brand/model system?
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)

Your sda is an old BIOS/MBR configuration.
UEFI & BIOS are not compatible. You may be able to boot sda, only by changing UEFI settings to CSM/Legacy/BIOS.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

---

