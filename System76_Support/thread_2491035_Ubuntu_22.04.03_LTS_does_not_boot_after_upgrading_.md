---
title: "Ubuntu 22.04.03 LTS does not boot after upgrading from version 20.04 LTS"
date: 2023-09-23
forum: System76 Support
---

### Post by jndro11 on 2023-09-23
Hello Ubuntu community,

Today I upgraded my ubuntu OS from 20.04 to 22.04 on my MSI prestige 15 laptop that has already dual boot alongside with windows 11. Until the upgrade, Ubuntu 20.04 was working perfectly on the dual boot with windows 11, but I am not able to do the same with the new upgraded version. I will try to explain what is happening now:

- I upgraded Ubuntu to version 22.04.3 and it requested at the end to restart the laptop.
- I clicked to the restart option and my laptop restarted properly. The GRUB menu appeared and I selected Ubuntu instead of Windows.
- The laptop starts the booting sequence to Ubuntu system but it gets stuck there, never starting Ubuntu. At this point I just have the possibility to turn on my laptop from the power button (no reaction to any other button).
- I powered up the laptop and from the GRUB menu I selected to boot into windows and all worked properly for windows 11 (it made me feel alleviated at the end, no dead laptop).
- Then, I restarted again the laptop and I choose advanced options for Ubuntu and then I selected the option for start in recovery mode. 
- Once inside recovery mode option, the system showed all options for that menu and I just pressed to resume in order to attempt starting Ubuntu -> It worked properly and I was able to enter into Ubuntu 22.04.3 and it seems to work properly.
- I restarted the laptop several times attempting to boot to Ubuntu without accessing to advanced options and all attempts failed -> I am only able to start Ubuntu from recovery menu option.
- I executed then the programme Boot-Repair and I gathered the following report (I did not choose the option to fix issues yet):

boot-repair-4ppa2056                                              [20230923_1824]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.

nvme0n1p1: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvme0n1p2: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/Microsoft/Boot/cbmr_driver.efi

nvme0n1p3: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

nvme0n1p4: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8 or 10
    Boot files:        /Windows/System32/winload.exe

nvme0n1p5: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvme0n1p6: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvme0n1p7: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub


================================ 2 OS detected =================================

OS#1:   Ubuntu 22.04.3 LTS on nvme0n1p7
OS#2:   Windows 8 or 10 on nvme0n1p4

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: Alder Lake-P Integrated Graphics Controller GA107M [GeForce RTX 3050 Ti Mobile] EFI VGA from Intel Corporation NVIDIA Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-5.15.0-84-generic root=UUID=1e1f8886-68a7-41be-9cc7-0f9dc277b349 ro recovery nomodeset dis_ucode_ldr
df -Th / : /dev/nvme0n1p7 ext4   192G    27G  156G  15% /

===================================== UEFI =====================================

BIOS/UEFI firmware: E16S8IMS.106(1.6) from American Megatrends International, LLC.
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0002,0000,0001,0003,0004
Boot0000* Windows Boot Manager    HD(2,GPT,6bdfa0a2-d0db-4967-8bf8-805d4a741399,0xfa000,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* UEFI:CD/DVD Drive    BBS(129,,0x0)
Boot0002* ubuntu    HD(2,GPT,6bdfa0a2-d0db-4967-8bf8-805d4a741399,0xfa000,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0003* UEFI:Removable Device    BBS(130,,0x0)
Boot0004* UEFI:Network Device    BBS(131,,0x0)

64349b3622c65f495a99dbf6102496e3   nvme0n1p2/Boot/bootx64.efi
a9c517741ac31962d7feb152948ad1ee   nvme0n1p2/Boot/fbx64.efi
a660182adef313615746a665966d2ccc   nvme0n1p2/Boot/mmx64.efi
5ddf997e8b025bfbc2009e85b32f60dc   nvme0n1p2/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   nvme0n1p2/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   nvme0n1p2/ubuntu/shimx64.efi
7c8dc272a3781364b96a42492133f037   nvme0n1p2/Microsoft/Boot/bootmgfw.efi
99c9de136b720b86e6184d40e4bfcbbb   nvme0n1p2/Microsoft/Boot/bootmgr.efi
b8796e68099026aabcebb8fcf75b21f6   nvme0n1p2/Microsoft/Boot/cbmr_driver.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p7    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
nvme0n1p5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p6    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p4    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far

Partitions info (2/3): _________________________________________________________

nvme0n1p7    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
nvme0n1p1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
nvme0n1p6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p2    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p7    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1
nvme0n1p5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p6    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
Disk identifier: 631C6ADE-1912-4ED1-B7F2-54EA899BAB8A
               Start        End    Sectors   Size Type
nvme0n1p1       2048    1023999    1021952   499M Windows recovery environment
nvme0n1p2    1024000    1228799     204800   100M EFI System
nvme0n1p3    1228800    1261567      32768    16M Microsoft reserved
nvme0n1p4    1261568 1568286719 1567025152 747.2G Microsoft basic data
nvme0n1p5 1977886720 1979435007    1548288   756M Windows recovery environment
nvme0n1p6 1979437056 2000408575   20971520    10G Microsoft basic data
nvme0n1p7 1568286720 1977886719  409600000 195.3G Linux filesystem
Partition table entries are not in disk order.

parted -lm (filtered): _________________________________________________________

nvme0n1:1024GB:nvme:512:512:gpt:SAMSUNG MZVL21T0HCLR-00B00:;
1:1049kB:524MB:523MB:ntfs:Basic data partition:hidden, diag;
2:524MB:629MB:105MB:fat32:EFI system partition:boot, esp;
3:629MB:646MB:16.8MB::Microsoft reserved partition:msftres;
4:646MB:803GB:802GB:ntfs:Basic data partition:msftdata;
7:803GB:1013GB:210GB:ext4::;
5:1013GB:1013GB:793MB:ntfs::hidden, diag;
6:1013GB:1024GB:10.7GB:ntfs:Basic data partition:msftdata;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL        PARTLABEL
nvme0n1                                                                                                     
&#9500;&#9472;nvme0n1p1 ntfs     5EF477FEF477D6AD                     c18a8b9f-2fb2-4f22-a7ed-54667f75b30e Recuperación Basic data partition
&#9500;&#9472;nvme0n1p2 vfat     4878-17EF                            6bdfa0a2-d0db-4967-8bf8-805d4a741399              EFI system partition
&#9500;&#9472;nvme0n1p3                                               5affe323-6429-4053-9612-c5867484f2b2              Microsoft reserved partition
&#9500;&#9472;nvme0n1p4 ntfs     9A4878EF4878CC0F                     9536225a-9bae-461f-a9f6-1090de0fe1e3              Basic data partition
&#9500;&#9472;nvme0n1p5 ntfs     CC52DFFE52DFEAEA                     9923c2bf-8f0b-402d-87c0-4d94440b1f1b              
&#9500;&#9472;nvme0n1p6 ntfs     741EC1471EC1035A                     76bc938f-5937-49c9-a71f-46eec6faf69b DriverCD     Basic data partition
&#9492;&#9472;nvme0n1p7 ext4     1e1f8886-68a7-41be-9cc7-0f9dc277b349 f0345f36-c0d4-4256-857a-0ecc88f2146b              

Mount points (filtered): _______________________________________________________

                                     Avail Use% Mounted on
/dev/nvme0n1p1                        489M   2% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p2                       60.6M  37% /mnt/boot-sav/nvme0n1p2
/dev/nvme0n1p4                      509.7G  32% /media/alejandro/9A4878EF4878CC0F
/dev/nvme0n1p5                       88.9M  88% /mnt/boot-sav/nvme0n1p5
/dev/nvme0n1p6                        3.7G  63% /media/alejandro/DriverCD
/dev/nvme0n1p7                      155.1G  14% /

Mount options (filtered): ______________________________________________________


=================== nvme0n1p2/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid 1e1f8886-68a7-41be-9cc7-0f9dc277b349 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

=================== nvme0n1p7/boot/grub/grub.cfg (filtered) ====================

Ubuntu   1e1f8886-68a7-41be-9cc7-0f9dc277b349
Ubuntu, with Linux 5.15.0-84-generic   1e1f8886-68a7-41be-9cc7-0f9dc277b349
Windows Boot Manager (on nvme0n1p2)   osprober-efi-4878-17EF
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme0n1p7/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p7 during installation
UUID=1e1f8886-68a7-41be-9cc7-0f9dc277b349 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p2 during installation
UUID=4878-17EF  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

==================== nvme0n1p7/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

================= nvme0n1p7: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
 832,001380920 = 893,354680320  boot/grub/grub.cfg                             1
 756,750072479 = 812,554203136  boot/vmlinuz                                   1
 756,750072479 = 812,554203136  boot/vmlinuz-5.15.0-84-generic                 1
 756,750072479 = 812,554203136  boot/vmlinuz.old                               1
 759,692378998 = 815,713480704  boot/initrd.img                                2
 759,692378998 = 815,713480704  boot/initrd.img-5.15.0-84-generic              2
 759,692378998 = 815,713480704  boot/initrd.img.old                            2

=================== nvme0n1p7: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 21  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Jan 11  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
nvme0n1p7,
using the following options:  nvme0n1p2/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.3 LTS entry (nvme0n1p2/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)


Then, could you tell me from your experience what can I do next? What is your recommendation on that topic? Shall I just let to the Boot-repair programme to fix all that is necessary? I am afraid of messing up my laptop and loose my windows 11 partition or its booting on the process, which is something cannot do because I need both partitions available and running properly...

Thank you very much for your support and your attention. If it is necessary from my side to give you more information about the issue let me know and I will try to do so ASAP. 

AC

---

### Post by jndro11 on 2023-10-01
Hello,

I posted the same thread in another forum that seems more appropriate than this as I understood. Could you please be so kind to help me closing this thread? 

Thank you very much for the support.

AC

---

