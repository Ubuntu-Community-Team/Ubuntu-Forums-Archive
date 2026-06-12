---
title: "mdadm raid problem at boot"
date: 2009-06-10
forum: Server Platforms
---

### Post by yaplimin on 2009-06-10
Ubuntu Gutsy 7.10 Server Edition on a PIII computer that I'm using as a home server.  OS on /dev/sda,  /home on /dev/md0 which are two 300 Gb IDE drives at /dev/sdb1 and /dev/sdc1. This configuration has been running fine for several months but just today got this error at bootup. 

Contents of /var/log/fsck/checkfs is:
> 
Log of fsck -C -R -A -a 
Wed Jun 10 18:37:31 2009

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Invalid argument while trying to open /dev/md0

/dev/md0: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Wed Jun 10 18:37:31 2009
----------------


cat /proc/mdstat produces 
> 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdb1[0](S) sdc1[2](S)
      586083136 blocks
       
unused devices: <none>


mdadm --query --detail /dev/md0 produces
> 
mdadm: md device /dev/md0 does not appear to be active.


Server still works but I've lost access to my home directories. I've reason to believe the individual drives are okay but I do not know how to recover from this error.  Any help and suggestions will be appreciated.
Thanks.

---

### Post by fjgaude on 2009-06-12
Maybe this command would show somthing:

```
sudo mdadm -E /dev/sdb1
```

Also what does this file show: /etc/mdadm/mdadm.conf?

Sounds like one of the drives went south or something changed in OS.

---

### Post by kdkirsch on 2009-06-27
Hi. Two of us encountered what appears to be the same problem. Please see our thread: [http://ubuntuforums.org/showthread.php?t=1194974]("http://ubuntuforums.org/showthread.php?t=1194974"). Thanks!

Moderator: If these threads address the same issue, could they be merged to increase visibility for this issue? Thanks!

---

### Post by dragos2 on 2009-06-27
Drivers or cables. Check cables first.

---

