---
title: "ionice vs. software raid"
date: 2009-11-11
forum: Server Platforms
---

### Post by der_flo on 2009-11-11
Does ionice work correctly in software-RAID environments? I cannot set the CFQ scheduler for the md devices, because there is no file /sys/block/md0/queue/scheduler . It seems that the scheduler settings for the underlying disks are not propagated to the raid devices.


```
$ cat /sys/block/*/queue/scheduler
noop anticipatory deadline [cfq] 
noop anticipatory deadline [cfq] 
none
none
none
none
none
none
none
none
none
none
none
none
none
none
none
none
none
none
none
none
none
none
none
none
none
none
none
none
none
noop anticipatory deadline [cfq] 
noop anticipatory deadline [cfq]

``````

# Now two "dd"s parallel
$ ionice -c3 dd if=/dev/zero of=test1 bs=10M count=100 oflag=dsync
100+0 records in
100+0 records out
1048576000 bytes (1,0 GB) copied, 29,9719 s, 35,0 MB/s
 
$ ionice -c2 -n1 dd if=/dev/zero of=test2 bs=10M count=100 oflag=dsync
100+0 records in
100+0 records out
1048576000 bytes (1,0 GB) copied, 37,251 s, 28,1 MB/s
  
#############
# Or also
$ ionice -c3 dd if=/dev/zero of=test1 bs=14M count=1000
1000+0 records in
1000+0 records out
14680064000 bytes (15 GB) copied, 255,732 s, 57,4 MB/s
 
$ ionice -c2 -n1 dd if=/dev/zero of=test2 bs=14M count=1000
1000+0 records in
1000+0 records out
14680064000 bytes (15 GB) copied, 254,077 s, 57,8 MB/s


```Of course I did the two dd's parallel in two seperate terminals.

Any ideas? Thanks,
der Flo

---

