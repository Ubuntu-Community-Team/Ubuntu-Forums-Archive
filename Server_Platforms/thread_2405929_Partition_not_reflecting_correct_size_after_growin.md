---
title: "Partition not reflecting correct size after growing disk space on EC2."
date: 2018-11-13
forum: Server Platforms
---

### Post by aekanshd on 2018-11-13
I have an EC2 hosted at Amazon Web Services. Initially my mounted volume was 8 GB and then I increased it to 16 GB. 
I went SSH'd into my Ubuntu Server and grew the partision size from 8 GB to 16 GB. But this isn't reflected anywhere.

```

lsblk
root@ip-***-**-**-**:~# lsblk
NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
loop0     7:0    0 87.9M  1 loop /snap/core/5328
loop1     7:1    0 12.7M  1 loop /snap/amazon-ssm-agent/495
loop2     7:2    0 87.9M  1 loop /snap/core/5742
loop3     7:3    0 16.5M  1 loop /snap/amazon-ssm-agent/784
xvda    202:0    0   16G  0 disk
&#9492;&#9472;xvda1 202:1    0   16G  0 part /
xvdf    202:80   0    8G  0 disk
&#9492;&#9472;xvdf1 202:81   0    8G  0 part

```

And then:

```
root@ip-***-**-**-**:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            481M     0  481M   0% /dev
tmpfs            99M  772K   98M   1% /run
/dev/xvda1      7.7G  5.9G  1.9G  77% /
tmpfs           492M     0  492M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           492M     0  492M   0% /sys/fs/cgroup
/dev/loop0       88M   88M     0 100% /snap/core/5328
/dev/loop1       13M   13M     0 100% /snap/amazon-ssm-agent/495
/dev/loop2       88M   88M     0 100% /snap/core/5742
/dev/loop3       17M   17M     0 100% /snap/amazon-ssm-agent/784
tmpfs            99M     0   99M   0% /run/user/1000

```

Please, can someone help me?

---

### Post by howefield on 2018-11-13
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2018-11-14
The xvda1 partition shows 16GB correctly. What you need now is to extend the filesystem.

```
resize2fs /dev/xvda1
```

That will extend the filesystem to the maximum size (in this case 16GB).

---

