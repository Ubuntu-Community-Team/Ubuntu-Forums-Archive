---
title: "Kernel 6.10 RC (Release Candidate) series"
date: 2024-05-26
forum: Ubuntu Development Version
---

### Post by Doug S on 2024-05-26
[Kernel 6.10 RC 1]("https://kernel.ubuntu.com/mainline/v6.10-rc1/") is available, so starting this thread. I am just installing and also compiling it now.

EDIT: Getting a lot of warnings during compile on a 20.04 server. Will try on a 24.04 server later.

EDIT 2: Compiling using a 24.04 server works better. This is new:

```
fs/bcachefs/btree_update.o: warning: objtool: bch2_trans_update_get_key_cache() falls through to next function flush_new_cached_update()
fs/bcachefs/btree_update.o: warning: objtool: flush_new_cached_update() falls through to next function bch2_trans_update_by_path()
```

But I looked at the code and it seems okay, but I didn't spend much time on it.

---

### Post by Doug S on 2024-07-01
I have been stuck on 6.10-rc2 for several weeks, due to some ongoing testing.
Hmmm... there wasn't any Ubuntu mainline 6.10-rc5 and now [6.10-rc6]("https://kernel.ubuntu.com/mainline/v6.10-rc6/") for amd64 is missing. Even the log file is missing.

---

### Post by Doug S on 2024-07-08
Kernel 6.10-rc7 has been released, but the [Ubuntu mainline stuff]("https://kernel.ubuntu.com/mainline/v6.10-rc7/") continues to be a mess.

```
doug@s19:~$ uname -a
Linux s19 6.10.0-rc7-stock #1269 SMP PREEMPT_DYNAMIC Sun Jul  7 17:20:36 PDT 2024 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by IanW on 2024-07-15
6.10 has been pushed out of the door by Linus without the need for an rc8.
Hope either Mainline gets fixed or Canonical adopt it _very_ soon.

[https://www.phoronix.com/news/Linux-6.10-Released](https://www.phoronix.com/news/Linux-6.10-Released)

---

### Post by IanW on 2024-07-23
Looks like [Sunday's daily build]("https://kernel.ubuntu.com/mainline/daily/2024-07-22/") for 6.10.0 on mainline succeeded for AMD64.

---

### Post by 3vi1 on 2024-07-26
Speaking of 6.10, has anyone noticed problems with memory usage from disk swap?  I've been using 6.10rc4 mainline since it came out, and if I try to rsync or copy large backups then the system will become unresponsive.  Kswapd0 starts eating all the CPU, and I have to echo 1 > /proc/sys/vm/drop_caches in order to cause it to return to normal.  I have 128GB or RAM, no defined swap, and memory utilization shows that my real memory usage is below 32GB. This was working fine in 6.9 versions, so I was waiting for the next successful mainline build before I make a serious attempt to test backleveling, gather data, and report upstream.

---

### Post by #&amp;thj^% on 2024-07-26
I've been on the release for two days now and I'm using zfs a big memory hog:
```
free -t
               total        used        free      shared  buff/cache   available
Mem:        14158756    10045056     3280200       35320     1138636     4113700
Swap:        4194300         512     4193788
Total:      18353056    10045568     7473988
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> uname -r
6.10.0-15-generic

```
```
apt list --installed | grep -e linux-image -e linux-headers -e linux-modules

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-headers-6.10.0-15-generic/oracular-proposed,now 6.10.0-15.15 amd64 [installed]
linux-headers-6.10.0-15/oracular-proposed,now 6.10.0-15.15 all [installed,automatic]
linux-headers-6.8.0-31-generic/oracular,now 6.8.0-31.31 amd64 [installed,automatic]
linux-headers-6.8.0-31/oracular,now 6.8.0-31.31 all [installed,automatic]
linux-headers-generic/oracular,now 6.8.0-31.31 amd64 [installed,automatic]
linux-image-6.8.0-31-generic/oracular,now 6.8.0-31.31 amd64 [installed,automatic]
linux-image-generic/oracular,now 6.8.0-31.31 amd64 [installed,automatic]
linux-image-unsigned-6.10.0-15-generic/oracular-proposed,now 6.10.0-15.15 amd64 [installed]
linux-modules-6.10.0-15-generic/oracular-proposed,now 6.10.0-15.15 amd64 [installed]
linux-modules-6.8.0-31-generic/oracular,now 6.8.0-31.31 amd64 [installed,automatic]
linux-modules-extra-6.10.0-15-generic/oracular-proposed,now 6.10.0-15.15 amd64 [installed]
linux-modules-extra-6.8.0-31-generic/oracular,now 6.8.0-31.31 amd64 [installed,automatic]

```
Nothing like what your seeing though
This is just now rsync /home to /dozer
```
free -t
               total        used        free      shared  buff/cache   available
Mem:        14158756    11567188     1747464       46544     1186872     2591568
Swap:        4194300         512     4193788
Total:      18353056    11567700     5941252

```
```
 cd /dozer && ls
balenaEtcher-1.18.11-x64.AppImage  ExtremeCooling4Linux-v0.3-x86_64.AppImage  Pictures
balenaEtcher-1.9.0-x64.AppImage    fpinstalled.txt                            Public
cachyos-repo                       installed.txt                              surfshark-install.sh
dead.letter                        me                                         temp.file
Desktop                            Music                                      Templates
Documents                          nohup.out                                  Videos
Downloads                          nvidia-bug-report.log.gz                   zc-master
Dropbox                            os

```
```
swapon --show
NAME      TYPE      SIZE USED PRIO
/dev/sda3 partition   4G 512K   -2

```

---

### Post by 3vi1 on 2024-07-26
Thanks for the comparative data.  Is your home directory bigger than your RAM?  I'm rsyncing lots of VMs in my process, several terabytes of data.

Once my buff/cache reaches the unused size of my RAM:
```
(base) 18:12:19 evil@H510 ~» free -t
               total        used        free      shared  buff/cache   available
Mem:       131847292    27336272     3691844     2048028   111778340   104511020
Swap:              0           0           0
Total:     131847292    27336272     3691844

```

Rather than simply drop some of the used buff/cache mem, kswapd0 goes nuts for CPU:
```

top - 18:14:47 up 3 days,  1:36,  6 users,  load average: 5.69, 4.23, 3.90
Tasks: 782 total,   2 running, 780 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.0 us, 11.7 sy,  0.0 ni, 75.8 id, 10.5 wa,  0.0 hi,  0.1 si,  0.0 st 
MiB Mem : 128757.1 total,   3420.5 free,  26759.6 used, 109292.5 buff/cache     
MiB Swap:      0.0 total,      0.0 free,      0.0 used. 101997.5 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                          
    196 root      20   0       0      0      0 R 100.0   0.0   0:03.87 kswapd0                                                          
2172579 root      20   0  305492 155252   2064 S  50.5   0.1   1:35.14 rsync                                                            
2172577 root      20   0  130996 119128   7152 D  35.0   0.1   2:39.27 rsync     
```

Telling drop_caches to flush returns kswapd0 to normal CPU utilization.  Until I have time to test with newer/older kernels, I just poke 1 into /proc/sys/vm/drop_caches every 30 seconds with a script to keep the system from exhausting memory.

Thanks,

---

### Post by Doug S on 2024-07-26
I never compiled or installed -rc4. Nor did I ever compile the final release. I tested -rc7:

```
doug@s19:~$ uname -a
Linux s19 6.10.0-rc7-stock #1269 SMP PREEMPT_DYNAMIC Sun Jul  7 17:20:36 PDT 2024 x86_64 x86_64 x86_64 GNU/Linux
```

I am doing an rsync of 1.2 Terabytes from another computer to this one. While I did notice an increase in kswad0 once the buffers started auto flushing, it wasn't significant.

```
doug@s19:~$ free -t
               total        used        free      shared  buff/cache   available
Mem:        32696840      853532      267392        5084    32058208    31843308
Swap:        8388604         256     8388348
Total:      41085444      853788     8655740
```

```
top - 17:03:56 up 20 min,  3 users,  load average: 0.63, 0.41, 0.18
Tasks: 229 total,   2 running, 227 sleeping,   0 stopped,   0 zombie
%Cpu0  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu1  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu2  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu3  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu4  :  0.0 us,  2.0 sy,  0.0 ni, 97.7 id,  0.3 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu5  :  2.4 us,  6.2 sy,  0.0 ni, 91.4 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu6  :  0.0 us,  0.0 sy,  0.0 ni, 96.9 id,  0.0 wa,  0.0 hi,  3.1 si,  0.0 st
%Cpu7  : 18.7 us,  9.2 sy,  0.0 ni, 72.1 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu8  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu9  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu10 :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu11 :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :  31930.5 total,    332.6 free,    897.6 used,  31171.2 buff/cache
MiB Swap:   8192.0 total,   8191.7 free,      0.2 used.  31032.9 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
   1607 doug      20   0   15532   9276   7244 S  27.9   0.0   1:10.53 ssh
   1608 doug      20   0   15656   4244   1480 S  10.6   0.0   0:25.02 rsync
    117 root      20   0       0      0      0 S   1.7   0.0   0:00.45 [COLOR="#FF0000"]kswapd0[/COLOR]
   1592 doug      20   0   12052   6056   3752 R   0.3   0.0   0:00.60 top
      1 root      20   0   22380  13112   9272 S   0.0   0.0   0:00.72 systemd
```

Long shot: In the past, I have observed that sometimes systems with large amounts of RAM benefit by increasing the minimum free kilobytes at /proc/sys/vm/min_free_kbytes.
Although, I increased mine from 67584 to 1024000 and it didn't make much if any difference.

---

### Post by 3vi1 on 2024-07-26
> **Doug S said:**
> Long shot: In the past, I have observed that sometimes systems with large amounts of RAM benefit by increasing the minimum free kilobytes at /proc/sys/vm/min_free_kbytes.
Although, I increased mine from 67584 to 1024000 and it didn't make much if any difference.

I actually thought about that too.  Last weekend I tried changing it to various values between 64K and 2G... but the same problem occurred no matter the value.  I also played with swapiness, though I'm not using SWAP.

Thanks again for letting me know your experience though, I'll keep it in mind when I do further testing.

---

### Post by Doug S on 2024-07-26
In an attempt to increase data rates, I switched to rsync'ing between two HDDs on this same computer. It did increase use of kswapd0 a little:

```
top - 17:41:24 up 57 min,  3 users,  load average: 2.10, 1.56, 0.93
Tasks: 235 total,   2 running, 233 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.5 us,  2.5 sy,  0.0 ni, 81.8 id, 15.1 wa,  0.0 hi,  0.1 si,  0.0 st
MiB Mem :  31930.5 total,    420.4 free,    889.5 used,  31091.9 buff/cache
MiB Swap:   8192.0 total,   8191.7 free,      0.2 used.  31041.0 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
   1777 doug      20   0  428000  16640   1396 S  14.4   0.1   0:55.95 rsync
   1775 doug      20   0   16508  10400   6264 D  11.8   0.0   0:45.78 rsync
   1521 root      20   0       0      0      0 D   4.6   0.0   0:09.42 kworker/u48:0+flush-8:16
    117 root      20   0       0      0      0 S   3.3   0.0   0:26.47 kswapd0
```

This transfer is all little files. I should try some big files (my earlier test was big files, but network limited). Observe the CPU usage of rsync is quite different between our tests. I'll compile -rc4 and try it later.

EDIT: I forgot I had the Ubuntu mainline -rc4 installed: Results the same:

```
doug@s19:~$ uname -a
Linux s19 6.10.0-061000rc4-generic #202406161734 SMP PREEMPT_DYNAMIC Sun Jun 16 21:47:04 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
```

```
top - 17:53:26 up 5 min,  2 users,  load average: 1.98, 0.92, 0.36
Tasks: 244 total,   1 running, 243 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.7 us,  2.6 sy,  0.0 ni, 80.4 id, 16.2 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :  31924.4 total,    535.6 free,    893.9 used,  30965.6 buff/cache
MiB Swap:   8192.0 total,   8191.7 free,      0.2 used.  31030.5 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
   1426 doug      20   0  220444  16724   1328 S  17.8   0.1   0:30.41 rsync
   1424 doug      20   0   16668  10532   6208 D  15.4   0.0   0:26.18 rsync
    116 root      20   0       0      0      0 S   4.3   0.0   0:01.68 kswapd0
    273 root      20   0       0      0      0 D   2.4   0.0   0:02.72 kworker/u48:5+flush-8:16
```

EDIT 2: I made a big file (966,367,641,600 bytes) and rsync'd it. no difference.

---

### Post by #&amp;thj^% on 2024-07-27
> **3vi1 said:**
> Thanks for the comparative data.  Is your home directory bigger than your RAM?  I'm rsyncing lots of VMs in my process, several terabytes of data.


Yes it is, but not terabytes of data. (RAM 16G Swap 4G)
```
Memory:
  System RAM: total: 16 GiB available: 13.51 GiB used: 10.12 GiB (74.9%)
  Array-1: capacity: 32 GiB slots: 2 modules: 2 EC: None
  Device-1: Channel-A DIMM 0 type: DDR4 size: 8 GiB speed: 3200 MT/s
  Device-2: Channel-B DIMM 0 type: DDR4 size: 8 GiB speed: 3200 MT/s

```
```
df /home/$USER
Filesystem     Type  Size  [COLOR="#FF0000"]Used[/COLOR] Avail Use% Mounted on
/dev/sdb2      ext4  458G  [COLOR="#FF0000"]110G [/COLOR] 325G  26% /

```
I begin to choke, when transfers exceed 1.5TB, but never stops.

---

### Post by 3vi1 on 2024-07-28
Looks like it was just a bug in the rc4 build.  Updated to the 6.10.2 kernel yesterday after it was posted to the mainline builds and, while I do see kswapd0 kick in once the buffer/cache fills memory, it is now just a brief blip which immediately settles back down to a negligible utilization.

---

