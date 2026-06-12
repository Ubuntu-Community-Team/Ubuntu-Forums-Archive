---
title: "Load high, nothing running on server (new server)"
date: 2010-10-14
forum: Server Platforms
---

### Post by Ivan C on 2010-10-14
Hello guys,

we have new server running for last few days, it's a PowerEdge 410 - 2 x 5660 system

Load sometimes goes beyond 1.0+ for no reasons, but cpu's ar IDLE at 100% (12 cores + HT)

At the moment we dont have any issues with it, but we ar woried to put it in production.

--------------

top - 13:31:26 up 6:42, 1 user, load average: 2.33, 1.35, 0.69
Tasks: 388  total, 1 running, 387 sleeping, 0 stopped, 0 zombie
Cpu(s): 0.0%us, 0.0%sy,  0.0%ni,100.0%id, 0.0%wa, 0.0%hi, 0.0%si, 0.0%st
Mem: 33003384k total, 759656k  used, 32243728k free, 13776k buffers
Swap: 15625208k total, 0k used,  15625208k free, 57252k cached

-------------

This is snap from yesterday, we upgrade the kernel, reboot it, today we have load up to 1.0+ or so

Look's like this

---------------------------------

top - 13:49:57 up 1 day, 8 min,  1 user,  load average: 0.60, 0.52, 0.47
Tasks: 390 total,   1 running, 389 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.0%us,  0.4%sy,  0.0%ni, 99.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu4  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu5  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu6  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu7  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu8  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu9  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu10 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu11 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu12 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu13 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu14 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu15 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu16 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu17 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu18 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu19 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu20 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu21 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu22 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu23 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  33003360k total,   904688k used, 32098672k free,    57856k buffers
Swap: 15625208k total,        0k used, 15625208k free,   146788k cached

--------------------

If anyone have any idea what could be goin on - or advice, it would be much appriciated.

caro@sonic:~$ uname -a
Linux sonic 2.6.32-25-server #44-Ubuntu SMP Fri Sep 17 21:13:39 UTC 2010 x86_64 GNU/Linux
caro@sonic:~$
-------------------

Thank you

Ivan

---

### Post by arrrghhh on 2010-10-14
Do you see proc spikes with any particular applications?  You also have nothing running on the server, as you in just installed it from a CD and haven't installed anything else...?

---

### Post by Ivan C on 2010-10-14
Hello,

on "top" CPU's ar almost always 100% idle, so that's OK, the only problem is "load avarage" that goes up and down, for no reason what so ever.

I never seen anything like this before.

Other then this "anomaly" server is working fine, but even so we cant push this in production like this, since we have no idea what is it.

Is it maybe "load avarage" confused by something (maybe how it messure some cycles or what) and showing this numbers?

I am listing everything running just now on server.

Curent load on server

caro@sonic:~$ w
 16:47:27 up 1 day,  3:06,  1 user,  load average: 0.91, 0.60, 0.54


------------------------------------

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  23688  1864 ?        Ss   Oct13   0:05 /sbin/init
root         2  0.0  0.0      0     0 ?        S    Oct13   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    Oct13   0:02 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/2]
root        10  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/2]
root        11  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/2]
root        12  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/3]
root        13  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/3]
root        14  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/3]
root        15  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/4]
root        16  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/4]
root        17  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/4]
root        18  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/5]
root        19  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/5]
root        20  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/5]
root        21  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/6]
root        22  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/6]
root        23  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/6]
root        24  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/7]
root        25  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/7]
root        26  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/7]
root        27  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/8]
root        28  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/8]
root        29  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/8]
root        30  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/9]
root        31  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/9]
root        32  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/9]
root        33  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/10]
root        34  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/10]
root        35  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/10]
root        36  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/11]
root        37  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/11]
root        38  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/11]
root        39  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/12]
root        40  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/12]
root        41  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/12]
root        42  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/13]
root        43  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/13]
root        44  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/13]
root        45  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/14]
root        46  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/14]
root        47  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/14]
root        48  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/15]
root        49  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/15]
root        50  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/15]
root        51  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/16]
root        52  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/16]
root        53  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/16]
root        54  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/17]
root        55  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/17]
root        56  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/17]
root        57  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/18]
root        58  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/18]
root        59  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/18]
root        60  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/19]
root        61  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/19]
root        62  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/19]
root        63  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/20]
root        64  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/20]
root        65  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/20]
root        66  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/21]
root        67  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/21]
root        68  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/21]
root        69  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/22]
root        70  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/22]
root        71  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/22]
root        72  0.0  0.0      0     0 ?        S    Oct13   0:00 [migration/23]
root        73  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksoftirqd/23]
root        74  0.0  0.0      0     0 ?        S    Oct13   0:00 [watchdog/23]
root        75  0.0  0.0      0     0 ?        S    Oct13   0:04 [events/0]
root        76  0.0  0.0      0     0 ?        S    Oct13   0:02 [events/1]
root        77  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/2]
root        78  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/3]
root        79  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/4]
root        80  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/5]
root        81  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/6]
root        82  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/7]
root        83  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/8]
root        84  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/9]
root        85  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/10]
root        86  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/11]
root        87  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/12]
root        88  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/13]
root        89  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/14]
root        90  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/15]
root        91  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/16]
root        92  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/17]
root        93  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/18]
root        94  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/19]
root        95  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/20]
root        96  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/21]
root        97  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/22]
root        98  0.0  0.0      0     0 ?        S    Oct13   0:00 [events/23]
root        99  0.0  0.0      0     0 ?        S    Oct13   0:00 [cpuset]
root       100  0.0  0.0      0     0 ?        S    Oct13   0:00 [khelper]
root       101  0.0  0.0      0     0 ?        S    Oct13   0:00 [netns]
root       102  0.0  0.0      0     0 ?        S    Oct13   0:00 [async/mgr]
root       103  0.0  0.0      0     0 ?        S    Oct13   0:00 [pm]
root       105  0.0  0.0      0     0 ?        S    Oct13   0:00 [sync_supers]
root       106  0.0  0.0      0     0 ?        S    Oct13   0:00 [bdi-default]
root       107  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/0]
root       108  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/1]
root       109  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/2]
root       110  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/3]
root       111  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/4]
root       112  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/5]
root       113  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/6]
root       114  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/7]
root       115  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/8]
root       116  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/9]
root       117  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/10]
root       118  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/11]
root       119  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/12]
root       120  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/13]
root       121  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/14]
root       122  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/15]
root       123  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/16]
root       124  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/17]
root       125  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/18]
root       126  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/19]
root       127  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/20]
root       128  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/21]
root       129  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/22]
root       130  0.0  0.0      0     0 ?        S    Oct13   0:00 [kintegrityd/23]
root       131  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/0]
root       132  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/1]
root       133  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/2]
root       134  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/3]
root       135  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/4]
root       136  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/5]
root       137  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/6]
root       138  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/7]
root       139  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/8]
root       140  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/9]
root       141  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/10]
root       142  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/11]
root       143  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/12]
root       144  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/13]
root       145  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/14]
root       146  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/15]
root       147  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/16]
root       148  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/17]
root       149  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/18]
root       150  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/19]
root       151  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/20]
root       152  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/21]
root       153  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/22]
root       154  0.0  0.0      0     0 ?        S    Oct13   0:00 [kblockd/23]
root       155  0.0  0.0      0     0 ?        S    Oct13   0:00 [kacpid]
root       156  0.0  0.0      0     0 ?        S    Oct13   0:00 [kacpi_notify]
root       157  0.0  0.0      0     0 ?        S    Oct13   0:00 [kacpi_hotplug]
root       158  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/0]
root       159  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/1]
root       160  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/2]
root       161  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/3]
root       162  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/4]
root       163  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/5]
root       164  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/6]
root       165  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/7]
root       166  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/8]
root       167  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/9]
root       168  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/10]
root       169  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/11]
root       170  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/12]
root       171  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/13]
root       172  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/14]
root       173  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/15]
root       174  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/16]
root       175  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/17]
root       176  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/18]
root       177  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/19]
root       178  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/20]
root       179  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/21]
root       180  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/22]
root       181  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata/23]
root       182  0.0  0.0      0     0 ?        S    Oct13   0:00 [ata_aux]
root       183  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksuspend_usbd]
root       184  0.0  0.0      0     0 ?        S    Oct13   0:00 [khubd]
root       185  0.0  0.0      0     0 ?        S    Oct13   0:00 [kseriod]
root       186  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmmcd]
root       211  0.0  0.0      0     0 ?        S    Oct13   0:00 [khungtaskd]
root       212  0.0  0.0      0     0 ?        S    Oct13   0:00 [kswapd0]
root       213  0.0  0.0      0     0 ?        S    Oct13   0:00 [kswapd1]
root       214  0.0  0.0      0     0 ?        SN   Oct13   0:00 [ksmd]
root       215  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/0]
root       216  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/1]
root       217  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/2]
root       218  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/3]
root       219  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/4]
root       220  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/5]
root       221  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/6]
root       222  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/7]
root       223  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/8]
root       224  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/9]
root       225  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/10]
root       226  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/11]
root       227  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/12]
root       228  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/13]
root       229  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/14]
root       230  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/15]
root       231  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/16]
root       232  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/17]
root       233  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/18]
root       234  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/19]
root       235  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/20]
root       236  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/21]
root       237  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/22]
root       238  0.0  0.0      0     0 ?        S    Oct13   0:00 [aio/23]
root       239  0.0  0.0      0     0 ?        S    Oct13   0:00 [ecryptfs-kthrea]
root       240  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/0]
root       241  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/1]
root       242  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/2]
root       243  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/3]
root       244  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/4]
root       245  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/5]
root       246  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/6]
root       247  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/7]
root       248  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/8]
root       249  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/9]
root       250  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/10]
root       251  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/11]
root       252  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/12]
root       253  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/13]
root       254  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/14]
root       255  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/15]
root       256  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/16]
root       257  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/17]
root       258  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/18]
root       259  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/19]
root       260  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/20]
root       261  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/21]
root       262  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/22]
root       263  0.0  0.0      0     0 ?        S    Oct13   0:00 [crypto/23]
root       314  0.0  0.0      0     0 ?        S    Oct13   0:00 [scsi_eh_0]
root       315  0.0  0.0      0     0 ?        S    Oct13   0:00 [scsi_eh_1]
root       317  0.0  0.0      0     0 ?        S    Oct13   0:00 [scsi_eh_2]
root       318  0.0  0.0      0     0 ?        S    Oct13   0:00 [scsi_eh_3]
root       321  0.0  0.0      0     0 ?        S    Oct13   0:00 [kstriped]
root       322  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/0]
root       323  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/1]
root       324  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/2]
root       325  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/3]
root       326  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/4]
root       327  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/5]
root       328  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/6]
root       329  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/7]
root       330  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/8]
root       331  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/9]
root       332  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/10]
root       333  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/11]
root       334  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/12]
root       335  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/13]
root       336  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/14]
root       337  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/15]
root       338  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/16]
root       339  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/17]
root       340  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/18]
root       341  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/19]
root       342  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/20]
root       343  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/21]
root       344  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/22]
root       345  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpathd/23]
root       346  0.0  0.0      0     0 ?        S    Oct13   0:00 [kmpath_handlerd]
root       347  0.0  0.0      0     0 ?        S    Oct13   0:00 [ksnapd]
root       348  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/0]
root       349  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/1]
root       350  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/2]
root       351  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/3]
root       352  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/4]
root       353  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/5]
root       354  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/6]
root       355  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/7]
root       356  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/8]
root       357  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/9]
root       358  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/10]
root       359  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/11]
root       360  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/12]
root       361  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/13]
root       362  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/14]
root       363  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/15]
root       364  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/16]
root       365  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/17]
root       366  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/18]
root       367  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/19]
root       368  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/20]
root       369  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/21]
root       370  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/22]
root       371  0.0  0.0      0     0 ?        S    Oct13   0:00 [kondemand/23]
root       372  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/0]
root       373  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/1]
root       374  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/2]
root       375  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/3]
root       376  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/4]
root       377  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/5]
root       378  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/6]
root       379  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/7]
root       380  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/8]
root       381  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/9]
root       382  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/1]
root       383  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/1]
root       384  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/1]
root       385  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/1]
root       386  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/1]
root       387  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/1]
root       388  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/1]
root       389  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/1]
root       390  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/1]
root       391  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/1]
root       392  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/2]
root       393  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/2]
root       394  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/2]
root       395  0.0  0.0      0     0 ?        S    Oct13   0:00 [kconservative/2]
root       540  0.0  0.0      0     0 ?        S    Oct13   0:00 [scsi_eh_4]
root       543  0.0  0.0      0     0 ?        S    Oct13   0:00 [usbhid_resumer]
root       563  0.0  0.0      0     0 ?        S    Oct13   0:00 [jbd2/sda3-8]
root       564  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       565  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       566  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       567  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       568  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       569  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       570  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       571  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       572  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       573  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       574  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       575  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       576  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       577  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       578  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       579  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       580  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       581  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       582  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       583  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       584  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       585  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       586  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       587  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       629  0.0  0.0  16904   864 ?        S    Oct13   0:00 upstart-udev-bridge --daemon
root       632  0.0  0.0  17016   848 ?        S<s  Oct13   0:00 udevd --daemon
root       857  0.0  0.0      0     0 ?        S    Oct13   0:00 [kpsmoused]
root       904  0.0  0.0  17012   756 ?        S<   Oct13   0:00 udevd --daemon
root       907  0.0  0.0  17012   716 ?        S<   Oct13   0:00 udevd --daemon
root       943  0.0  0.0      0     0 ?        S    Oct13   0:00 [jbd2/sda1-8]
root       944  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       945  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       946  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       947  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       948  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       949  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       584  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       585  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       586  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       587  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       629  0.0  0.0  16904   864 ?        S    Oct13   0:00 upstart-udev-bridge --daemon
root       632  0.0  0.0  17016   848 ?        S<s  Oct13   0:00 udevd --daemon
root       857  0.0  0.0      0     0 ?        S    Oct13   0:00 [kpsmoused]
root       904  0.0  0.0  17012   756 ?        S<   Oct13   0:00 udevd --daemon
root       907  0.0  0.0  17012   716 ?        S<   Oct13   0:00 udevd --daemon
root       943  0.0  0.0      0     0 ?        S    Oct13   0:00 [jbd2/sda1-8]
root       944  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       945  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       946  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       947  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       948  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       949  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       950  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       951  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       952  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       953  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       954  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       955  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       956  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       957  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       958  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       959  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       960  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       961  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       962  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       963  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       964  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       965  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       966  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
root       967  0.0  0.0      0     0 ?        S    Oct13   0:00 [ext4-dio-unwrit]
syslog     986  0.0  0.0 125980  1936 ?        Sl   Oct13   0:02 rsyslogd -c4
root      1031  0.0  0.0   6080   648 tty4     Ss+  Oct13   0:00 /sbin/getty -8 38400 tty4
root      1035  0.0  0.0   6080   652 tty5     Ss+  Oct13   0:00 /sbin/getty -8 38400 tty5
root      1039  0.0  0.0   6080   648 tty2     Ss+  Oct13   0:00 /sbin/getty -8 38400 tty2
root      1041  0.0  0.0   6080   652 tty3     Ss+  Oct13   0:00 /sbin/getty -8 38400 tty3
root      1044  0.0  0.0   6080   648 tty6     Ss+  Oct13   0:00 /sbin/getty -8 38400 tty6
root      1052  0.0  0.0  11284   676 ?        Ss   Oct13   0:30 /usr/sbin/irqbalance
root      1056  0.0  0.0  21076  1024 ?        Ss   Oct13   0:00 cron
daemon    1057  0.0  0.0  18884   460 ?        Ss   Oct13   0:00 atd
root      1164  0.0  0.0   6080   648 tty1     Ss+  Oct13   0:00 /sbin/getty -8 38400 tty1
root      1181  0.0  0.0  49260  1096 ?        Ss   Oct13   0:02 /usr/sbin/sshd
root      1488  0.0  0.0  70616  3200 ?        Ss   Oct13   0:00 sshd: caro [priv]
caro      1556  0.0  0.0  70616  1664 ?        S    Oct13   0:02 sshd: caro@pts/0
caro      1557  0.0  0.0  20600  3404 pts/0    Ss   Oct13   0:00 -bash
root     23502  0.0  0.0      0     0 ?        S    16:45   0:00 [flush-8:0]
caro     23508  0.0  0.0  15256  1224 pts/0    R+   16:45   0:00 ps aux
caro     23509  0.0  0.0   9872  1016 pts/0    S+   16:45   0:00 more

---------------

Thanks for any advice.

I.

---

### Post by arrrghhh on 2010-10-14
Hrm.  Load average looks fine now... I'm honestly not sure, if you don't see any processes stealing cycles, then I'm not sure what could cause the load to look out of whack...

---

### Post by Ivan C on 2010-10-14
But load is still 0.90+

That's still to much. Again, everything look's good on server, except "load avarage"

Load avarage should be 0.00 or close to that number when server is IDLE

I dont understand how it can go up to 1.0+ and beyond witout doin any work what so ever.

Did anyone had similar issue ?

I.

---

### Post by WinstonChurchill on 2010-10-14
I think you're forgetting that the load average is not adjusted based on the number of processors in your system: if your system has 12 cores, than a load of 12.00 would be a full system load - a load of 1.00 is next to nothing. If we're willing to be (more than) a little mathematically dubious, we could say that a load of 1.00 on a 12-core system is equivalent to a load of 0.08 (1/12) on a single-core system. 

You're correct that if nothing is going on the load should be near zero, but are you logging in over SSH? Especially if you're running top over an SSH connection with a high refresh rate, you're going to see some increase in load due to the work SSH is doing to encrypt your connection.

Here are a few good articles that explain the load average in depth:
[http://www.teamquest.com/resources/gunther/display/5/index.htm](http://www.teamquest.com/resources/gunther/display/5/index.htm)
[http://www.linuxjournal.com/article/9001](http://www.linuxjournal.com/article/9001)

---

### Post by arrrghhh on 2010-10-14
That number is very deceptive... and it just got even more so!  I did not realize the numbers would become that skewed over multiple cores like that...

---

### Post by Ivan C on 2010-10-15
Winston,

I was thinking something in same line, but even if you dont run "top" command, and you ar loged out, even for hours, and you just loged back in, you can see load was there all this time.

You can just type simple "w" and you get numbers like:

caro@sonic:~$ w
 02:49:44 up 1 day, 13:08,  1 user,  load average: 0.42, 0.32, 0.38


TOP command is not making this number, also refresh rate is normal, standard one. Nothing special is goin on at that server.

We also have few other servers similar configuration, but none of them is running ubuntu, and none of them same issue.

I.

---

### Post by WinstonChurchill on 2010-10-18
I honestly don't think this is something you really need to worry too much about - that server you're describing is pretty beefy. What are you planning to do with it anyway? 

For a more in-depth picture of what the processor is spending its time doing, run the 'procinfo' command and read it's output. (You'll probably have to do 'sudo apt-get install procinfo' - I don't think it's default installed...) On my laptop, I see the following:
```

user@Laptop:~$ procinfo
Memory:        Total        Used        Free     Buffers                       
RAM:         4024436     1339532     2684904       57136                       
Swap:              0           0           0                                   

Bootup: Mon Oct 18 09:48:54 2010   Load average: 0.56 0.44 0.29 1/316 4787     

user  :   00:07:32.27   3.7%  page in :           510778                       
nice  :   00:00:00.94   0.0%  page out:           236649                       
system:   00:03:57.75   1.9%  page act:            79836                       
IOwait:   00:02:16.00   1.1%  page dea:                0                       
hw irq:   00:00:00.20   0.0%  page flt:          2967383                       
sw irq:   00:00:08.28   0.1%  swap in :                0                       
idle  :   03:11:25.40  93.2%  swap out:                0                       
uptime:   02:55:41.74         context :          4984445                       

irq   0:     935024  timer               irq  19:          0  uhci_hcd:usb5, uh
irq   1:       5747  i8042               irq  21:          0  uhci_hcd:usb4    
irq   8:          1  rtc0                irq  23:      19682  ehci_hcd:usb2, uh
irq   9:      11034  acpi                irq  42:          0  pciehp           
irq  12:     347582  i8042               irq  43:      27839  ahci             
irq  16:          0  uhci_hcd:usb3       irq  44:      17116  i915@pci:0000:00:
irq  17:     229415  ath9k               irq  45:        629  hda_intel        
irq  18:         35  ehci_hcd:usb1, uh   irq  46:          0  eth0             

sda             9067r           17251w   sdb              371r               0w

eth0        TX 0.00B         RX 0.00B         wlan0       TX 2.35MiB       RX 12.94MiB     
lo          TX 480.00B       RX 480.00B
```If there's an inordinate amount of time spend in the IRQ handlers, you could have some sort of a hardware issue (drivers, probably)... other than that, I don't really know what else to tell you.

---

