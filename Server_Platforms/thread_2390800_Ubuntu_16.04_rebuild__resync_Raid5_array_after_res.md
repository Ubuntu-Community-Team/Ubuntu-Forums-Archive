---
title: "Ubuntu 16.04 rebuild / resync Raid5 array after restart, which make disk very slow"
date: 2018-05-02
forum: Server Platforms
---

### Post by civilman on 2018-05-02
My current disks were configured by someone else. it should be software raid. I am not sure why each time i restart the server, the raid5 rebuild. this process take very long time and make read disk very slow. i have to kill resync manually each time just after reboot.


The output of **cat /proc/mdstat**

scopeserver@scopephotos:~$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md126 : active raid5 sdb[2] sdc[1] sdd[0]
      5860528128 blocks super external:/md127/0 level 5, 128k chunk, algorithm 0 [3/3] [UUU]
          resync=PENDING
      
md127 : inactive sdc[2](S) sdd[1](S) sdb[0](S)
      7164 blocks super external:imsm
       
unused devices: <none>


--------------------

scopeserver@scopephotos:~$** cat /etc/mdadm/mdadm.conf**
# mdadm.conf
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



# definitions of existing MD arrays
ARRAY metadata=imsm UUID=52c79c25:2facc0a5:2f19f917:9170804d
ARRAY /dev/md/Disk Raid container=52c79c25:2facc0a5:2f19f917:9170804d member=0 UUID=653a5e40:b154d55e:51e20c11:8777ad76

---

