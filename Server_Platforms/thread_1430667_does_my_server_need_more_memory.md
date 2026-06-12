---
title: "does my server need more memory?"
date: 2010-03-15
forum: Server Platforms
---

### Post by wbloos on 2010-03-15
Hi,

I have a server that runs mainly apache, mapserver, postgres.
I would like to be able to give postgres some more resources (memory).

Below is my top output on a quiet evening.
I notice that there is hardly any memory left according to the upper section. However, when i look at the per-process section (sorted on MEM), the greatest memory consumers use only 0.2%
Also (since VIRT= RES+SWAP) the greatest memory consumers seem to use a lot of SWAP, but according to the upper section, the system is only using 20MB of SWAP space (lots of cached swap though..).

What i would like to know is: is all this "used" memory in some kind of virtual part of the usage by those processses, or do i actually need more memory?

```

top - 21:17:48 up 27 days, 15:48,  2 users,  load average: 0.00, 0.00, 0.00
Tasks: 150 total,   2 running, 148 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  0.3%sy,  0.0%ni, 97.0%id,  0.7%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   8192644k total,  8144468k used,    48176k free,   130400k buffers
Swap:  3903784k total,    19388k used,  3884396k free,  7548908k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                           
 6370 www-data  20   0  401m  19m 7048 S    0  0.2   0:02.09 apache2                                                                                                                                           
 5762 root      20   0  395m  18m  12m S    0  0.2   0:42.55 apache2                                                                                                                                           
 7012 www-data  20   0  401m  18m 6992 S    4  0.2   0:02.47 apache2                                                                                                                                           
 6343 www-data  20   0  401m  17m 6984 S    0  0.2   0:01.31 apache2                                                                                                                                           
 7010 www-data  20   0  401m  17m 6968 S    0  0.2   0:01.34 apache2                                                                                                                                           
 7011 www-data  20   0  401m  17m 6976 S    0  0.2   0:01.34 apache2                                                                                                                                           
 7016 www-data  20   0  401m  17m 6964 S    0  0.2   0:01.40 apache2                                                                                                                                           
 7159 www-data  20   0  401m  17m 6968 S    0  0.2   0:00.85 apache2                                                                                                                                           
 7163 www-data  20   0  401m  17m 6968 S    0  0.2   0:01.38 apache2                                                                                                                                           
21112 www-data  20   0  401m  16m 5416 S    0  0.2   0:00.03 apache2                                                                                                                                           
16146 www-data  20   0  173m  13m  10m S    0  0.2   0:00.13 mapserv                                                                                                                                           
 6818 www-data  20   0  172m  12m  10m S    0  0.2   0:00.09 mapserv                                                                                                                                           
13594 www-data  20   0  172m  12m  10m S    0  0.2   0:00.12 mapserv                                                                                                                                           
27335 www-data  20   0  172m  12m  10m S    0  0.2   0:00.01 mapserv                                                                                                                                           
 6617 www-data  20   0  172m  12m  10m S    0  0.2   0:00.02 mapserv                                                                                                                                           
20475 www-data  20   0  171m  12m  10m S    0  0.2   0:00.02 mapserv                                                                                                                                           
 6168 www-data  20   0  172m  12m  10m S    0  0.2   0:00.02 mapserv                                                                                                                                           
18689 www-data  20   0  171m  12m  10m S    0  0.2   0:00.02 mapserv                                                                                                                                           
18685 www-data  20   0  171m  12m  10m S    0  0.2   0:00.02 mapserv                                                                                                                                           
18691 www-data  20   0  171m  12m  10m S    0  0.2   0:00.02 mapserv                                                                                                                                           
 3582 www-data  20   0  171m  12m  10m S    0  0.2   0:00.02 mapserv                                                                                                                                           
13256 www-data  20   0  171m  12m  10m S    0  0.2   0:00.01 mapserv                                                                                                                                           
29641 www-data  20   0  171m  12m  10m S    0  0.2   0:00.02 mapserv                                                                                                                                           
13150 www-data  20   0  171m  12m  10m S    0  0.2   0:00.02 mapserv                                                                                                                                           
21984 www-data  20   0  171m  12m  10m S    0  0.2   0:00.01 mapserv                                                                                                                                           
 9101 www-data  20   0  171m  12m  10m S    0  0.2   0:00.01 mapserv                                                                                                                                           
29648 www-data  20   0  171m  12m  10m S    0  0.2   0:00.02 mapserv                                                                                                                                           
13717 www-data  20   0  171m  12m  10m S    0  0.2   0:00.02 mapserv                                                                                                                                           
27997 www-data  20   0  171m  12m  10m S    0  0.2   0:00.02 mapserv                                                                                                                                           
26506 www-data  20   0  171m  12m 9.9m S    0  0.2   0:00.01 mapserv                                                                                                                                           
31246 www-data  20   0  171m  12m 9.9m S    0  0.2   0:00.02 mapserv                                                                                                                                           
27116 www-data  20   0  171m  12m 9.9m S    0  0.2   0:00.02 mapserv                                                                                                                                           
12446 root      20   0  141m  10m 8604 S    0  0.1   0:00.02 ogr2ogr                                                                                                                                           
 6800 postgres  20   0  279m 9980 9060 S    0  0.1   0:01.52 postgres                                                                                                                                          
11797 www-data  20   0  396m 9120 2356 S    0  0.1   0:00.00 apache2                                                                                                                                           
 5159 postgres  20   0 98.8m 6240 5324 S    0  0.1   2:17.66 postgres                                                                                                                                          
 5184 postgres  20   0 98.8m 6240 5332 S    0  0.1   2:07.73 postgres                                                                                                                                          
 2351 www-data  20   0  133m 5100  424 S    0  0.1   0:00.00 apache2                                                                                                                                           
 5493 snmp      20   0 49600 5032 2196 S    0  0.1  11:02.01 snmpd                                                                                                                                             
 5186 postgres  20   0 98.9m 4044 3108 S    0  0.0   0:46.70 postgres                                                                                                                                          
 4850 wbloos    20   0 20880 3812 1516 S    0  0.0   0:00.11 bash                                                                                                                                              
 5676 wbloos    20   0 20880 3812 1508 S    0  0.0   0:00.10 bash                                                                                                                                              
 6802 postgres  20   0  279m 3000 2028 S    0  0.0   0:00.03 postgres


```

---

### Post by n0dix on 2010-03-15
Post the output from free -m.

---

### Post by dudumomo on 2010-03-15
Hi,
What the command: free  gives you ?

EDIT: Grilled

---

### Post by wbloos on 2010-03-15
```
wbloos@sovon2:/data/restore$ free -m
             total       used       free     shared    buffers     cached
Mem:          8000       7933         67          0        122       7340
-/+ buffers/cache:        470       7530
Swap:         3812         18       3793
wbloos@sovon2:/data/restore$ 

```

---

### Post by wbloos on 2010-03-15
it's all cache, so i'm cool.
is that right?

it's confusing that, in top, it's on the same line as "Swap", not "Mem".
So confusing actually, that i'm still not 100% sure.
Also, no mention of "cached" in the man-pages of free and top.

---

### Post by n0dix on 2010-03-15
> **wbloos said:**
> it's all cache, so i'm cool.
is that right?

it's confusing that, in top, it's on the same line as "Swap", not "Mem".
So confusing actually, that i'm still not 100% sure.
Also, no mention of "cached" in the man-pages of free and top.

Yes, the memory you are using, really, is 470. If you install htop you will see better.

---

### Post by soltanis on 2010-03-16
Jeez. 8 GB and you need more memory?

"Cached" memory is if I am recalling correctly, memory that isn't actively in use but used to have something loaded in it. I think it's kept around in case you restart a process or something, it speeds up the process. In other words, it's basically free.

---

### Post by Queue29 on 2010-03-16
You could get away with a single stick of 512 Mb. You have 8 Gb. You're doing just fine. 

It's amazing what happens when you don't run a GUI, isn't it?

---

### Post by CharlesA on 2010-03-16
> **Queue29 said:**
> You could get away with a single stick of 512 Mb. You have 8 Gb. You're doing just fine. 

It's amazing what happens when you don't run a GUI, isn't it?

No kidding, I wonder how much memory usage the GUI adds.

The OP is definitely doing better then I am:

```
charles@thor:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3962       3815        146          0        192        616
-/+ buffers/cache:       3005        956
Swap:        11609        197      11411

```

---

