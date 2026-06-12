---
title: "I need help with a Boot-Repair Disk info file"
date: 2017-02-06
forum: Windows
---

### Post by krikri on 2017-02-06
Hello.

Here's the situation: I have a server with Windows Server 2008 R2 with the error of \Boot\BCD is missing. I tried offline repair and the result was "No OS file found on disk". Also tried all typicals commands as bootrec.exe ..... and nothing works. I dont have any backup.

I found this program Boot-Repair Disk i ran the info tool, but i dont know if this will be the solution.. 

The moment i run the tool i had:
- a USB drive (16GB) and 
- a HP HD 300GB with a the following partitions:
* system reserved (100mb) 
* C: 78GB
* D: 201GB in raw format.

So i need your kind help to guide me cause i dont know if this tool works with Windows server and if i shoul use the recomend repair option.

I attached the .txt file.

Thanks.

---

### Post by howefield on 2017-02-06
Thread moved to the "*Windows*" forum.

---

### Post by oldfred on 2017-02-06
Cannot open your .zip file. Better to just post link.

But looks like standard Windows BIOS/MBR configuration.
Do you have boot flag on sda1?
In sda1 are bootmgr and /Boot/BCD?

Boot-Repair can only do minor fixes to Windows, it really is for Linux systems. About all it can do is install a Windows type boot loader to MBR.
Most of Windows is copyrighted, so Linux tools cannot have files needed to repair a Windows system.

If you can start to boot into Windows does f8 get you into internal repair console?
If not you need your Windows repair/recovery disk or installer with repair console.

Often better to use command prompt and run Windows fixes.
[https://www.sevenforums.com/tutorials/681-startup-repair.html](https://www.sevenforums.com/tutorials/681-startup-repair.html)
[https://support.microsoft.com/en-us/help/927392/use-bootrec.exe-in-the-windows-re-to-troubleshoot-startup-issues](https://support.microsoft.com/en-us/help/927392/use-bootrec.exe-in-the-windows-re-to-troubleshoot-startup-issues)

---

### Post by krikri on 2017-02-06
It look like i do have the boot files in the windows partition but they dont work.. I cant enter with F8 i used the CD.

I dont have the link cause I save the file into the usb but and can copy it:

```

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]




============================= Boot Info Summary: ===============================


 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => Windows 7/8/2012 is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe


sda3: __________________________________________________________________________


    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''


sdb1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /menu.lst /grldr /grldr


sdb2: __________________________________________________________________________


    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''


sdb4: __________________________________________________________________________


    File system:       iso9660
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 300.0 GB, 299966445568 bytes
255 heads, 63 sectors/track, 36468 cylinders, total 585871964 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   163,839,999   163,633,152   7 NTFS / exFAT / HPFS
/dev/sda3         163,840,000   585,869,311   422,029,312   7 NTFS / exFAT / HPFS




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 15.6 GB, 15611199488 bytes
255 heads, 63 sectors/track, 1897 cylinders, total 30490624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *          2,048    30,459,176    30,457,129   7 NTFS / exFAT / HPFS
/dev/sdb2          30,459,177    30,459,239            63  21 Unknown
/dev/sdb4          12,888,616    14,144,359     1,255,744   0 Empty


/dev/sdb1 overlaps with /dev/sdb4


"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        0C0AF6770AF65D60                       ntfs       System Reserved
/dev/sda2        6E06244006240C21                       ntfs       
/dev/sdb1        7278D6F578D6B757                       ntfs       E2B
/dev/sdb4                                               iso9660    Boot-Repair-Disk 64bit
/dev/zram0       ee219182-5e07-4fd9-82c3-19e948246735   swap       
/dev/zram1       a85435c9-0a3d-4b2d-8647-7e4e0ae1ed8f   swap       
/dev/zram2       c596ae29-2939-4478-a5e5-6be6e74fd0c7   swap       
/dev/zram3       3a4f8733-652c-4fb9-b489-b3a5a13f0e41   swap       
/dev/zram4       e6ae1562-887d-49aa-b194-a730ac44ce6f   swap       
/dev/zram5       9f65288e-f336-4d69-8a82-260ad34e9d4a   swap       
/dev/zram6       ce4f9a5f-6290-4722-b598-415265b14e3a   swap       
/dev/zram7       0a5a630b-7236-4f23-97dc-ccac765e695e   swap       


========================= "ls -l /dev/disk/by-id" output: ======================


total 0
lrwxrwxrwx 1 root root  9 Feb  6 10:41 scsi-3600508b1001cac7a16929c6e5ad45ac0 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb  6 10:44 scsi-3600508b1001cac7a16929c6e5ad45ac0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb  6 10:44 scsi-3600508b1001cac7a16929c6e5ad45ac0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb  6 10:41 scsi-3600508b1001cac7a16929c6e5ad45ac0-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Feb  6 10:41 usb-Kingston_DataTraveler_2.0_60A44C3FAC7DED81E9721676-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb  6 10:41 usb-Kingston_DataTraveler_2.0_60A44C3FAC7DED81E9721676-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Feb  6 10:41 usb-Kingston_DataTraveler_2.0_60A44C3FAC7DED81E9721676-0:0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Feb  6 10:41 usb-Kingston_DataTraveler_2.0_60A44C3FAC7DED81E9721676-0:0-part4 -> ../../sdb4
lrwxrwxrwx 1 root root  9 Feb  6 10:41 wwn-0x600508b1001cac7a16929c6e5ad45ac0 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb  6 10:44 wwn-0x600508b1001cac7a16929c6e5ad45ac0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb  6 10:44 wwn-0x600508b1001cac7a16929c6e5ad45ac0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb  6 10:41 wwn-0x600508b1001cac7a16929c6e5ad45ac0-part3 -> ../../sda3


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/lubuntu/E2B       fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb4        /cdrom                   iso9660    (ro,noatime)




================================ sdb1/menu.lst: ================================


--------------------------------------------------------------------------------
#this is only to prevent the grub4dos default menu from appearing for a brief second!
clear
if "%grub%"=="" if exist (bd)/_ISO/e2b/grub/E2B_GRUB.txt set grub=_ISO/e2b/grub
if not "%grub%"=="" cat /%grub%/menu.lst > (md)0xa100+0x50 && configfile (md)0xa100+0x50
echo SORRY - CAN'T FIND \_ISO\e2b\grub\E2B_GRUB.txt FILE (please edit \menu.lst file)! && pause && commandline
--------------------------------------------------------------------------------


========================== sdb1/grldr embedded menu: ===========================


--------------------------------------------------------------------------------
pxe detect
configfile
default 0
timeout 1


title find /menu.lst, /boot/grub/menu.lst, /grub/menu.lst
	errorcheck off
	configfile /boot/grub/menu.lst
	configfile /grub/menu.lst
	if "%@root%"=="(ud)" && calc *0x82A0=*0x82b9&0xff
	if "%@root:~1,1%"=="f" && find --set-root --devices=f /menu.lst && configfile /menu.lst
	find --set-root --ignore-floppies --ignore-cd /menu.lst && configfile /menu.lst
	find --set-root --ignore-floppies --ignore-cd /boot/grub/menu.lst && configfile /boot/grub/menu.lst
	find --set-root --ignore-floppies --ignore-cd /grub/menu.lst && configfile /grub/menu.lst
	configfile [http://b.chenall.net/menu.lst](http://b.chenall.net/menu.lst)
	errorcheck on
	commandline


title commandline
	commandline


title reboot
	reboot


title halt
	halt




--------------------------------------------------------------------------------


=========================== sdb4/boot/grub/grub.cfg: ===========================


--------------------------------------------------------------------------------


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi


set menu_color_normal=white/black
set menu_color_highlight=black/light-gray


menuentry "Boot-Repair-Disk session" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------


======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sda3


00000000  cb cb cb cb cb cb cb cb  cb cb cb cb cb cb cb cb  |................|
*
00000200


Unknown BootLoader on sdb2


00000000  a6 be 03 e8 b9 68 b3 60  00 1d f4 cb da 04 57 42  |.....h.`......WB|
00000010  5b ba 96 22 5c b4 95 78  3a a2 34 80 0f d5 cf 9f  |[.."\..x:.4.....|
00000020  87 6b 35 ec de 5e 10 bd  9e 97 e7 03 65 88 57 04  |.k5..^......e.W.|
00000030  12 6d dd e3 1c 1f 01 00  09 7d 5d 53 e0 7f ca c5  |.m.......}]S....|
00000040  c0 98 f0 97 7a e8 17 1d  1b 3f bf 5c 46 db b7 b2  |....z....?.\F...|
00000050  03 d1 ed e4 24 c0 2f 3b  dc b9 ad f8 4e 2d 46 78  |....$./;....N-Fx|
00000060  88 48 30 d6 bd db 7f 85  34 8d 72 2f 85 2a 01 8c  |.H0.....4.r/.*..|
00000070  df ce 6f 4b e6 c3 a3 a1  f2 b0 aa 32 ba 79 bf 8a  |..oK.......2.y..|
00000080  c3 25 bd 05 8c 5f 1c 37  be 2e 7a 3e 5a 47 ca 58  |.%..._.7..z>ZG.X|
00000090  16 10 68 1f e0 5f 77 57  8a a0 4a 1c 17 0a f0 6b  |..h.._wW..J....k|
000000a0  a8 16 45 2d 82 47 22 f8  78 60 fa c7 15 c0 3b 26  |..E-.G".x`....;&|
000000b0  be 0c c2 71 98 1d 3f 20  f1 9d de 86 84 f3 ef 6a  |...q..? .......j|
000000c0  fe 13 0b cc 95 20 24 10  2d c7 ae c8 61 5d 43 5c  |..... $.-...a]C\|
000000d0  8b e1 4a 80 63 37 f3 9b  d2 f9 b0 e8 ec 7c ac 2a  |..J.c7.......|.*|
000000e0  88 ae 9e af e2 b0 c9 2f  41 63 17 c7 0d ef 8b 9e  |......./Ac......|
000000f0  8f b7 11 f2 95 05 84 1c  07 f8 17 fd cd e2 a8 12  |................|
00000100  87 05 c2 b5 dd e3 1c 1f  08 76 6a 00 00 17 5f 9a  |.........vj..._.|
00000110  0b 8f fc 58 43 54 77 40  26 ba 1d fe 3f 3e df a1  |...XCTw@&...?>..|
00000120  84 4c 31 87 98 56 c2 d8  ce 85 d1 76 e8 87 54 9b  |.L1..V.....v..T.|
00000130  d7 d8 35 eb 82 b0 11 f1  51 10 ec 29 5f 9e f2 21  |..5.....Q..)_..!|
00000140  6c 37 44 e7 48 df ad 02  b4 8d 36 ce 77 0a 40 80  |l7D.H.....6.w.@.|
00000150  85 20 5a df 4b 63 e7 b2  8f 57 31 20 9e 76 82 15  |. Z.Kc...W1 .v..|
00000160  b3 d8 16 3d f0 cc 7b 01  31 7d 89 97 11 e9 4f 98  |...=..{.1}....O.|
00000170  ed b8 79 4e fc 7f d2 b3  32 5b ca 71 f5 98 5f ea  |..yN....2[.q.._.|
00000180  f0 91 f3 d4 d6 4e b5 2e  83 27 ce a0 c0 33 01 b4  |.....N...'...3..|
00000190  5d 9a 01 a5 06 38 f2 8d  fc ee a3 fe 74 6c 3c 5b  |]....8......tl<[|
000001a0  0b 57 e7 bc 88 5b 0d d1  39 d2 37 f3 40 ad 2b 4d  |.W...[..9.7.@.+M|
000001b0  d2 9d c2 90 20 21 48 16  b7 d2 d8 f9 ec a3 f5 cc  |.... !H.........|
000001c0  48 27 9d 20 95 6d f6 25  8d 7c 33 1e c0 4c 5f 66  |H'. .m.%.|3..L_f|
000001d0  65 c4 9a 53 77 78 c7 07  c0 00 00 06 3d 5c 4c 4a  |e..Swx......=\LJ|
000001e0  5e 81 f3 cd 15 bc 1f ea  0a 01 23 d0 eb a1 3c 9a  |^.........#...<.|
000001f0  ac e8 bf 73 78 f5 c3 38  4e 77 0b 81 c5 74 da 39  |...sx..8Nw...t.9|
00000200




=============================== StdErr Messages: ===============================


File descriptor 9 (/proc/2821/mounts) leaked on lvs invocation. Parent PID 10370: bash
File descriptor 63 (pipe:[20259]) leaked on lvs invocation. Parent PID 10370: bash
  No volume groups found


ADDITIONAL INFORMATION :
=================== log of boot-repair 2017-02-06__10h41 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/2821/mounts) leaked on lvs invocation. Parent PID 4540: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --


=================== os-prober:




=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="System Reserved" UUID="0C0AF6770AF65D60" TYPE="ntfs"
/dev/sda2: UUID="6E06244006240C21" TYPE="ntfs"
/dev/sdb1: LABEL="E2B" UUID="7278D6F578D6B757" TYPE="ntfs"
/dev/sdb4: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/zram0: UUID="ee219182-5e07-4fd9-82c3-19e948246735" TYPE="swap"
/dev/zram1: UUID="a85435c9-0a3d-4b2d-8647-7e4e0ae1ed8f" TYPE="swap"
/dev/zram2: UUID="c596ae29-2939-4478-a5e5-6be6e74fd0c7" TYPE="swap"
/dev/zram3: UUID="3a4f8733-652c-4fb9-b489-b3a5a13f0e41" TYPE="swap"
/dev/zram4: UUID="e6ae1562-887d-49aa-b194-a730ac44ce6f" TYPE="swap"
/dev/zram5: UUID="9f65288e-f336-4d69-8a82-260ad34e9d4a" TYPE="swap"
/dev/zram6: UUID="ce4f9a5f-6290-4722-b598-415265b14e3a" TYPE="swap"
/dev/zram7: UUID="0a5a630b-7236-4f23-97dc-ccac765e695e" TYPE="swap"


Windows not detected by os-prober on sda2.
=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.




=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	bootmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda2.
sdb1	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/media/lubuntu/E2B.


sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes
sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	liveusb,	no-os,	2048 sectors * 512 bytes




=================== parted -l:


Model: HP LOGICAL VOLUME (scsi)
Disk /dev/sda: 300GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
1      1049kB  106MB   105MB   primary  ntfs         boot
2      106MB   83.9GB  83.8GB  primary  ntfs
3      83.9GB  300GB   216GB   primary




Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
1      1049kB  15.6GB  15.6GB  primary  ntfs         boot
2      15.6GB  15.6GB  32.3kB  primary






                                                                          
Error: /dev/zram0: unrecognised disk label




                                                                          
Error: /dev/zram1: unrecognised disk label




                                                                          
Error: /dev/zram2: unrecognised disk label




                                                                          
Error: /dev/zram3: unrecognised disk label




                                                                          
Error: /dev/zram4: unrecognised disk label




                                                                          
Error: /dev/zram5: unrecognised disk label




                                                                          
Error: /dev/zram6: unrecognised disk label




                                                                          
Error: /dev/zram7: unrecognised disk label


=================== parted -lm:


BYT;
/dev/sda:300GB:scsi:512:512:msdos:HP LOGICAL VOLUME;
1:1049kB:106MB:105MB:ntfs::boot;
2:106MB:83.9GB:83.8GB:ntfs::;
3:83.9GB:300GB:216GB:::;


BYT;
/dev/sdb:15.6GB:scsi:512:512:msdos:Kingston DataTraveler 2.0;
1:1049kB:15.6GB:15.6GB:ntfs::boot;
2:15.6GB:15.6GB:32.3kB:::;




                                                                          
Error: /dev/zram0: unrecognised disk label




                                                                          
Error: /dev/zram1: unrecognised disk label




                                                                          
Error: /dev/zram2: unrecognised disk label




                                                                          
Error: /dev/zram3: unrecognised disk label




                                                                          
Error: /dev/zram4: unrecognised disk label




                                                                          
Error: /dev/zram5: unrecognised disk label




                                                                          
Error: /dev/zram6: unrecognised disk label




                                                                          
Error: /dev/zram7: unrecognised disk label




=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb4 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sdb1 on /media/lubuntu/E2B type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)




=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb4 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet hpilo input kmsg kvm log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sdb2 sdb4 sg0 sg1 sg2 shm snapshot snd stderr stdin stdout uhid uinput urandom vga_arbiter vhci vhost-net watchdog zero
ls /dev/mapper:  control


=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  20 00 ff 00 00 08 00 00  |........ .......|
00000020  00 00 00 00 81 00 80 00  ff 1f 03 00 00 00 00 00  |................|
00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|
00000040  f6 00 00 00 01 00 00 00  60 5d f6 0a 77 f6 0a 0c  |........`]..w...|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200


=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  20 00 ff 00 00 28 03 00  |........ ....(..|
00000020  00 00 00 00 81 00 80 00  ff d7 c0 09 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  21 0c 24 06 40 24 06 6e  |........!.$.@$.n|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200


=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 00 00  28 bd d0 01 00 00 00 00  |........(.......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  57 b7 d6 78 f5 d6 78 72  |........W..x..xr|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200


=================== df -Th:


Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.9G  7.2M  3.9G   1% /
udev           devtmpfs   3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs      798M  1.2M  797M   1% /run
/dev/sdb4      iso9660    614M  614M     0 100% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.9G  8.0K  3.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      3.9G     0  3.9G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sdb1      fuseblk     15G  6.5G  8.1G  45% /media/lubuntu/E2B
/dev/sda1      fuseblk    100M   27M   74M  27% /mnt/boot-sav/sda1
/dev/sda2      fuseblk     79G   73G  5.5G  94% /mnt/boot-sav/sda2


=================== fdisk -l:


Disk /dev/sda: 300.0 GB, 299966445568 bytes
255 heads, 63 sectors/track, 36468 cylinders, total 585871964 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9e3a6bfb


Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   163839999    81816576    7  HPFS/NTFS/exFAT
/dev/sda3       163840000   585869311   211014656    7  HPFS/NTFS/exFAT


Disk /dev/sdb: 15.6 GB, 15611199488 bytes
255 heads, 63 sectors/track, 1897 cylinders, total 30490624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8609a4e8


Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    30459176    15228564+   7  HPFS/NTFS/exFAT
/dev/sdb2        30459177    30459239          31+  21  Unknown
/dev/sdb4        12888616    14144359      627872    0  Empty




adding: log/ (stored 0%)
adding: log/2017-02-06__10h41boot-repair42/ (stored 0%)
adding: log/2017-02-06__10h41boot-repair42/sdb1/ (stored 0%)
adding: log/2017-02-06__10h41boot-repair42/sdb/ (stored 0%)
adding: log/2017-02-06__10h41boot-repair42/sdb/partition_table.dmp (deflated 46%)
adding: log/2017-02-06__10h41boot-repair42/sdb/current_mbr.imgSET@_progressbar1.pulse()
(deflated 99%)
adding: log/2017-02-06__10h41boot-repair42/sda2/ (stored 0%)
adding: log/2017-02-06__10h41boot-repair42/sda1/ (stored 0%)
adding: log/2017-02-06__10h41boot-repair42/sda/ (stored 0%)
adding: log/2017-02-06__10h41boot-repair42/sda/partition_table.dmp (deflated 46%)
adding: log/2017-02-06__10h41boot-repair42/sda/current_mbr.img (deflated 100%)
adding: log/2017-02-06__10h41boot-repair42/boot-repair.log
zip warning:  file size changed while zipping log/2017-02-06__10h41boot-repair42/boot-repair.log
(deflated 76%)




=================== Suggested repair
The default repair of the Boot-Repair utility would restore the [(generic mbr)] MBR in sda, and make it boot on sda2.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot




=================== User settings
The settings chosen by the user will not act on the boot.

```

---

### Post by oldfred on 2017-02-06
Just as you said in first post, you are missing /Boot/BCD.
That cannot be fixed from Linux.

Whatever operating system you are running, you always need a repair/recovery flash drive or DVD to fix it.
And good backups as drives to fail, users make mistakes, and just things happen.

Did you run:
[FONT=arial]bootrec /rebuildbcd [/FONT]
[https://technet.microsoft.com/en-GB/library/hh824874.aspx](https://technet.microsoft.com/en-GB/library/hh824874.aspx) 
Repair BCD - not recommended for dual booting, just Windows repairs
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/) 

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp) 

      
 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

---

