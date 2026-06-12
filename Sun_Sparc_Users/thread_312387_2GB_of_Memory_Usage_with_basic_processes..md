---
title: "2GB of Memory Usage with basic processes."
date: 2006-12-04
forum: Sun Sparc Users
---

### Post by cwinslett on 2006-12-04
I've got Ubuntu 6.10 running on a v100.  There is 2 GB of memory in the box and Ubuntu uses every bit of it.

Has anyone else had this problem, and is there anyway to lower mem usage to typical Linux level?

Below are all the processes running on a ps aux command:

```
root         1  0.1  0.0   1872   752 ?        S    08:47   0:02 init [2]
root         2  0.0  0.0      0     0 ?        S    08:47   0:00 [migration/1]
root         3  0.0  0.0      0     0 ?        SN   08:47   0:00 [ksoftirqd/1]
root         4  0.0  0.0      0     0 ?        S    08:47   0:00 [migration/0]
root         5  0.0  0.0      0     0 ?        SN   08:47   0:00 [ksoftirqd/0]
root         6  0.0  0.0      0     0 ?        S<   08:47   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   08:47   0:00 [events/1]
root         8  0.0  0.0      0     0 ?        S<   08:47   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S<   08:47   0:00 [kthread]
root        31  0.0  0.0      0     0 ?        S    08:47   0:00 [powerd]
root        32  0.0  0.0      0     0 ?        S<   08:47   0:00 [kblockd/0]
root        33  0.0  0.0      0     0 ?        S<   08:47   0:00 [kblockd/1]
root        36  0.0  0.0      0     0 ?        S<   08:47   0:00 [khubd]
root        73  0.0  0.0      0     0 ?        S    08:47   0:00 [pdflush]
root        74  0.0  0.0      0     0 ?        S    08:47   0:00 [pdflush]
root        76  0.0  0.0      0     0 ?        S<   08:47   0:00 [aio/0]
root        75  0.0  0.0      0     0 ?        S    08:47   0:00 [kswapd0]
root        77  0.0  0.0      0     0 ?        S<   08:47   0:00 [aio/1]
root       669  0.0  0.0      0     0 ?        S<   08:47   0:00 [kseriod]
root      1594  0.0  0.0      0     0 ?        S<   08:47   0:00 [scsi_eh_0]
root      1607  0.0  0.0      0     0 ?        S<   08:47   0:00 [scsi_eh_1]
root      1853  0.1  0.0      0     0 ?        S    08:47   0:02 [kjournald]
root      2034  0.0  0.0   3040   728 ?        S<s  08:47   0:00 /sbin/udevd --daemon
root      3119  0.0  0.0      0     0 ?        S    08:48   0:00 [kjournald]
root      3452  0.0  0.0   9808  1416 ?        Ssl  08:48   0:00 /usr/sbin/nscd
syslog    3472  0.0  0.0   2648   872 ?        Ss   08:48   0:00 /sbin/syslogd -r -u syslog
root      3489  0.0  0.0   2136   720 ?        Ss   08:48   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      3491  0.0  0.0   2616  1360 ?        Ss   08:48   0:00 /sbin/klogd -P /var/run/klogd/kmsg
cupsys    3546  0.0  0.1   6880  2232 ?        Ss   08:48   0:00 /usr/sbin/cupsd
106       3570  0.0  0.0   2976   672 ?        Ss   08:48   0:00 /usr/bin/dbus-daemon --system
nagios    3811  0.0  0.0   4344  1024 ?        Ss   08:48   0:00 /usr/local/nagios/bin/nrpe -c /usr/local/nagios/etc/nrpe.cfg -d
root      3919  0.0  0.0   6312  1440 ?        Ss   08:48   0:00 /usr/sbin/sshd
root      4039  0.0  0.0   1928   392 ?        Ss   08:48   0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
daemon    4080  0.0  0.0   2488   512 ?        Ss   08:48   0:00 /usr/sbin/atd
root      4092  0.0  0.0   2752   888 ?        Ss   08:48   0:00 /usr/sbin/cron
root      4214  0.0  0.0   1872   752 tty1     Ss+  08:48   0:00 /sbin/getty 38400 tty1
root      4216  0.0  0.0   1872   752 tty2     Ss+  08:48   0:00 /sbin/getty 38400 tty2
root      4217  0.0  0.0   1872   752 tty3     Ss+  08:48   0:00 /sbin/getty 38400 tty3
root      4218  0.0  0.0   1872   752 tty4     Ss+  08:48   0:00 /sbin/getty 38400 tty4
root      4220  0.0  0.0   1872   752 tty5     Ss+  08:48   0:00 /sbin/getty 38400 tty5
root      4221  0.0  0.0   1872   752 tty6     Ss+  08:48   0:00 /sbin/getty 38400 tty6
root      4581  0.0  0.1  10672  3336 ?        Ss   08:50   0:00 sshd: user [priv]
1000      4843  0.0  0.1  10832  2128 ?        S    08:50   0:00 sshd: user@pts/0
1000      4875  0.0  0.1   5408  2800 pts/0    Ss   08:50   0:00 -bash
root      7299  0.0  0.1   5152  2784 pts/0    S    08:55   0:00 bash
nagios    8685  0.2  0.0  12512  2032 ?        Ssl  08:59   0:02 /usr/local/nagios/bin/nagios -d /usr/local/nagios/etc/nagios.cfg
root     10295  0.0  0.1  10672  3336 ?        Ss   09:05   0:00 sshd: user [priv]
1000     10311  0.0  0.1  10832  2128 ?        S    09:05   0:00 sshd: user@pts/1
1000     10312  0.0  0.1   5408  2776 pts/1    Ss   09:05   0:00 -bash
nagios   14243  0.0  0.0  12520  1424 ?        S    09:17   0:00 /usr/local/nagios/bin/nagios -d /usr/local/nagios/etc/nagios.cfg
nagios   14244  0.2  0.0   3352  1168 ?        S    09:17   0:00 /usr/local/nagios/libexec/check_ping -H xxx.xxx.xxx.xxx -w 100.0,20% -c 50
nagios   14245  0.0  0.0   2104   760 ?        S    09:17   0:00 /bin/ping -n -U -w 10 -c 5 xxx.xxx.xxx.xxx
```

/proc/meminfo

```
MemTotal:      2072104 kB
MemFree:         16296 kB
Buffers:         18288 kB
Cached:        1955576 kB
SwapCached:         56 kB
Active:         448352 kB
Inactive:      1542216 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:      2072104 kB
LowFree:         16296 kB
SwapTotal:     2932720 kB
SwapFree:      2932448 kB
Dirty:          209424 kB
Writeback:           0 kB
Mapped:          23232 kB
Slab:            52056 kB
CommitLimit:   3968768 kB
Committed_AS:   111616 kB
PageTables:        928 kB
VmallocTotal:  4194304 kB
VmallocUsed:       816 kB
VmallocChunk:  4193464 kB
HugePages_Total:     0
HugePages_Free:      0
Hugepagesize:     4096 kB
```

top command:

```
Cpu(s): 50.6% us,  3.3% sy, 43.3% ni,  0.5% id,  2.3% wa,  0.0% hi,  0.0% si
Mem:   2072104k total,  2052232k used,    19872k free,    18512k buffers
Swap:  2932720k total,      272k used,  2932448k free,  1942872k cached
```

---

### Post by padre999 on 2006-12-04
It's not a problem, it's good.

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Overview_of_memory_management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Overview_of_memory_management)

---

### Post by cwinslett on 2006-12-04
It still makes me feel dirty to see 

```
Mem:   2072104k total,  2052232k used,    19872k free
```

---

### Post by padre999 on 2006-12-04
I can understand you feel a bit miserable after spending so much money on 2GB of memory and then it tells you "20MB free"...

But I think you understood that the cached memory is basically "free" memory. You can also use Gkrellm to give you a better idea of the free memory available.

---

### Post by cwinslett on 2006-12-04
O, I didn't spend jack.

It's a vestige box from an accounting app.

---

### Post by CGW on 2006-12-08
I recently discovered this also.  I freaked out after seeing the ProcessTable.  After a little research I found that this wasn't a 'bad' thing.  Also, using a gDesklets memory desklet correctly shows the memory in use.  That helps to ease my obsessive compulsive disorder a bit.

---

### Post by ryanclemson on 2007-12-06
I came across this post today and I wanted to add to the discussion in case anyone else comes across this topic.

Ubuntu may be using 2GB of RAM, but not in the same way we traditionally think of Windows using RAM. 

First, use the ```
free
``` command to view memory usage on your system.

```
             total       used       free     shared    buffers     cached
Mem:       2075512    1699612     375900          0     142232    1178848
-/+ buffers/cache:     378532    1696980
Swap:      6080560          0    6080560
```

The important numbers here are the first number after -+ buffers/cache (378532) which indicates that Ubuntu is consuming about 378MB of RAM for programs. The second most important number here is the amount of used swap (in my case is 0), which indicates the system isn't using the disk for slower swap-space. 

Where is the rest of the memory you ask? Ubuntu uses the majority of it as buffers or cached files to improve the performance on my system. So don't worry that only 375MB is free.:) If your interested about more information there is a great post here:

[http://www.ibm.com/developerworks/linux/library/l-linux-memory.html]("http://www.ibm.com/developerworks/linux/library/l-linux-memory.html")

---

### Post by takowl on 2008-02-07
I have run across the same thing, and got similarly concerned before finding out about the caching thing.

I would suggest that 'common user' tools such as KDE System Guard should report a value of "free memory" that includes the cached memory, as opposed to the current strategy of reporting only truly free memory. This is perhaps less technically truthful, but:
[LIST]
[*]It is confusing and concerning for average users to see these very small 'free memory' numbers even with little running.
[*]It's not (in normal operation) very helpful to report a value that the system is attempting to keep roughly constant.
[*]For practical purposes, memory used for caching is 'free' since, AFAIU, it is rapidly reallocated when programs need it.
[*]Expert users who might be interested in the amount of really free memory are more likely to understand the difference, and be able to find it via e.g. command line tools.
[/LIST]

---

