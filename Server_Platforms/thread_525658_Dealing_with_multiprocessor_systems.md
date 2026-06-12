---
title: "Dealing with multiprocessor systems"
date: 2007-08-14
forum: Server Platforms
---

### Post by Blazeix on 2007-08-14
Hi, I have two servers, one is a dual processor (2 Core 2 Duos) machine and the other has one Dual-Core AMD Opteron processor. Both machines are running Ubuntu 6.06. The problem is that I'm not convinced that the dual processor machine is using both processors. Both machines  have the following entries in /sys/devices/system/cpu:
```
$ ls /sys/devices/system/cpu/
cpu0  cpu1
```
Also, when I do the 'top' command and press '1', both display the same info:

```

Cpu0  :  2.4% us,  1.2% sy,  0.0% ni, 86.5% id,  9.8% wa,  0.0% hi,  0.1% si
Cpu1  :  1.5% us,  0.3% sy,  0.0% ni, 97.7% id,  0.5% wa,  0.0% hi,  0.0% si

```

'uname -a' output from dual processor machine: Linux hostnameA 2.6.15-28-server #1 SMP Wed Jul 18 23:11:55 UTC 2007 i686 GNU/Linux
'uname -a' output from single processor machine: Linux hostnameB 2.6.18-4-amd64 #1 SMP Fri May 4 00:37:33 UTC 2007 x86_64 GNU/Linux

Since Cpu0 and Cpu1 show up for both the single and dual processor machines, how can I tell if the dual processor machine is using both processors? Thanks for any help.

---

### Post by a9k on 2007-08-21
With the new Intel names like Core 2 Duo vs Core Duo 2, t is becoming hard to know how many CPUs you have. Try 'cat /proc/cpuinfo'. Look for "cpu cores" and "siblings". In my case 2 and 4. So I should have 2x4=8 CPUs and I see 8 Cpu lines when I hit 1 in 'top'.

---

### Post by ssam on 2007-08-21
see what happens when you load 2 or 4 bir processes.

for example running boinic on a dual core xeon machine with 2 boinc processes i see
```

top - 22:19:48 up 13:52,  5 users,  load average: 2.23, 2.15, 2.11
Tasks: 147 total,   3 running, 144 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  1.1%sy, 96.5%ni,  0.2%id,  0.0%wa,  0.1%hi,  0.1%si,  0.0%st
Mem:   2062620k total,  2037572k used,    25048k free,   145520k buffers
Swap:  2104472k total,     4172k used,  2100300k free,   954044k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                         
 2404 sam       39  19  156m  76m   12 R   99  3.8 138:23.40 rosetta_beta_5.                 
 3413 sam       39  19  165m  83m   20 R   93  4.1  82:30.68 rosetta_beta_5.                 
  302 sam       16   0  915m 230m  66m S    2 11.5  12:19.39 epiphany-browse                 
 7171 root      15   0  254m 161m  16m S    2  8.0   6:02.74 Xorg                            
    1 root      18   0  5112 1964  572 S    0  0.1   0:00.97 init                            
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
```

so at full load my total %cpu is around 200%.

you should be able to get that up to 400% with 4 cores.

---
when i press 1 in top i see 2 cpus.
cat /proc/cpu shows me 2 cpus

---

### Post by wirelessmonkey on 2007-08-22
You can use htop, available in the repositories, which will give you a much better idea of how/if both cores are running.

---

