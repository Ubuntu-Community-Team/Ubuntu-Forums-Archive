---
title: "MDADM increased raid size, new size is not being detected"
date: 2014-03-16
forum: Server Platforms
---

### Post by darkapec on 2014-03-16
Hello,

I recently upgraded my raid 5 from 3 x 4tb drives to 4 x 4tb drives. It completed the resync process without issue and according to WEBMIN the new raid size is 10.93tb, however if I create a share for the raid, windows only says there is 7.21tb available. 

My current setup is ubuntu 13.04 with KVM installed. The physical machine shares the mdadm raid via NFS to a virtual machine. The virtual machine is then sharing the mount via SAMBA so the windows machines on my network can access the data. 

cat / proc/mdstat gives me the following:
```

jake@Morpheus:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc[1] sdd[3] sde[0] sdb[4]
      11720661504 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>
jake@Morpheus:~$

```

NFS Exports (on physical machine):
```
/Backup       192.168.1.145(rw,fsid=0,insecure,no_subtree_check,async)

```

SAMBA config (on virtual machine):
```
[Backup]
        writeable = yes
        public = yes
        path = /Backup


```

I have removed and re installed mdadm, I have recreated the SAMBA share, I have recreated the NFS export. No matter what windows is still only detecting 7tb of space. If anyone has any ideas please let me know.

Thanks
Jake
I have also attached a picture showing what WEBMIN is detecting

---

### Post by rubylaser on 2014-03-17
Besides expanding the mdadm array, you need to expand your filesystem as well.  To do this safely, I normally: 1. unmount the filesystem, 2. run and fsck on the the array, and 3. then resize the filesystem.  Here is how it works on an ext4 filesystem.

```

umount /Backup
fsck.ext4 -f /dev/md0
resize2fs /dev/md0

```

---

### Post by darkapec on 2014-03-17
As usual RUBYLASER saves the day. Thanks a lot

---

### Post by rubylaser on 2014-03-18
No problem.  Glad you got it figured out :)

---

