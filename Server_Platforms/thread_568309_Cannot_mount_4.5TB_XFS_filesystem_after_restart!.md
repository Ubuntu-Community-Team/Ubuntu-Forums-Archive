---
title: "Cannot mount 4.5TB XFS filesystem after restart!"
date: 2007-10-05
forum: Server Platforms
---

### Post by smagister on 2007-10-05
Hello,

I have a problem with a large RAID-5 fileserver (4.5TB) and I would really appreciate any insight.
I'm running an Ubuntu 7.04 Server system (64-bit)

The output of uname -a is below (includes the kernel version):
Linux octo7 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64 GNU/Linux

The system is a Dell Poweredge 1950 dual quad core server, 4GB RAM with two PERC 5/I RAID controllers. One of the controllers controls an internal RAID-1 array of two 80GB drives. The second controller controls an external Dell FileVault MD1000 with 7x750GB drives in RAID-5 configuration. The problem I'm having is with this large (4.5TB) FileVault array.

I can do the following:
1)create a large 4.5TB partition using parted
2)then create an XFS filesystem,
3)mount the drive
4)write data to the drive

The problem is on restart: when I try to mount the drive I always get the following error:
mount: /dev/sdb1: can't read superblock

Luckily I found this before I put the machine into operation. I've looked pretty extensively through the forums here and elsewhere and haven't found much.

I'm planning on using LVM but I got the problem with LVM so I'm not using it at the moment while I troubleshoot this issue.

Below are the full details:

I started fresh, rebuilding the RAID-5 array using Dell's omconfig tools. Below is the output from omreport. It looks like the controller sees the disk array ok at /dev/sdb.

sam@octo7:~$ sudo omreport storage vdisk controller=1
Virtual Disk 0 on Controller PERC 5/E Adapter (Slot 1)

Controller PERC 5/E Adapter (Slot 1)
ID : 0
Status : Ok
Name : Virtual Disk 0
State : Ready
Progress : Not Applicable
Layout : RAID-5
Size : 4,188.75 GB (4497636065280 bytes)
Device Name : /dev/sdb
Type : SATA
Read Policy : No Read Ahead
Write Policy : Write Back
Cache Policy : Not Applicable
Stripe Element Size : 64 KB

Next, I run parted to create the disk label and the partition:

sam@octo7:~$ sudo parted /dev/sdb
Password:
GNU Parted 1.7.1
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mklabel gpt
(parted) print

Disk /dev/sdb: 4498GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number Start End Size File system Name Flags

(parted) mkpart primary 0 -1
(parted) print

Disk /dev/sdb: 4498GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number Start End Size File system Name Flags
1 17.4kB 4498GB 4498GB primary

(parted) quit

Then, I create an XFS partition:

sam@octo7:~$ sudo mkfs.xfs /dev/sdb1
meta-data=/dev/sdb1 isize=256 agcount=32, agsize=34314239 blks
= sectsz=512 attr=0
data = bsize=4096 blocks=1098055648, imaxpct=25
= sunit=0 swidth=0 blks, unwritten=1
naming =version 2 bsize=4096
log =internal log bsize=4096 blocks=32768, version=1
= sectsz=512 sunit=0 blks
realtime =none extsz=4096 blocks=0, rtextents=0

Then I mount the array:

sam@octo7:~$ sudo mount /dev/sdb1 /media/fileserver/
sam@octo7:~$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 70G 47G 20G 71% /
varrun 2.0G 72K 2.0G 1% /var/run
varlock 2.0G 0 2.0G 0% /var/lock
procbususb 2.0G 72K 2.0G 1% /proc/bus/usb
udev 2.0G 72K 2.0G 1% /dev
devshm 2.0G 0 2.0G 0% /dev/shm
lrm 2.0G 39M 1.9G 2% /lib/modules/2.6.20-16-generic/volatile
octo0:/home 448G 232G 193G 55% /misc/home
/dev/sdb1 4.1T 1.1M 4.1T 1% /media/fileserver


So far so good. I then copy a few hundred MB of files to test stuff out and everything works fine.

Then I restart, and the problems begin.

sam@octo7:/media/fileserver$ sudo shutdown -r now

Broadcast message from sam@octo7
(/dev/pts/2) at 23:30 ...

The system is going down for reboot NOW!

The system boots up fine, and I see this in dmesg, which seems fine...

[ 106.596261] scsi 1:2:0:0: Direct-Access DELL PERC 5/E Adapter 1.03 PQ: 0 ANSI: 5
[ 106.604643] scsi 1:0:17:0: Attached scsi generic sg2 type 13
[ 106.604747] sdb : very big device. try to use READ CAPACITY(16).
[ 106.604776] SCSI device sdb: 8784445440 512-byte hdwr sectors (4497636 MB)
[ 106.604815] sdb: Write Protect is off
[ 106.604817] sdb: Mode Sense: 1f 00 10 08
[ 106.604873] SCSI device sdb: write cache: disabled, read cache: enabled, supports DPO and FUA
[ 106.604970] sdb : very big device. try to use READ CAPACITY(16).
[ 106.604997] SCSI device sdb: 8784445440 512-byte hdwr sectors (4497636 MB)
[ 106.605028] sdb: Write Protect is off
[ 106.605030] sdb: Mode Sense: 1f 00 10 08
[ 106.605085] SCSI device sdb: write cache: disabled, read cache: enabled, supports DPO and FUA
[ 106.605088] sdb: sdb1
[ 106.626409] sd 1:2:0:0: Attached scsi disk sdb

Then I get kicked in the teeth:

sam@octo7:~$ sudo mount /dev/sdb1 /media/fileserver/
Password:
mount: /dev/sdb1: can't read superblock


And checking dmesg again, we see the following appended to the end:

[ 250.562878] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[ 250.564176] SGI XFS Quota Management subsystem
[ 250.564665] attempt to access beyond end of device
[ 250.564670] sdb1: rw=0, want=8784445184, limit=194510781
[ 250.564675] I/O error in filesystem ("sdb1") meta-data dev sdb1 block 0x20b97feff ("xfs_read_buf") error 5 buf count 512
[ 250.564816] XFS: size check 2 failed


And the following is at the end of /var/log/syslog

Oct 4 23:35:26 octo7 kernel: [ 250.562878] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Oct 4 23:35:26 octo7 kernel: [ 250.564176] SGI XFS Quota Management subsystem
Oct 4 23:35:26 octo7 kernel: [ 250.564665] attempt to access beyond end of device
Oct 4 23:35:26 octo7 kernel: [ 250.564670] sdb1: rw=0, want=8784445184, limit=194510781
Oct 4 23:35:26 octo7 kernel: [ 250.564675] I/O error in filesystem ("sdb1") meta-data dev sdb1 block 0x20b97feff ("xfs_read_buf") error 5 buf count 512
Oct 4 23:35:26 octo7 kernel: [ 250.564816] XFS: size check 2 failed
Oct 4 23:35:44 octo7 Server Administrator: Storage Service EventID: 2164 See readme.txt for a list of validated controller driver versions.

So I have two thoughts:
The kernel/version of Ubuntu is not playing nice with the RAID controller. The last message about "See readme.txt for a list of validated controller driver versions" is kind of cryptic...where exactly is this file? The main problem seems to be the business about "attempt to access beyond end of device" Why is it doing that?
OR
The RAID controller is messed up and I should talk to DELL.

Sorry if this message is on the long side, I've tried to make it as complete as I can. Like I said, I would GREATLY appreciate any insight here.

Sam

---

