---
title: "Idling load averages of ~2.0 on Amazon EC2 with Ubuntu"
date: 2014-02-13
forum: Server Platforms
---

### Post by User4519 on 2014-02-13
Hi :)

I'm running the latest Ubuntu Tahr server AMI (from Canonical) on a c3.large EC2 instance.

I'm puzzled by the fact that at login I'm told, "[FONT=courier new]System information disabled due to load higher than 2.0[/FONT]", and that top reports the same. In fact, I've never seen it report anything below 2.0. 

It looks like 2.0 actually **means** 0.0, check out the top of top:

```
top - 08:39:03 up 3 days, 20:22,  2 users,  load average: 2.00, 2.01, 2.05
Tasks: 144 total,   1 running, 143 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.2 us,  0.0 sy,  0.0 ni, 99.8 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   3854940 total,  2057852 used,  1797088 free,   179780 buffers
KiB Swap:        0 total,        0 used,        0 free.  1527252 cached Mem

```

It's currently being set up, and it's serving no requests. Has anyone here seen anything like this? It really doesn't seem to be stressed at all, it just seems to be reporting wrong numbers.

I'm running it on hvm, by the way. Not sure if that's relevant.

TIA,
Daniel

---

