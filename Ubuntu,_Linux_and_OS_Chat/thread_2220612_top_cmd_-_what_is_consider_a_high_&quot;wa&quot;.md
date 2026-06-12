---
title: "top cmd - what is consider a high &quot;wa&quot;"
date: 2014-04-28
forum: Ubuntu, Linux and OS Chat
---

### Post by jladew@calmetrics.com on 2014-04-28
Hello,

I am looking for some sort of yard stick or comparision.  What would a high "wa" be when looking at the top statistic?  Obviously 50%+ I think is bad.  Is there a optimal % that it should be under?

Here is a snap shot of summary top stats for a ESXi 5.0 Ubuntu 12.04 VM, the 2 main processes are Java and MySQL:
top - 15:39:38 up 7 days,  6:48,  2 users,  load average: 0.38, 0.77, 0.73
Tasks: 170 total,   1 running, 169 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.4%us,  0.1%sy,  0.0%ni, 89.6%id,  9.9%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   8178376k total,  7670048k used,   508328k free,   160104k buffers
Swap:  8388604k total,   587740k used,  7800864k free,  2513628k cached


BTW, on average the "wa" is anywhere between 2-3% with occasional spikes to 13-15%

thanks!

Jason

---

### Post by ssam on 2014-04-29
It depends what you are doing. High wa just tells you that your process is waiting for disk rather than CPU. If you are coping a file then you would expect to be waiting for disk. If you are transcoding media files then you can tell by looking at wa if you are disk bound or CPU bound. If you RAM is full, the wa can be high to swapping.

---

