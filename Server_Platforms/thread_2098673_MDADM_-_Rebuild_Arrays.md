---
title: "MDADM - Rebuild Arrays"
date: 2012-12-27
forum: Server Platforms
---

### Post by Platano on 2012-12-27
I currently have a RAID-1 setup on a server which was setup by my provider.

Recently, one of my hard drives failed and it was replaced. As a result, I now have to rebuild my whole array.

This is something I have never done and something I am unfamiliar with. I have read some documentation on mdadm and understand I need to rebuild my array but I don't want to mess up my production server.

Currently, this is the output on my mdstat file.

```

root@falcon:~# cat  /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md3 : active raid1 sdb7[2]
      9763768 blocks super 1.2 [2/1] [_U]
      
md5 : active raid1 sdb9[1]
      19528632 blocks super 1.2 [2/1] [_U]
      
md6 : active raid1 sdb10[1]
      97653688 blocks super 1.2 [2/1] [_U]
      
md1 : active raid1 sdb5[1]
      242676 blocks super 1.2 [2/1] [_U]
      
md0 : active raid1 sdb1[1]
      975860 blocks super 1.2 [2/1] [_U]
      
md4 : active raid1 sdb8[1]
      9763768 blocks super 1.2 [2/1] [_U]
      
md2 : active raid1 sdb6[1]
      1950708 blocks super 1.2 [2/1] [_U]
      
unused devices: <none>

```

This is the output of my configuration file.

```

root@falcon:~# cat /etc/mdadm/mdadm.conf
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
HOMEHOST falcom

# instruct the monitoring daemon where to send mail alerts
MAILADDR email@domain.com

# definitions of existing MD arrays
ARRAY /dev/md/3 metadata=1.2 UUID=43a5e7f6:ef3d07f0:aca66d8d:19cef933 name=ubuntu:3
ARRAY /dev/md/0 metadata=1.2 UUID=a8eec62a:485fe0fb:80d0d71b:55161abd name=ubuntu:0
ARRAY /dev/md/1 metadata=1.2 UUID=686ddd20:2ab0ab1c:7f7edfe4:536f1a32 name=ubuntu:1
ARRAY /dev/md/2 metadata=1.2 UUID=1f1d1074:acafc866:0376536a:cb13ce42 name=ubuntu:2
ARRAY /dev/md/4 metadata=1.2 UUID=a73f0b5c:380426cb:03c0a8eb:7128e347 name=ubuntu:4
ARRAY /dev/md/5 metadata=1.2 UUID=33042af7:f4a66fb2:a96a8376:1837747e name=ubuntu:5
ARRAY /dev/md/6 metadata=1.2 UUID=be467d34:742012c0:4803a100:a3930c6f name=ubuntu:6

# This file was auto-generated on Thu, 30 Aug 2012 18:24:03 -0500
# by mkconf $Id$

```

Could any one indicate an appropriate resource or guide or point me towards the right direction to rebuild this array?

Thanks in advance :)

---

### Post by catalin.vasilescu on 2012-12-27
Hello,

Follow the steps from [here]("http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array") . 
Just be careful with replacing the partitions and disk names to yours .

---

### Post by Platano on 2013-01-01
Thanks for pointing out the guide, it helped me complete the task.

---

