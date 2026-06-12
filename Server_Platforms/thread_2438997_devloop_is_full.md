---
title: "/dev/loop is full???"
date: 2020-03-21
forum: Server Platforms
---

### Post by MickSulley on 2020-03-21
I am trying to run Unison on a newly built server to sync with a Raspberry Pi and it is failing with an out of memory issue.  I have checked the Pi and that is fine.  
If I run df -haT on the server I see that /dev/loop0, 1, 2 & 3 are all full
```
mick@zen:~$ df -haT
Filesystem     Type         Size  Used Avail Use% Mounted on
sysfs          sysfs           0     0     0    - /sys
proc           proc            0     0     0    - /proc
udev           devtmpfs     3.8G     0  3.8G   0% /dev
devpts         devpts          0     0     0    - /dev/pts
tmpfs          tmpfs        777M  1.2M  776M   1% /run
/dev/sda2      ext4         110G  8.3G   96G   8% /
securityfs     securityfs      0     0     0    - /sys/kernel/security
tmpfs          tmpfs        3.8G     0  3.8G   0% /dev/shm
tmpfs          tmpfs        5.0M     0  5.0M   0% /run/lock
tmpfs          tmpfs        3.8G     0  3.8G   0% /sys/fs/cgroup
cgroup2        cgroup2         0     0     0    - /sys/fs/cgroup/unified
cgroup         cgroup          0     0     0    - /sys/fs/cgroup/systemd
pstore         pstore          0     0     0    - /sys/fs/pstore
bpf            bpf             0     0     0    - /sys/fs/bpf
cgroup         cgroup          0     0     0    - /sys/fs/cgroup/memory
cgroup         cgroup          0     0     0    - /sys/fs/cgroup/cpuset
cgroup         cgroup          0     0     0    - /sys/fs/cgroup/devices
cgroup         cgroup          0     0     0    - /sys/fs/cgroup/net_cls,net_prio
cgroup         cgroup          0     0     0    - /sys/fs/cgroup/cpu,cpuacct
cgroup         cgroup          0     0     0    - /sys/fs/cgroup/blkio
cgroup         cgroup          0     0     0    - /sys/fs/cgroup/hugetlb
cgroup         cgroup          0     0     0    - /sys/fs/cgroup/rdma
cgroup         cgroup          0     0     0    - /sys/fs/cgroup/freezer
cgroup         cgroup          0     0     0    - /sys/fs/cgroup/perf_event
cgroup         cgroup          0     0     0    - /sys/fs/cgroup/pids
systemd-1      -               -     -     -    - /proc/sys/fs/binfmt_misc
hugetlbfs      hugetlbfs       0     0     0    - /dev/hugepages
debugfs        debugfs         0     0     0    - /sys/kernel/debug
mqueue         mqueue          0     0     0    - /dev/mqueue
fusectl        fusectl         0     0     0    - /sys/fs/fuse/connections
configfs       configfs        0     0     0    - /sys/kernel/config
/dev/loop0     squashfs      68M   68M     0 100% /snap/lxd/13901
/dev/loop1     squashfs      68M   68M     0 100% /snap/lxd/13840
/dev/loop2     squashfs      90M   90M     0 100% /snap/core/7917
/dev/loop3     squashfs      92M   92M     0 100% /snap/core/8689
/dev/sdb1      ext4         1.8T  393G  1.4T  23% /common
/dev/sdc1      ext4         5.5T  1.6T  3.7T  30% /home
tmpfs          tmpfs        777M  1.2M  776M   1% /run/snapd/ns
nsfs           nsfs            0     0     0    - /run/snapd/ns/lxd.mnt
tmpfs          tmpfs        777M     0  777M   0% /run/user/1000
binfmt_misc    binfmt_misc     0     0     0    - /proc/sys/fs/binfmt_misc
mick@zen:~$ 

``` 
It seems that these are linked to snap, I have researched it a bit but don't see what is happening, I have not installed snap.
Any ideas how to fix this?
Thanks
Mick

---

### Post by darkod on 2020-03-21
This is normal. In the new ubuntu version /dev/loopX always shows as 100%. Haven't looked into why, but my desktop and all servers work great and they also say 100% for those loop devices.

Your problem lies somewhere else.

Does it complain about memory or disk space? Because there is a difference.

You can check used and free memory with:
```
free -m
```

---

### Post by The Cog on 2020-03-21
I think the loop mounts are files containing snap applications. They are formatted like disks (squahfs filesystem) and are only as large as the app they contain, hence 100% full.

---

### Post by MickSulley on 2020-03-21
Thanks for you replies.
I had tried it a few times, sometimes getting connection to server lost and sometimes a space issue, can't remember if it was disk or memory, and I have rebooted since.

I just tried it again and now it works fine!?!?  Don't understand but it seems OK now. 

Thanks
Mick

---

