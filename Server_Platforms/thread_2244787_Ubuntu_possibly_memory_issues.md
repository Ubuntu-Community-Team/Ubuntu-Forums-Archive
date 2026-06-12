---
title: "Ubuntu possibly memory issues?"
date: 2014-09-18
forum: Server Platforms
---

### Post by Marc-NJ on 2014-09-18
I have an Ubuntu server with 8 GB of RAM in it (it was previously a Win desktop that I turned into an Ubuntu Server).  Previously, there hadn't been any memory issues, but lately it seems like I'm using almost all of my available memory on the machine.  I'm not that experienced with how Ubuntu truly works, but I have a remote access program installed on the server (ScreenConnect) which shows that my memory is being almost all used, and the developers of this software have confirmed this information is accurate.

The only thing I can think of is VirtualBox that I'm running on the Ubuntu Server (and keeping a Win7 VM running at all times), but I configured it to only use 2 GB of RAM.  I don't even know if that could be the cause of this issue or not (or even if such an issue exists, since the server seems to run fine in fact), but was hoping someone on here might be able to lend a quick hand.  

Thanks!

---

### Post by Doug S on 2014-09-18
My suggestion is to use free to observe the big picture. Example:```
doug@s15:~/docs-1410$ [COLOR=#ff0000]free -m[/COLOR]
             total       used       free     shared    buffers     cached
Mem:         15627       6918       8708          7        646       3001
-/+ buffers/cache:       3270      12356
Swap:         8099          0       8099
```And top to observe details. Example (after depressing the "<" key 4 times so as to sort by virtual memory usage):```
top - 14:53:26 up 1 day, 14:42,  2 users,  load average: 0.00, 0.01, 0.09
Tasks: 167 total,   1 running, 166 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  16002500 total,  7074640 used,  8927860 free,   662380 buffers
KiB Swap:  8294396 total,        0 used,  8294396 free.  3073076 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 4393 libvirt+  20   0 12.465g 2.762g   9432 S   0.3 18.1 386:06.29 qemu-system-x86
 2115 root      20   0  765772  12860   8580 S   0.0  0.1   0:00.19 libvirtd
 1708 mysql     20   0  550072  56280   6964 S   0.0  0.4   1:01.23 mysqld
 1932 whoopsie  20   0  335684   3620   2456 S   0.0  0.0   0:00.00 whoopsie
 2914 www-data  20   0  326344   6496    428 S   0.0  0.0   0:00.24 apache2
 2915 www-data  20   0  326344   6496    428 S   0.0  0.0   0:00.00 apache2
 2916 www-data  20   0  326344   6496    428 S   0.0  0.0   0:00.00 apache2
 2918 www-data  20   0  326344   6496    428 S   0.0  0.0   0:00.00 apache2
 2919 www-data  20   0  326344   6496    428 S   0.0  0.0   0:00.00 apache2
 2797 root      20   0  326320  16896  10836 S   0.0  0.1   0:03.01 apache2
 1452 root      20   0  318508  39172   1176 S   0.0  0.2   0:10.47 zfs-fuse
 6037 root      20   0  277228   7856   5232 S   0.0  0.0   0:01.58 smbd
  919 root      20   0  274120   8040   6144 S   0.0  0.1   0:02.26 smbd
 1064 root      20   0  274120   3240   1344 S   0.0  0.0   0:00.24 smbd
 4253 doug      20   0  272252   3252   1180 S   0.0  0.0   0:01.00 sshd
 4154 root      20   0  272108   8224   6140 S   0.0  0.1   0:00.23 sshd
  963 syslog    20   0  255844   1824   1036 S   0.0  0.0   0:00.09 rsyslogd
 2954 root      20   0  251160   6160   4500 S   0.0  0.0   0:00.01 login
 1063 root      20   0  239472   4204   2600 S   0.0  0.0   0:00.13 winbindd
  920 root      20   0  235140   6028   4472 S   0.0  0.0   0:00.10 winbindd
 1062 root      20   0  235140   3732   2156 S   0.0  0.0   0:00.12 winbindd
 1049 root      20   0  234420   3936   2364 S   0.0  0.0   0:00.26 winbindd
  987 root      20   0  195616   3528   2192 S   0.0  0.0   0:01.12 nmbd
 1659 root      20   0   61364   3060   2384 S   0.0  0.0   0:00.00 sshd
  504 root      20   0   51436   1736   1004 S   0.0  0.0   0:00.03 systemd-udevd
  981 root      20   0   43452   1916   1540 S   0.0  0.0   0:00.01 systemd-logind
  965 message+  20   0   39236   1372    984 S   0.0  0.0   0:00.05 dbus-daemon
    1 root      20   0   33912   3296   1488 S   0.0  0.0   0:02.77 init
 1936 lxc-dns+  20   0   28208    952    700 S   0.0  0.0   0:00.00 dnsmasq
 2868 libvirt+  20   0   28208    976    724 S   0.0  0.0   0:00.00 dnsmasq
 2155 postfix   20   0   27460   1608   1324 S   0.0  0.0   0:00.08 qmgr
 9541 postfix   20   0   27408   1580   1300 S   0.0  0.0   0:00.00 pickup
 2137 root      20   0   25344   1688   1376 S   0.0  0.0   0:00.44 master
 9624 doug      20   0   24960   1720   1156 R   0.0  0.0   0:00.12 top
 3019 doug      20   0   24128   5292   1740 S   0.0  0.0   0:00.07 bash
 4254 doug      20   0   24096   5284   1756 S   0.0  0.0   0:00.23 bash
  384 root      20   0   23664   1432   1188 S   0.0  0.0   0:00.02 cgmanager
 1682 root      20   0   23656   1044    792 S   0.0  0.0   0:00.12 cron
  495 root...
```You can see I have a virtual machine using a lot of memory at the moment (which I gave it). 
Post your results back here and maybe readers can comment further.

---

### Post by ajgreeny on 2014-09-18
It also sounds as if you are not aware of how Linux manages memory, which is very different to the way that Windows does the same job.

Linux often appears to be using a lot more memory than Windows but that is because empty memory is deemed to be wasted memory, and the system keeps data in cache (memory) and only frees it when it is needed by a more recently opened application.

In Doug S's example you will see the figure 6918 for used memory in the Mem: line of output, but below that is the third line +/- buffers/cache where the used figure is 3270, less than half the first figure.  This shows the difference between the amount that contains data (6918) that is cached but may still be available if needed, and the true amount that is used and not available because it is still in use by open applications.

---

### Post by Doug S on 2014-09-18
Here is another example, after I copied a 10 gigabyte file:```
doug@s15:~/c$ [COLOR=#ff0000]free -m[/COLOR]
             total       used       free     shared    buffers     cached
Mem:         15627      15464        [COLOR=#ff0000]162[/COLOR]          7        449      14218
-/+ buffers/cache:        796      [COLOR=#ff0000]14830[/COLOR]
Swap:         8099          0       8099
```As ajgreeny pointed out, at first I might be alarmed by the only 162 megabytes free number, but that is mostly still the cached big file and I really have 14.8 Gigabytes free.

---

### Post by Marc-NJ on 2014-09-21
Thanks so much for the responses everyone!

So, first, let me post all the information regarding memory from my Ubuntu server:

```

root@Eagle:~# free -m             total       used       free     shared    buffers     cached
Mem:          7893       7672        220          0        459       3015
-/+ buffers/cache:       4197       3695
Swap:        14307         38      14269

```

```

top - 14:25:33 up 11 days, 16:55,  1 user,  load average: 0.18, 0.37, 0.22
Tasks: 129 total,   2 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.0%us,  0.4%sy,  0.0%ni, 98.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8082548k total,  7858896k used,   223652k free,   470692k buffers
Swap: 14651388k total,    38924k used, 14612464k free,  3087852k cached


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1607 root      20   0 4223m 351m 5776 S    0  4.4  41:00.83 java
20710 vbox      20   0 3509m 2.1g 2.0g S    2 27.4   1075:10 VBoxHeadless
20617 root      20   0 3502m  69m 5968 S    0  0.9   6:49.36 java
 9354 root      39  19 3335m 607m 6284 S    0  7.7 415:19.84 java
15569 root      20   0 2258m 192m  17m S    0  2.4   2:48.64 mono
12329 root      20   0 2042m 3188 2144 S    0  0.0   0:00.03 console-kit-dae
 1249 mysql     20   0 1699m  69m 4460 S    0  0.9   5:36.66 mysqld
 5242 tomcat6   20   0 1650m  82m 2396 S    0  1.0   8:23.17 java
 1705 vbox      20   0  945m  13m 6448 S    0  0.2   0:26.12 vboxwebsrv
 1745 vbox      20   0  645m 6708 2908 S    0  0.1   9:49.25 VBoxSVC
  854 colord    20   0  439m 2624 2124 S    0  0.0   0:00.18 colord
17043 www-data  20   0  320m  32m 4956 S    0  0.4   0:05.03 apache2
10740 www-data  20   0  320m  32m 5172 S    0  0.4   0:24.88 apache2
10741 www-data  20   0  320m  32m 5196 S    0  0.4   0:25.78 apache2
14627 www-data  20   0  320m  31m 5120 S    0  0.4   0:11.04 apache2
16822 www-data  20   0  319m  31m 5004 S    0  0.4   0:06.56 apache2
16447 www-data  20   0  319m  31m 5072 S    0  0.4   0:06.64 apache2

```

On Webmin, here's what it displays:

[TABLE="width: 100%"]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**Real memory**[/TD]
[TD="class: ui_form_value"]4.09 GB used, 7.71 GB total[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**Virtual memory**[/TD]
[TD="class: ui_form_value"]38.01 MB used, 13.97 GB total[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**Local disk space**[/TD]
[TD="class: ui_form_value"]209.98 GB used, 1019.81 GB total[/TD]
[/TR]
[/TABLE]


And on my ScreenConnect hosts page:

Available Memory:249 MB / 7893 MB



Obviously, that 249 MB available out of 7893 MB total worried me, but given the other information and from what I can understand from everyone's posts, I shouldn't be worried about this at all and nothing is using up all my memory, right?

Thanks again!

---

### Post by Marc-NJ on 2014-10-10
Can anyone confirm?  Thanks so much!

---

### Post by Doug S on 2014-10-11
> **Marc_Bressman said:**
> Obviously, that 249 MB available out of 7893 MB total worried me, but given the other information and from what I can understand from everyone's posts, I shouldn't be worried about this at all and nothing is using up all my memory, right?Right.

For educational purposes, try flushing things, like this:```
doug@s15:~/sguide-1404/classroom/build/help$ [COLOR=#ff0000]cat ~/c/flush_memory[/COLOR]
#! /bin/bash
free
sync
echo 3 > /proc/sys/vm/drop_caches
free
doug@s15:~/sguide-1404/classroom/build/help$ [COLOR=#ff0000]sudo ~/c/flush_memory[/COLOR]
             total       used       free     shared    buffers     cached
Mem:      16002488    [COLOR=#ff0000]5608404[/COLOR]   10394084       8096     137412    3115156
-/+ buffers/cache:    2355836   13646652
Swap:      8294396          0    8294396
             total       used       free     shared    buffers     cached
Mem:      16002488    [COLOR=#ff0000]2150584[/COLOR]   13851904       8096        992      45848
-/+ buffers/cache:    2103744   13898744
Swap:      8294396          0    8294396
```

---

### Post by Marc-NJ on 2014-10-11
> **Doug S said:**
> Right.

For educational purposes, try flushing things, like this:```
doug@s15:~/sguide-1404/classroom/build/help$ [COLOR=#ff0000]cat ~/c/flush_memory[/COLOR]
#! /bin/bash
free
sync
echo 3 > /proc/sys/vm/drop_caches
free
doug@s15:~/sguide-1404/classroom/build/help$ [COLOR=#ff0000]sudo ~/c/flush_memory[/COLOR]
             total       used       free     shared    buffers     cached
Mem:      16002488    [COLOR=#ff0000]5608404[/COLOR]   10394084       8096     137412    3115156
-/+ buffers/cache:    2355836   13646652
Swap:      8294396          0    8294396
             total       used       free     shared    buffers     cached
Mem:      16002488    [COLOR=#ff0000]2150584[/COLOR]   13851904       8096        992      45848
-/+ buffers/cache:    2103744   13898744
Swap:      8294396          0    8294396
```

First off, thanks for the confirmation.  Glad I don't have anything to worry about! :)

Also - not sure exactly what those flush commands do and what it would demonstrate - could you elaborate?  Thanks!

---

### Post by Doug S on 2014-10-11
> **Marc_Bressman said:**
> Also - not sure exactly what those flush commands do and what it would demonstrate - could you elaborate?  Thanks!They truly free up any and all memory that isn't really in use. Maybe this example is better:```
doug@s15:~/c$ [COLOR=#ff0000]sudo ./flush_memory[/COLOR]
             total       used       free     shared    buffers     cached
Mem:      16002488   [COLOR=#ff0000]15841060     161428[/COLOR]       6900       3844   15272664
-/+ buffers/cache:     564552   15437936
Swap:      8294396       4660    8289736
             total       used       free     shared    buffers     cached
Mem:      16002488     [COLOR=#ff0000]378964   15623524[/COLOR]       6904        548      40396
-/+ buffers/cache:     338020   15664468
Swap:      8294396       4660    8289736
```Under normal circumstances, it wouldn't make any sense to do this. I do it for specific testing, where, and for example, I need to be certain that there is no memory cache of a previously copied file.

---

