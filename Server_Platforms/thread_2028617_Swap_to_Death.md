---
title: "Swap to Death"
date: 2012-07-18
forum: Server Platforms
---

### Post by visualblind on 2012-07-18
Gradually, after 2-3 days, the swap usage increases incrementally until the system swaps itself into an unresponsive state, I experience a high % of cpu wait time, then I have to reboot. This is happening to me on every Ubuntu Server I have, which is two **Ubuntu Server x64 virtual machines** (one running 11.04, other is 12.04). The Ubuntu taste in my mouth is not great. One running internally on an ESX 3.5 host (Dell PowerEdge 2950 dual quadcore Xeon procs 32GB memory), the other running in Amazon EC2. I run CentOS x64 on my ESX hosts and EC2 without a single problem whatsoever.

cat /proc/version
Linux version 3.2.0-25-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012

cat /etc/debian_version
wheezy/sid

uptime
 13:49:30 up 19 days, 20:14,  1 user,  load average: 0.33, 0.44, 0.40

free -m
             total       **used**       free     shared    buffers     cached
Mem:           491        465         26          0         93        202
-/+ buffers/cache:        169        322
**Swap**:         1715         **14**       1701

Tomorrow I am expecting 15-16MB used, then when it hits a critical ammount, I will need to reboot. Reboot Linux? What?? This "inconvenience" has caused me to increase the Ubuntu Server EC2 instance to a m1.large instance size with 7GB memory just so it does not use swap. This costs us $$ to run the larger size. The only things running on the systems is Nagios, Apache, Mysql, Postfix. I've tested turning all of these services off, but it does not help. From my experience with Ubuntu Server, while virtualized it is a horrible operating system to rely on. If anyone can point me in the right direction or provide some assistance, I would greatly appreciate it. Please don't recommend that I sudo sh -c "sync && echo 3 > /proc/sys/vm/drop_caches" or set vm.swappinness to 1, that doesn't provide a permanent solution.

Thank you,
Travis Runyard

---

### Post by LHammonds on 2012-07-18
> **visualblind said:**
> 
cat /etc/debian_version
wheezy/sid

wheezy/sid? Isn't that a development / unstable build?
 
I have used Ubuntu Server 10.04 LTS and 12.04 LTS under VMware's ESXi 4.1 and my servers are VERY stable and rarely touch swap at all, even with only 1 or 2 GB RAM (I also have a Nagios server).  I don't use Amazon hosts, we have IBM Blade servers hosted internally and I use the 7078 AC1 blades.
 
LHammonds

---

### Post by visualblind on 2012-07-18
Thanks for the reply. Apparently Wheezy is a Debian build classified under testing, not unstable. I suppose that happened when I upgraded Ubuntu 11.04 to 12.04 following the instructions on Ubuntu's website. The problem happened prior to the upgrade also, I upgraded to try to rectify the problem. The swap problem is also happening on my other system running Ubuntu 11.04 (Debian Squeeze). Not sure if physical host is relevant but it's Dell PowerEdge 2950 dual quadcore Xeon procs 32GB memory. 

Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-25-generic x86_64)

PS output:

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.3  24320  1664 ?        Ss   Jun28   3:47 /sbin/init
root         2  0.0  0.0      0     0 ?        S    Jun28   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Jun28   2:45 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    Jun28   1:40 [kworker/u:0]
root         6  0.0  0.0      0     0 ?        S    Jun28   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    Jun28   2:00 [watchdog/0]
root         8  0.0  0.0      0     0 ?        S<   Jun28   0:00 [cpuset]
root         9  0.0  0.0      0     0 ?        S<   Jun28   0:00 [khelper]
root        10  0.0  0.0      0     0 ?        S    Jun28   0:00 [kdevtmpfs]
root        11  0.0  0.0      0     0 ?        S<   Jun28   0:00 [netns]
root        12  0.0  0.0      0     0 ?        S    Jun28   0:12 [sync_supers]
root        13  0.0  0.0      0     0 ?        S    Jun28   0:00 [bdi-default]
root        14  0.0  0.0      0     0 ?        S<   Jun28   0:00 [kintegrityd]
root        15  0.0  0.0      0     0 ?        S<   Jun28   0:00 [kblockd]
root        16  0.0  0.0      0     0 ?        S<   Jun28   0:00 [ata_sff]
root        17  0.0  0.0      0     0 ?        S    Jun28   0:00 [khubd]
root        18  0.0  0.0      0     0 ?        S<   Jun28   0:00 [md]
root        20  0.0  0.0      0     0 ?        S    Jun28   0:00 [khungtaskd]
root        21  0.0  0.0      0     0 ?        S    Jun28   0:24 [kswapd0]
root        22  0.0  0.0      0     0 ?        SN   Jun28   0:00 [ksmd]
root        23  0.0  0.0      0     0 ?        S    Jun28   0:00 [fsnotify_mark]
root        24  0.0  0.0      0     0 ?        S    Jun28   0:00 [ecryptfs-kthre]
root        25  0.0  0.0      0     0 ?        S<   Jun28   0:00 [crypto]
root        33  0.0  0.0      0     0 ?        S<   Jun28   0:00 [kthrotld]
root        35  0.0  0.0      0     0 ?        S    Jun28   2:28 [scsi_eh_0]
root        36  0.0  0.0      0     0 ?        S    Jun28   0:00 [scsi_eh_1]
root        37  0.0  0.0      0     0 ?        S    Jun28   0:00 [kworker/u:2]
root        58  0.0  0.0      0     0 ?        S<   Jun28   0:00 [devfreq_wq]
root       159  0.0  0.0      0     0 ?        S<   Jun28   0:00 [mpt_poll_0]
root       160  0.0  0.0      0     0 ?        S<   Jun28   0:00 [mpt/0]
root       163  0.0  0.0      0     0 ?        S    Jun28   0:00 [scsi_eh_2]
root       176  0.0  0.0      0     0 ?        S<   Jun28   0:00 [kdmflush]
root       184  0.0  0.0      0     0 ?        S<   Jun28   0:00 [kdmflush]
root       238  0.0  0.0      0     0 ?        S    Jun28  18:40 [jbd2/dm-0-8]
root       239  0.0  0.0      0     0 ?        S<   Jun28   0:00 [ext4-dio-unwri]
root       328  0.0  0.0  17224   384 ?        S    Jun28   0:00 upstart-udev-bri
root       330  0.0  0.1  21576   984 ?        Ss   Jun28   0:00 /sbin/udevd --da
root       444  0.0  0.0      0     0 ?        S<   Jun28   0:00 [kpsmoused]
root       591  0.0  0.2  49948  1168 ?        Ss   Jun28   0:05 /usr/sbin/sshd -
root       597  0.0  0.0  15180   192 ?        S    Jun28   0:00 upstart-socket-b
syslog     626  0.0  0.8 249852  4168 ?        Sl   Jun28   1:23 rsyslogd -c5
104        627  0.0  0.1  23940   576 ?        Ss   Jun28   0:00 dbus-daemon --sy
root       633  0.0  0.0  23344   444 ?        Ss   Jun28   0:00 /usr/sbin/vsftpd
root       702  0.0  0.1  15788   680 tty4     Ss+  Jun28   0:00 /sbin/getty -8 3
root       706  0.0  0.1  15788   672 tty5     Ss+  Jun28   0:00 /sbin/getty -8 3
root       714  0.0  0.1  15788   672 tty2     Ss+  Jun28   0:00 /sbin/getty -8 3
root       716  0.0  0.1  15788   676 tty3     Ss+  Jun28   0:00 /sbin/getty -8 3
root       722  0.0  0.1  15788   688 tty6     Ss+  Jun28   0:00 /sbin/getty -8 3
daemon     731  0.0  0.0  16900   216 ?        Ss   Jun28   0:00 atd
root       735  0.0  0.1  19104   840 ?        Ss   Jun28   0:14 cron
root       746  0.7  0.0      0     0 ?        S    Jun28 214:29 [flush-252:0]
mysql      753  0.0  5.4 623732 27528 ?        Ssl  Jun28  16:28 /usr/sbin/mysqld
root       775  0.0  1.8 233456  9300 ?        Ss   Jun28   4:04 /usr/sbin/apache
www-data   930  0.0  2.0 235548 10376 ?        S    14:58   0:00 /usr/sbin/apache
root      1065  0.2  0.1  17500   984 ?        Ss   Jun28  61:01 /usr/sbin/vmware
root      1096  0.0  1.2  57044  6188 ?        Ss   Jun28   0:39 /usr/bin/perl /o
root      1203  0.0  0.2  25096  1116 ?        Ss   Jun28   0:24 /usr/lib/postfix
postfix   1212  0.0  0.2  27324  1208 ?        S    Jun28   0:13 qmgr -l -t fifo
root      3059  0.0  0.7  95540  3980 ?        Ss   15:03   0:00 sshd: trunyard [
trunyard  3107  0.0  0.3  95540  1952 ?        S    15:03   0:00 sshd: trunyard@p
trunyard  3108  0.0  1.5  26648  7956 pts/0    Ss   15:03   0:00 -bash
root      5067  0.1  0.0      0     0 ?        S    15:08   0:00 [kworker/0:2]
root      5408  0.0  0.1  15788   824 tty1     Ss+  Jun28   0:00 /sbin/getty -8 3
postfix   7298  0.0  0.3  27264  1776 ?        S    15:15   0:00 cleanup -z -t un
postfix   7299  0.0  0.3  27172  1548 ?        S    15:15   0:00 trivial-rewrite
postfix   7300  0.0  0.4  27400  2316 ?        S    15:15   0:00 local -t unix
nagios    7899  0.0  0.2  99244  1120 ?        S    15:16   0:00 /usr/local/nagio
nagios    7901  0.0  0.1   4396   616 ?        S    15:16   0:00 sh -c /usr/local
nagios    7902  0.0  0.2  99244  1120 ?        S    15:16   0:00 /usr/local/nagio
nagios    7903  0.0  0.1  15744   812 ?        S    15:16   0:00 /usr/local/nagio
nagios    7904  0.0  0.1   4396   612 ?        S    15:16   0:00 sh -c /usr/local
trunyard  7905  0.0  0.2  18164  1264 pts/0    R+   15:16   0:00 ps aux
www-data 17130  0.0  2.5 238728 13048 ?        S    Jul15   0:01 /usr/sbin/apache
www-data 17133  0.0  2.5 238736 13052 ?        S    Jul15   0:01 /usr/sbin/apache
www-data 21045  0.0  2.1 235564 10576 ?        S    02:23   0:00 /usr/sbin/apache
www-data 21583  0.0  2.1 235564 10576 ?        S    02:24   0:00 /usr/sbin/apache
www-data 21676  0.0  2.1 235564 10576 ?        S    02:24   0:00 /usr/sbin/apache
www-data 22295  0.0  2.0 235548 10328 ?        S    02:26   0:00 /usr/sbin/apache
root     22404  0.1  0.0      0     0 ?        S    14:27   0:03 [kworker/0:1]
www-data 24834  0.0  2.5 238736 13084 ?        S    Jul16   0:00 /usr/sbin/apache
root     25036  0.0  0.0      0     0 ?        S<   Jun29   0:00 [xfs_mru_cache]
root     25037  0.0  0.0      0     0 ?        S<   Jun29   0:00 [xfslogd]
root     25038  0.0  0.0      0     0 ?        S<   Jun29   0:00 [xfsdatad]
root     25039  0.0  0.0      0     0 ?        S<   Jun29   0:00 [xfsconvertd]
root     25042  0.0  0.0      0     0 ?        S    Jun29   0:00 [jfsIO]
root     25043  0.0  0.0      0     0 ?        S    Jun29   0:00 [jfsCommit]
root     25044  0.0  0.0      0     0 ?        S    Jun29   0:00 [jfsSync]
www-data 25996  0.0  2.5 238720 12896 ?        S    Jul16   0:00 /usr/sbin/apache
postfix  27491  0.0  0.3  27160  1640 ?        S    14:41   0:00 pickup -l -t fif
postfix  29685  0.0  0.5  38112  2692 ?        S    Jul04   0:01 tlsmgr -l -t uni
www-data 30550  0.0  2.6 238720 13164 ?        S    Jul17   0:00 /usr/sbin/apache
nagios   30919  0.4  0.4  99240  2164 ?        Ssl  Jul17   6:19 /usr/local/nagio
root     31598  0.0  0.0      0     0 ?        S    14:53   0:01 [kworker/0:0]

Now I'm up to almost 15MB of swap used, since I've created this thread
Tasks:  89 total,   1 running,  88 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.2%us,  3.5%sy,  0.0%ni, 93.9%id,  0.1%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:    503416k total,   463760k used,    39656k free,   102104k buffers
Swap:  1757180k total,    **15200k used**,  1741980k free,   187536k cached

---

### Post by LHammonds on 2012-07-18
I just happen to have some Dell 2950 servers sitting around (no longer used since we virtualized everything).
 
I am currently out-of-state in training so I can't fire them up and try out an install of 12.04 though. I am interested in how Ubuntu would run now that you mentioned it but I doubt I will have time to try it out for a while since we are in the middle of migrating our core application servers to different applicaitons (new EMR system...yippie /snark)
 
**EDIT:** If you have some downtime available, you might want to perform a full (and verified) backup of your server and then wipe it out, install a fresh copy of 12.04 to see if the swap issue goes away. If so, then lay down your application and see if the swap issue does not come back. However, it is risky and requires downtime...part of the reason I don't like physical server installs. :)  I'm also worthless for troubleshooting since I'm a noob.
 
Another option would be to install 12.04 into a virtual and see if you can get your application setup and configured on it and keep an eye on swap usage just to make sure it is not the OS or application. Maybe it has something to do with the hardware (correcting for errors, etc.)
 
LHammonds

---

### Post by Lyfang on 2012-07-18
Please post the following output:
```
cat /proc/meminfo
```

See also: [swapoff / swapon not running in a script]("http://ubuntuforums.org/showthread.php?t=1766875") & [install a cache flusher]("http://ubuntuforums.org/showthread.php?t=1769521")

---

### Post by visualblind on 2012-07-18
Lyfang,
MemTotal:         503416 kB
MemFree:           33360 kB
Buffers:          106016 kB
Cached:           189788 kB
SwapCached:         4648 kB
Active:           154728 kB
Inactive:         230624 kB
Active(anon):      11328 kB
Inactive(anon):    78324 kB
Active(file):     143400 kB
Inactive(file):   152300 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       1757180 kB
SwapFree:        1741980 kB
Dirty:               868 kB
Writeback:             0 kB
AnonPages:         85028 kB
Mapped:            11904 kB
Shmem:               104 kB
Slab:              60220 kB
SReclaimable:      49140 kB
SUnreclaim:        11080 kB
KernelStack:         840 kB
PageTables:         5832 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2008888 kB
Committed_AS:     590048 kB
VmallocTotal:   34359738367 kB
VmallocUsed:        6940 kB
VmallocChunk:   34359728680 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      333824 kB
DirectMap2M:      190464 kB

LHammonds,
Sorry for the confusion. They are all virtualized, one is a vm guest on ESX and the other is in Amazon EC2. Thank you for the suggestions, that is what I will probably have to do unless we can solve the issue. One of the Ubuntu systems is a production web server with a lot of configuration so I'd rather not rebuild it if possible. So far, nobody has been able to figure out the problem. I thought it was a Ubuntu bug at first, but I seem to be the only one with a problem. However, it's not isolated to one system or version or even location (one internal on ESX, other in EC2).

---

### Post by spynappels on 2012-07-19
I presume they are both running the same (or very similar) software stacks?

It sounds like the interaction of your different installed services is creating memory conflicts. What could be happening is that processes are not releasing memory quickly enough, for other processes needs, and this is forcing these processes to swap. The end result is similar to a memory leak in that swap fills, but often memory usage appears normal.

You could try using sar -S to track the state of swap usage. You can then track back to see which process is allocating swap, and perhaps a workaround would be to write a reap script which restarts the process when it goes above a certain size.

---

### Post by QuaxEros on 2013-03-19
Hi guys,

Found your thread because i'm experiencing similar problems. Post just to let yo know that you're not the only one!
I'm on a laptop running 12.04.2-LTS. My high I/O latency criples my system regularly and all i can do then is reboot. The iowait% skyrockets as a result of kswapd0 kicking in at nearly 100% and staying there for ~30s every few minutes or on user interaction. I used "latencytop" and "iotop" (apt-get install ... :) ) to analyze the cause of sluggishness.
Now, all this is hardly happening just after boot. [kswapd0] is always greedy (>90%, ...normal?) but only takes ~4-8s to finish. It seems that as soon as i have a process that crashes (i don't know how UbuntuServer handles this. Automatic or manual with notification?) the swap-daemon gets confused and starts working overtime. 
Maybe "apport" provokes the problem. I will do some more research and then file a bug report.
Posted to share my findings with people that found this thread trying to solve their problem.

Kind regards to y'all !

---

