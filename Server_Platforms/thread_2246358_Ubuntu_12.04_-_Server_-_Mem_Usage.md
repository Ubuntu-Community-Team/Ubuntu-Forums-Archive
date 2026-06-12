---
title: "Ubuntu 12.04 - Server - Mem Usage"
date: 2014-09-30
forum: Server Platforms
---

### Post by RickJC on 2014-09-30
Hi All,

Sorry for the silly quesiton here but i'm at a loss. My Ubuntu server Virtual Machine (12.04) is showing that almost 6GB of it's memory is in use but it's not telling me what it using it.
```
/# free -m
             total       used       free     shared    buffers     cached
Mem:          7983       5641       2341          0         58       5262
-/+ buffers/cache:        319       7663
Swap:         4023          8       4015
```


Top results in 'top' in order of Mem usage%:
```
top - 10:25:39 up 39 days,  1:02,  2 users,  load average: 0.00, 0.06, 0.26
Tasks:  84 total,   1 running,  83 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.1%us,  0.1%sy,  0.0%ni, 99.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8175204k total,  5777716k used,  2397488k free,    60448k buffers
Swap:  4120568k total,     9084k used,  4111484k free,  5389540k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6021 root      20   0 23408 4184 1272 S    0  0.1   0:00.37 bash
20780 root      20   0 23164 4020 1332 S    0  0.0   0:00.54 bash
20589 root      20   0 73444 2324 1492 S    0  0.0   0:01.92 sshd
 5836 root      20   0 73444 2316 1472 S    0  0.0   0:04.91 sshd
  981 syslog    20   0  243m 2160  452 S    0  0.0   4:52.16 rsyslogd
 1124 snmp      20   0 48328 2104 1060 S    0  0.0  15:14.71 snmpd


```

What i found strange was that 'htop' was showing much less result which looks more genuine:
320/7983MB

Thoughts? Again, sorry if this is a silly question.

R

---

### Post by mastablasta on 2014-09-30
it was used before, but would be cleared when needed. this is not the memory status immediately on boot I presume.

yeah htop seems to give a bit better info while running the os.

---

### Post by TheFu on 2014-09-30
disk buffers are automatic.
Any data in them is freed as necessary when programs need the RAM.

---

