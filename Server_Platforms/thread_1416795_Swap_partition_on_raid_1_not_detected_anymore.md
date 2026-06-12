---
title: "Swap partition on raid 1 not detected anymore"
date: 2010-02-26
forum: Server Platforms
---

### Post by malarie on 2010-02-26
Good day,

After upgrading to 9.1 my swap partition on my raid array is not detected anymore. So i get dropped  in maintenance mode..
 I booted with as live CD, and was able to mount md0, but md1 is no where to be found.

when i run mdadm --assemble --scan i get this message:


ubuntu@ubuntu:~$ sudo mdadm --assemble --scan
mdadm: /dev/md0 has been started with 2 drives.
mdadm: no devices found for /dev/md1


/proc/mdstat says this:
ubuntu@ubuntu:~$ sudo cat  /proc/mdstat
Personalities : [raid1] 
md0 : active raid1 sda1[0] sdb1[1]
      234372160 blocks [2/2] [UU]
      
unused devices: <none>

My /etcmdadm/mdadm.conf says this:
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=743cc23b:d8a07722:52074cff:8a3b0676
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=c2b63389:53ec60d6:790b3fad:e5cacb62

---

