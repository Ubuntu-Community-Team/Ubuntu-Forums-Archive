---
title: "High cpu usage in migration/3 &amp; /4 maybe"
date: 2012-01-30
forum: Server Platforms
---

### Post by ian dobson on 2012-01-30
Hi,

I've just upgraded my backebd server to kernel to:-
Linux alpha2 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

And I'm now seeing high CPU usage in my munin graphs. Looking at the reason I've found this:-

```
 ps aux | sort -k 4 | grep migration
root         6  0.0  0.0      0     0 ?        S    Jan27   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    Jan27   0:00 [migration/1]
root        11  0.0  0.0      0     0 ?        S    Jan27   0:00 [migration/2]
root        20  0.0  0.0      0     0 ?        S    Jan27   0:00 [migration/5]
root        23  0.0  0.0      0     0 ?        S    Jan27   0:00 [migration/6]
root        26  0.0  0.0      0     0 ?        S    Jan27   0:00 [migration/7]
root        17 34.0  0.0      0     0 ?        S    Jan27 1543:32 [migration/4]
root        14 95.1  0.0      0     0 ?        S    Jan27 4312:06 [migration/3]
```

So ps is showing a very high CPU usage mirgration/4 and mirgration/3 but

```
 top -n 1 -p 14
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
   14 root      RT   0     0    0    0 S    0  0.0   4312:06 migration/3
```

So who is lieing/telling the truth.

Regards
Ian Dobson

---

### Post by edeefelt on 2012-02-28
I am seeing exactly the same issue:

```

edfelt@cedfelt-Latitude-E6500 [~]# uname -a
Linux cedfelt-Latitude-E6500 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

edfelt@cedfelt-Latitude-E6500 [~]# ps aux | sort -k 4 | grep migration
root         6 91.3  0.0      0     0 ?        S    10:33 230:30 [migration/0]
root         7 98.9  0.0      0     0 ?        S    10:33 249:50 [migration/1]

edfelt@cedfelt-Latitude-E6500 [~]# top -n 1 -p 6 -p 7

top - 14:48:08 up  4:14,  0 users,  load average: 0.08, 0.07, 0.06
Tasks:   2 total,   0 running,   2 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.4%us,  3.2%sy,  0.0%ni, 85.6%id,  0.8%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3979532k total,  2566720k used,  1412812k free,   121664k buffers
Swap:  4115452k total,        0k used,  4115452k free,  1035532k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                
    6 root      RT   0     0    0    0 S    0  0.0 230:30.20 migration/0                                                                                            
    7 root      RT   0     0    0    0 S    0  0.0 249:50.25 migration/1             

```

Anyone have any idea why this is happening?

---

### Post by ian dobson on 2012-02-28
Hi,

I've not found anything, so I gave up and am now running a self compiled 3.0.0-13-generic (with afew backported patches that I need for my dvb tuner cards)

Regards
Ian Dobson

---

