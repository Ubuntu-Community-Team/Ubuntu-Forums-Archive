---
title: "Ecrypted external hard drive partition won't mount or unmount"
date: 2010-11-15
forum: Security
---

### Post by Blueyak on 2010-11-15
Hi,

I've been running Linux for a year on our family computers (one desktop, one laptop and two netbooks).  I've run into a problem with the encrypted ext4 partition (270GB) on a LaCie external hard drive which also has a NTFS partition (50GB) which is not encrypted .  First two times I tried using the encrypted ext4 partition (from two different computers) it worked fine but now I can't access it at all.  I can still access the NTFS partition.

[LIST]
[*]Encrypted external hard drive partition will unlock but won't mount (or unmount).  The computer says "Opening 320GB Hard Disk" but after a minute says, "Unable to mount location.  DBus error org.freedesktop.DBus.Error.NoReply"
[*]Disk utility (GUI for gparted I believe) states that the encrypted partition (/dev/sdb1) is unlocked and the underlying partition (/dev/dm-0) is not mounted but it has a "busy circle sign" on it that will not turn off. The NTFS partition on the same drive mounts and accesses normally.
[*]But if I try to unmount the NTFS partition, it says:  "Unable to stop drive.  One or more partitions are busy on /dev/sdb"
[*]If I try to shut down the computer, it is unable to shut down  because (I assume) it can't shut down that drive either.  So I have to  just turn off the computer.
[*]fdisk states that /dev/dm-0 doesn't have a valid partition table [full output attached]
[*]fsck suggests:  "Filesystem mounted or opened exclusively by another program?"
[*]ps axuf shows some processes running on /dev/dm-0 but killing them doesn't release the drive either. [full  output attached]
[*]I checked /etc/blkid.tab (suggested in one vaguely related thread) and there's no actual file only a broken link pointing to /dev/.blkid.tab (which doesn't exist).  I tried deleting this link and rebooting but that didn't change anything.
[*]when I finally gave up my data as lost, I tried to format the  partition (using Disk Utility) and it refused saying, "One or more block  devices are holding /dev/sdb"
[/LIST]
 Thanks for any help you can give me with this!

---

### Post by bodhi.zazen on 2010-11-23
Bump:

Thread moved at OP request.

---

