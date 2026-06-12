---
title: "Buffers flush(?) every GMT midnight"
date: 2008-10-29
forum: Server Platforms
---

### Post by maximk on 2008-10-29
Hi!

I'm running self-written script which every 5 minutes read and updates tens of thousands small files. Most of the time cache is heavily used (i tuned some of 'vm.dirty_*' parameters to increse performance) - and all is ok.

But every GMT midnight (local time 04:00 MSD or 03:00 MSK) system runs very slow for about 15 minutes. Analysis of collected performance data shows that 'Buffers' values greatly decreases during that period (and then again - increases). So, I suppose there is a rule making kernel to flush all buffered data, therefore large amount of disk I/O occurs.

How could I fix that behaviour? I dont need any per-day global buffer flush.

---

### Post by maximk on 2008-11-01
The problem actually relates to RRD update mechanism, so question is taked off.

Details could be found in rrd-ml thread:
[https://lists.oetiker.ch/pipermail/rrd-users/2008-October/014801.html](https://lists.oetiker.ch/pipermail/rrd-users/2008-October/014801.html)

---

