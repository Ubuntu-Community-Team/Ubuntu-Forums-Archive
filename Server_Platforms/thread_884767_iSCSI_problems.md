---
title: "iSCSI problems"
date: 2008-08-09
forum: Server Platforms
---

### Post by lymond01 on 2008-08-09
I'm using Ubuntu with openiscsi as a target.  The fileserver is a Windows 2003 box pointing to the Ubuntu target.  This was all fine until I needed to reboot the Ubuntu box.  Even after also rebooting the Windows box, the "drive" in Windows Disk Administrator shows as unallocated space, ready to be partitioned and formatted.  It lost its drive letter, etc.

Do I need to do something on the Linux side to get the data viewable again?

---

### Post by promodus on 2008-08-09
> **lymond01 said:**
> I'm using Ubuntu with openiscsi as a target.  The fileserver is a Windows 2003 box pointing to the Ubuntu target.  This was all fine until I needed to reboot the Ubuntu box.  Even after also rebooting the Windows box, the "drive" in Windows Disk Administrator shows as unallocated space, ready to be partitioned and formatted.  It lost its drive letter, etc.

Do I need to do something on the Linux side to get the data viewable again?


Did you reboot the Linux server while the server 2003 box was still on?

---

### Post by lymond01 on 2008-08-09
Yes...we were testing a UPS and downed a bunch of boxes, including the raid with the iSCSI target.  What's the proper sequence to handle an iSCSI reboot?

---

### Post by lymond01 on 2008-08-12
Turns out that unexpected iSCSI disconnects have the effect of yanking a live drive -- multiple results could occur.  In our case, the partition table was corrupted and Windows saw the iSCSI target as a fresh drive (or at least unreadable so it just wanted to format it).  Using Active Partition Recovery ([http://www.partition-recovery.com/](http://www.partition-recovery.com/)) fixed the drive in a couple seconds.  Back to normal.

So, the order things should happen:

1) Use MS iSCSI initiator and log off the iSCSI target, or simply down the Windows host server.
2) THEN do whatever you need to do with the iSCSI target.

---

### Post by promodus on 2008-08-13
> **lymond01 said:**
> Turns out that unexpected iSCSI disconnects have the effect of yanking a live drive -- multiple results could occur.  In our case, the partition table was corrupted and Windows saw the iSCSI target as a fresh drive (or at least unreadable so it just wanted to format it).  Using Active Partition Recovery ([http://www.partition-recovery.com/](http://www.partition-recovery.com/)) fixed the drive in a couple seconds.  Back to normal.

So, the order things should happen:

1) Use MS iSCSI initiator and log off the iSCSI target, or simply down the Windows host server.
2) THEN do whatever you need to do with the iSCSI target.

Well... yeah :)

First get unlocker for windows:
[http://ccollomb.free.fr/unlocker/](http://ccollomb.free.fr/unlocker/)
You'll want to make sure there are no open file pointers on the drive!
Stop all services, close any programs.

Secondly sync the drive before disconnecting.
Get a program called "Sync" 
[http://technet.microsoft.com/en-us/sysinternals/bb897438.aspx](http://technet.microsoft.com/en-us/sysinternals/bb897438.aspx)

Disclaimer:
Depending on what is on the drive and how it was being used - some of your data could be corrupt... There is no way to tell if there where any open file pointers where files where being written to. If you have any sort of database running on this drive, I'd be running tests to check data integrity.

Lastly, if you have to, disable the drive in the device manager if you are unable to disconnect the initiator. Make the drive unavailable via software before doing a hard disconnect.

---

