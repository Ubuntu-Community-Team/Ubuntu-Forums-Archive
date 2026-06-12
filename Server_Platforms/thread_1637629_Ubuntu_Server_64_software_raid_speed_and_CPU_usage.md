---
title: "Ubuntu Server 64 software raid speed and CPU usage."
date: 2010-12-04
forum: Server Platforms
---

### Post by Coder68 on 2010-12-04
I am playing with my new 5 disk 2TB software RAID 5 setup and after I had a hard drop out, I deleted the RAID set and recreated it with only 4 drives.  I am working on getting the other drive included by doing a grow. (I hope)

The RAID is now rebuilding and seems to average a write speed of around 87 meg/sec, with lows in the high 60's to highs in the mid 90's but mostly in the higher 80's. But it is only showing about 16% CPU usage and maybe a second usage of around 7%.  

Is this normal? It seems low to me, but it is a a quad core 2.5 GHZ processor. Screen shots attached. 

Is it "normal" for software RAID to drop a drive?  I thought that was only a hardware RAID issue.

Coder68

---

### Post by Coder68 on 2010-12-04
Now that I have added a 5th drive to the array, the write speeds have gone way down and the CPU time has gone up.

See attached.

Is this possibly due to it being a resize and not rebuild? At this rate it is going to take 29 hours to resize with NO DATA on the RAID array!

Thanks,

Coder68

---

