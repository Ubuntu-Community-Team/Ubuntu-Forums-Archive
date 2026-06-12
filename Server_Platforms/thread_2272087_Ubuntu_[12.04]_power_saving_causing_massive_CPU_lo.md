---
title: "Ubuntu [12.04] power_saving causing massive CPU loading"
date: 2015-04-03
forum: Server Platforms
---

### Post by danielchau on 2015-04-03
Hi all,

I have faced a problem that one of our server running ubuntu 12.04 have high loading problem of [power_saving/xx]

root@host:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:        12.04
Codename:       precise

top - 10:36:18 up 4 days, 18:39,  1 user,  load average: 21.98, 21.49, 21.15
Tasks: 162 total,  24 running, 138 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us, 75.0%sy,  0.0%ni, 23.9%id,  0.9%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  16386692k total, 15810516k used,   576176k free,   443600k buffers
Swap: 15623208k total,        0k used, 15623208k free, 14254620k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
10083 root      -2   0     0    0    0 R  266  0.0 642:36.78 power_saving/2
10086 root      -2   0     0    0    0 R  265  0.0 647:23.51 power_saving/5
10080 root      -2   0     0    0    0 R  208  0.0 648:04.06 power_saving/0
10088 root      -2   0     0    0    0 R   95  0.0 653:57.99 power_saving/7
10091 root      -2   0     0    0    0 R   95  0.0 645:53.48 power_saving/10
10087 root      -2   0     0    0    0 R   42  0.0 634:35.87 power_saving/6
10085 root      -2   0     0    0    0 R   28  0.0 639:23.88 power_saving/4
10081 root      -2   0     0    0    0 R   25  0.0 640:22.52 power_saving/1

root@host:~# iostat
Linux 3.2.0-54-generic (host)         04/04/15        _x86_64_        (12 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.42    0.24    8.74    0.05    0.00   90.55

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda              13.79       529.00        79.45  218375631   32797413
drbd0            42.43       177.03        21.62   73079105    8925460

Actually this is not the first time we faced this problem, before we just reboot it and the problem will gone. But this didn't solve this issue permanently.
This issue also not caused by dust, mahcine is clean.
Would you please kindly advise how can i solve this problem?

Thanks

Daniel

---

### Post by Doug S on 2015-04-04
Hi and welcome to Ubuntu forums.

You seem to be running a not up to date system. Perhaps bring it up to date as a first step, and re-assess the situation.

I haven't updated for a month or so myself, but my 12.04 server is at:```
doug@doug-64:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise
doug@doug-64:~$ uname -a
Linux doug-64 3.2.0-76-generic #111-Ubuntu SMP Tue Jan 13 22:16:09 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by tgalati4 on 2015-04-05
Install *htop* and watch what is happening.  What are the CPU's?

```
cat /proc/cpuinfo
```

You might benefit from a later kernel than 3.2.

---

