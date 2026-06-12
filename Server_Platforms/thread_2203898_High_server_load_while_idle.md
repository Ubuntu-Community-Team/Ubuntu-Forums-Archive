---
title: "High server load while idle"
date: 2014-02-05
forum: Server Platforms
---

### Post by alexclifford47 on 2014-02-05
Hi,
The following server sits at a load of 24 by default while not doing anything. But I cannot figure out why this has ocurred. Lately I did upgrade this 10.04 box to get the latest kernels and things with dist-upgrade.
```
[COLOR=#000000]top - 09:39:37 up 2 days, 22:37,  1 user,  load average: 24.00, 24.00, 24.00
[/COLOR]Tasks: 235 total,   1 running, 233 sleeping,   0 stopped,   1 zombie
Cpu(s):  2.9%us,  1.1%sy,  0.0%ni, 96.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  16466348k total, 16177684k used,   288664k free,  1886960k buffers
Swap: 19803128k total,        0k used, 19803128k free, 11844068k cached

root@ubuntu:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid
root@ubuntu:~# uname -a
Linux ubuntu 2.6.32-55-generic #117-Ubuntu SMP Tue Dec 3 17:31:12 UTC 2013 x86_64 GNU/Linux
root@ubuntu:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done [COLOR=#000000]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]
```

---

### Post by Doug S on 2014-02-05
There is a zombie thread which is always a worry. There have been issues with reported load averages being incorrect, but I have no idea where kernel 2.6 is with that stuff. Is there any virtual machine running on that computer? I have seen ridiculous reported load averages when I run a VM. Use "top" to observe what is going on.

---

### Post by tgalati4 on 2014-02-05
Install *htop* and see what that says.  Use *uptime* or *w* (which stands for what) as a cross check for load.  It could be the zombie process that has waiting instructions on all of your cores.  If you have 4 cores, and you have 6 pending operations on each core, that would give you a load of 24 across the board.

---

### Post by alexclifford47 on 2014-02-05
Thanks for the quick replies. I've checked htop and w and do not see anything jumping out in relation to CPU, memory, or I/O wait.
The zombie process isn't there anymore when I check top. I now get:
```

top - 12:21:24 up 3 days,  1:19,  1 user,  load average: 24.05, 24.08, 24.06
Tasks: 219 total,   1 running, 218 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu4  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu5  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu6  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu7  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  16466348k total, 16161588k used,   304760k free,  1893648k buffers
Swap: 19803128k total,        0k used, 19803128k free, 11915020k cached

```
I have read through Google searches about issues with the kernel not reporting correct load averages. But I cannot pin point any of the issues I'm reading to match what I am seeing and what my system is running.

---

### Post by alexclifford47 on 2014-02-05
I do see a couple of problems worth mentioning. There is a zombie process on boot, and a lot of processes in uninterruptible sleep.

This is after a fresh reboot:
```

root@ubuntu:~# ps auxwwwf
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         2  0.0  0.0      0     0 ?        S    13:32   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [migration/0]
root         4  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [migration/1]
root         7  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [migration/2]
root        10  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ksoftirqd/2]
root        11  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [watchdog/2]
root        12  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [migration/3]
root        13  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ksoftirqd/3]
root        14  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [watchdog/3]
root        15  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [migration/4]
root        16  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ksoftirqd/4]
root        17  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [watchdog/4]
root        18  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [migration/5]
root        19  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ksoftirqd/5]
root        20  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [watchdog/5]
root        21  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [migration/6]
root        22  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ksoftirqd/6]
root        23  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [watchdog/6]
root        24  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [migration/7]
root        25  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ksoftirqd/7]
root        26  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [watchdog/7]
root        27  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [events/0]
root        28  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [events/1]
root        29  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [events/2]
root        30  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [events/3]
root        31  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [events/4]
root        32  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [events/5]
root        33  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [events/6]
root        34  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [events/7]
root        35  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [cpuset]
root        36  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [khelper]
root        37  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [netns]
root        38  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [async/mgr]
root        39  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [pm]
root        41  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [sync_supers]
root        42  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [bdi-default]
root        43  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kintegrityd/0]
root        44  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kintegrityd/1]
root        45  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kintegrityd/2]
root        46  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kintegrityd/3]
root        47  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kintegrityd/4]
root        48  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kintegrityd/5]
root        49  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kintegrityd/6]
root        50  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kintegrityd/7]
root        51  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kblockd/0]
root        52  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kblockd/1]
root        53  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kblockd/2]
root        54  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kblockd/3]
root        55  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kblockd/4]
root        56  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kblockd/5]
root        57  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kblockd/6]
root        58  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kblockd/7]
root        59  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kacpid]
root        60  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kacpi_notify]
root        61  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kacpi_hotplug]
root        62  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ata/0]
root        63  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ata/1]
root        64  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ata/2]
root        65  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ata/3]
root        66  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ata/4]
root        67  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ata/5]
root        68  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ata/6]
root        69  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ata/7]
root        70  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ata_aux]
root        71  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ksuspend_usbd]
root        72  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [khubd]
root        73  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kseriod]
root        74  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kmmcd]
root        83  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [khungtaskd]
root        84  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kswapd0]
root        85  0.0  0.0      0     0 ?        SN   13:32   0:00  \_ [ksmd]
root        86  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [aio/0]
root        87  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [aio/1]
root        88  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [aio/2]
root        89  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [aio/3]
root        90  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [aio/4]
root        91  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [aio/5]
root        92  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [aio/6]
root        93  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [aio/7]
root        94  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ecryptfs-kthrea]
root        95  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [crypto/0]
root        96  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [crypto/1]
root        97  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [crypto/2]
root        98  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [crypto/3]
root        99  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [crypto/4]
root       100  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [crypto/5]
root       101  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [crypto/6]
root       102  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [crypto/7]
root       105  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kstriped]
root       106  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kmpathd/0]
root       107  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kmpathd/1]
root       108  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kmpathd/2]
root       109  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kmpathd/3]
root       110  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kmpathd/4]
root       111  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kmpathd/5]
root       112  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kmpathd/6]
root       113  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kmpathd/7]
root       114  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kmpath_handlerd]
root       115  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ksnapd]
root       116  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kondemand/0]
root       117  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kondemand/1]
root       118  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kondemand/2]
root       119  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kondemand/3]
root       120  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kondemand/4]
root       121  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kondemand/5]
root       122  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kondemand/6]
root       123  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kondemand/7]
root       124  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kconservative/0]
root       125  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kconservative/1]
root       126  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kconservative/2]
root       127  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kconservative/3]
root       128  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kconservative/4]
root       129  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kconservative/5]
root       130  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kconservative/6]
root       131  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [kconservative/7]
root       331  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [scsi_eh_0]
root       342  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [scsi_eh_1]
root       348  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [scsi_eh_2]
root       351  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [scsi_eh_3]
root       358  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [khpsbpkt]
root       359  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [scsi_eh_4]
root       360  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [scsi_eh_5]
root       361  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [scsi_eh_6]
root       362  0.0  0.0      0     0 ?        D    13:32   0:00  \_ [scsi_eh_7]
root       363  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [scsi_eh_8]
root       364  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [scsi_eh_9]
root       368  0.0  0.0      0     0 ?        D    13:32   0:00  \_ [async/7]
root       369  0.0  0.0      0     0 ?        D    13:32   0:00  \_ [async/8]
root       370  0.0  0.0      0     0 ?        D    13:32   0:00  \_ [async/9]
root       371  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [scsi_eh_10]
root       372  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [scsi_eh_11]
root       373  0.0  0.0      0     0 ?        D    13:32   0:00  \_ [async/10]
root       374  0.0  0.0      0     0 ?        D    13:32   0:00  \_ [async/11]
root       375  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [scsi_eh_12]
root       376  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [scsi_eh_13]
root       377  0.0  0.0      0     0 ?        D    13:32   0:00  \_ [async/12]
root       378  0.0  0.0      0     0 ?        D    13:32   0:00  \_ [async/13]
root       394  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [jbd2/sda1-8]
root       395  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ext4-dio-unwrit]
root       396  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ext4-dio-unwrit]
root       397  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ext4-dio-unwrit]
root       398  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ext4-dio-unwrit]
root       399  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ext4-dio-unwrit]
root       400  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ext4-dio-unwrit]
root       401  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ext4-dio-unwrit]
root       402  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [ext4-dio-unwrit]
root       435  0.0  0.0      0     0 ?        S    13:32   0:00  \_ [flush-8:0]
root       807  0.0  0.0      0     0 ?        S    13:33   0:00  \_ [knodemgrd_0]
root      1188  0.0  0.0      0     0 ?        S    13:33   0:00  \_ [kvm-irqfd-clean]
root         1  0.5  0.0  23828  2096 ?        Ss   13:32   0:01 /sbin/init
root       282  0.0  0.0   4128   732 ?        D<   13:32   0:00 /sbin/modprobe -b pci:v0000197Bd00002363sv00001458sd0000B000bc01sc06i01
root       292  0.0  0.0   4060   660 ?        D<   13:32   0:00 /sbin/modprobe -b pci:v0000197Bd00002363sv00001458sd0000B000bc01sc01i85
root       294  0.0  0.0   4120   720 ?        D<   13:32   0:00 /sbin/modprobe -b pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00
root       327  0.0  0.0   4212   808 ?        D<   13:32   0:00 /sbin/modprobe -b pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10
root       436  0.0  0.0  18972   204 ?        S    13:32   0:00 /sbin/ureadahead --daemon
root       460  0.0  0.0  17052   936 ?        S    13:33   0:00 upstart-udev-bridge --daemon
root       502  0.0  0.0  17436  1368 ?        S<s  13:33   0:00 udevd --daemon
root       723  0.0  0.0  17432  1200 ?        S<   13:33   0:00  \_ udevd --daemon
root       724  0.0  0.0  17432  1196 ?        S<   13:33   0:00  \_ udevd --daemon
root       504  0.0  0.0  94288  4516 ?        Ss   13:33   0:00 smbd -F
root       896  0.0  0.0  94288  1376 ?        S    13:33   0:00  \_ smbd -F
root       506  0.0  0.0  17668  1388 ?        Ss   13:33   0:00 /bin/sh -e /proc/self/fd/8
root       513  0.0  0.0  17672   796 ?        S    13:33   0:00  \_ /bin/sh -e /proc/self/fd/8
root       673  0.0  0.0   4120   704 ?        D    13:33   0:00      \_ modprobe lp
syslog     510  0.0  0.0 126764  2452 ?        Sl   13:33   0:00 rsyslogd -c4
root       526  0.0  0.0   4124   724 ?        D<   13:33   0:00 /sbin/modprobe -b pci:v00001033d00000194sv00001458sd00005007bc0Csc03i30
root       532  0.0  0.0   4092   692 ?        D<   13:33   0:00 /sbin/modprobe -b pci:v000010DEd00000BE3sv00001458sd000034D7bc04sc03i00
root       533  0.0  0.0   4064   668 ?        D<   13:33   0:00 /sbin/modprobe -b pci:v000010DEd00000A65sv00001458sd000034D7bc03sc00i00
root       555  0.0  0.0   4072   676 ?        D<   13:33   0:00 /sbin/modprobe -b pci:v00008086d00003A3Esv00001458sd0000A102bc04sc03i00
root       588  0.0  0.0   4064   656 ?        D<   13:33   0:00 /sbin/modprobe -b serio:ty01pr00id00ex00
102        692  0.0  0.0  23568  1096 ?        Ss   13:33   0:00 dbus-daemon --system --fork
root       804  0.0  0.0   4104   704 ?        D<   13:33   0:00 /sbin/modprobe -b pci:v0000104Cd00008024sv00001458sd00001000bc0Csc00i10
avahi      822  0.0  0.0  34308  1880 ?        S    13:33   0:00 avahi-daemon: running [ubuntu.local]
avahi      823  0.0  0.0  33944   580 ?        Ss   13:33   0:00  \_ avahi-daemon: chroot helper
daemon     846  0.0  0.0   8272   528 ?        Ss   13:33   0:00 portmap
root       872  0.0  0.0  85040  4892 ?        Ss   13:33   0:00 NetworkManager
root       879  0.0  0.0  57888  2528 ?        S    13:33   0:00 /usr/sbin/modem-manager
root       884  0.0  0.0  28388  2096 ?        S    13:33   0:00 /sbin/wpa_supplicant -u -s
root       946  0.0  0.0  44184  8788 ?        Ss   13:33   0:00 /usr/sbin/munin-node
root       979  0.0  0.0  49280  2552 ?        Ss   13:33   0:00 /usr/sbin/sshd -D
root      2009  0.1  0.0  85340  3656 ?        Ss   13:37   0:00  \_ sshd: root@pts/0    
root      2085  0.0  0.0  19492  2244 pts/0    Ss   13:37   0:00      \_ -bash
root      2099  0.0  0.0  15412  1284 pts/0    R+   13:38   0:00          \_ ps auxwwwf
root       997  0.0  0.0  14812   300 ?        Ss   13:33   0:00 /usr/sbin/in.tftpd --listen --user tftp --address 0.0.0.0:69 --secure /var/lib/tftpboot
root      1050  0.0  0.0  60616  1752 ?        Ss   13:33   0:00 nmbd -D
root      1073  0.0  0.0  17668  1420 ?        Ss   13:33   0:00 /bin/sh -e /proc/self/fd/12
root      1176  0.0  0.0   4532  1116 ?        D    13:33   0:00  \_ modprobe -b kvm_intel
root      1074  0.0  0.0  17920  1804 ?        Ss   13:33   0:00 /bin/sh /etc/init.d/rc 2
root      1583  0.0  0.0  17876  1760 ?        S    13:33   0:00  \_ /bin/sh /etc/rc2.d/S50cups start
root      1611  0.0  0.0   4072   668 ?        D    13:33   0:00      \_ modprobe -q -b lp
root      1075  0.0  0.0   6096   656 tty4     Ss+  13:33   0:00 /sbin/getty -8 38400 tty4
root      1080  0.0  0.0   6096   660 tty5     Ss+  13:33   0:00 /sbin/getty -8 38400 tty5
root      1168  0.0  0.0   6096   660 tty2     Ss+  13:33   0:00 /sbin/getty -8 38400 tty2
root      1169  0.0  0.0   6096   656 tty3     Ss+  13:33   0:00 /sbin/getty -8 38400 tty3
root      1172  0.0  0.0   6096   656 tty6     Ss+  13:33   0:00 /sbin/getty -8 38400 tty6
root      1175  0.0  0.0   4444  1116 ?        Ss   13:33   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
daemon    1183  0.0  0.0  18900   460 ?        Ss   13:33   0:00 atd
root      1184  0.0  0.0  21092  1028 ?        Ss   13:33   0:00 cron
root      1194  0.0  0.0  11300   620 ?        Ss   13:33   0:00 /usr/sbin/irqbalance
mysql     1217  0.0  0.1 189756 25644 ?        Ssl  13:33   0:00 /usr/sbin/mysqld
root      1298  0.0  0.0 122696  3700 ?        Sl   13:33   0:00 /usr/sbin/console-kit-daemon --no-daemon
hudson    1405  0.0  0.0  18312   592 ?        Ss   13:33   0:00 /usr/bin/daemon --name=hudson --inherit --env=HUDSON_HOME=/var/lib/hudson --output=/var/log/hudson/hudson.log --pidfile=/var/run/hudson/hudson.pid -- /usr/bin/java -jar /usr/share/hudson/hudson.war --webroot=/var/run/hudson/war
hudson    1418  8.4  1.7 4921624 285272 ?      Sl   13:33   0:24  \_ /usr/bin/java -jar /usr/share/hudson/hudson.war --webroot=/var/run/hudson/war
nagios    1529  0.0  0.0  24812  1124 ?        Ss   13:33   0:00 /usr/sbin/nrpe -c /etc/nagios/nrpe.cfg -d
ntp       1532  0.0  0.0  27880  1544 ?        Ss   13:33   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 119:123
root      1833  0.0  0.0  28820  1212 ?        Ss   13:36   0:00 kdm
root      1861  0.0  0.0  19212  1732 ?        S    13:36   0:00  \_ /bin/bash /etc/gdm/failsafeXServer
root      1872  0.0  0.0  15672   828 ?        S    13:36   0:00      \_ xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe -- /usr/bin/X -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log
root      1873  0.0  0.0      0     0 ?        Z<   13:36   0:00          \_ [Xorg] <defunct>
root      1849  0.0  0.0   4384   972 ?        D    13:36   0:00 modprobe nouveau

```

---

### Post by thnewguy on 2014-02-06
This may seem like a silly question, but is the server acting like it is under heavy load. The CPU and IO indicators seem to show that the machine is more or less idle. That suggests to me that the load of 24 might be calculated incorrectly. Is the server responsive/fast when you run programs, try to login, etc? I am curious as to whether the server performs as though it is under heavy load or if it acts in a way which suggests it is idle.

---

### Post by tgalati4 on 2014-02-06
Install *cpuburn* read the man page and run several instances and watch the load after each instance.

```
burnP6 &
burnP6 &
burnP6 &
```

Each instance of *burnP6* will give you a load of 1.0 on that core.  As you add load, the load indicator should go up by increments of 1.0.

If this is a server, then why is there a zombie xorg process?

---

### Post by Doug S on 2014-02-06
> **alexclifford47 said:**
> I do see a couple of problems worth mentioning. There is a zombie process on boot, and a lot of processes in uninterruptible sleep.

This is after a fresh reboot:
```

root@ubuntu:~# ps auxwwwf
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
... deleted a bunch...
hudson    1405  0.0  0.0  18312   592 ?        Ss   13:33   0:00 /usr/bin/daemon --name=hudson --inherit --env=HUDSON_HOME=/var/lib/hudson --output=/var/log/hudson/hudson.log --pidfile=/var/run/hudson/hudson.pid -- /usr/bin/java -jar /usr/share/hudson/hudson.war --webroot=/var/run/hudson/war
hudson    1418  8.4  1.7 4921624 285272 ?      Sl   13:33   0:24  \_ /usr/bin/java -jar /usr/share/hudson/hudson.war --webroot=/var/run/hudson/war

```We can not tell much from a snapshot just after re-boot, but if the uninterruptible sleep tasks persist, that would explain the high load average (I count 20). While I have no proof, I suspect the hudson stuff as a contributor.

---

### Post by alexclifford47 on 2014-02-06
> **thnewguy said:**
> This may seem like a silly question, but is the server acting like it is under heavy load. The CPU and IO indicators seem to show that the machine is more or less idle. That suggests to me that the load of 24 might be calculated incorrectly. Is the server responsive/fast when you run programs, try to login, etc? I am curious as to whether the server performs as though it is under heavy load or if it acts in a way which suggests it is idle.
No, the server is basically idle. hudson is doing a tiny bit now and then, but basically nothing. The server is very responsive when using it, so the load average calculation isn't coming from CPU/memory/IO.

> **tgalati4 said:**
> Install *cpuburn* read the man page and run severall instances and watch the load after each instance.

```
burnP6 &
burnP6 &
burnP6 &
```

Each instance of *burnP6* will give you a load of 1.0 on that core. As you add load, the load indicator should go up by increments of 1.0.

If this is a server, then why is there a zombie xorg process?
cpuburn works as expected to add further 1.0 load for each core used up. System is still fine with 4 cpuburn processes running (load jumped to 26, then back down to 22 again). There were 22 D state processes at the time of the test. I've gone ahead and removed xorg-server also, as you were right it should not have been installed in the first place.

> **Doug S said:**
> We can not tell much from a snapshot just after re-boot, but if the uninterruptible sleep tasks persist, that would explain the high load average (I count 20). While I have no proof, I suspect the hudson stuff as a contributor.
It stays in this stage for hours after a fresh reboot. The load seems to stick with the current amount of processes in uninterruptible sleep. At the moment the load averages are at 22 and there are 22 processes still in uninterruptible sleep. All the D state processes appear related to modprobe. I do not really know where to begin investigating what could be going wrong with that sort of thing.

---

### Post by tgalati4 on 2014-02-06
You would normally blacklist modules that don't load properly.  If this is a headless server, then you can put the nouveau module into the blacklist so it is not loaded.  It's not needed for just a text terminal.  The dead PCI processes you will have to investigate.  The kernel obviously sent out commands to those PCI addresses but nothing came back or it was unrecognizable to the kernel.

I would spend some time going through *dmesg | more* and take note of each hiccup during boot.  Sometimes researching and cleaning up these kernel problems can make your server run much smoother.

---

