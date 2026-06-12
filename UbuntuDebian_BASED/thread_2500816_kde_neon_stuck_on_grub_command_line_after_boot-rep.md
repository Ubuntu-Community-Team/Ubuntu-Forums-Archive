---
title: "kde neon: stuck on grub command line after boot-repair"
date: 2024-09-12
forum: Ubuntu/Debian BASED
---

### Post by bighunk on 2024-09-12
I'm using KDE neon and I was having trouble booting correctly, so I used boot repair to fix the problem. However, I am stuck on the grub command line after rebooting. I have the paste here. I am still pretty new to linux, so I would appreciate any help.
boot-repair-4ppa2081                                              [20240912_1755]
```

============================= Boot Repair Summary ==============================






Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub2 of
nvme1n1p1 into the MBR of nvme1n1,
using the following options:  kernel-purge
Grub-efi will not be selected by default because no ESP detected.
Additional repair will be performed:  unhide-bootmenu-10s


chroot /media/neon/49a7f042-b214-4e36-9123-42826e7b9eef apt-get -y update
W: file:/var/lib/preinstalled-pool/dists/jammy/Release.gpg: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.

================== dpkg -l | grep linux- before kernel purge ===================

ii  linux-base                                    4.5ubuntu9                                                   all          Linux image base package
ii  linux-firmware                                20220329.git681281e4-0ubuntu3.31                             all          Firmware for Linux kernel drivers
ii  linux-generic                                 5.15.0.119.119                                               amd64        Complete Generic Linux kernel and headers
ii  linux-generic-hwe-22.04                       6.8.0-40.40~22.04.3                                          amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.15.0-119                      5.15.0-119.129                                               all          Header files related to Linux kernel version 5.15.0
ii  linux-headers-5.15.0-119-generic              5.15.0-119.129                                               amd64        Linux kernel headers for version 5.15.0 on 64 bit x86 SMP
ii  linux-headers-6.8.0-40-generic                6.8.0-40.40~22.04.3                                          amd64        Linux kernel headers for version 6.8.0 on 64 bit x86 SMP
ii  linux-headers-generic                         5.15.0.119.119                                               amd64        Generic Linux kernel headers
ii  linux-headers-generic-hwe-22.04               6.8.0-40.40~22.04.3                                          amd64        Generic Linux kernel headers
ii  linux-hwe-6.8-headers-6.8.0-40                6.8.0-40.40~22.04.3                                          all          Header files related to Linux kernel version 6.8.0
ii  linux-hwe-6.8-tools-6.8.0-40                  6.8.0-40.40~22.04.3                                          amd64        Linux kernel version specific tools for version 6.8.0-40
ii  linux-image-5.15.0-119-generic                5.15.0-119.129                                               amd64        Signed kernel image generic
ii  linux-image-6.8.0-40-generic                  6.8.0-40.40~22.04.3                                          amd64        Signed kernel image generic
ii  linux-image-generic                           5.15.0.119.119                                               amd64        Generic Linux kernel image
ii  linux-image-generic-hwe-22.04                 6.8.0-40.40~22.04.3                                          amd64        Generic Linux kernel image
ii  linux-modules-5.15.0-119-generic              5.15.0-119.129                                               amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-6.8.0-40-generic                6.8.0-40.40~22.04.3                                          amd64        Linux kernel extra modules for version 6.8.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.15.0-119-generic        5.15.0-119.129                                               amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-6.8.0-40-generic          6.8.0-40.40~22.04.3                                          amd64        Linux kernel extra modules for version 6.8.0 on 64 bit x86 SMP
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu7                                         all          base package for ALSA and OSS sound systems
ii  linux-tools-6.8.0-40-generic                  6.8.0-40.40~22.04.3                                          amd64        Linux kernel version specific tools for version 6.8.0-40
ii  linux-tools-common                            5.15.0-119.129                                               all          Linux kernel version specific tools for version 5.15.0

======================== Purge kernel of /dev/nvme1n1p1 ========================

linux-generic available

Starting pkgProblemResolver with broken count: 0
Starting 2 pkgProblemResolver with broken count: 0
Done
The following packages were automatically installed and are no longer required:
colord-data libcolorhug2 libdbusmenu-glib4 libdbusmenu-gtk3-4 xul-ext-ubufox
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 386 not upgraded.
DEBCHECK debOK, linux-generic
DEBCHECKLINUX debOK
ls /media/neon/49a7f042-b214-4e36-9123-42826e7b9eef/boot/:

chroot /media/neon/49a7f042-b214-4e36-9123-42826e7b9eef apt-get install -y linux-generic

Starting pkgProblemResolver with broken count: 0
Starting 2 pkgProblemResolver with broken count: 0
Done
linux-generic is already the newest version (5.15.0.119.119).
The following packages were automatically installed and are no longer required:
colord-data libcolorhug2 libdbusmenu-glib4 libdbusmenu-gtk3-4 xul-ext-ubufox
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 386 not upgraded.

chroot /media/neon/49a7f042-b214-4e36-9123-42826e7b9eef apt-get install -y linux-base
Starting pkgProblemResolver with broken count: 0
Starting 2 pkgProblemResolver with broken count: 0
Done
linux-base is already the newest version (4.5ubuntu9).
linux-base set to manually installed.
The following packages were automatically installed and are no longer required:
colord-data libcolorhug2 libdbusmenu-glib4 libdbusmenu-gtk3-4 xul-ext-ubufox
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 386 not upgraded.

=================== dpkg -l | grep linux- after kernel reinstall
ii  linux-base                                    4.5ubuntu9                                                   all          Linux image base package
ii  linux-firmware                                20220329.git681281e4-0ubuntu3.31                             all          Firmware for Linux kernel drivers
ii  linux-generic                                 5.15.0.119.119                                               amd64        Complete Generic Linux kernel and headers
ii  linux-generic-hwe-22.04                       6.8.0-40.40~22.04.3                                          amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.15.0-119                      5.15.0-119.129                                               all          Header files related to Linux kernel version 5.15.0
ii  linux-headers-5.15.0-119-generic              5.15.0-119.129                                               amd64        Linux kernel headers for version 5.15.0 on 64 bit x86 SMP
ii  linux-headers-6.8.0-40-generic                6.8.0-40.40~22.04.3                                          amd64        Linux kernel headers for version 6.8.0 on 64 bit x86 SMP
ii  linux-headers-generic                         5.15.0.119.119                                               amd64        Generic Linux kernel headers
ii  linux-headers-generic-hwe-22.04               6.8.0-40.40~22.04.3                                          amd64        Generic Linux kernel headers
ii  linux-hwe-6.8-headers-6.8.0-40                6.8.0-40.40~22.04.3                                          all          Header files related to Linux kernel version 6.8.0
ii  linux-hwe-6.8-tools-6.8.0-40                  6.8.0-40.40~22.04.3                                          amd64        Linux kernel version specific tools for version 6.8.0-40
ii  linux-image-5.15.0-119-generic                5.15.0-119.129                                               amd64        Signed kernel image generic
ii  linux-image-6.8.0-40-generic                  6.8.0-40.40~22.04.3                                          amd64        Signed kernel image generic
ii  linux-image-generic                           5.15.0.119.119                                               amd64        Generic Linux kernel image
ii  linux-image-generic-hwe-22.04                 6.8.0-40.40~22.04.3                                          amd64        Generic Linux kernel image
ii  linux-modules-5.15.0-119-generic              5.15.0-119.129                                               amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-6.8.0-40-generic                6.8.0-40.40~22.04.3                                          amd64        Linux kernel extra modules for version 6.8.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.15.0-119-generic        5.15.0-119.129                                               amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-6.8.0-40-generic          6.8.0-40.40~22.04.3                                          amd64        Linux kernel extra modules for version 6.8.0 on 64 bit x86 SMP
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu7                                         all          base package for ALSA and OSS sound systems
ii  linux-tools-6.8.0-40-generic                  6.8.0-40.40~22.04.3                                          amd64        Linux kernel version specific tools for version 6.8.0-40
ii  linux-tools-common                            5.15.0-119.129                                               all          Linux kernel version specific tools for version 5.15.0



Unhide GRUB boot menu in nvme1n1p1/etc/default/grub

==================== Reinstall the grub2 of /dev/nvme1n1p1 =====================

chroot /media/neon/49a7f042-b214-4e36-9123-42826e7b9eef grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.2

==> Reinstall the GRUB of /dev/nvme1n1p1 into the MBR of /dev/nvme1n1

chroot /media/neon/49a7f042-b214-4e36-9123-42826e7b9eef grub-install /dev/nvme1n1
Installing for i386-pc platform.
Installation finished. No error reported.

chroot /media/neon/49a7f042-b214-4e36-9123-42826e7b9eef update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/99_breeze-grub.cfg'
Sourcing file `/etc/default/grub.d/init-select.cfg'

Unhide GRUB boot menu in nvme1n1p1/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on nvme1n1 (CT500P2SSD8) disk!

The boot files of [nvme1n1p1 (end>100GB)] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

============================ Boot Info After Repair ============================

 => Grub2 (v2.00) is installed in the MBR of /dev/nvme0n1 and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/nvme1n1 and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

nvme1n1p1: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  KDE neon 6.1
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

nvme1n1p2: _____________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg


================================ 1 OS detected =================================

OS#1 (linux):   KDE neon 6.0 (22.04) on nvme1n1p1

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: Navi 23 [Radeon RX 6600/6600 XT/6600M] from Advanced Micro Devices, Inc. [AMD/ATI]
Live-session OS is Neon 64-bit (KDE neon 6.1, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: FC(5.17) from American Megatrends International, LLC.
The firmware seems EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme1n1	: notGPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, has-os,	no-wind,	2048 sectors * 512 bytes
sda	: notGPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes
sdb	: notGPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme1n1p1	: is-os,	64, apt-get,	signed grub-pc grub-efi ,	grub2,	grub-install,	no-grubenv,	update-grub,	end-after-100GB
sda1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB
sdb1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB

Partitions info (2/3): _________________________________________________________

nvme1n1p1	: isnotESP,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, ext4
sda1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, ext4
sdb1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, ntfs

Partitions info (3/3): _________________________________________________________

nvme1n1p1	: not--sepboot,	no---boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	nvme1n1
sda1	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sdb1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sdb

fdisk -l (filtered): ___________________________________________________________

Disk sda: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0x0f2236cc
     Boot Start       End   Sectors   Size Id Type
sda1        2048 976773119 976771072 465.8G 83 Linux
Disk sdb: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk identifier: 0xa0fad416
     Boot Start        End    Sectors  Size Id Type
sdb1        2048 3907026943 3907024896  1.8T  7 HPFS/NTFS/exFAT
Disk nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: 0x10abee76
Disk nvme1n1: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0x12451cfe
         Boot     Start       End   Sectors   Size Id Type
nvme1n1p1 *         2048 904657871 904655824 431.4G 83 Linux
nvme1n1p2      904657872 976768064  72110193  34.4G 82 Linux swap / Solaris
Disk sdc: 14.57 GiB, 15640625152 bytes, 30548096 sectors
Disk identifier: 0x6b8b4567
     Boot Start      End  Sectors  Size Id Type
sdc1         464     9295     8832  4.3M ef EFI (FAT-12/16/32)
sdc2       10240 30545919 30535680 14.6G  6 FAT16

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:512:msdos:ATA WDC WDS500G2B0A:;
1:1049kB:500GB:500GB:ext4::;
sdb:2000GB:scsi:512:4096:msdos:ATA ST2000DM008-2FR1:;
1:1049kB:2000GB:2000GB:ntfs::;
sdc:15.6GB:scsi:512:512:msdos:General USB Flash Disk:;
1:238kB:4760kB:4522kB:::esp;
2:5243kB:15.6GB:15.6GB:::;
nvme0n1:512GB:nvme:512:512:msdos:PCIe SSD:;
nvme1n1:500GB:nvme:512:512:msdos:CT500P2SSD8:;
1:1049kB:463GB:463GB:ext4::boot;
2:463GB:500GB:36.9GB:linux-swap(v1)::;

Free space >10MiB: ______________________________________________________________

nvme0n1: 0.00MiB:488386MiB:488386MiB

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                     
&#9492;&#9472;sda1      ext4     34c0574c-5ad2-48d0-9a0f-b94bea02524a 0f2236cc-01                          Steam Library            
sdb                                                                                                                     
&#9492;&#9472;sdb1      ntfs     B09E69319E68F0F0                     a0fad416-01                          Hard Drive               
sdc         iso9660  2024-08-22-07-40-09-00                                                    neon user 20240822-07:40 
&#9500;&#9472;sdc1      vfat     B4E0-7D6E                            6b8b4567-01                                                   
&#9492;&#9472;sdc2                                                    6b8b4567-02                                                   
nvme0n1                                                                                                                 
nvme1n1                                                                                                                 
&#9500;&#9472;nvme1n1p1 ext4     49a7f042-b214-4e36-9123-42826e7b9eef 12451cfe-01                                                   
&#9492;&#9472;nvme1n1p2 swap     dd25c3aa-9977-4f29-8abe-d96127129909 12451cfe-02                          swap                     

Mount points (filtered): _______________________________________________________

                Avail Use% Mounted on
/dev/nvme1n1p1 376.5G   6% /media/neon/49a7f042-b214-4e36-9123-42826e7b9eef
/dev/sda1      329.7G  23% /mnt/boot-sav/sda1
/dev/sdb1        1.5T  20% /mnt/boot-sav/sdb1
/dev/sdc            0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/nvme1n1p1 ext4        rw,nosuid,nodev,relatime,errors=remount-ro
/dev/sda1      ext4        rw,relatime
/dev/sdb1      fuseblk     rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdc       iso9660     ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8

=================== nvme1n1p1/boot/grub/grub.cfg (filtered) ====================

### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme1n1p1/etc/fstab (filtered) ========================

# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=49a7f042-b214-4e36-9123-42826e7b9eef /              ext4    defaults   0 1
UUID=dd25c3aa-9977-4f29-8abe-d96127129909 swap           swap    defaults   0 0
tmpfs                                     /tmp           tmpfs   defaults,noatime,mode=1777 0 0

==================== nvme1n1p1/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

================= nvme1n1p1: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
 420.136066437 = 451.117666304  boot/grub/i386-pc/core.img                     1

=================== nvme1n1p1: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Apr 10 21:09 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom

====================== sdc/boot/grub/grub.cfg (filtered) =======================

KDE neon
KDE neon (safe graphics)
KDE neon (OEM mode - for manufacturers)
KDE neon (OEM mode + safe graphics)
Boot from next volume
UEFI Firmware Settings

==================== sdc: Location of files loaded by Grub =====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on sdc

*******.us ko ()
```

---

### Post by tea for one on 2024-09-13
> **bighunk said:**
> I am still pretty new to linux, so I would appreciate any help.
> KDE Neon is primarily intended for technical Linux/KDE users who want immediate access to the latest KDE offerings.
The above text from here [https://neon.kde.org/faq](https://neon.kde.org/faq)
```
Grub-efi will not be selected by default because [COLOR="#0000FF"]no ESP detected.[/COLOR]
```
Are you familiar with the differences between old-fashioned Legacy systems and modern UEFI systems?
You have installed KDE Neon in Legacy mode.

Backup your personal data (if any)
Download an Ubuntu flavour i.e. Kubuntu 24.04 for KDE environment
Install in UEFI mode with GPT

---

### Post by coffeecat on 2024-09-13
Not an official Ubuntu flavour. *Thread moved to the **Ubuntu/Debian BASED** sub-forum.*

@bighunk, I've added BBCode code tags to your boot repair output. See how that this has restored the columnar formatting lost by pasting text into a post without code tags. Please use code tags for script output, terminal output, config files, etc. There's a link in my sig if you need it.

---

### Post by oldfred on 2024-09-13
It looks like you also have Windows in old BIOS/MBR configuration.
Microsoft in 2012 required vendors to install Windows 8 in UEFI boot mode to gpt partitioned drives. BIOS mode with old MBR(msdos) partitioning was only offer for installs for older hardware prior to 2012 that could only boot in BIOS mode.

But conversion from MBR to gpt erases entire hard drive. So good backups required. And you have to backup data & reinstall as you cannot restore a BIOS/MBR image to UEFI/gpt system.
So best to plan longer term conversion to UEFI.

---

