---
title: "Bootmanager moved Ubuntu on Windows Partition"
date: 2024-03-03
forum: Ubuntu/Debian BASED
---

### Post by kapyrus on 2024-03-03
Hi, 

From one boot to another my BIOS suddenly thinks that my ubuntu is on NVME0n1, where Windows is installed, instead of NVME1n1. 

I ran bootrepair, which is not able to fix my issue because of locked NVRAM. Found other threads about it, but those did not work for me.

I post the whole summary, but first the important part of it. BOOT004 is my Ubuntu distro, its pointing on UUID of WIndows (BOOT005):

```
BIOS/UEFI firmware: N.1.07A01(5.19) from American Megatrends International, LLC.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 000C
Timeout: 0 seconds
BootOrder: 0004,000B,000C,000D,0002,0003,0000,000E
Boot0000  Pop!_OS 21.10    HD(1,GPT,2d5b1612-6792-4cf7-aba9-67dedf4d1b6e,0x800,0x12e000)/File(\EFI\SYSTEMD\SYSTEMD-BOOTX64.EFI)
Boot0002  UEFI: PXE IPv4 Realtek PCIe 2.5GBE Family Controller    PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(b025aa449ce5,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot0003  UEFI: PXE IPv6 Realtek PCIe 2.5GBE Family Controller    PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(b025aa449ce5,0)/IPv6([::]:<->[::]:,0,0)..BO
Boot0004* Pop!_OS 22.04 LTS    HD(1,GPT,2d5b1612-6792-4cf7-aba9-67dedf4d1b6e,0x800,0x12e000)/File(\EFI\SYSTEMD\SYSTEMD-BOOTX64.EFI)
Boot000B* Windows Boot Manager    HD(1,GPT,2d5b1612-6792-4cf7-aba9-67dedf4d1b6e,0x800,0x12e000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)..BO
Boot000C* UEFI: Generic-SD/MMC 1.00    PciRoot(0x0)/Pci(0x14,0x0)/USB(18,0)/CDROM(1,0x1e8,0x8000)..BO
Boot000D* UEFI: Generic-SD/MMC 1.00, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(18,0)/HD(2,MBR,0x7251d6df,0x1e8,0x2000)..BO
Boot000E  Windows Boot Manager    HD(3,GPT,36b5e4ff-55cf-11ec-9015-845cf33541bf,0x3a258000,0x12dffd)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)..BO

a217aa02bc9c05db5177fbffe8689859   nvme0n1p1/BOOT/bkpbootx64.efi
a1da253696a304dce6b4668b70151c0e   nvme0n1p1/BOOT/bootx64.efi
1c8c6bc9e0b5877341c47d0629ddf928   nvme0n1p1/Pop_OS-88150b98-ddcd-47bb-bb2c-510a0aa6b9aa/vmlinuz-previous.efi
b8d66fb6d7dc730ef05463927f9c7a63   nvme0n1p1/Pop_OS-88150b98-ddcd-47bb-bb2c-510a0aa6b9aa/vmlinuz.efi
a1da253696a304dce6b4668b70151c0e   nvme0n1p1/pop/grubx64.efi
a217aa02bc9c05db5177fbffe8689859   nvme0n1p1/systemd/systemd-bootx64.efi
df480f092e56b632513b4616bdeade95   nvme0n1p1/Microsoft/Boot/bootmgfw.efi
0a70ebdfe73694eb6188f70e81b47a79   nvme0n1p1/Microsoft/Boot/bootmgr.efi
a1da253696a304dce6b4668b70151c0e   nvme1n1p3/BOOT/bkpbootx64.efi
a1da253696a304dce6b4668b70151c0e   nvme1n1p3/BOOT/bootx64.efi
1c8c6bc9e0b5877341c47d0629ddf928   nvme1n1p3/Pop_OS-88150b98-ddcd-47bb-bb2c-510a0aa6b9aa/vmlinuz-previous.efi
b8d66fb6d7dc730ef05463927f9c7a63   nvme1n1p3/Pop_OS-88150b98-ddcd-47bb-bb2c-510a0aa6b9aa/vmlinuz.efi
a1da253696a304dce6b4668b70151c0e   nvme1n1p3/pop/grubx64.efi
b2a00c1874d22aa1585ad4ab34f9094a   nvme1n1p3/systemd/systemd-bootx64.efi
2efa3903d89ff64f51dec6ed96e40941   nvme1n1p3/Microsoft/Boot/bootmgfw.efi
edad6ce3a0215d232e1f8ee172737d1a   nvme1n1p3/Microsoft/Boot/bootmgr.efi
```

Do I need to unlock my nvram, or is there a different route to take?

Heres my complete summary:

```
boot-repair-4ppa2075                                              [20240303_1500]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => No boot loader is installed in the MBR of /dev/nvme1n1.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, nvme0n1p1 
                       starts at sector 975536128. But according to the info 
                       from fdisk, nvme0n1p1 starts at sector 2048.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/Pop_OS-88150b98-ddcd-47bb-bb2c-510a0aa6b9aa/vmlinu
                       z-previous.efi 
                       /efi/Pop_OS-88150b98-ddcd-47bb-bb2c-510a0aa6b9aa/vmlinu
                       z.efi /efi/pop/grubx64.efi 
                       /efi/systemd/systemd-bootx64.efi 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

nvme0n1p2: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, nvme0n1p2 
                       starts at sector 2048. But according to the info from 
                       fdisk, nvme0n1p2 starts at sector 1239040.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe

nvme1n1p1: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Pop!_OS 22.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

nvme1n1p2: _____________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

nvme1n1p3: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/Pop_OS-88150b98-ddcd-47bb-bb2c-510a0aa6b9aa/vmlinu
                       z-previous.efi 
                       /efi/Pop_OS-88150b98-ddcd-47bb-bb2c-510a0aa6b9aa/vmlinu
                       z.efi /efi/pop/grubx64.efi 
                       /efi/systemd/systemd-bootx64.efi /efi/pop/grub.cfg 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

sda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sda: /dev/sda already mounted or mount point busy.


================================ 2 OS detected =================================

OS#1:   Pop!_OS 22.04 LTS (22.04) on nvme1n1p1
OS#2:   Windows 10 or 11 on nvme0n1p2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GA104M [GeForce RTX 3080 Mobile / Max-Q 8GB/16GB] TigerLake-H GT1 [UHD Graphics] from NVIDIA Corporation Intel Corporation
Live-session OS is Pop 64-bit (Pop!_OS 22.04 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: N.1.07A01(5.19) from American Megatrends International, LLC.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 000C
Timeout: 0 seconds
BootOrder: 0004,000B,000C,000D,0002,0003,0000,000E
Boot0000  Pop!_OS 21.10    HD(1,GPT,2d5b1612-6792-4cf7-aba9-67dedf4d1b6e,0x800,0x12e000)/File(\EFI\SYSTEMD\SYSTEMD-BOOTX64.EFI)
Boot0002  UEFI: PXE IPv4 Realtek PCIe 2.5GBE Family Controller    PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(b025aa449ce5,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot0003  UEFI: PXE IPv6 Realtek PCIe 2.5GBE Family Controller    PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(b025aa449ce5,0)/IPv6([::]:<->[::]:,0,0)..BO
Boot0004* Pop!_OS 22.04 LTS    HD(1,GPT,2d5b1612-6792-4cf7-aba9-67dedf4d1b6e,0x800,0x12e000)/File(\EFI\SYSTEMD\SYSTEMD-BOOTX64.EFI)
Boot000B* Windows Boot Manager    HD(1,GPT,2d5b1612-6792-4cf7-aba9-67dedf4d1b6e,0x800,0x12e000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)..BO
Boot000C* UEFI: Generic-SD/MMC 1.00    PciRoot(0x0)/Pci(0x14,0x0)/USB(18,0)/CDROM(1,0x1e8,0x8000)..BO
Boot000D* UEFI: Generic-SD/MMC 1.00, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(18,0)/HD(2,MBR,0x7251d6df,0x1e8,0x2000)..BO
Boot000E  Windows Boot Manager    HD(3,GPT,36b5e4ff-55cf-11ec-9015-845cf33541bf,0x3a258000,0x12dffd)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)..BO

a217aa02bc9c05db5177fbffe8689859   nvme0n1p1/BOOT/bkpbootx64.efi
a1da253696a304dce6b4668b70151c0e   nvme0n1p1/BOOT/bootx64.efi
1c8c6bc9e0b5877341c47d0629ddf928   nvme0n1p1/Pop_OS-88150b98-ddcd-47bb-bb2c-510a0aa6b9aa/vmlinuz-previous.efi
b8d66fb6d7dc730ef05463927f9c7a63   nvme0n1p1/Pop_OS-88150b98-ddcd-47bb-bb2c-510a0aa6b9aa/vmlinuz.efi
a1da253696a304dce6b4668b70151c0e   nvme0n1p1/pop/grubx64.efi
a217aa02bc9c05db5177fbffe8689859   nvme0n1p1/systemd/systemd-bootx64.efi
df480f092e56b632513b4616bdeade95   nvme0n1p1/Microsoft/Boot/bootmgfw.efi
0a70ebdfe73694eb6188f70e81b47a79   nvme0n1p1/Microsoft/Boot/bootmgr.efi
a1da253696a304dce6b4668b70151c0e   nvme1n1p3/BOOT/bkpbootx64.efi
a1da253696a304dce6b4668b70151c0e   nvme1n1p3/BOOT/bootx64.efi
1c8c6bc9e0b5877341c47d0629ddf928   nvme1n1p3/Pop_OS-88150b98-ddcd-47bb-bb2c-510a0aa6b9aa/vmlinuz-previous.efi
b8d66fb6d7dc730ef05463927f9c7a63   nvme1n1p3/Pop_OS-88150b98-ddcd-47bb-bb2c-510a0aa6b9aa/vmlinuz.efi
a1da253696a304dce6b4668b70151c0e   nvme1n1p3/pop/grubx64.efi
b2a00c1874d22aa1585ad4ab34f9094a   nvme1n1p3/systemd/systemd-bootx64.efi
2efa3903d89ff64f51dec6ed96e40941   nvme1n1p3/Microsoft/Boot/bootmgfw.efi
edad6ce3a0215d232e1f8ee172737d1a   nvme1n1p3/Microsoft/Boot/bootmgr.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
nvme1n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p2    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
nvme1n1p1    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
nvme1n1p3    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p2    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme1n1p1    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme1n1p3    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme1n1p1    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme1n1
nvme1n1p3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme1n1

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 69F6527A-55CB-11EC-9014-845CF33541BF
           Start        End    Sectors   Size Type
nvme0n1p1    2048    1239039    1236992   604M EFI System
nvme0n1p2 1239040 1953525063 1952286024 930.9G Microsoft basic data
Disk nvme1n1: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 7D87D9EB-B75C-492B-8D91-EE78E7371502
             Start       End   Sectors   Size Type
nvme1n1p1      2048 959356927 959354880 457.5G Linux filesystem
nvme1n1p2 959356928 975536123  16179196   7.7G Linux swap
nvme1n1p3 975536128 976773116   1236989   604M EFI System
Disk sda: 29.72 GiB, 31914983424 bytes, 62333952 sectors
Disk identifier: 0x7251d6df
     Boot   Start      End  Sectors  Size Id Type
sda1  *          0  5931007  5931008  2.8G  0 Empty
sda2           488     8679     8192    4M ef EFI (FAT-12/16/32)
sda3       5931008 62333951 56402944 26.9G 83 Linux
Disk zram0: 16 GiB, 17179869184 bytes, 4194304 sectors

parted -lm (filtered): _________________________________________________________

sda:31.9GB:scsi:512:512:msdos:Generic- SD/MMC:;
2:250kB:4444kB:4194kB:::esp;
3:3037MB:31.9GB:28.9GB:ext4::;
nvme0n1:1000GB:nvme:512:512:gpt:Samsung SSD 980 PRO 1TB:;
1:1049kB:634MB:633MB:fat32::boot, esp;
2:634MB:1000GB:1000GB:ntfs::msftdata;
nvme1n1:500GB:nvme:512:512:gpt:Samsung SSD 980 500GB:;
1:1049kB:491GB:491GB:ext4::;
2:491GB:499GB:8284MB:linux-swap(v1)::swap;
3:499GB:500GB:633MB:fat32::boot, esp;

Free space >10MiB: ______________________________________________________________

sda: 4.24MiB:2896MiB:2892MiB

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                     PARTLABEL
sda         iso9660  2023-09-13-19-15-11-00                                                    Pop_OS 22.04 amd64 Nvidia 
&#9500;&#9472;sda1      iso9660  2023-09-13-19-15-11-00               7251d6df-01                          Pop_OS 22.04 amd64 Nvidia 
&#9500;&#9472;sda2      vfat     A38C-CAF4                            7251d6df-02                                                    
&#9492;&#9472;sda3      ext4     8ba939e2-1ea9-4509-9bf6-e475f2452790 7251d6df-03                          writable                  
nvme0n1                                                                                                                  
&#9500;&#9472;nvme0n1p1 vfat     69CC-6BC5                            2d5b1612-6792-4cf7-aba9-67dedf4d1b6e                           
&#9492;&#9472;nvme0n1p2 ntfs     6F7DE9AE344C57EF                     69f6527c-55cb-11ec-9014-845cf33541bf                           
nvme1n1                                                                                                                  
&#9500;&#9472;nvme1n1p1 ext4     88150b98-ddcd-47bb-bb2c-510a0aa6b9aa 0ddc8604-08d7-46b0-b417-9c69d9f14331                           
&#9500;&#9472;nvme1n1p2 swap     a6dfed6c-6202-4b05-a2bf-25feb1bbea1d 7a08cb6d-65ae-4bb5-b63a-bd0298687b53                           
&#9492;&#9472;nvme1n1p3 vfat     69CC-6BC5                            36b5e4ff-55cf-11ec-9015-845cf33541bf                           

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/nvme0n1p1                                                314.8M  48% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p2                                                219.2G  76% /mnt/boot-sav/nvme0n1p2
/dev/nvme1n1p1                                                 67.1G  80% /mnt/boot-sav/nvme1n1p1
/dev/nvme1n1p3                                                312.3M  48% /mnt/boot-sav/nvme1n1p3
/dev/sda1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/nvme0n1p1                                                vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/nvme0n1p2                                                fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/nvme1n1p1                                                ext4            rw,relatime,stripe=32
/dev/nvme1n1p3                                                vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8

=================== nvme1n1p1/boot/grub/grub.cfg (filtered) ====================

Pop GNU/Linux   88150b98-ddcd-47bb-bb2c-510a0aa6b9aa
Windows Boot Manager (on nvme0n1p1)   osprober-efi-69CC-6BC5
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme1n1p1/etc/fstab (filtered) ========================

# <file system>  <mount point>  <type>  <options>  <dump>  <pass>
/dev/nvme1n1p1  /  ext4  noatime,errors=remount-ro  0  1
/dev/nvme1n1p2  none  swap  sw  0  0
UUID=69CC-6BC5  /boot/efi       vfat    defaults      0       1

==================== nvme1n1p1/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=9
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="root=/dev/nvme1n1p1"
GRUB_DISABLE_OS_PROBER=false

================= nvme1n1p1: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
 138.573253632 = 148.791898112  boot/grub/grub.cfg                             1
 219.740882874 = 235.944976384  boot/vmlinuz                                   2
 224.618160248 = 241.181913088  boot/vmlinuz-5.19.0-76051900-generic           2
 214.746681213 = 230.582493184  boot/vmlinuz-6.0.12-76060006-generic           2
  31.480991364 = 33.802457088   boot/vmlinuz-6.0.6-76060006-generic            1
 275.248245239 = 295.545552896  boot/vmlinuz-6.2.0-76060200-generic            1
 352.420116425 = 378.408218624  boot/vmlinuz-6.2.6-76060206-generic            2
 224.915035248 = 241.500680192  boot/vmlinuz-6.4.6-76060406-generic            2
 219.740882874 = 235.944976384  boot/vmlinuz-6.6.10-76060610-generic           2
 224.915035248 = 241.500680192  boot/vmlinuz.old                               2
  73.219722748 = 78.619078656   boot/initrd.img                                4
 420.875972748 = 451.912134656  boot/initrd.img-5.19.0-76051900-generic        6
  92.831260681 = 99.676807168   boot/initrd.img-5.3.0-7648-generic             3
 325.500972748 = 349.504008192  boot/initrd.img-6.0.12-76060006-generic        6
 300.610347748 = 322.777903104  boot/initrd.img-6.0.6-76060006-generic         5
 440.688472748 = 473.185644544  boot/initrd.img-6.2.0-76060200-generic         6
 399.657222748 = 429.128675328  boot/initrd.img-6.2.6-76060206-generic         4
 448.375972748 = 481.440034816  boot/initrd.img-6.4.6-76060406-generic         6
  73.219722748 = 78.619078656   boot/initrd.img-6.6.10-76060610-generic        4
 448.375972748 = 481.440034816  boot/initrd.img.old                            6

=================== nvme1n1p1: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   722 May  2  2023 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom

==================== nvme1n1p3/efi/pop/grub.cfg (filtered) =====================

search.fs_uuid 88150b98-ddcd-47bb-bb2c-510a0aa6b9aa root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
nvme1n1p1,
using the following options:  nvme1n1p3/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Pop!_OS 22.04 LTS (22.04) entry (nvme1n1p3/efi/****/grub****.efi (**** will be updated in the final message) file) !

The boot files of [nvme1n1p3 (end>100GB)] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a ESP partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot/efi partition:] option of [Boot Repair].If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)



```

---

### Post by oldfred on 2024-03-03
Moved to Other OS as Pop is not Ubuntu.

This is part of your problem, duplicate UUIDs not allowed. Did you copy ESP from one drive to another?
nvme0n1p1 vfat     69CC-6BC5
nvme1n1p3 vfat     69CC-6BC5
Looks like you have all boot files in ESP(s) in both ESP.

---

### Post by tea for one on 2024-03-03
```
The boot files of [nvme1n1p3 (end>100GB)] are far from the start of the disk. Your BIOS may not detect them. 
You may want to retry after creating a ESP partition (FAT32, 100MB~250MB, start of the disk, boot flag). 
This can be performed via tools such as gParted.
```
This might also need attention.

---

### Post by kapyrus on 2024-03-03
Thx for your feedback and moving the topic to the right place.

I did nothing special.. Only installed virtualbox7 on Linux and created a windows 10 vm on it.. System was running for almost 2 years, no issues.. 

I am not sure if I booted into windows before the issue occured though.. I heard windows update can cause those issues. 

I removed windows ssd to see what happens, but now the whole linux boot options are gone, even after putting back windows ssd I only have 

windows on 1tb ssd
windows on 500gb ssd, which should not exist

Now I try to figure out how to remove the whole boot partition to install a new one..

---

### Post by oldfred on 2024-03-03
When you remove a drive, UEFI forgets UEFI entries or changes them to something that usually does not work.
You have to create new entries.
Some systems auto find Windows in the ESP, but none seem to find any other installs.

If you fix duplicate UUIDs/ESPs you can reinstall grub and a Windows UEFI boot entry to UEFI.
Not sure if Windows is in a VM how that works.

---

### Post by tea for one on 2024-03-03
> **kapyrus said:**
> I removed windows ssd to see what happens, but now the whole linux boot options are gone
After removing the Windows disk nvme0n1, you should still be able to boot nvme1n1 as there are boot files in partition nvme1n1p3
```
nvme1n1p3: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/Pop_OS-88150b98-ddcd-47bb-bb2c-510a0aa6b9aa/vmlinu
                       z-previous.efi 
                       /efi/Pop_OS-88150b98-ddcd-47bb-bb2c-510a0aa6b9aa/vmlinu
                       z.efi /efi/pop/grubx64.efi 
                       /efi/systemd/systemd-bootx64.efi /efi/pop/grub.cfg 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi
```
Does this disk not boot from the one-time boot menu?

---

