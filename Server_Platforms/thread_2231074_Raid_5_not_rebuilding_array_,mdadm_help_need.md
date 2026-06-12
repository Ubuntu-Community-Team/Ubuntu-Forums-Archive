---
title: "Raid 5 not rebuilding array ,mdadm help need"
date: 2014-06-23
forum: Server Platforms
---

### Post by shadowfire36 on 2014-06-23
I currently have a raid 5 with 5 drives on ubuntu 13.10 . I had blackout and some how i lost 2 of my drives . members were as followed 
md1=
sdb2
sdc2
sdd2
sde2
sdf2

so i restarted and found sdb2 dead and for what ever crazy reason sde2 disappaered . now is showing as sde and is listed as a spare .
I followed this guide :
[http://ubuntuforums.org/showthread.php?t=1293780](http://ubuntuforums.org/showthread.php?t=1293780)

and managed to ger the raid to come online degraded  with 3 disks it said resync complete after  i replaced the dead drive , i restarted and i dont know what happened... my drives completely changed . it went from the ordered i gave .. but know my drive ordered changed to ;
md0=
sda
sdb2
sdc2
sde
this just blew my mind and my raid disappeared .
after many hours of screw around i managed to the array to show again as md1 ,but know i cant get the degraded raid back or the md1 to show .
im completly lost and dont even know what information to show 
here is cat /proc/mdstat

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : inactive sdc2[1](S) sdf2[4](S) sdd2[6](S)
      4383301632 blocks super 1.2

unused devices: <none>


and mdadm.conf

#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/1 metadata=1.2 UUID=4a67c493:2d1baedc:d9086f29:db0c418d name=1

# This file was auto-generated on Tue, 22 Apr 2014 02:00:17 -0400
# by mkconf $Id$


If anything else is need please just tell me what to provide thank you !!!

---

