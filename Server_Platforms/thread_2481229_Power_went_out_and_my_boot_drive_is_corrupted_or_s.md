---
title: "Power went out and my boot drive is corrupted or something?"
date: 2022-11-22
forum: Server Platforms
---

### Post by madmandrew on 2022-11-22
Power went out and now my server won't boot.  I have a dell r710.  I have the boot drive installed on an internal usb flash drive which I suspect could be part of the problem? 

I've attached the pastebin log from my attempt to do a boot repair which did not fix the problem.  I tried to do the automatic repair.

Any way I can recover this? or should I give up and reinstall linux and start over?

Also any advice on creating an image for future so I don't have to worry about starting from scratch again?  I've found rescuezilla is a good one?

```
boot-repair-4ppa125                                              [20221123_0034]

============================= Boot Repair Summary ==============================


User choice:


Is there RAID on this computer? yes
[dmraid] packages may interfere with MDraid. Do you want to remove them? no


================================ LVM activation ================================


modprobe dm-mod  
vgscan --mknodes
  Reading volume groups from cache.
  Found volume group "ubuntu-vg" using metadata type lvm2
vgchange -ay
  1 logical volume(s) in volume group "ubuntu-vg" now active
lvscan
  ACTIVE            '/dev/ubuntu-vg/ubuntu-lv' [<114.48 GiB] inherit
blkid -g


Unusual RAID (no raid in blkid).


=================== blkid (filtered) before raid activation: ===================
/dev/sda: UUID="a9f73fb0-7d1b-44c4-a47c-e2b5e57f3ff5" TYPE="ext4"
/dev/mapper/ubuntu--vg-ubuntu--lv: UUID="60e93bdb-852b-4e0c-ab1d-b0d073d1cb08" TYPE="ext4"
/dev/sdb1: UUID="2020-06-13-00-42-55-00" LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660" PTUUID="2c534026" PTTYPE="dos" PARTUUID="2c534026-01"
/dev/sdb2: SEC_TYPE="msdos" UUID="D055-8513" TYPE="vfat" PARTUUID="2c534026-02"
/dev/sdc2: UUID="c3a3245b-1df7-4a88-9c1f-a08aa411119f" TYPE="ext4" PARTUUID="aaf526da-3290-453a-a168-157a683a597b"
/dev/sdc3: UUID="7zhqz8-9h9o-SLjw-opyK-Zf8l-83Pa-amr4OC" TYPE="LVM2_member" PARTUUID="93e0e685-f57a-44e7-8a4d-a792e7bd244f"
/dev/zram0: UUID="cb7e4aa9-18f8-44a2-b565-983811b60cd8" TYPE="swap"
/dev/zram1: UUID="840f2af9-1947-4c2c-9869-5a438ea1c7cb" TYPE="swap"
/dev/zram2: UUID="be1a3f1a-f19f-4bfe-b718-425015b2d72f" TYPE="swap"
/dev/zram3: UUID="d092687f-eaff-463f-9dbc-4cb7f074ec0c" TYPE="swap"
/dev/zram4: UUID="f0526fa8-1bc2-48fc-8bbf-0e9dc69f3afc" TYPE="swap"
/dev/zram5: UUID="4d8b8eb4-ff76-46f2-9d91-bf6020407429" TYPE="swap"
/dev/zram6: UUID="89972c01-fa15-4a9e-9d2f-9131705ea143" TYPE="swap"
/dev/zram7: UUID="9d2a2282-3de7-4a02-b1db-1e1a8e0060a7" TYPE="swap"
/dev/zram8: UUID="724bf33f-bc8e-4476-ba2c-e3f173720515" TYPE="swap"
/dev/zram9: UUID="fe6c05bc-f580-484e-8e38-37f20bb27687" TYPE="swap"
/dev/zram10: UUID="eb7bf7d0-a37f-4702-95bd-dc03d89f2c86" TYPE="swap"
/dev/zram11: UUID="303e7bbc-f4cd-44be-8b48-7f5713a35482" TYPE="swap"
/dev/zram12: UUID="9ba53e42-b26f-4c91-a37d-c70654511010" TYPE="swap"
/dev/zram13: UUID="920dca29-8939-4255-8919-208b7c84c2a1" TYPE="swap"
/dev/zram14: UUID="a2f7da8a-7a4c-4e2b-8bc4-365949c51e70" TYPE="swap"
/dev/zram15: UUID="7e93e13d-005b-425b-9707-25a87c6262c2" TYPE="swap"
/dev/zram16: UUID="f6ed5959-564b-479f-8feb-efed0accafe7" TYPE="swap"
/dev/zram17: UUID="35c94f60-07e7-4be6-a255-a091efc355a6" TYPE="swap"
/dev/zram18: UUID="6abf536a-c71b-4517-b889-e841d4a704ac" TYPE="swap"
/dev/zram19: UUID="0d828f48-80d5-479d-bb13-e16fcb88d58f" TYPE="swap"
/dev/zram20: UUID="86b9452c-a76f-4bd7-b626-5bcf0cf70a37" TYPE="swap"
/dev/zram21: UUID="af14b549-8525-4bcf-a353-380d365a3fdc" TYPE="swap"
/dev/zram22: UUID="48781bd1-6031-42ee-adbc-8356e86033ea" TYPE="swap"
/dev/zram23: UUID="0a1f6799-f901-43b3-a50c-4dd9918f30c0" TYPE="swap"
/dev/sdc1: PARTUUID="9c1db13e-ad71-4d64-9758-9eb1b7adb1bc"
dmraid -si -c
no raid disks
No DMRAID disk.
User chose to keep dmraid. It may interfere with mdadm.
mdadm --assemble --scan


mdadm --detail --scan


Warning: no active raid (DMRAID nor MD_ARRAY).
Error code 32
mount -r /dev/mapper/ubuntu--vg-ubuntu--lv /mnt/boot-sav/mapper/ubuntu--vg-ubuntu--lv


mount -r /dev/mapper/ubuntu--vg-ubuntu--lv : Error code 32
Error code 32
mount -r /dev/sdc2 /mnt/boot-sav/sdc2


mount -r /dev/sdc2 : Error code 32
Error code 32
mount -r /dev/mapper/ubuntu--vg-ubuntu--lv /mnt/boot-sav/mapper/ubuntu--vg-ubuntu--lv


mount -r /dev/mapper/ubuntu--vg-ubuntu--lv : Error code 32
Error code 32
mount -r /dev/sdc2 /mnt/boot-sav/sdc2


mount -r /dev/sdc2 : Error code 32


This will install the [mdadm] packages. Do you want to continue?
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin:
mdadm: No arrays found in config file or automatically
Warning: Unable to open /dev/sdc read-write (Read-only file system).  /dev/sdc has been opened read-only.
sda may have broken partition table.
[dmraid -sa -c] no
[dmraid -sa -c] raid
[dmraid -sa -c] disks
Set sda as corresponding disk of mapper/ubuntu--vg-ubuntu--lv
grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
[dmraid -sa -c] no
[dmraid -sa -c] raid
[dmraid -sa -c] disks
Set sda as corresponding disk of mapper/ubuntu--vg-ubuntu--lv
mount: /mnt/boot-sav/mapper/ubuntu--vg-ubuntu--lv: can't read superblock on /dev/mapper/ubuntu--vg-ubuntu--lv.
mount: /mnt/boot-sav/mapper/ubuntu--vg-ubuntu--lv: can't read superblock on /dev/mapper/ubuntu--vg-ubuntu--lv.
mount: /mnt/boot-sav/sdc2: cannot mount /dev/sdc2 read-only.
mount: /mnt/boot-sav/sdc2: cannot mount /dev/sdc2 read-only.
grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
mount: /mnt/boot-sav/mapper/ubuntu--vg-ubuntu--lv: can't read superblock on /dev/mapper/ubuntu--vg-ubuntu--lv.
mount: /mnt/boot-sav/mapper/ubuntu--vg-ubuntu--lv: can't read superblock on /dev/mapper/ubuntu--vg-ubuntu--lv.
mount: /mnt/boot-sav/sdc2: cannot mount /dev/sdc2 read-only.
mount: /mnt/boot-sav/sdc2: cannot mount /dev/sdc2 read-only.
sfdisk: /dev/sda: does not contain a recognized partition table


Recommended repair: ____________________________________________________________


The default repair of the Boot-Repair utility will restore the [(generic mbr)] MBR in sda, and make it boot on sdc2.
Additional repair will be performed: unhide-bootmenu-13s






============================== Restore MBR of sda ==============================


dd if=/usr/lib/syslinux/mbr/mbr.bin of=/dev/sda
parted /dev/sdc set 2 boot on
Warning: Unable to open /dev/sdc read-write (Read-only file system).  /dev/sdc
has been opened read-only.
Warning: Unable to open /dev/sdc read-write (Read-only file system).  /dev/sdc
has been opened read-only.
Error: Can't write to /dev/sdc, because it is opened read-only.


                                                                          


                                                                          


                                                                          
SET@_progressbar1.pulse()


Boot successfully repaired.


You can now reboot your computer.




============================ Boot Info After Repair ============================


 => Grub2 (v2.00) is installed in the MBR of /dev/sdc and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt2)/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------


sdc1: __________________________________________________________________________


    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 


sdc2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sdc2: cannot mount /dev/sdc2 read-only.


sdc3: __________________________________________________________________________


    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 


sda: ___________________________________________________________________________


    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info: 
    Operating System:  
    Boot files:        


sdb: ___________________________________________________________________________


    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg




================================ 1 OS detected =================================


OS#1:   Ubuntu 22.04.1 LTS on mapper/ubuntu--vg-ubuntu--lv


============================ Architecture/Host Info ============================


CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)




===================================== UEFI =====================================


This live-session is not in EFI-mode.






============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda	: notGPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, has-os,	2048 sectors * 512 bytes
sdc	: is-GPT,	hasBIOSboot,	has-noESP, 	usb-disk,	not-mmc, no-os,	2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


mapper/ubuntu--vg-ubuntu--lv	: is-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sdc2	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far


Partitions info (2/3): _________________________________________________________


mapper/ubuntu--vg-ubuntu--lv	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sdc2	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot


Partitions info (3/3): _________________________________________________________


mapper/ubuntu--vg-ubuntu--lv	: not-sepboot,	no-boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	std-grub.d,	sda
sdc2	: maybesepboot,	no-boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	std-grub.d,	sdc


fdisk -l (filtered): ___________________________________________________________


Disk sda: 10.9 TiB, 12000675495936 bytes, 23438819328 sectors
Disk sdb: 29.1 GiB, 31260704768 bytes, 61056064 sectors
Disk identifier: 0x2c534026
      Boot Start     End Sectors  Size Id Type
sdb1  *        0 1802239 1802240  880M  0 Empty
sdb2         964    5891    4928  2.4M ef EFI (FAT-12/16/32)
Disk sdc: 116.5 GiB, 125069950976 bytes, 244277248 sectors
Disk identifier: A7792ED5-F38C-4F42-B434-3E211C93CB88
        Start       End   Sectors   Size Type
sdc1     2048      4095      2048     1M BIOS boot
sdc2     4096   4198399   4194304     2G Linux filesystem
sdc3  4198400 244275199 240076800 114.5G Linux filesystem
Disk mapper/ubuntu--vg-ubuntu--lv: 114.5 GiB, 122918273024 bytes, 240074752 sectors
Disk zram0: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram1: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram2: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram3: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram4: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram5: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram6: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram7: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram8: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram9: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram10: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram11: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram12: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram13: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram14: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram15: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram16: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram17: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram18: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram19: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram20: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram21: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram22: 1005.8 MiB, 1054621696 bytes, 257476 sectors
Disk zram23: 1005.8 MiB, 1054621696 bytes, 257476 sectors


parted -lm (filtered): _________________________________________________________


sda:12.0TB:scsi:512:512:loop:DELL PERC H700:;
1:0.00B:12.0TB:12.0TB:ext4::;
sdb:31.3GB:scsi:512:512:msdos:SanDisk Cruzer Glide:;
2:494kB:3017kB:2523kB:::esp;
sdc:125GB:scsi:512:512:gpt:Multiple Card Reader:;
1:1049kB:2097kB:1049kB:::bios_grub;
2:2097kB:2150MB:2147MB:ext4::;
3:2150MB:125GB:123GB:::;
mapper/ubuntu--vg-ubuntu--lv:123GB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:123GB:123GB:ext4::;
zram21:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram5:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram11:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram3:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram18:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram1:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram16:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram8:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram14:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram22:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram6:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram12:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram20:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram4:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram10:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram19:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram2:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram17:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram0:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram9:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram15:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram23:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram7:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;
zram13:1055MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1055MB:1055MB:linux-swap(v1)::;


blkid (filtered): ______________________________________________________________


NAME                      FSTYPE      UUID                                   PARTUUID                             LABEL                  PARTLABEL
sda                       ext4        a9f73fb0-7d1b-44c4-a47c-e2b5e57f3ff5                                                               
sdb                       iso9660     2020-06-13-00-42-55-00                                                      Boot-Repair-Disk 64bit 
&#9500;&#9472;sdb1                    iso9660     2020-06-13-00-42-55-00                 2c534026-01                          Boot-Repair-Disk 64bit 
&#9492;&#9472;sdb2                    vfat        D055-8513                              2c534026-02                          Boot-Repair-Disk 64bit 
sdc                                                                                                                                      
&#9500;&#9472;sdc1                                                                       9c1db13e-ad71-4d64-9758-9eb1b7adb1bc                        
&#9500;&#9472;sdc2                    ext4        c3a3245b-1df7-4a88-9c1f-a08aa411119f   aaf526da-3290-453a-a168-157a683a597b                        
&#9492;&#9472;sdc3                    LVM2_member 7zhqz8-9h9o-SLjw-opyK-Zf8l-83Pa-amr4OC 93e0e685-f57a-44e7-8a4d-a792e7bd244f                        
  &#9492;&#9472;ubuntu--vg-ubuntu--lv ext4        60e93bdb-852b-4e0c-ab1d-b0d073d1cb08                                                               
zram0                                                                                                                                    
zram1                                                                                                                                    
zram2                                                                                                                                    
zram3                                                                                                                                    
zram4                                                                                                                                    
zram5                                                                                                                                    
zram6                                                                                                                                    
zram7                                                                                                                                    
zram8                                                                                                                                    
zram9                                                                                                                                    
zram10                                                                                                                                   
zram11                                                                                                                                   
zram12                                                                                                                                   
zram13                                                                                                                                   
zram14                                                                                                                                   
zram15                                                                                                                                   
zram16                                                                                                                                   
zram17                                                                                                                                   
zram18                                                                                                                                   
zram19                                                                                                                                   
zram20                                                                                                                                   
zram21                                                                                                                                   
zram22                                                                                                                                   
zram23                                                                                                                                   


df (filtered): _________________________________________________________________


      Avail Use% Mounted on
sdb        0 100% /cdrom


Mount options: __________________________________________________________________


sdb    ro,noatime,nojoliet,check=s,map=n,blocksize=2048


============================== ls -R /dev/mapper/ ==============================


/dev/mapper:
control
ubuntu--vg-ubuntu--lv


====================== sdb/boot/grub/grub.cfg (filtered) =======================


Boot-Repair-Disk session
Boot-Repair-Disk session (failsafe)


==================== sdb: Location of files loaded by Grub =====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1




======================== Unknown MBRs/Boot Sectors/etc =========================


Unknown BootLoader on sda


00000000  33 c0 fa 8e d8 8e d0 bc  00 7c 89 e6 06 57 8e c0  |3........|...W..|
00000010  fb fc bf 00 06 b9 00 01  f3 a5 ea 1f 06 00 00 52  |...............R|
00000020  52 b4 41 bb aa 55 31 c9  30 f6 f9 cd 13 72 13 81  |R.A..U1.0....r..|
00000030  fb 55 aa 75 0d d1 e9 73  09 66 c7 06 8d 06 b4 42  |.U.u...s.f.....B|
00000040  eb 15 5a b4 08 cd 13 83  e1 3f 51 0f b6 c6 40 f7  |..Z......?Q...@.|
00000050  e1 52 50 66 31 c0 66 99  e8 66 00 e8 35 01 4d 69  |.RPf1.f..f..5.Mi|
00000060  73 73 69 6e 67 20 6f 70  65 72 61 74 69 6e 67 20  |ssing operating |
00000070  73 79 73 74 65 6d 2e 0d  0a 66 60 66 31 d2 bb 00  |system...f`f1...|
00000080  7c 66 52 66 50 06 53 6a  01 6a 10 89 e6 66 f7 36  ||fRfP.Sj.j...f.6|
00000090  f4 7b c0 e4 06 88 e1 88  c5 92 f6 36 f8 7b 88 c6  |.{.........6.{..|
000000a0  08 e1 41 b8 01 02 8a 16  fa 7b cd 13 8d 64 10 66  |..A......{...d.f|
000000b0  61 c3 e8 c4 ff be be 7d  bf be 07 b9 20 00 f3 a5  |a......}.... ...|
000000c0  c3 66 60 89 e5 bb be 07  b9 04 00 31 c0 53 51 f6  |.f`........1.SQ.|
000000d0  07 80 74 03 40 89 de 83  c3 10 e2 f3 48 74 5b 79  |..t.@.......Ht[y|
000000e0  39 59 5b 8a 47 04 3c 0f  74 06 24 7f 3c 05 75 22  |9Y[.G.<.t.$.<.u"|
000000f0  66 8b 47 08 66 8b 56 14  66 01 d0 66 21 d2 75 03  |f.G.f.V.f..f!.u.|
00000100  66 89 c2 e8 ac ff 72 03  e8 b6 ff 66 8b 46 1c e8  |f.....r....f.F..|
00000110  a0 ff 83 c3 10 e2 cc 66  61 c3 e8 76 00 4d 75 6c  |.......fa..v.Mul|
00000120  74 69 70 6c 65 20 61 63  74 69 76 65 20 70 61 72  |tiple active par|
00000130  74 69 74 69 6f 6e 73 2e  0d 0a 66 8b 44 08 66 03  |titions...f.D.f.|
00000140  46 1c 66 89 44 08 e8 30  ff 72 27 66 81 3e 00 7c  |F.f.D..0.r'f.>.||
00000150  58 46 53 42 75 09 66 83  c0 04 e8 1c ff 72 13 81  |XFSBu.f......r..|
00000160  3e fe 7d 55 aa 0f 85 f2  fe bc fa 7b 5a 5f 07 fa  |>.}U.......{Z_..|
00000170  ff e4 e8 1e 00 4f 70 65  72 61 74 69 6e 67 20 73  |.....Operating s|
00000180  79 73 74 65 6d 20 6c 6f  61 64 20 65 72 72 6f 72  |ystem load error|
00000190  2e 0d 0a 5e ac b4 0e 8a  3e 62 04 b3 07 cd 10 3c  |...^....>b.....<|
000001a0  0a 75 f1 cd 18 f4 eb fd  00 00 00 00 00 00 00 00  |.u..............|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200


Unknown BootLoader on sdb


00000000  33 ed 90 90 90 90 90 90  90 90 90 90 90 90 90 90  |3...............|
00000010  90 90 90 90 90 90 90 90  90 90 90 90 90 90 90 90  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f3 06 b4 42 eb 15 eb 02  |...t.f.....B....|
00000070  31 c9 5a 51 b4 08 cd 13  5b 0f b6 c6 40 50 83 e1  |1.ZQ....[...@P..|
00000080  3f 51 f7 e1 53 52 50 bb  00 7c b9 04 00 66 a1 b0  |?Q..SRP..|...f..|
00000090  07 e8 44 00 0f 82 80 00  66 40 80 c7 02 e2 f2 66  |..D.....f@.....f|
000000a0  81 3e 40 7c fb c0 78 70  75 09 fa bc ec 7b ea 44  |.>@|..xpu....{.D|
000000b0  7c 00 00 e8 83 00 69 73  6f 6c 69 6e 75 78 2e 62  ||.....isolinux.b|
000000c0  69 6e 20 6d 69 73 73 69  6e 67 20 6f 72 20 63 6f  |in missing or co|
000000d0  72 72 75 70 74 2e 0d 0a  66 60 66 31 d2 66 03 06  |rrupt...f`f1.f..|
000000e0  f8 7b 66 13 16 fc 7b 66  52 66 50 06 53 6a 01 6a  |.{f...{fRfP.Sj.j|
000000f0  10 89 e6 66 f7 36 e8 7b  c0 e4 06 88 e1 88 c5 92  |...f.6.{........|
00000100  f6 36 ee 7b 88 c6 08 e1  41 b8 01 02 8a 16 f2 7b  |.6.{....A......{|
00000110  cd 13 8d 64 10 66 61 c3  e8 1e 00 4f 70 65 72 61  |...d.fa....Opera|
00000120  74 69 6e 67 20 73 79 73  74 65 6d 20 6c 6f 61 64  |ting system load|
00000130  20 65 72 72 6f 72 2e 0d  0a 5e ac b4 0e 8a 3e 62  | error...^....>b|
00000140  04 b3 07 cd 10 3c 0a 75  f1 cd 18 f4 eb fd 00 00  |.....<.u........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  04 17 00 00 00 00 00 00  26 40 53 2c 00 00 80 00  |........&@S,....|
000001c0  01 00 00 3f e0 6f 00 00  00 00 00 80 1b 00 00 fe  |...?.o..........|
000001d0  ff ff ef fe ff ff c4 03  00 00 40 13 00 00 00 00  |..........@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




=============================== StdErr Messages ================================


File descriptor 63 (pipe:[29324]) leaked on lvs invocation. Parent PID 2184: /bin/bash
File descriptor 63 (pipe:[29324]) leaked on lvchange invocation. Parent PID 14200: /bin/bash
/usr/share/boot-sav/b-i-s-functions.sh: line 1653: 240074752S: value too great for base (error token is "240074752S")
mdadm: No arrays found in config file or automatically
```

---

### Post by oldfred on 2022-11-22
You say RAID, but no RAID found.
You do show LVM on sdc.
And unpartitioned, formatted 12TB sda drive.
Your sdb is the flash drive.
Is that all correct or is another drive missing for the RAID?

And is sda really unpartitioned. Most Linux tools expect partitions, and unpartitioned drives are like very large floppy drives. You often then have to mount in a manner similar to a floppy drive as standard tools mount partitions.

Power failure often corrupts data. And then at the minimum you need to run fsck or e2fsck on all ext4 partitions.

---

### Post by madmandrew on 2022-11-23
I'm not sure how to dump the logs when it's not fully booting.  so I took some pictures.  I did try fsck already and it fails.  and yes I have a hardware raid that stores all my media then I mount to the linux system (for plex server).  I did that so I wouldn't loose data if something like this happened.

here's some images of the logs from failing to boot and failing to fsck
[https://ibb.co/HtDH69n](https://ibb.co/HtDH69n)
[https://ibb.co/RzmxY6r](https://ibb.co/RzmxY6r)
[https://ibb.co/xmwsF1H](https://ibb.co/xmwsF1H)
[https://ibb.co/zHLJ8pW](https://ibb.co/zHLJ8pW)

---

### Post by oldfred on 2022-11-23
I do not know RAID nor LVM.
Those that do know LVM, suggest if repairs take more than an hour, better to just reinstall & restore from backup.

You missed that RAID is not backup, but is for uptime.
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

Is sdc your boot drive and then do you mount RAID for data only.
Can you comment out RAID mount, so you can boot?
Or fix LVM install. But if part of boot on RAID then you have to resolve that first.
What type of RAID?

---

### Post by madmandrew on 2022-11-23
I have a 128gb internal usb flash drive that the os is installed on I think thats the LVM?  The RAID should be irrelevant (I think) to the boot issues. and yes it's external so I have it mount the RAID drive on boot for data only.

---

### Post by oldfred on 2022-11-23
Flash drives are known to be the least reliable of drives compared to HDDs & SSDs.
Some are better than others.

If system cannot mount a drive in fstab when booting, it has to timeout, but then should boot.
It does look like the sdc in the report is the boot drive.
sdc:125GB:scsi:512:512:gpt:Multiple Card Reader:;

---

### Post by madmandrew on 2022-11-23
ya I just ordered a cheap nvme and PCIE adapter to replace that setup... 

is there any way I can try and recover the boot drive though?  I have a solid day or so of work into getting the whole system setup it would be nice get it up and working to make an image that I could transfer to the new drive?

---

### Post by oldfred on 2022-11-23
From a live installer flash drive can you then mount your boot drive?

I always suggest new install & restore from backup.

I have a SSD in a USB3 to m.2 adapter. It is almost as fast as internal SSD.
Not sure NVMe to USB3 will be faster than SSD unless you have faster USB-C type connections. 
Since I already have multiple flash drives, I now plan the use SSD in M.2/USB adapter or external SSD drives for data backup & installing.

---

