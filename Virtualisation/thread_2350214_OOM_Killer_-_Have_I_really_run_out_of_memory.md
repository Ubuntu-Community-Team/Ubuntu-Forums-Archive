---
title: "OOM Killer - Have I really run out of memory"
date: 2017-01-22
forum: Virtualisation
---

### Post by freeflyer2 on 2017-01-22
Hi

I have a Lubuntu VM running under VirtualBox on a Ubuntu 16.04.1 LTS headless host with 8GB RAM that has started to intermittently enter an aborted state, requiring me to restart it. I've tracked the issue down (I believe) to it getting killed by the OOM Killer on the host.

Reading about the OOM Killer I understand from high level that it will choose processes to kill when the system gets low on memory. The VM uses more memory that any other process so I guess that's the one that gets killed when the OOM Killer does its thing (based on it having the highest score).

What I don't understand (and this is where I've hit my knowledge wall as it were) is to me it doesn't look like the system has run out of memory when this happens. I'm assuming I'm missing something obvious, I'm still learning many aspect of Linux.

I've run a few tests to repeat the issue (running more processes than normal in an attempt to force it). Attached are the OOM Killer syslog entries (from the host machine). In it you will see a couple of VMs and a Plex transcode get killed.

I was monitoring htop during this example and didn't see any huge change in memory usage other than the drop after processes were killed. htop showed about 50% used memory, with the other 50% split between buffers and cache, with 60MB of 1.86GB swap.

I'm not able to fully understand what the syslog is telling me, Is it really indicating very low memory? I'm assuming somewhere in the snippet below it telling me that:

```
Jan 22 14:46:18 lakeviewserver kernel: [97681.315458] Mem-Info:
Jan 22 14:46:18 lakeviewserver kernel: [97681.315461] active_anon:154781 inactive_anon:172803 isolated_anon:0
Jan 22 14:46:18 lakeviewserver kernel: [97681.315461]  active_file:446530 inactive_file:448715 isolated_file:0
Jan 22 14:46:18 lakeviewserver kernel: [97681.315461]  unevictable:4 dirty:1974 writeback:0 unstable:0
Jan 22 14:46:18 lakeviewserver kernel: [97681.315461]  slab_reclaimable:69576 slab_unreclaimable:20393
Jan 22 14:46:18 lakeviewserver kernel: [97681.315461]  mapped:661973 shmem:7460 pagetables:6815 bounce:0
Jan 22 14:46:18 lakeviewserver kernel: [97681.315461]  free:52623 free_pcp:0 free_cma:0
Jan 22 14:46:18 lakeviewserver kernel: [97681.315463] Node 0 DMA free:15852kB min:132kB low:164kB high:196kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15936kB managed:15852kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Jan 22 14:46:18 lakeviewserver kernel: [97681.315466] lowmem_reserve[]: 0 3379 7840 7840 7840
Jan 22 14:46:18 lakeviewserver kernel: [97681.315468] Node 0 DMA32 free:90960kB min:29072kB low:36340kB high:43608kB active_anon:254960kB inactive_anon:258752kB active_file:843320kB inactive_file:848896kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:3578400kB managed:3497780kB mlocked:0kB dirty:2756kB writeback:0kB mapped:1095944kB shmem:6364kB slab_reclaimable:104432kB slab_unreclaimable:32684kB kernel_stack:3296kB pagetables:13064kB unstable:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Jan 22 14:46:18 lakeviewserver kernel: [97681.315471] lowmem_reserve[]: 0 0 4460 4460 4460
Jan 22 14:46:18 lakeviewserver kernel: [97681.315472] Node 0 Normal free:103680kB min:38376kB low:47968kB high:57564kB active_anon:364164kB inactive_anon:432460kB active_file:942800kB inactive_file:945964kB unevictable:16kB isolated(anon):0kB isolated(file):0kB present:4700160kB managed:4567776kB mlocked:16kB dirty:5140kB writeback:0kB mapped:1551948kB shmem:23476kB slab_reclaimable:173872kB slab_unreclaimable:48888kB kernel_stack:4880kB pagetables:14196kB unstable:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Jan 22 14:46:18 lakeviewserver kernel: [97681.315475] lowmem_reserve[]: 0 0 0 0 0
Jan 22 14:46:18 lakeviewserver kernel: [97681.315476] Node 0 DMA: 1*4kB (U) 1*8kB (U) 0*16kB 1*32kB (U) 1*64kB (U) 1*128kB (U) 1*256kB (U) 0*512kB 1*1024kB (U) 1*2048kB (M) 3*4096kB (M) = 15852kB
Jan 22 14:46:18 lakeviewserver kernel: [97681.315483] Node 0 DMA32: 17815*4kB (UME) 2504*8kB (UM) 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 91292kB
Jan 22 14:46:18 lakeviewserver kernel: [97681.315487] Node 0 Normal: 9796*4kB (UME) 7853*8kB (UM) 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 1*2048kB (H) 0*4096kB = 104056kB
Jan 22 14:46:18 lakeviewserver kernel: [97681.315492] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=1048576kB
Jan 22 14:46:18 lakeviewserver kernel: [97681.315493] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
Jan 22 14:46:18 lakeviewserver kernel: [97681.315493] 906282 total pagecache pages
Jan 22 14:46:18 lakeviewserver kernel: [97681.315495] 3480 pages in swap cache
Jan 22 14:46:18 lakeviewserver kernel: [97681.315496] Swap cache stats: add 35772, delete 32292, find 2718992/2724187
Jan 22 14:46:18 lakeviewserver kernel: [97681.315496] Free swap  = 1888668kB
Jan 22 14:46:18 lakeviewserver kernel: [97681.315497] Total swap = 1950652kB
Jan 22 14:46:18 lakeviewserver kernel: [97681.315497] 2073624 pages RAM
Jan 22 14:46:18 lakeviewserver kernel: [97681.315498] 0 pages HighMem/MovableOnly
Jan 22 14:46:18 lakeviewserver kernel: [97681.315498] 53272 pages reserved
Jan 22 14:46:18 lakeviewserver kernel: [97681.315499] 0 pages cma reserved
Jan 22 14:46:18 lakeviewserver kernel: [97681.315500] 0 pages hwpoisoned
```

---

### Post by Doug S on 2017-01-22
Hi and welcome to Ubuntu forums.

You appear to have a "tainted" kernel, and the related information is that "an externally-built ("out-of-tree") module has been loaded" and "an unsigned module has been loaded in a kernel supporting module signature". So, that is certainly a worry.

---

### Post by SeijiSensei on 2017-01-22
How much memory did you allocate to the VM?  I generally use 2048 MB for Linux VMs and 3072 MB for Windows.  An 8 GB machine should certainly have enough space to support VMs of that size.

Also does the host have a swap partition or swap file?  If not, you should [add a swap file]("https://www.howtoforge.com/ubuntu-swap-file").

---

### Post by freeflyer2 on 2017-01-22
Thanks for the welcome.

@Doug S Where are you seeing that in the attached logs? I can't see any of those phrases in there.

@SeijiSensei Each VM has 1GB RAM, normally I only have 1 running, for this test there were 3. Not sure about the swap partition, would i see that in df -h? --> just noticed your link explains that, reading it now.

---

### Post by oldos2er on 2017-01-22
Thread moved to *Virtualisation*

---

### Post by Doug S on 2017-01-22
> **freeflyer2 said:**
> @Doug S Where are you seeing that in the attached logs? I can't see any of those phrases in there.I decoded the "Tainted" message (for myself as much as for you). It was the "O" and "E" portion of the tainted message.

@SeijiSensei : Looks as though there is ~ 2 gigs if swap.

---

### Post by freeflyer2 on 2017-01-22
I've got the following swap:

```
sudo swapon -s
Filename                                Type            Size    Used    Priority
/dev/md0                                partition       1950652 60724   -1
```

```
cat /etc/fstab
# swap was on /dev/md0 during installation
UUID=8e14eab0-0301-4c45-98cf-b74a0d15c157       none                            swap    sw                      0       0
```


@oldos2er - Is *Virtualisation *the right forum, it just happens to mostly be the VM that gets killed by OOM killer but not exclusively? I'm new here so maybe it is.

@Doug S

A quick bit of reading/searching and I've found the following in my syslogs.

```
Jan 21 11:17:21 lakeviewserver kernel: [   66.011003] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
Jan 21 11:39:24 lakeviewserver kernel: [   65.377365] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel

Jan 17 17:59:52 lakeviewserver kernel: [   66.126363] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
```

Other than the connection to virtualbox it doesn't mean much to me. [http://www.linuxquestions.org/questions/linux-virtualization-and-cloud-90/module-verification-failed-signature-and-or-required-key-missing-tainting-kernel-4175533442/](http://www.linuxquestions.org/questions/linux-virtualization-and-cloud-90/module-verification-failed-signature-and-or-required-key-missing-tainting-kernel-4175533442/) talks about it.

This is all new to me, is there a possible link between this and OOM Killer getting triggered?

---

### Post by Doug S on 2017-01-22
> **freeflyer2 said:**
> This is all new to me, is there a possible link between this and OOM Killer getting triggered?I don't know. I just get worried when I see "tainted".

---

### Post by SeijiSensei on 2017-01-23
"Tainted" just means that there are kernel modules in use that are not compliant with the General Public License.  For instance, the proprietary NVIDIA driver generates these warnings:
```

[    0.684767] nvidia: module license 'NVIDIA' taints kernel.
[    0.684769] Disabling lock debugging due to kernel taint
[    0.689026] nvidia: module verification failed: signature and/or  required key missing - tainting kernel

```

OP, are you using the version of VirtualBox from the repositories or the one at Oracle's VB site?  If you're using the repository version, I suggest replacing it with the Oracle version using the instructions here:  [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

What if you give the VM 2 GB of memory rather than just one?  You've got plenty of memory on the host.

---

### Post by freeflyer2 on 2017-01-23
I'm already using VirtualBox from the link you gave, rather than from the repositories.

If I give the Guest VM more RAM won't OOM Killer on the host be more likely to kill it (i.e. it will think the host has run out of RAM sooner) or am I misunderstanding. I'm willing to give it a go, as you say there is plenty of RAM available on the host.

---

### Post by kpatz on 2017-01-23
Here's information on OOM Killer and how to configure it: [http://www.oracle.com/technetwork/articles/servers-storage-dev/oom-killer-1911807.html](http://www.oracle.com/technetwork/articles/servers-storage-dev/oom-killer-1911807.html)

Running 3 GB of VMs on a system with 8 GB RAM shouldn't cause an OOM condition normally.  I would make swap bigger, like 8 GB and see if that helps.

---

### Post by freeflyer2 on 2017-01-24
Normally I only run 1 VM (with 1GB) RAM, so in theory like you say I should have plenty with a host that has 8GB. The only other major process sitting on the host in Plex. This seems to be more CPU hungry though.

I'd looked at some of those settings regarding OOM Killer and had considered getting it to ignore certain processes (such as the vm) but it kind of feels I'll end up with other issues and should try to find the root cause first.

I also get other processes killed. For example overnight the below happened:

```
Jan 23 21:09:01 lakeviewserver kernel: [207045.579678] Out of memory: Kill process 26767 (VBoxHeadless) score 213 or sacrifice child
Jan 23 21:09:01 lakeviewserver kernel: [207045.579732] Killed process 26767 (VBoxHeadless) total-vm:3874192kB, anon-rss:75416kB, file-rss:2057572kB
Jan 23 21:09:01 lakeviewserver kernel: [207045.584085] Out of memory: Kill process 1450 (Plex Media Serv) score 14 or sacrifice child
Jan 23 21:09:01 lakeviewserver kernel: [207045.584120] Killed process 26652 (Plex Script Hos) total-vm:2056260kB, anon-rss:54196kB, file-rss:7656kB
Jan 24 01:36:23 lakeviewserver kernel: [223088.329362] Out of memory: Kill process 27967 (VBoxHeadless) score 128 or sacrifice child
Jan 24 01:36:23 lakeviewserver kernel: [223088.329413] Killed process 27967 (VBoxHeadless) total-vm:2889732kB, anon-rss:76300kB, file-rss:1212796kB
Jan 24 02:21:43 lakeviewserver kernel: [225808.049141] Out of memory: Kill process 31149 (Plex Media Scan) score 100 or sacrifice child
Jan 24 02:21:43 lakeviewserver kernel: [225808.049195] Killed process 31149 (Plex Media Scan) total-vm:1383408kB, anon-rss:969352kB, file-rss:34184kB

```

So its not just affecting the vm.

I'm currently running the following command to gather stats every 10 seconds in the hope it can be compared to the syslog and show something meaningful to someone here:

 vmstat -SMt 10 1000 > memoryusage.out &

I normally only see around 60-120 MB swap (at least that my interpretation without fully understanding linux RAM usage). For example the above command has so far output:

```
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu----- -----timestamp-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st                 GMT
 2  0    111    139   3295   2446    0    0     0     4 1032 3860  1  2 98  0  0 2017-01-24 07:42:49
 0  0    111    137   3296   2447    0    0     0    16 1105 5026  1  2 97  0  0 2017-01-24 07:42:59
 0  0    111    130   3300   2451    0    0     0   832 1095 4854  1  2 97  0  0 2017-01-24 07:43:09
 0  0    111    129   3300   2451    0    0     0    12 1109 4349  1  2 97  0  0 2017-01-24 07:43:19
 0  0    111    120   3304   2455    0    0     0    10 1329 6210  1  3 96  0  0 2017-01-24 07:43:29
 0  0    111    132   3300   2445    0    0     0  1248 1180 5175  1  2 97  0  0 2017-01-24 07:43:39
```

Which I believe is telling me I have used 111MB of swap space out of the 2GB available. I'm willing to create more though if things point in that direction?


I'll post back when I have the vmstat output to compare to the syslog.

If anyone has any more useful logging let me know.

---

### Post by freeflyer2 on 2017-01-24
I've caught another OOM Kill today. This time it killed a Plex Media Server process not the guest VM.

The syslog segment is:  

```
Jan 24 13:49:59 lakeviewserver kernel: [267104.374271] EMT invoked oom-killer: gfp_mask=0x24042c0, order=3, oom_score_adj=0
Jan 24 13:49:59 lakeviewserver kernel: [267104.374274] EMT cpuset=/ mems_allowed=0
Jan  24 13:49:59 lakeviewserver kernel: [267104.374280] CPU: 2 PID: 9284  Comm: EMT Tainted: G           OE   4.4.0-59-generic #80-Ubuntu
Jan 24 13:49:59 lakeviewserver kernel: [267104.374281] Hardware name: Dell Inc. PowerEdge T20/0VD5HY, BIOS A05 09/18/2014
Jan 24 13:49:59 lakeviewserver kernel: [267104.374282]  0000000000000286 000000006aeacab6 ffff880057c3b988 ffffffff813f7583
Jan 24 13:49:59 lakeviewserver kernel: [267104.374285]  ffff880057c3bb60 ffff8802101b6200 ffff880057c3b9f8 ffffffff8120ad5e
Jan 24 13:49:59 lakeviewserver kernel: [267104.374287]  0000000000000015 0000000000000000 ffff880214bfe9c0 ffff880035862a00
Jan 24 13:49:59 lakeviewserver kernel: [267104.374289] Call Trace:
Jan 24 13:49:59 lakeviewserver kernel: [267104.374294]  [<ffffffff813f7583>] dump_stack+0x63/0x90
Jan 24 13:49:59 lakeviewserver kernel: [267104.374297]  [<ffffffff8120ad5e>] dump_header+0x5a/0x1c5
Jan 24 13:49:59 lakeviewserver kernel: [267104.374300]  [<ffffffff81390584>] ? apparmor_capable+0xc4/0x1b0
Jan 24 13:49:59 lakeviewserver kernel: [267104.374303]  [<ffffffff81192722>] oom_kill_process+0x202/0x3c0
Jan 24 13:49:59 lakeviewserver kernel: [267104.374304]  [<ffffffff81192b49>] out_of_memory+0x219/0x460
Jan  24 13:49:59 lakeviewserver kernel: [267104.374307]   [<ffffffff81198abd>]  __alloc_pages_slowpath.constprop.88+0x8fd/0xa70
Jan 24 13:49:59 lakeviewserver kernel: [267104.374310]  [<ffffffff81198eb6>] __alloc_pages_nodemask+0x286/0x2a0
Jan 24 13:49:59 lakeviewserver kernel: [267104.374313]  [<ffffffff811e271c>] alloc_pages_current+0x8c/0x110
Jan 24 13:49:59 lakeviewserver kernel: [267104.374315]  [<ffffffff81196b49>] alloc_kmem_pages+0x19/0x90
Jan 24 13:49:59 lakeviewserver kernel: [267104.374318]  [<ffffffff811b449e>] kmalloc_order_trace+0x2e/0xe0
Jan 24 13:49:59 lakeviewserver kernel: [267104.374321]  [<ffffffff811ee49e>] __kmalloc+0x22e/0x250
Jan 24 13:49:59 lakeviewserver kernel: [267104.374337]  [<ffffffffc06ea445>] rtR0MemAllocEx+0x175/0x240 [vboxdrv]
Jan 24 13:49:59 lakeviewserver kernel: [267104.374345]  [<ffffffffc06e8037>] VBoxHost_RTMemAllocTag+0x27/0x60 [vboxdrv]
Jan 24 13:49:59 lakeviewserver kernel: [267104.374352]  [<ffffffffc06de4f2>] supdrvIOCtl+0x2f12/0x3260 [vboxdrv]
Jan  24 13:49:59 lakeviewserver kernel: [267104.374359]   [<ffffffffc06d75d0>] VBoxDrvLinuxIOCtl_5_1_14+0x150/0x250  [vboxdrv]
Jan 24 13:49:59 lakeviewserver kernel: [267104.374361]  [<ffffffff8122272f>] do_vfs_ioctl+0x29f/0x490
Jan 24 13:49:59 lakeviewserver kernel: [267104.374364]  [<ffffffff8106b514>] ? __do_page_fault+0x1b4/0x400
Jan 24 13:49:59 lakeviewserver kernel: [267104.374365]  [<ffffffff81222999>] SyS_ioctl+0x79/0x90
Jan 24 13:49:59 lakeviewserver kernel: [267104.374368]  [<ffffffff818384f2>] entry_SYSCALL_64_fastpath+0x16/0x71
Jan 24 13:49:59 lakeviewserver kernel: [267104.374370] Mem-Info:
Jan 24 13:49:59 lakeviewserver kernel: [267104.374373] active_anon:65672 inactive_anon:112078 isolated_anon:0
Jan 24 13:49:59 lakeviewserver kernel: [267104.374373]  active_file:748064 inactive_file:885636 isolated_file:0
Jan 24 13:49:59 lakeviewserver kernel: [267104.374373]  unevictable:0 dirty:26 writeback:0 unstable:0
Jan 24 13:49:59 lakeviewserver kernel: [267104.374373]  slab_reclaimable:71044 slab_unreclaimable:20335
Jan 24 13:49:59 lakeviewserver kernel: [267104.374373]  mapped:23549 shmem:6425 pagetables:3913 bounce:0
Jan 24 13:49:59 lakeviewserver kernel: [267104.374373]  free:101977 free_pcp:0 free_cma:0
Jan  24 13:49:59 lakeviewserver kernel: [267104.374376] Node 0 DMA  free:15852kB min:132kB low:164kB high:196kB active_anon:0kB  inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB  isolated(anon):0kB isolated(file):0kB present:15936kB managed:15852kB  mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB  slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB  pagetables:0kB unstable:0kB bounce:0kB free_pcp:0kB local_pcp:0kB  free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Jan 24 13:49:59 lakeviewserver kernel: [267104.374379] lowmem_reserve[]: 0 3379 7840 7840 7840
Jan  24 13:49:59 lakeviewserver kernel: [267104.374382] Node 0 DMA32  free:226308kB min:29072kB low:36340kB high:43608kB active_anon:112520kB  inactive_anon:206484kB active_file:1313444kB inactive_file:1491924kB  unevictable:0kB isolated(anon):0kB isolated(file):0kB present:3578400kB  managed:3497780kB mlocked:0kB dirty:36kB writeback:0kB mapped:61420kB  shmem:17640kB slab_reclaimable:104940kB slab_unreclaimable:27836kB  kernel_stack:1504kB pagetables:5348kB unstable:0kB bounce:0kB  free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB  pages_scanned:0 all_unreclaimable? no
Jan 24 13:49:59 lakeviewserver kernel: [267104.374386] lowmem_reserve[]: 0 0 4460 4460 4460
Jan  24 13:49:59 lakeviewserver kernel: [267104.374388] Node 0 Normal  free:165748kB min:38376kB low:47968kB high:57564kB active_anon:150168kB  inactive_anon:241828kB active_file:1678812kB inactive_file:2050620kB  unevictable:0kB isolated(anon):0kB isolated(file):0kB present:4700160kB  managed:4567776kB mlocked:0kB dirty:68kB writeback:0kB mapped:32776kB  shmem:8060kB slab_reclaimable:179236kB slab_unreclaimable:53504kB  kernel_stack:3824kB pagetables:10304kB unstable:0kB bounce:0kB  free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB  pages_scanned:0 all_unreclaimable? no
Jan 24 13:49:59 lakeviewserver kernel: [267104.374392] lowmem_reserve[]: 0 0 0 0 0
Jan  24 13:49:59 lakeviewserver kernel: [267104.374394] Node 0 DMA: 1*4kB  (U) 1*8kB (U) 0*16kB 1*32kB (U) 1*64kB (U) 1*128kB (U) 1*256kB (U)  0*512kB 1*1024kB (U) 1*2048kB (M) 3*4096kB (M) = 15852kB
Jan 24  13:49:59 lakeviewserver kernel: [267104.374402] Node 0 DMA32: 11783*4kB  (UME) 22410*8kB (UM) 2*16kB (U) 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB  0*1024kB 0*2048kB 0*4096kB = 226444kB
Jan 24 13:49:59 lakeviewserver  kernel: [267104.374408] Node 0 Normal: 15644*4kB (UME) 12654*8kB (UM)  0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 1*2048kB (H)  0*4096kB = 165856kB
Jan 24 13:49:59 lakeviewserver kernel:  [267104.374415] Node 0 hugepages_total=0 hugepages_free=0  hugepages_surp=0 hugepages_size=1048576kB
Jan 24 13:49:59  lakeviewserver kernel: [267104.374417] Node 0 hugepages_total=0  hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
Jan 24 13:49:59 lakeviewserver kernel: [267104.374417] 1642457 total pagecache pages
Jan 24 13:49:59 lakeviewserver kernel: [267104.374419] 2198 pages in swap cache
Jan 24 13:49:59 lakeviewserver kernel: [267104.374420] Swap cache stats: add 61770, delete 59572, find 2803500/2810636
Jan 24 13:49:59 lakeviewserver kernel: [267104.374421] Free swap  = 1838420kB
Jan 24 13:49:59 lakeviewserver kernel: [267104.374421] Total swap = 1950652kB
Jan 24 13:49:59 lakeviewserver kernel: [267104.374422] 2073624 pages RAM
Jan 24 13:49:59 lakeviewserver kernel: [267104.374423] 0 pages HighMem/MovableOnly
Jan 24 13:49:59 lakeviewserver kernel: [267104.374424] 53272 pages reserved
Jan 24 13:49:59 lakeviewserver kernel: [267104.374424] 0 pages cma reserved
Jan 24 13:49:59 lakeviewserver kernel: [267104.374425] 0 pages hwpoisoned
Jan  24 13:49:59 lakeviewserver kernel: [267104.374426] [ pid ]   uid  tgid  total_vm      rss nr_ptes nr_pmds swapents oom_score_adj name
Jan 24  13:49:59 lakeviewserver kernel: [267104.374431] [  373]     0   373     10972     2611      23       3       42             0 systemd-journal
Jan  24 13:49:59 lakeviewserver kernel: [267104.374433] [  415]     0    415    11226      411      24       3      302         -1000  systemd-udevd
Jan 24 13:49:59 lakeviewserver kernel: [267104.374435]  [  795]     0   795    27598    24937      59       3        48             0 mount.ntfs
Jan 24 13:49:59 lakeviewserver kernel:  [267104.374437] [  801]     0   801    26222    23600      54        4       51             0 mount.ntfs
Jan 24 13:49:59 lakeviewserver  kernel: [267104.374438] [  859]   109   859    25596      356       20       3       53             0 systemd-timesyn
Jan 24 13:49:59  lakeviewserver kernel: [267104.374440] [  972]     0   972     7252       559      19       3       26             0 cron
Jan 24 13:49:59  lakeviewserver kernel: [267104.374442] [  980]     0   980     5025       430      14       3       46             0 systemd-logind
Jan 24  13:49:59 lakeviewserver kernel: [267104.374443] [  985]   104   985     11230      460      26       3       63             0 avahi-daemon
Jan  24 13:49:59 lakeviewserver kernel: [267104.374445] [  988]   102    988    10745      335      25       3       86          -900 dbus-daemon
Jan  24 13:49:59 lakeviewserver kernel: [267104.374447] [ 1000]   101   1000    64100      472      27       3      124             0 rsyslogd
Jan  24 13:49:59 lakeviewserver kernel: [267104.374448] [ 1004]   104   1004    11197        7      25       3       75             0  avahi-daemon
Jan 24 13:49:59 lakeviewserver kernel: [267104.374450] [  1005]     0  1005     7470       71      19       3        64             0 cgmanager
Jan 24 13:49:59 lakeviewserver kernel:  [267104.374452] [ 1021]     0  1021     6416      474      19        3      249             0 smartd
Jan 24 13:49:59 lakeviewserver  kernel: [267104.374453] [ 1023]     0  1023    41608      419       38       3      127             0 thermald
Jan 24 13:49:59  lakeviewserver kernel: [267104.374455] [ 1027]     0  1027    68972      1108      38       3      585             0 accounts-daemon
Jan 24  13:49:59 lakeviewserver kernel: [267104.374456] [ 1073]     0  1073      3383      122      11       3       32             0 mdadm
Jan 24  13:49:59 lakeviewserver kernel: [267104.374458] [ 1077]     0  1077      4868       31      14       3       35             0 irqbalance
Jan  24 13:49:59 lakeviewserver kernel: [267104.374459] [ 1098]     0   1098    69278      695      40       4      121             0 polkitd
Jan  24 13:49:59 lakeviewserver kernel: [267104.374461] [ 1176]  1000   1176   333392     4598     101       5      677             0 vboxwebsrv
Jan  24 13:49:59 lakeviewserver kernel: [267104.374463] [ 1178]  1000   1178    41648      521      66       3      597             0  VBoxXPCOMIPCD
Jan 24 13:49:59 lakeviewserver kernel: [267104.374464] [  1197]  1000  1197   232185     3000      93       4       609             0 VBoxSVC
Jan 24 13:49:59 lakeviewserver kernel:  [267104.374466] [ 1212]     0  1212     3533      864      11        3       59             0 mount.ntfs
Jan 24 13:49:59 lakeviewserver  kernel: [267104.374467] [ 1215]     0  1215     3474      837       11       3       59             0 mount.ntfs
Jan 24 13:49:59  lakeviewserver kernel: [267104.374469] [ 1216]     0  1216     3313       684      11       3       70             0 mount.ntfs
Jan 24  13:49:59 lakeviewserver kernel: [267104.374470] [ 1218]     0  1218      3333      639      10       3       66             0 mount.ntfs
Jan  24 13:49:59 lakeviewserver kernel: [267104.374472] [ 1262]     0   1262    84472      917     160       3      541             0 smbd
Jan  24 13:49:59 lakeviewserver kernel: [267104.374473] [ 1271]     0   1271    82478      273     154       3      545             0 smbd
Jan  24 13:49:59 lakeviewserver kernel: [267104.374475] [ 1303]     0   1303    84472      585     154       3      571             0 smbd
Jan  24 13:49:59 lakeviewserver kernel: [267104.374476] [ 1315]     0   1315     4030      517      10       3      164             0 dhclient
Jan  24 13:49:59 lakeviewserver kernel: [267104.374478] [ 1413]  1000   1413   648383    16946     203       5    10854             0  calibre-server
Jan 24 13:49:59 lakeviewserver kernel: [267104.374480]  [ 1416]     0  1416    16380      602      35       3      152          -1000 sshd
Jan 24 13:49:59 lakeviewserver kernel: [267104.374481] [  1448]   105  1448     1127       74       8       3       23              0 sh
Jan 24 13:49:59 lakeviewserver kernel: [267104.374483] [  1450]   105  1450   218538    27210     350       4     2096              0 Plex Media Serv
Jan 24 13:49:59 lakeviewserver kernel:  [267104.374484] [ 1480]     0  1480     3985      264      13        3       39             0 agetty
Jan 24 13:49:59 lakeviewserver  kernel: [267104.374486] [ 1515]     0  1515    71290     6570      101       4       74             0 apache2
Jan 24 13:49:59  lakeviewserver kernel: [267104.374487] [ 1525]     0  1525    60002       568     113       3      385             0 nmbd
Jan 24 13:49:59  lakeviewserver kernel: [267104.374489] [17776]   114 17776   465601     23335     136       5     2105             0 python
Jan 24 13:49:59  lakeviewserver kernel: [267104.374490] [16758]     0 16758    73117      2363      45       3     1522             0 fail2ban-server
Jan 24  13:49:59 lakeviewserver kernel: [267104.374492] [27677]   105 27677    530959    21205     141       5        0             0 Plex Script Hos
Jan  24 13:49:59 lakeviewserver kernel: [267104.374494] [ 1327]    33   1327    73952     6609     103       4       74             0 apache2
Jan  24 13:49:59 lakeviewserver kernel: [267104.374495] [ 1329]    33   1329    73430     6062     102       4       74             0 apache2
Jan  24 13:49:59 lakeviewserver kernel: [267104.374497] [ 1331]    33   1331    73430     6417     102       4       74             0 apache2
Jan  24 13:49:59 lakeviewserver kernel: [267104.374498] [ 1332]    33   1332    74047     6525     104       4       74             0 apache2
Jan  24 13:49:59 lakeviewserver kernel: [267104.374500] [ 1716]    33   1716    73940     6096     103       4       74             0 apache2
Jan  24 13:49:59 lakeviewserver kernel: [267104.374501] [ 1733]    33   1733    73942     6433     103       4       74             0 apache2
Jan  24 13:49:59 lakeviewserver kernel: [267104.374503] [ 1741]    33   1741    73537     6180     103       4       74             0 apache2
Jan  24 13:49:59 lakeviewserver kernel: [267104.374504] [ 1742]    33   1742    73439     6111     102       4       74             0 apache2
Jan  24 13:49:59 lakeviewserver kernel: [267104.374506] [ 1743]    33   1743    73942     6365     103       4       74             0 apache2
Jan  24 13:49:59 lakeviewserver kernel: [267104.374507] [ 2197]    33   2197    73942     6510     103       4       74             0 apache2
Jan  24 13:49:59 lakeviewserver kernel: [267104.374509] [ 8466]     0   8466    17020     1514      37       4        0             0 sshd
Jan  24 13:49:59 lakeviewserver kernel: [267104.374510] [ 8471]  1000   8471    17020      793      35       4        0             0 sshd
Jan  24 13:49:59 lakeviewserver kernel: [267104.374512] [ 8472]  1000   8472     4988     1247      15       3        0             0 bash
Jan  24 13:49:59 lakeviewserver kernel: [267104.374513] [ 8767]     0   8767    17020     1525      38       3        0             0 sshd
Jan  24 13:49:59 lakeviewserver kernel: [267104.374515] [ 8770]  1000   8770    17020      764      35       3        0             0 sshd
Jan  24 13:49:59 lakeviewserver kernel: [267104.374516] [ 8771]  1000   8771     4990     1263      15       3        0             0 bash
Jan  24 13:49:59 lakeviewserver kernel: [267104.374517] [ 8912]     0   8912    17020     1522      36       3        0             0 sshd
Jan  24 13:49:59 lakeviewserver kernel: [267104.374519] [ 8914]  1000   8914    17020      748      34       3        0             0 sshd
Jan  24 13:49:59 lakeviewserver kernel: [267104.374520] [ 8915]  1000   8915     4988     1275      15       3        0             0 bash
Jan  24 13:49:59 lakeviewserver kernel: [267104.374522] [ 9114]  1000   9114     1103      175       8       3        0             0 tail
Jan  24 13:49:59 lakeviewserver kernel: [267104.374523] [ 9119]     0   9119    13588      733      31       3        9             0 cron
Jan  24 13:49:59 lakeviewserver kernel: [267104.374525] [ 9121]  1000   9121     1127      174       8       3        0             0 sh
Jan  24 13:49:59 lakeviewserver kernel: [267104.374526] [ 9123]  1000   9123     7075      374      18       3        0             0 vmstat
Jan  24 13:49:59 lakeviewserver kernel: [267104.374528] [ 9260]    33   9260    71296     2035      91       4       74             0 apache2
Jan  24 13:49:59 lakeviewserver kernel: [267104.374529] [ 9273]  1000   9273   171410     4882      95       4        0             0  VBoxHeadless
Jan 24 13:49:59 lakeviewserver kernel: [267104.374531]  Out of memory: Kill process 1450 (Plex Media Serv) score 11 or sacrifice  child
Jan 24 13:49:59 lakeviewserver kernel: [267104.375727] Killed  process 27677 (Plex Script Hos) total-vm:2123836kB, anon-rss:75488kB,  file-rss:9332kB
Jan 24 13:49:59 lakeviewserver kernel: [267104.380518] vboxdrv: ffffffffc0f61020 VMMR0.r0
Jan 24 13:49:59 lakeviewserver kernel: [267104.474819] vboxdrv: ffffffffc1064020 VBoxDDR0.r0
Jan 24 13:49:59 lakeviewserver kernel: [267104.551092] vboxdrv: ffffffffc04b7020 VBoxEhciR0.r0
```


The associated output from vmstat -SMt is:

```
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st                 GMT
 0  1    109    414   2947   3804    0    0   211   168   34   29  4  1 92  3  0 2017-01-24 13:45:01
 0  0    109    414   2947   3804    0    0     0    18  131  279  0  0 100  0  0 2017-01-24 13:45:11
 0  0    109    414   2947   3804    0    0     0    11  131  288  0  0 100  0  0 2017-01-24 13:45:21
 0  0    109    414   2947   3804    0    0     0     1  126  257  0  0 100  0  0 2017-01-24 13:45:31
 0  0    109    413   2947   3804    0    0     1    19  150  311  0  0 100  0  0 2017-01-24 13:45:41
 0  0    109    412   2947   3804    0    0     0     4  158  464  0  0 100  0  0 2017-01-24 13:45:51
 0  0    109    414   2947   3804    0    0     0     1  138  380  0  0 100  0  0 2017-01-24 13:46:01
 0  0    109    413   2947   3804    0    0     0     8  145  393  0  0 100  0  0 2017-01-24 13:46:11
 0  0    109    414   2947   3804    0    0     0    11  155  402  0  0 99  0  0 2017-01-24 13:46:21
 0  0    109    414   2947   3804    0    0     0     2  128  263  0  0 100  0  0 2017-01-24 13:46:31
 0  0    109    413   2947   3804    0    0     0     6  133  284  0  0 100  0  0 2017-01-24 13:46:41
 0  0    109    413   2947   3804    0    0     0     9  127  260  0  0 100  0  0 2017-01-24 13:46:51
 0  0    109    415   2947   3804    0    0     0     2  143  355  0  0 99  0  0 2017-01-24 13:47:01
 0  0    109    416   2947   3804    0    0     0     6  126  268  0  0 100  0  0 2017-01-24 13:47:11
 0  0    109    417   2947   3804    0    0     0    13  133  285  0  0 100  0  0 2017-01-24 13:47:21
 0  0    109    417   2947   3804    0    0     0     5  124  259  0  0 100  0  0 2017-01-24 13:47:31
 0  0    109    417   2947   3804    0    0     0     7  140  313  0  0 100  0  0 2017-01-24 13:47:41
 0  0    109    417   2947   3804    0    0     0     6  130  269  0  0 100  0  0 2017-01-24 13:47:51
 0  0    109    417   2947   3804    0    0     0     1  123  258  0  0 100  0  0 2017-01-24 13:48:01
 0  0    109    416   2947   3804    0    0     0     6  127  256  0  0 100  0  0 2017-01-24 13:48:11
 0  0    109    416   2947   3804    0    0     0    17  134  289  0  0 100  0  0 2017-01-24 13:48:21
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu----- -----timestamp-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st                 GMT
 1  0    109    417   2947   3804    0    0     0     2  132  292  0  0 100  0  0 2017-01-24 13:48:31
 0  0    109    417   2947   3804    0    0     0     9  144  300  0  0 100  0  0 2017-01-24 13:48:41
 0  0    109    419   2947   3804    0    0     0    13  162  318  0  0 100  0  0 2017-01-24 13:48:51
 0  0    109    419   2947   3804    0    0     0    11  137  280  0  0 100  0  0 2017-01-24 13:49:01
 0  0    109    419   2947   3804    0    0     0     6  143  294  0  0 100  0  0 2017-01-24 13:49:11
 0  0    109    419   2947   3804    0    0    43    16  147  302  0  0 100  0  0 2017-01-24 13:49:21
 0  0    109    419   2947   3804    0    0     0    11  134  268  0  0 100  0  0 2017-01-24 13:49:31
 0  0    109    409   2947   3811    0    0   691    11  316 10547  1  1 96  2  0 2017-01-24 13:49:41
 0  0    109    409   2947   3811    0    0     0     8  137  315  0  0 100  0  0 2017-01-24 13:49:51
 0  1    109    283   2947   3823    0    0  1435    55  350 4641  1  1 98  0  0 2017-01-24 13:50:01
 1  0    109    140   2736   3694    0    0 20823   341 1989 7428  1 12 87  0  0 2017-01-24 13:50:11
 0  0    109   1623   2571   2105    0    0  8100   119 1748 8365  1  8 91  0  0 2017-01-24 13:50:21
 0  0    109   1608   2571   2107    0    0   166    46  705 2476  0  1 99  0  0 2017-01-24 13:50:31
 0  0    109   1608   2571   2107    0    0     1    23  687 2213  0  0 99  0  0 2017-01-24 13:50:41
 0  0    109   1607   2571   2107    0    0     2   173  705 2177  0  0 99  0  0 2017-01-24 13:50:51
 0  0    109   1604   2571   2107    0    0     0    29  683 2317  0  0 99  0  0 2017-01-24 13:51:01
 0  0    109   1605   2571   2107    0    0     0    12  676 2146  0  0 99  0  0 2017-01-24 13:51:11
 0  0    109   1595   2571   2107    0    0     0    13  677 2197  0  0 99  0  0 2017-01-24 13:51:21
 2  0    109   1591   2571   2107    0    0     2    10  753 5844  1  1 98  0  0 2017-01-24 13:51:31
 0  0    109   1586   2571   2108    0    0     1    76  797 10782  1  1 98  0  0 2017-01-24 13:51:41
 0  1    109   1402   2572   2110    0    0 10787  1620 1202 5534  1  8 84  7  0 2017-01-24 13:51:51
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu----- -----timestamp-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st                 GMT
 2  0    109   1277   2572   2111    0    0 10783   268 1178 17319  1  5 73 21  0 2017-01-24 13:52:01
 0  0    109   1279   2572   2111    0    0    15   136  857 3817  0  1 98  0  0 2017-01-24 13:52:11
 0  0    109   1292   2572   2111    0    0    13    18  795 1570  0  1 99  0  0 2017-01-24 13:52:21
 1  0    109   1292   2572   2111    0    0    27   152  756 1442  0  1 99  0  0 2017-01-24 13:52:31
 0  0    109   1290   2572   2111    0    0     1   302  769 1524  0  1 99  0  0 2017-01-24 13:52:41
 0  0    109   1290   2572   2111    0    0     0    11  742 1456  0  1 99  0  0 2017-01-24 13:52:51
 0  0    109   1287   2572   2111    0    0     2    60  786 1478  0  1 99  0  0 2017-01-24 13:53:01
 0  0    109   1287   2572   2111    0    0     0     6  759 1511  0  1 99  0  0 2017-01-24 13:53:11
 0  0    109   1290   2572   2110    0    0     0    28  762 1524  0  1 99  0  0 2017-01-24 13:53:21
 0  0    109   1290   2572   2110    0    0     0    13  750 1462  0  1 99  0  0 2017-01-24 13:53:31
 0  0    109   1290   2572   2110    0    0     0    20  779 1462  0  1 99  0  0 2017-01-24 13:53:41
 0  0    109   1290   2572   2110    0    0     0     1  746 1460  0  1 99  0  0 2017-01-24 13:53:51
 0  0    109   1290   2572   2110    0    0     0     7  762 1460  0  0 99  0  0 2017-01-24 13:54:01
 0  0    109   1290   2572   2110    0    0     0    14  771 1516  0  0 99  0  0 2017-01-24 13:54:11
```


I can see the jump in free space in the vmstat log at 13:50 that coincides with the OOM Kill in the syslog. Is there any clue in there though as to why this has happened. Does it look like I have run out of memory or is it not possible to determine that from these logs?

---

### Post by ravinglogic on 2017-01-24
For what it's worth, there's an apparent known issue with false OOM triggering with the 4.4.0-59 kernel: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1655842](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1655842)

You might try typing ```
uname -a
``` into a terminal and see which kernel you're on.

---

### Post by freeflyer2 on 2017-01-25
I seem to be on that very version:

```
4.4.0-59-generic #80-Ubuntu SMP Fri Jan 6 17:47:47 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

Thanks for the link. I'll have a read of it later, got the morning rush on right now.

It would be good if that turned out to be the issue. 

I'm going to do some reading about Linux and memory use in the meantime also, might as well use this as a learning opportunity. If anyone does spot an explanation for the Kill in the logs (assuming there is one and I have the right logs) let me know.

---

### Post by freeflyer2 on 2017-01-27
> **ravinglogic said:**
> For what it's worth, there's an apparent known issue with false OOM triggering with the 4.4.0-59 kernel: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1655842](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1655842)

You might try typing ```
uname -a
``` into a terminal and see which kernel you're on.


Thought I'd report back. I've been running a few days now rolled back to 4.4.0-53-generic without issue so am fairly confident I'm experiencing the bug you referenced. Its fixed and planned to be rolled out in a kernel update on the 20th Feb so I'll stick with 4.4.0-53-generic for now and try the new update then.

Thanks for pointing out the link.

---

