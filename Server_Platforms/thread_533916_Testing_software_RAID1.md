---
title: "Testing software RAID1"
date: 2007-08-24
forum: Server Platforms
---

### Post by mtime2457 on 2007-08-24
I running into problems rebuilding a failed hard drive, the following is what I'm getting;

root@dns1:/# cat /proc/mdstat
Personalities : [raid1] 
md2 : active raid1 sda3[1]
      1967872 blocks [2/1] [_U]
      
md1 : active raid1 sda2[1]
      9767424 blocks [2/1] [_U]
      
md0 : active raid1 sdb1[0] sda1[1]
      23824256 blocks [2/2] [UU]
      
unused devices: <none>
root@dns1:/# 
root@dns1:/# 
root@dns1:/# mdadm --add /dev/md1 /dev/sdb2
mdadm: cannot find /dev/sdb2: No such file or directory
root@dns1:/# 
root@dns1:/# mdadm --add /dev/md2 /dev/sdb3
mdadm: cannot find /dev/sdb3: No such file or directory
root@dns1:/# 
root@dns1:/# 

I was able to rebuilt the root partition with no problem, but then the other two partitions I get the above error....any help would be greatly appreciated.

---

