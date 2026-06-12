---
title: "Cannot boot up in 'normal' mode into Vista 64 bit on dual Xp &amp; Vista Operating system"
date: 2016-12-03
forum: Windows
---

### Post by sonicpulse on 2016-12-03
Hello,

            I'm new to this forum and pretty much a novice when it comes to getting inside my operating system to solve problems and was hoping you bright people can advise me accordingly to get me out of this infuriating predicament I now find myself in.

I've recently used Partition Assistant Pro to increase the size of my program drive C . This entailed the operations of decreasing my D drive, moving my C drive across to where some of my D drive once was and increasing my C drive to take up that space left by my D drive.

Problem is that I cannot now boot up properly in normal mode into Vista. I can get past the dual boot option (which now states 'older version of windows' instead of XP?) and after choosing Vista I only get to the signing in page window where I add my password and press enter and it seems to then go blank after that....  nothing...

I've downloaded and ran the Ubuntu Bootable Repair Disc numerous times but although it states it has repaired the problems I still can't get any further than before and can only open in safe mode or suffer the same fate as above, and when I run the repair disc again in the default automatic mode it states there are repairs to be made and it does state that it repairs them but they don't seem to be repaired each time enough for me to overcome the boot problem in normal mode into Vista.

I presume I will need to do some manual commands to over come this problem but I have no idea what to do or when to do it or for that matter where to do it from!

Please can you assist me?

Specs:-

Toshiba Satellite P100 - 150
Upgraded to 4 GB memory
Dual Boot Windows XP Home & Vista 64 Bit Ultimate

Novice Repairer - Please be clear and concise  - One step at a time so I can't make matters worse?!



Repair Result File:-

*
```
**Paste from boot-repair at Sat, 3 Dec 2016 17:53:37 +0000**

  [Download as text]("http://paste.ubuntu.com/23573818/plain/")
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   209,728,574   209,728,512   7 NTFS / exFAT / HPFS
/dev/sda2         209,728,575   557,142,061   347,413,487   7 NTFS / exFAT / HPFS
/dev/sda3         557,142,062   976,771,119   419,629,058   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        8474115F741154F0                       ntfs       
/dev/sda2        400C2F301EC28A25                       ntfs       
/dev/sda3        469A614B7E7EEEA4                       ntfs       
/dev/sr0                                                iso9660    Boot-Repair-Disk 64bit
/dev/zram0       0bdb4fff-bb14-4648-936b-514e1acd6365   swap       
/dev/zram1       6214dc2f-7f17-4a05-95f8-78ba8a940ce7   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Dec  3 17:51 ata-MATSHITADVD-RAM_UJ-850S_HB86_134394 -> ../../sr0
lrwxrwxrwx 1 root root  9 Dec  3 17:53 ata-TOSHIBA_MK5055GSX_39JIF4NZS -> ../../sda
lrwxrwxrwx 1 root root 10 Dec  3 17:53 ata-TOSHIBA_MK5055GSX_39JIF4NZS-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Dec  3 17:53 ata-TOSHIBA_MK5055GSX_39JIF4NZS-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Dec  3 17:53 ata-TOSHIBA_MK5055GSX_39JIF4NZS-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Dec  3 17:53 wwn-0x50000391a7005ca0 -> ../../sda
lrwxrwxrwx 1 root root 10 Dec  3 17:53 wwn-0x50000391a7005ca0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Dec  3 17:53 wwn-0x50000391a7005ca0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Dec  3 17:53 wwn-0x50000391a7005ca0-part3 -> ../../sda3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/2953/mounts) leaked on lvs invocation. Parent PID 9726: bash
File descriptor 63 (pipe:[27183]) leaked on lvs invocation. Parent PID 9726: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-12-03__17h52 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/2953/mounts) leaked on lvs invocation. Parent PID 4705: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

=================== os-prober:
/dev/sda1:Windows Vista (loader):Windows:chain

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="8474115F741154F0" TYPE="ntfs"
/dev/sda2: UUID="400C2F301EC28A25" TYPE="ntfs"
/dev/sda3: UUID="469A614B7E7EEEA4" TYPE="ntfs"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/zram0: UUID="0bdb4fff-bb14-4648-936b-514e1acd6365" TYPE="swap"
/dev/zram1: UUID="6214dc2f-7f17-4a05-95f8-78ba8a940ce7" TYPE="swap"


1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda2.
=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA TOSHIBA MK5055GS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  107GB  107GB  primary  ntfs         boot
2      107GB   285GB  178GB  primary  ntfs
3      285GB   500GB  215GB  primary  ntfs



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:512:msdos:ATA TOSHIBA MK5055GS;
1:32.3kB:107GB:107GB:ntfs::boot;
2:107GB:285GB:178GB:ntfs::;
3:285GB:500GB:215GB:ntfs::;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
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
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  agpgart autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse fw0 hidraw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  ff 33 80 0c 00 00 00 00  |.........3......|
00000030  00 00 0c 00 00 00 00 00  0d 2b 00 00 00 00 00 00  |.........+......|
00000040  f6 00 00 00 01 00 00 00  f0 54 11 74 5f 11 74 84  |.........T.t_.t.|
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

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 34 80 0c  |........?...?4..|
00000020  00 00 00 00 80 00 80 00  ee 1b b5 14 00 00 00 00  |................|
00000030  04 00 00 00 00 00 00 00  9b bb 98 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  25 8a c2 1e 30 2f 0c 40  |........%...0/.@|
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

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 2e 50 35 21  |........?....P5!|
00000020  00 00 00 00 80 00 80 00  01 08 03 19 00 00 00 00  |................|
00000030  04 00 00 00 00 00 00 00  d5 4f 01 00 00 00 00 00  |.........O......|
00000040  f6 00 00 00 01 00 00 00  a4 ee 7e 7e 4b 61 9a 46  |..........~~Ka.F|
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
/cow           overlayfs  1.5G  5.1M  1.5G   1% /
udev           devtmpfs   1.5G   12K  1.5G   1% /dev
tmpfs          tmpfs      301M  1.1M  300M   1% /run
/dev/sr0       iso9660    614M  614M     0 100% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.5G  8.0K  1.5G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.5G     0  1.5G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sda1      fuseblk    101G   68G   33G  68% /mnt/boot-sav/sda1
/dev/sda2      fuseblk    166G  147G   19G  89% /mnt/boot-sav/sda2
/dev/sda3      fuseblk    201G   99G  102G  50% /mnt/boot-sav/sda3

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x15651564

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   209728574   104864256    7  HPFS/NTFS/exFAT
/dev/sda2       209728575   557142061   173706743+   7  HPFS/NTFS/exFAT
/dev/sda3       557142062   976771119   209814529    7  HPFS/NTFS/exFAT



=================== Recommended repair
The default repair of the Boot-Repair utility will restore the [(generic mbr)] MBR in sda, and make it boot on sda1.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 2
Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out

Boot successfully repaired.

You can now reboot your computer.
```

I have numerous repair disk results but they seem to say the same thing - Please can anyone assist me so I can overcome these repeated problems and so I can get back normal access into my Windows Vista 64 bit Ultimate operating system and then I'll try my XP option on the dual boot and see what happens there?!

Thank you for your time and understanding.

---

### Post by howefield on 2016-12-03
Thread moved to the "*Windows*" forum.

---

### Post by yancek on 2016-12-03
This forum is primarily for dealing with problems using Ubuntu/Linux and not windows.  Some minor problems may be solved by members who use both Ubuntu/Linux and windows.    The boot repair software may be able to solve some minor problems with booting windows but not all, it wasn't designed for that.

Moving the partitions moved the boot files in all likelihood.

You indicate you have tried numerous repair disk and they all 'said the same thing' but you neglected to post what that 'same thing' is??
You also do not indicate whether you can boot xp??
Do you have a vista install DVD?  That would be the place to start.  I would suggest you try to get help for your exclusive windows problem at support.microsoft.com or at some windows forum where you will find people who are more familiar with windows.

---

### Post by sonicpulse on 2016-12-03
Thank you for getting back to me Yancek.

Could you recommend any windows forums that you think may be of assistance please?

When I state they all seem give the same results I meant what is repaired at the end of the file log:-
"Recommended repair
The default repair of the Boot-Repair utility will restore the [(generic mbr)] MBR in sda, and make it boot on sda1.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 2
Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out

Boot successfully repaired.

You can now reboot your computer."

I've not tried the XP boot yet as I've been trying to overcome this Vista problem as this is the one I use all the time.

I don't have the installation discs. I think it was an OEM that came with the laptop and any discs that came with it are lost so that is why I tried the Ubuntu repair disc as research online suggests that it could fix windows problems. Microsoft are not much use as they no longer support Vista on their website and their helpline informed me that I'm on my own as they would not give me a repair disc to help resolve issues!

I suspect that the evidence in the sfc scan file log suggests that the 'move' request for the resizing of the drive partitions is still active from the numerous times I tried it but on restart it didn't do anything. It was only when restarting in safe mode in windows option that the resizing page came up and did what was requested. The problem is that now I can't open windows in 'normal' mode and I think it is to do with the remnants of the drive resizing instructions which repeatedly failed to come to fruition that may be u the underlying problem.

Anyone that can cast some light on the subject would be appreciated?

Thanks again for your reply.

---

### Post by yancek on 2016-12-03
I haven't really used windows on a regular basis for over ten years and never used vista.  If you just google 'vista support forums' you will get a lot of links.  Never used it so I don't know which are better/best.  Boot repair usually repairs the Grub bootloader which is Linux.  It may do minor repairs for a windows only system using syslinux.

After you changed the partitions, did you run chkdsk from windows until no errors were reported?  Should always do that when modifying a windows partition.

Windows bootloaders are backward compatible so booting xp from vista or a later windows version should not be difficult.  Doing the reverse will be problematic for a new user so stick with trying to boot vista.  If you don't have a vista CD/DVD, you can try to find a windows repair disk.  The only two I can think of that might help are Hirens Boot CD and Ultimate Bood CD.  Good luck.

---

### Post by sonicpulse on 2016-12-05
Thank you for the information in your reply - I didn't know about the Ultimate Boot CD.

I've ran a chkdsk which took hours but I wasn't around when it finished so I don't know the results or how to access them. At the start there were no errors but there may well have been in the later 4 & 5 stages - I'll do it again just in case.

I've downloaded Hiren's boot disc but to be honest once I entered that arena of options I had no idea how or what I should do so I thought it best to get out of there without doing anything before I could mess it up any more!

If anyone knows how to use this disc or what option to use and could give a novice like me a complete step by step guide so I can't make matters worse I may try using some of these programs but I'll feel happier with an easy repair disc that automatically corrects things at the press of a button as that may be the safer option at the moment. 

After lots of hours trying to find a free repairs disc or a copy of the Vista 64 bit installation or repair disc the only option seems to be to purchase one at Neosmart for about £20 - looks like Microsoft don't want people to access these discs any more leaving just one option to pay for it again?!

Many thanks for your time and information - It is appreciated!

---

### Post by yancek on 2016-12-05
Try googling "hirens boot cd tutorial", should get a lot of results so just pick one, or more.

---

