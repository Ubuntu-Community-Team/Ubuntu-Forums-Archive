---
title: "Dual booted kali with windows, deleted kali partition now broken grub exists..."
date: 2024-10-28
forum: Ubuntu/Debian BASED
---

### Post by danrees77 on 2024-10-28
[B]Complete Problem:

[/B]I have HDD and SSD, Windows is installed on SSD and I dual booted it with Kali... Later I deleted Kali Partition and merged the available space back. Boot menu shows Kali and windows. Ofcourse the Kali boot doesn't work grub>rescue starts... Now the real problem. I installed Zorin OS on 2nd Drive HDD in a separate partition according to instructions and it's not shown in boot menu. I tryed to manually install grub in efi partion on hdd but canonical path not found error occured. I think i need to repair my boot and remove old grub. Here is my [report]("http://paste.ubuntu.com/p/TZ3ZsvMzS8/") from Boot repair. I'm using Live version of ZorinOS right now. Is my data safe if i run bootrepair? Really concerned!!

For each I'm also throwing it here:

```

boot-repair-4ppa2081                                              [20241028_1451]

============================== Boot Info Summary ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Zorin OS 17.2
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sdc: /dev/sdc already mounted or mount point busy.


================================ 2 OS detected =================================

OS#1 (linux):   Zorin OS 17.2 (17) on sda4
OS#2 (windows):   Windows 10 or 11 on sdb2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: HD Graphics 620 GM107 [GeForce 940MX] from Intel Corporation NVIDIA Corporation
Live-session OS is Zorin 64-bit (Zorin OS 17.2, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: V1.47(1.47) from Insyde Corp.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot enabled according to mokutil - Please report this message to boot.repair@gmail.com.
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0002,0003,0000,2001,2002,2003
Boot0000* BlackLinux    PciRoot(0x0)/Pci(0x17,0x0)/Sata(0,0,0)/HD(1,GPT,057c726f-e05f-4b75-9d96-93426fc0be39,0x800,0x32000)/File(\EFI\kali\grubx64.efi)A01 ..
Boot0001* Unknown Device:     HD(1,GPT,057c726f-e05f-4b75-9d96-93426fc0be39,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0002* Windows Boot Manager    HD(1,GPT,057c726f-e05f-4b75-9d96-93426fc0be39,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...}................
Boot0003* Linux    HD(1,MBR,0x339ad900,0x23c,0x2780)/File(\EFI\Boot\grubx64.efi)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
sdb    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda3    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda4    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
sdb2    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdb3    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, vfat
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
sda4    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4
sdb2    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
sdb3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot, ntfs

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda4    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sdb2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdb3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb

fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: A53CD5C6-3AD2-4D78-B127-5637C972C878
          Start        End    Sectors   Size Type
sda1        2048     206847     204800   100M EFI System
sda2      206848     239615      32768    16M Microsoft reserved
sda3      239616 1422067711 1421828096   678G Microsoft basic data
sda4  1422067712 1953523711  531456000 253.4G Linux filesystem
Disk sdb: 223.57 GiB, 240057409536 bytes, 468862128 sectors
Disk identifier: 5E4A7EF6-39AE-45FB-B7E2-29AA4744C430
         Start       End   Sectors   Size Type
sdb1       2048     34815     32768    16M Microsoft reserved
sdb2      34816 467822591 467787776 223.1G Microsoft basic data
sdb3  467824640 468858879   1034240   505M Windows recovery environment
Disk sdc: 58.59 GiB, 62914560000 bytes, 122880000 sectors
Disk identifier: 0x339ad900
     Boot   Start       End   Sectors  Size Id Type
sdc1  *          0   6678143   6678144  3.2G  0 Empty
sdc2           572     10683     10112  4.9M ef EFI (FAT-12/16/32)
sdc3       6680576 122879999 116199424 55.4G 83 Linux

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:4096:gpt:ATA ST1000LM035-1RK1:;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot, esp;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres;
3:123MB:728GB:728GB:ntfs:Basic data partition:msftdata;
4:728GB:1000GB:272GB:ext4::;
sdb:240GB:scsi:512:512:gpt:ATA Lexar 240GB SSD:;
1:1049kB:17.8MB:16.8MB::Microsoft reserved partition:msftres;
2:17.8MB:240GB:240GB:ntfs:Basic data partition:msftdata;
3:240GB:240GB:530MB:ntfs::hidden, diag;
sdc:62.9GB:scsi:512:512:msdos:VendorCo ProductCode:;
2:293kB:5470kB:5177kB:::esp;
3:3420MB:62.9GB:59.5GB:ext4::;

Free space >10MiB: ______________________________________________________________

sdc: 5.22MiB:3262MiB:3257MiB

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                
&#9500;&#9472;sda1 vfat     0A61-8EC4                            057c726f-e05f-4b75-9d96-93426fc0be39                          EFI system partition
&#9500;&#9472;sda2                                               2fdf6b3e-17e6-480b-960c-f8d1d066adce                          Microsoft reserved partition
&#9500;&#9472;sda3 ntfs     FA328A033289C55B                     a4107019-bb31-4924-8817-38350fdc5d86 BIG Drive                Basic data partition
&#9492;&#9472;sda4 ext4     ab29300f-d475-4532-9acd-cb595898c720 ef6d2ef8-4a8f-4ac1-aeca-fca373646ddb                          
sdb                                                                                                                
&#9500;&#9472;sdb1                                               c628b3ae-3d24-42b2-b3c5-6b46d78d4170                          Microsoft reserved partition
&#9500;&#9472;sdb2 ntfs     0C2A70192A6FFDD0                     4e794a6a-1ce8-4760-9e1c-145844042778                          Basic data partition
&#9492;&#9472;sdb3 ntfs     B248CEE248CEA507                     64c54709-ccd0-469e-be3f-e747269788a5                          
sdc    iso9660  2024-09-18-12-00-16-00                                                    Zorin OS 17.2 Core 64bit 
&#9500;&#9472;sdc1 iso9660  2024-09-18-12-00-16-00               339ad900-01                          Zorin OS 17.2 Core 64bit 
&#9500;&#9472;sdc2 vfat     0C83-C5F2                            339ad900-02                                                   
&#9492;&#9472;sdc3 ext4     5d5ce05d-dde3-4fc5-a50f-e636e8ef7ac2 339ad900-03                          writable                 

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/sda1                                                     225.3G   4% /mnt/boot/efi
/dev/sda3                                                     285.5G  58% /media/zorin/BIG Drive
/dev/sda4                                                     225.3G   4% /mnt
/dev/sdb2                                                      55.6G  75% /media/zorin/0C2A70192A6FFDD0
/dev/sdb3                                                      87.9M  83% /mnt/boot-sav/sdb3
/dev/sdc1                                                          0 100% /cdrom
efivarfs                                                        3.1K  92% /sys/firmware/efi/efivars

Mount options (filtered): ______________________________________________________

/dev/sda1                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda3                                                     ntfs3           rw,nosuid,nodev,relatime,uid=999,gid=999,windows_names,iocharset=utf8
/dev/sda4                                                     ext4            rw,relatime
/dev/sdb2                                                     ntfs3           rw,nosuid,nodev,relatime,uid=999,gid=999,windows_names,iocharset=utf8
/dev/sdb3                                                     fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdc1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8

====================== sda4/boot/grub/grub.cfg (filtered) ======================

Zorin   ab29300f-d475-4532-9acd-cb595898c720
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda4/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=ab29300f-d475-4532-9acd-cb595898c720 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=0A61-8EC4  /boot/efi       vfat    umask=0077      0       1

======================= sda4/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_THEME=/usr/share/grub/themes/zorin/theme.txt

==================== sda4: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 740.223651886 = 794.809094144  boot/grub/grub.cfg                             1
 681.899410248 = 732.183916544  boot/vmlinuz                                   2
 681.899410248 = 732.183916544  boot/vmlinuz-6.8.0-40-generic                  2
 683.889862061 = 734.321147904  boot/vmlinuz-6.8.0-47-generic                  1
 907.394935608 = 974.307893248  boot/initrd.img                                1
 907.394935608 = 974.307893248  boot/initrd.img-6.8.0-40-generic               1
 913.727104187 = 981.107007488  boot/initrd.img-6.8.0-47-generic               1
 907.394935608 = 974.307893248  boot/initrd.img.old                            1

===================== sda4: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18673 May 10  2023 10_linux
-rwxr-xr-x 1 root root 43021 May 10  2023 10_linux_zfs
-rwxr-xr-x 1 root root 14387 May 10  2023 20_linux_xen
-rwxr-xr-x 1 root root 13369 May 10  2023 30_os-prober
-rwxr-xr-x 1 root root  1372 May 10  2023 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17  2023 35_fwupd
-rwxr-xr-x 1 root root   214 May 10  2023 40_custom
-rwxr-xr-x 1 root root   215 May 10  2023 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of
sda4,
using the following options:  sda1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Confirmation request before suggested repair: __________________________________

LegacyWindows detected. You may want to retry after deactivating the [Separate /boot/efi partition:] option.
Are you sure you want to continue anyway?

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Zorin OS 17.2 (17) entry (sda1/efi/****/shim****.efi (**** will be updated in the final message) file) !

*******.us ko ()

```

---

### Post by grahammechanical on 2024-10-28
> I installed Zorin OS on 2nd Drive HDD in a separate partition according to instructions and it's not shown in boot menu.

It would not be, would it? The Grub boot menu is on the SSD and controlled by Kali which had been wiped from the SSD drive. If Kali was still there you could boot into Kali and run

```
sudo update-grub
```

And then watch the printout to see that Zorin would be listed as found by Grub. And then the Grub menu would offer to boot Zorin.

I know nothing about Kali and Zorin but I assume that Zorin also uses Grub as the boot loader. I also assume that when you installed Zorin you instructed the Zorin installer to install Grub into the HHD. So, use the UEFI/BIOS to set the boot priority to the HHD and you should see another Grub menu that lists both Zorin and Windows.

Regards

---

### Post by deadflowr on 2024-10-28
*Thread moved to **Ubuntu/Debian BASED***

---

### Post by danrees77 on 2024-10-28
**Thanks I think that would work let me change the priority and come back.**
Edit: No it didn't show anything new, changing priority also showed the same windows bootloader and kali like before.

---

### Post by danrees77 on 2024-10-28
Kindly can you check the report and tell whether I should run boot repair default or not.

---

### Post by yancek on 2024-10-28
I don't know what you did but the boot repair report shows both your hard drives (sda and sdb) which contain windows and Zorin are GPT drives.  Windows requires an EFI installation on GPT drives.  You have an EFI partition but there is nothing shown on it in boot repair.  Boot the Zorin live then run sudo parted -l and find the EFI partition.  Boot repair shows it as sda1 but if you boot Zorin from a USB, it may see itself as sda and your internal drive as sdb/sdc... You will be able to tell which drive it is as the size of the drive will show in the parted output , 1TB.

If parted shows your EFI partition as sdb1, open a terminal and run:  sudo mkdir /mnt/efi  THEN RUN sudo mount /dev/sdb1 /mnt/efi.  Make sure you get the correct drive and partition.  If it mounts successfully, you should see both a Microsoft directory and a zorin (or maybe ubuntu) directory.  Probably the won't be there as I would expect boot repair would have found those files.  If you don't have those, neither will boot in EFI mode so you would need to reinstall Grub from Zorin or using boot repair.  The suggested install from boot repair should do that.  That won't help to boot windows if the Microsoft directory and its files are not there but it should boot Zorin.  You will need a windows installation or recovery media to do that as that is the only way to get the proprietary microsoft boot files.

The message at the end of boot repair shows Legacy windows detected.  I don't know why it shows that.   Maybe because windows boot code shows in the MBR of both devices.  Did you do that when trying to repair the windows boot?  A windows OS on a GPT drive would not be set up that way.   

In your initial post you refer to a boot menu.  Is that the BIOS boot options as grub from Kali would not be expected to appear as the grub.cfg would have been on the / filesystem partition on which you had Kali installed.  When you deleted Kali, did you also delete files/directories on the EFI partition.  You could have just deleted the Kali directory.

---

### Post by danrees77 on 2024-10-30
@yancek I had windows on my SSD and later installed Kali in it too. Then I only deleted the kali partition from windows disk management. What else I did I don't remember but now when I wanted ZorinOS I installed it on my HDD new partition following the instructions in documentation with only difference being that I already shrunk my partition to later use unallocated space for zorin which i did and installed zorin on hdd. But then after pc restart windows booted up normally... I looked in boot menu and found Kali's Grub and on running it only gave filesystem not found error and another one and grub>rescue showed. I changed disk priority but still the same. I live booted and tried to mount efi in sda1 because that's what chatgpt told me :D But it didn't work when i tried to install grub on efi it said can't get canonical address so i found about boot repair and posted dignosis here... Now what?

---

### Post by yancek on 2024-10-30
If you had windows and Kali on the SSD and deleted the Kali / filesystem partition, you apparently also deleted the EFI partition with the EFI windows and Linux boot files since they don't show in boot repair.

>  can't get canonical address

That means you were trying to install Grub to the 'live' USB you were using so the instructions were wrong.  You should use chroot to do that as explained at the link below.  Look at the menu on the right of the page under Reinstalling Grub2.''

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

>   Now what?         

There are a number of questions I asked in my last post that you did not answer so how about starting there.  If you don't have EFI boot code on any EFI partition for Zorin, there is no way for it to boot.  You could run boot repair again so that we could check if anything has changed but if you do, do not try to make any repairs but select only the Create BootInfo Summary option and post the link you get from it here.

---

