---
title: "Problem setting up iSCSI to a ZFS vol on Opensolaris"
date: 2009-06-08
forum: Server Platforms
---

### Post by PorterHouse_01 on 2009-06-08
Can anyone help me with some advice on use/syntax and error conditions with iscsi.
I'm trying to establish an iscsi connection to a ZFS drive on an Opensolaris box. My ultimate objective (if it can be achieved) is have a Ubuntu/MythTV HTPC rsync'ing to a ZFS NAS, effectively. Note that neither box is running a server version but I don't think that's an issue here.
I have eventually established both target and initiator setups.
Target sees:

iscsitadm list target -v >

Target: idisk1
iSCSI Name: iqn.1986-03.com.sun:02:...(ctd)....idisk1
Connections: 1
Initiator: iSCSI Name: iqn. 1993-08.org.debian:01:...(etc)
Alias: HTPC_U904
ACL List:
TPGT List:
LUN Information:
LUN: 0
GUID: 600144f04a...(etc)
VID: Sun
PID: Solaris
Type: Disk
Size 10G
Backing Store: /tamk/backups/idisk1
Status: online


Initiator sees:

sudo iscsiadm -m node >
192.168.1.70:3260,1  iqn.1986-03.com.sun:02:...(ctd)....idisk1

Also note that there are errors which may or may not be significant -->
tail var/log/messages >
[95287.724068] scsi8 : iSCSI Initiator over TCP/IP
[95287.732916] nautilus [12221]: segfault at 21 ip 00000021 sp bff93b0c error 4 in nautilus [8048000+140000]
[95288.023281] scsi 8:0:0:0: Direct-Access SUN SOLARIS 1 PQ: 0 ANSI:5
[95288.024528] sd 8:0:0:0: [sdd] 20971520 512-byte hardware sectors (10737Mb)
[95288.024666] sd 8:0:0:0: [sdd] Write protect is off
[95288.024921] sd 8:0:0:0: [sdd] Write Cache: disabled, read cache enables, doesn't support DPO or FUA
[95288.025567] sd 8:0:0:0: [sdd] 20971520 512-byte hardware sectors (10737Mb)
[95288.025703] sd 8:0:0:0: [sdd] Write protect is off
[95288.026201] sd 8:0:0:0: [sdd] Write Cache: disabled, read cache enables, doesn't support DPO or FUA    
[95288.026207] sdd: unknown partition table
[95288.060686] sd 8:0:0:0: [sdd] Attached SCSI disk
[95288.060780] sd 8:0:0:0: [sdd] Attached scsi generic sg4 type 0
[95288.195103] nautilus [14210]: segfault at 21 ip 00000021 sp bfc43fbc error 4 in nautilus [8048000+140000]

sudo fdisk /dev/sdd >
Device contains neither a valid DOS partition table, nor SUN, SGI or OSF disklabel
Building a new DOS disklable with disk identifier 0xd123eaee
Changes will remain in memory only  until you decide to write them - after that the content won't be recoverable.
The number of cylinders for this disk is set to 10240. 
There is nothing wrong with that but this is larger than 1024 and could in certain setups cause problems with:
1) software that runs at boot time (eg old versions of LILO)
2) booting and partitioning software from other OSs (eg DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)
.
.

Can someone please explain:
1. Why should I need to fdisk the vol. Ideally I just want to mount it and use it as-is.
2. What are the errors telling me.
3. Note that the target is not a whole disk. Is this part of the problem.
4. If this isn't going to work, where should I go next ?

Any advice welcome.
Thanks
Duncan

---

### Post by bab1 on 2009-06-08
> **PorterHouse_01 said:**
> Can anyone help me with some advice on use/syntax and error conditions with iscsi...

Can someone please explain:
1. Why should I need to fdisk the vol. Ideally I just want to mount it and use it as-is.
2. What are the errors telling me.
3. Note that the target is not a whole disk. Is this part of the problem.
4. If this isn't going to work, where should I go next ?

Any advice welcome.
Thanks
Duncan

This is a great question for the folks at [_Nexenta_]("http://www.osnews.com/story/20280/Nexenta_Ubuntu_Server_with_ZFS_goodness").  

You can reach them at: [**http://www.nexenta.org/os/Community**]("http://www.nexenta.org/os/Community")

---

### Post by ghstridr on 2009-06-19
(If I understand ZFS correctly, the follow is true)
ZFS is a file system, not a raw device.
If you want to mount a zfs file system, export it via samba or nfs or use fuse.
If you want to use iscsi, you have to setup a target on the server to point at an unused disk, not one already formatted with zfs.
Then you setup an iscsi initiator on the client to import the target, then you fdisk/format it.  ZFS isn't involved.
(The preceeding may be false).

---

