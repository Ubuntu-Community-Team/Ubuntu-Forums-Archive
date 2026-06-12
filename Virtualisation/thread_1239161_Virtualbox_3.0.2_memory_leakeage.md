---
title: "Virtualbox 3.0.2 memory leakeage?"
date: 2009-08-13
forum: Virtualisation
---

### Post by rollinga on 2009-08-13
Im running a headless server with only one Windows XP machine. I've setted 1 GB for this XP but seems like the memory usage is getting bigger and bigger

The server Specifications are:

Pentium Dual Core processor and 2 GB of ram. This is a fresh Ubuntu 9.04 amd64 Jaunty installation.

top:

```

top - 13:26:51 up 26 min,  1 user,  load average: 0.54, 0.50, 0.40
Tasks: 103 total,   1 running, 102 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us,  6.5%sy,  1.7%ni, 90.8%id,  0.4%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   2025200k total,  2010120k used,    15080k free,    12752k buffers
Swap:  2931704k total,        0k used,  2931704k free,   802160k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3093 domolife  20   0 1296m 1.1g  34m S   34 55.4  13:09.86 VBoxHeadless
    4 root      15  -5     0    0    0 S    1  0.0   0:06.67 ksoftirqd/0
   15 root      15  -5     0    0    0 S    0  0.0   0:00.81 events/0
  742 root      15  -5     0    0    0 S    0  0.0   0:00.56 md1_raid1
    1 root      20   0  4104  920  632 S    0  0.0   0:01.16 init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.01 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1
    7 root      15  -5     0    0    0 S    0  0.0   0:01.06 ksoftirqd/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2
   10 root      15  -5     0    0    0 S    0  0.0   0:01.93 ksoftirqd/2
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3
   13 root      15  -5     0    0    0 S    0  0.0   0:05.42 ksoftirqd/3
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/3

```any ideas?

---

### Post by jocampo on 2009-08-13
I do not see any problem...

Your machine is using the RAM it needs. In fact, you are not swapping at all, which is good. It could be bad if the "used" value is low or the "swap" value is high, means... your servers is not managing memory well.

Look at your cached value, is high as well. The higher, the faster Ubuntu will be, because next time the software or operating system needs something, the information is going to be "there" in memory, not in disk, so is faster and easier to retrieve.

The more you use your VM, the more RAM Ubuntu will allocate for it ....

---

