---
title: "Slow file transfers 10 MB/s (between internal sata drives) vs 60-80MB/s from W7"
date: 2013-09-01
forum: Server Platforms
---

### Post by mousse2 on 2013-09-01
Hello all, I have an HP N36L microserver running ubuntu server 12.04. I'm upgrading one of the hard drives to a 3TB and need to move over about 2TB of large media files. I've tried nautilus (livecd) and rsync and both give me about 10 MB/s.

At the same time, when I move files from my Windows 7 machine over the network to the new (3TB) or older (2TB) drive mounted on the Ubuntu server, I get speeds from 60-80MB/s. It's very frustrating as this is taking way too long. I have other drives I will need to upgrade soon so not looking forward to 35hr+ transfers. 

Any idea why this might be happening?

---

### Post by Doug S on 2013-09-01
Hi, and welcome to Ubuntu forums.

I do not know why your transfer rate is so low. Just out of curiosity, and for a comparison I did similar on one of my computers. I made a 100 gigabyte file (107374182400 bytes) and then used "cp" to copy it to a different physical drive on the same computer. It took 1053.69 seconds or 97 mega bytes per second (101,920,671.3 bytes per second). Perhaps have a look at "top" while the transfer is occurring, you should observe mainly I/O wait as the main use of CPU times. For example:```
top - 16:16:00 up  1:05,  3 users,  load average: 3.00, 2.93, 2.29
Tasks: 134 total,   1 running, 133 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.0%us,  4.1%sy,  0.0%ni,  0.4%id, [COLOR=#ff0000]94.8%wa[/COLOR],  0.0%hi,  0.7%si,  0.0%st
Cpu1  :  0.3%us,  0.0%sy,  0.0%ni, 96.6%id,  [COLOR=#ff0000]3.1%wa[/COLOR],  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.0%us,  1.2%sy,  0.0%ni, 24.9%id, [COLOR=#ff0000]73.9%wa[/COLOR],  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu4  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu5  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu6  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu7  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  16004108k total, 15846488k used,   157620k free,    15180k buffers
Swap:  8294396k total,        0k used,  8294396k free, 15262460k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3135 doug      20   0 19892  820  656 D   [COLOR=#ff0000]12  0.0   2:11.32 cp[/COLOR]
   51 root      20   0     0    0    0 S    2  0.0   0:33.55 kswapd0
 3130 root      20   0     0    0    0 D    1  0.0   0:14.60 flush-8:16
 2842 root      20   0     0    0    0 D    1  0.0   0:15.50 jbd2/sdb3-8
 3175 root      20   0     0    0    0 S    0  0.0   0:00.25 kworker/0:1
```Edit: Even if I boot with maxcpus=1, the file copy only takes few seconds longer, 1078.87 seconds.

---

### Post by ValiDOM on 2013-09-03
If you install iotop, you might get a better idea with the information provided by iotop.

---

### Post by mousse2 on 2013-09-15
Thank you both for the advice. Just to help close this thread and for anyone else. In my case, the problem was a specific WD Green 2TB hard drive that was experiencing extremely slow read speeds. This was the problem in my case at least.

---

