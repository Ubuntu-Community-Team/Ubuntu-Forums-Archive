---
title: "Error No Boot device available"
date: 2014-06-30
forum: Server Platforms
---

### Post by ebank36 on 2014-06-30
Hello I am running Ubuntu Server Edition 14.04 and I keep running into this problem. When I start the computer it says " No boot device available - strike F1 to retry  boot, F2 for setup utility" 
I have looked everywhere for a fix, but I found nothing that works. I just tried a Boot repair disc found at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and it did not work either. Here is another link to what it logged after [http://paste.ubuntu.com/7728122/](http://paste.ubuntu.com/7728122/).

```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 31Jan2013]


============================= Boot Info Summary: ===============================

 => No known boot loader is installed in the MBR of /dev/sda.

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sr0                                                iso9660    Boot-Repair-Disk 32bit

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sda



========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
File descriptor 8 (/proc/2493/mounts) leaked on lvscan invocation. Parent PID 27397: bash
File descriptor 18 (/usr/share/icons/lubuntu/places/16/folder.svg) leaked on lvscan invocation. Parent PID 27397: bash
  /dev/sda: read failed after 0 of 4096 at 0: Input/output error
  /dev/sda: read failed after 0 of 4096 at 4096: Input/output error
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-06-30__19h37 ===================
boot-repair version : 3.198~ppa16~raring
boot-sav version : 3.198~ppa16~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.198~ppa16~raring
File descriptor 8 (/proc/2493/mounts) leaked on lvs invocation. Parent PID 5307: /bin/sh
File descriptor 18 (/usr/share/icons/lubuntu/places/16/folder.svg) leaked on lvs invocation. Parent PID 5307: /bin/sh
/dev/sda: read failed after 0 of 4096 at 0: Input/output error
/dev/sda: read failed after 0 of 4096 at 4096: Input/output error
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 32bit 24avr2013, raring, Ubuntu, i686)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Boot-Repair-Disk 32bit" TYPE="iso9660"

=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:



=================== parted -l:


                                                                          
Error: /dev/sda: unrecognised disk label


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label

=================== parted -lm:


                                                                          
Error: /dev/sda: unrecognised disk label


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


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
gvfsd-fuse on /run/user/lubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)


=================== ls:
/sys/block/fd0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrom1 cdrw char console core cpu cpu_dma_latency disk dri dvd dvd1 dvdrw ecryptfs fb0 fd fd0 full fuse hidraw0 hidraw1 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sdb sdc sdd sde sg0 sg1 sg2 sg3 sg4 sg5 sg6 shm snapshot snd sr0 sr1 stderr stdin stdout uinput urandom vga_arbiter vhost-net zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs 1008M   20M  988M   2% /
udev           devtmpfs   993M   12K  993M   1% /dev
tmpfs          tmpfs      202M  760K  201M   1% /run
/dev/sr0       iso9660    496M  496M     0 100% /cdrom
/dev/loop0     squashfs   431M  431M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     1008M  8.0K 1008M   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs     1008M     0 1008M   0% /run/shm
none           tmpfs      100M   12K  100M   1% /run/user

=================== fdisk -l:



Error: no partitions

=================== Default settings
Recommended-Repair
This setting would reinstall the  of .

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.
```

---

### Post by oldfred on 2014-06-30
Please use code tags for longer terminal output.

BootInfo report barely sees that you have an sda.

Does BIOS see drive correctly?
What does Disks say about drive. It should show Smart Status.

Was this RAID or LVM? Those partitions do not always show correctly, but Boot-Repair is good about adding the drivers to a desktop type install.

---

### Post by ebank36 on 2014-07-01
The picture shows what my bios sees in the drives. SATA 1-3 are nothing so I have them turned off. Also if LVM is the encryption before the system boot then maybe, but it has been a while so I don't know for sure. Right now my SATA Operation is set to 
Raid Autodetect / AHCI there are however 3 more options ( Raid Autodetect / ATA, Raid On, Combination).

---

### Post by oldfred on 2014-07-01
AHCI is normally preferred, but if RAID do not know. If only one drive it should not be RAID.

I do not know what this error is:

ERROR: hpt37x:

One thread said there was a lock setting in BIOS?

Does Disks show more info on drive? And Smart Status in Disks?

Does testdisk show anything?

---

