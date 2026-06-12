---
title: "Server froze - Out of Memory errors"
date: 2009-11-17
forum: Server Platforms
---

### Post by chrislynch8 on 2009-11-17
Hi I have a Dell PowerEdge 2950 with the following spec

Quad-Cor Xeon E5335 2.0Ghz/2X4MB 1333FSB
4GB of RAM
2 X 400GB SAS 10000rpm disk in Harddware Raid1
2 GiB network cards..

Yesterday It froze for the first time every. I received Out of Memory errors in the syslog once I rebooted the server and got it running again.

Below are the errors in the kern.log file up to the point that I held in the power button to shut it down and reboot.

How do you find out what caused the Memory Leak? I can see in the Logs that it Killed mc and apache2 processes - althought looking at the log there was alot of apache2 processes to kill.

```
Nov 16 16:52:37 server01 kernel: [977784.865515] oom-killer: gfp_mask=0x201d2, order=0
Nov 16 16:52:37 server01 kernel: [977784.865519] Mem-info:
Nov 16 16:52:37 server01 kernel: [977784.865521] Node 0 DMA per-cpu:
Nov 16 16:52:37 server01 kernel: [977784.865524] cpu 0 hot: low 0, high 0, batch 1 used:0
Nov 16 16:52:37 server01 kernel: [977784.865526] cpu 0 cold: low 0, high 0, batch 1 used:0
Nov 16 16:52:37 server01 kernel: [977784.865529] cpu 1 hot: low 0, high 0, batch 1 used:0
Nov 16 16:52:37 server01 kernel: [977784.865531] cpu 1 cold: low 0, high 0, batch 1 used:0
Nov 16 16:52:37 server01 kernel: [977784.865533] cpu 2 hot: low 0, high 0, batch 1 used:0
Nov 16 16:52:37 server01 kernel: [977784.865535] cpu 2 cold: low 0, high 0, batch 1 used:0
Nov 16 16:52:37 server01 kernel: [977784.865537] cpu 3 hot: low 0, high 0, batch 1 used:0
Nov 16 16:52:37 server01 kernel: [977784.865540] cpu 3 cold: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.865541] Node 0 DMA32 per-cpu:
Nov 16 16:52:39 server01 kernel: [977784.865544] cpu 0 hot: low 0, high 186, batch 31 used:36
Nov 16 16:52:39 server01 kernel: [977784.865546] cpu 0 cold: low 0, high 62, batch 15 used:61
Nov 16 16:52:39 server01 kernel: [977784.865549] cpu 1 hot: low 0, high 186, batch 31 used:82
Nov 16 16:52:39 server01 kernel: [977784.865551] cpu 1 cold: low 0, high 62, batch 15 used:34
Nov 16 16:52:39 server01 kernel: [977784.865553] cpu 2 hot: low 0, high 186, batch 31 used:46
Nov 16 16:52:39 server01 kernel: [977784.865555] cpu 2 cold: low 0, high 62, batch 15 used:57
Nov 16 16:52:39 server01 kernel: [977784.865558] cpu 3 hot: low 0, high 186, batch 31 used:53
Nov 16 16:52:39 server01 kernel: [977784.865560] cpu 3 cold: low 0, high 62, batch 15 used:13
Nov 16 16:52:39 server01 kernel: [977784.865562] Node 0 Normal per-cpu:
Nov 16 16:52:39 server01 kernel: [977784.865564] cpu 0 hot: low 0, high 186, batch 31 used:42
Nov 16 16:52:39 server01 kernel: [977784.865567] cpu 0 cold: low 0, high 62, batch 15 used:35
Nov 16 16:52:39 server01 kernel: [977784.865569] cpu 1 hot: low 0, high 186, batch 31 used:71
Nov 16 16:52:39 server01 kernel: [977784.865571] cpu 1 cold: low 0, high 62, batch 15 used:51
Nov 16 16:52:39 server01 kernel: [977784.865574] cpu 2 hot: low 0, high 186, batch 31 used:26
Nov 16 16:52:39 server01 kernel: [977784.865576] cpu 2 cold: low 0, high 62, batch 15 used:38
Nov 16 16:52:39 server01 kernel: [977784.865578] cpu 3 hot: low 0, high 186, batch 31 used:38
Nov 16 16:52:39 server01 kernel: [977784.865580] cpu 3 cold: low 0, high 62, batch 15 used:25
Nov 16 16:52:39 server01 kernel: [977784.865582] Node 0 HighMem per-cpu: empty
Nov 16 16:52:39 server01 kernel: [977784.865586] Free pages:       23636kB (0kB HighMem)
Nov 16 16:52:39 server01 kernel: [977784.865590] Active:398464 inactive:412872 dirty:0 writeback:0 unstable:0 free:5909 slab:61805 mapped:813349 pagetables:56272
Nov 16 16:52:39 server01 kernel: [977784.865592] Node 0 DMA free:12348kB min:20kB low:24kB high:28kB active:0kB inactive:0kB present:11992kB pages_scanned:26441 all_unreclaimable? yes
Nov 16 16:52:39 server01 kernel: [977784.865597] lowmem_reserve[]: 0 3251 4009 4009
Nov 16 16:52:39 server01 kernel: [977784.865600] Node 0 DMA32 free:9760kB min:6560kB low:8200kB high:9840kB active:1323132kB inactive:1323104kB present:3329568kB pages_scanned:3172208 all_unreclaimable? yes
Nov 16 16:52:39 server01 kernel: [977784.865606] lowmem_reserve[]: 0 0 757 757
Nov 16 16:52:39 server01 kernel: [977784.865609] Node 0 Normal free:1528kB min:1528kB low:1908kB high:2292kB active:270724kB inactive:328384kB present:775680kB pages_scanned:3189614 all_unreclaimable? yes
Nov 16 16:52:39 server01 kernel: [977784.865614] lowmem_reserve[]: 0 0 0 0
Nov 16 16:52:39 server01 kernel: [977784.865617] Node 0 HighMem free:0kB min:128kB low:128kB high:128kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
Nov 16 16:52:39 server01 kernel: [977784.865621] lowmem_reserve[]: 0 0 0 0
Nov 16 16:52:39 server01 kernel: [977784.865624] Node 0 DMA: 3*4kB 4*8kB 3*16kB 5*32kB 5*64kB 0*128kB 2*256kB 0*512kB 1*1024kB 1*2048kB 2*4096kB = 12348kB
Nov 16 16:52:39 server01 kernel: [977784.865632] Node 0 DMA32: 72*4kB 0*8kB 2*16kB 1*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 2*4096kB = 9760kB
Nov 16 16:52:39 server01 kernel: [977784.865640] Node 0 Normal: 42*4kB 2*8kB 0*16kB 6*32kB 0*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1528kB
Nov 16 16:52:39 server01 kernel: [977784.865648] Node 0 HighMem: empty
Nov 16 16:52:39 server01 kernel: [977784.865652] Swap cache: add 836969, delete 836756, find 139426/148155, race 0+60
Nov 16 16:52:39 server01 kernel: [977784.865654] Free swap  = 0kB
Nov 16 16:52:39 server01 kernel: [977784.865655] Total swap = 2955952kB
Nov 16 16:52:39 server01 kernel: [977784.865657] Free swap:            0kB
Nov 16 16:52:39 server01 kernel: [977784.890172] 1245184 pages of RAM
Nov 16 16:52:39 server01 kernel: [977784.890174] 233988 reserved pages
Nov 16 16:52:39 server01 kernel: [977784.890176] 1045543 pages shared
Nov 16 16:52:39 server01 kernel: [977784.890178] 213 pages swap cached
Nov 16 16:52:39 server01 kernel: [977784.896953] Out of Memory: Killed process 22461 (mc).
Nov 16 16:52:39 server01 kernel: [977784.908146] oom-killer: gfp_mask=0x201d2, order=0
Nov 16 16:52:39 server01 kernel: [977784.908150] Mem-info:
Nov 16 16:52:39 server01 kernel: [977784.908152] Node 0 DMA per-cpu:
Nov 16 16:52:39 server01 kernel: [977784.908155] cpu 0 hot: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.908157] cpu 0 cold: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.908160] cpu 1 hot: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.908162] cpu 1 cold: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.908164] cpu 2 hot: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.908166] cpu 2 cold: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.908168] cpu 3 hot: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.908170] cpu 3 cold: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.908172] Node 0 DMA32 per-cpu:
Nov 16 16:52:39 server01 kernel: [977784.908175] cpu 0 hot: low 0, high 186, batch 31 used:37
Nov 16 16:52:39 server01 kernel: [977784.908177] cpu 0 cold: low 0, high 62, batch 15 used:61
Nov 16 16:52:39 server01 kernel: [977784.908179] cpu 1 hot: low 0, high 186, batch 31 used:82
Nov 16 16:52:39 server01 kernel: [977784.908181] cpu 1 cold: low 0, high 62, batch 15 used:2
Nov 16 16:52:39 server01 kernel: [977784.908184] cpu 2 hot: low 0, high 186, batch 31 used:46
Nov 16 16:52:39 server01 kernel: [977784.908186] cpu 2 cold: low 0, high 62, batch 15 used:59
Nov 16 16:52:39 server01 kernel: [977784.908188] cpu 3 hot: low 0, high 186, batch 31 used:53
Nov 16 16:52:39 server01 kernel: [977784.908190] cpu 3 cold: low 0, high 62, batch 15 used:13
Nov 16 16:52:39 server01 kernel: [977784.908192] Node 0 Normal per-cpu:
Nov 16 16:52:39 server01 kernel: [977784.908195] cpu 0 hot: low 0, high 186, batch 31 used:42
Nov 16 16:52:39 server01 kernel: [977784.908197] cpu 0 cold: low 0, high 62, batch 15 used:35
Nov 16 16:52:39 server01 kernel: [977784.908202] oom-killer: gfp_mask=0x201d2, order=0
Nov 16 16:52:39 server01 kernel: [977784.908207] cpu 1 hot: low 0, high 186, batch 31 used:47
Nov 16 16:52:39 server01 kernel: [977784.908210] cpu 1 cold: low 0, high 62, batch 15 used:51
Nov 16 16:52:39 server01 kernel: [977784.908213] cpu 2 hot: low 0, high 186, batch 31 used:2
Nov 16 16:52:39 server01 kernel: [977784.908215] cpu 2 cold: low 0, high 62, batch 15 used:38
Nov 16 16:52:39 server01 kernel: [977784.908218] cpu 3 hot: low 0, high 186, batch 31 used:12
Nov 16 16:52:39 server01 kernel: [977784.908220] cpu 3 cold: low 0, high 62, batch 15 used:25
Nov 16 16:52:39 server01 kernel: [977784.908222] Node 0 HighMem per-cpu: empty
Nov 16 16:52:39 server01 kernel: [977784.908228] Mem-info:
Nov 16 16:52:39 server01 kernel: [977784.908231] Free pages:       23636kB (0kB HighMem)
Nov 16 16:52:39 server01 kernel: [977784.908235] Active:424365 inactive:387001 dirty:0 writeback:1727 unstable:0 free:5909 slab:61879 mapped:811617 pagetables:56272
Nov 16 16:52:39 server01 kernel: [977784.908237] Node 0 DMA free:12348kB min:20kB low:24kB high:28kB active:0kB inactive:0kB present:11992kB pages_scanned:26442 all_unreclaimable? yes
Nov 16 16:52:39 server01 kernel: [977784.908243] lowmem_reserve[]: 0 3251 4009 4009
Nov 16 16:52:39 server01 kernel: [977784.908249] Node 0 DMA32 free:9760kB min:6560kB low:8200kB high:9840kB active:1426736kB inactive:1219620kB present:3329568kB pages_scanned:3240097 all_unreclaimable? yes
Nov 16 16:52:39 server01 kernel: [977784.908255] lowmem_reserve[]: 0 0 757 757
Nov 16 16:52:39 server01 kernel: [977784.908261] Node 0 Normal free:1528kB min:1528kB low:1908kB high:2292kB active:270724kB inactive:328384kB present:775680kB pages_scanned:3189818 all_unreclaimable? yes
Nov 16 16:52:39 server01 kernel: [977784.908267] lowmem_reserve[]: 0 0 0 0
Nov 16 16:52:39 server01 kernel: [977784.908272] Node 0 HighMem free:0kB min:128kB low:128kB high:128kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
Nov 16 16:52:39 server01 kernel: [977784.908277] lowmem_reserve[]: 0 0 0 0
Nov 16 16:52:39 server01 kernel: [977784.908282] Node 0 DMA: 3*4kB 4*8kB 3*16kB 5*32kB 5*64kB 0*128kB 2*256kB 0*512kB 1*1024kB 1*2048kB 2*4096kB = 12348kB
Nov 16 16:52:39 server01 kernel: [977784.908299] Node 0 DMA32: 72*4kB 0*8kB 2*16kB 1*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 2*4096kB = 9760kB
Nov 16 16:52:39 server01 kernel: [977784.908315] Node 0 Normal: 42*4kB 2*8kB 0*16kB 6*32kB 0*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1528kB
Nov 16 16:52:39 server01 kernel: [977784.908330] Node 0 HighMem: empty
Nov 16 16:52:39 server01 kernel: [977784.908335] Swap cache: add 838703, delete 836758, find 139426/148155, race 0+60
Nov 16 16:52:39 server01 kernel: [977784.908339] Free swap  = 134948kB
Nov 16 16:52:39 server01 kernel: [977784.908341] Total swap = 2955952kB
Nov 16 16:52:39 server01 kernel: [977784.908344] Free swap:       135032kB
Nov 16 16:52:39 server01 kernel: [977784.908347] Node 0 DMA per-cpu:
Nov 16 16:52:39 server01 kernel: [977784.908351] cpu 0 hot: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.908353] cpu 0 cold: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.908356] cpu 1 hot: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.908358] cpu 1 cold: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.908360] cpu 2 hot: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.908362] cpu 2 cold: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.908365] cpu 3 hot: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.908367] cpu 3 cold: low 0, high 0, batch 1 used:0
Nov 16 16:52:39 server01 kernel: [977784.908369] Node 0 DMA32 per-cpu:
Nov 16 16:52:39 server01 kernel: [977784.908371] cpu 0 hot: low 0, high 186, batch 31 used:37
Nov 16 16:52:39 server01 kernel: [977784.908374] cpu 0 cold: low 0, high 62, batch 15 used:61
Nov 16 16:52:39 server01 kernel: [977784.908376] cpu 1 hot: low 0, high 186, batch 31 used:82
Nov 16 16:52:39 server01 kernel: [977784.908378] cpu 1 cold: low 0, high 62, batch 15 used:2
Nov 16 16:52:39 server01 kernel: [977784.908380] cpu 2 hot: low 0, high 186, batch 31 used:46
Nov 16 16:52:39 server01 kernel: [977784.908383] cpu 2 cold: low 0, high 62, batch 15 used:59
Nov 16 16:52:39 server01 kernel: [977784.908385] cpu 3 hot: low 0, high 186, batch 31 used:53
Nov 16 16:52:39 server01 kernel: [977784.908387] cpu 3 cold: low 0, high 62, batch 15 used:13
Nov 16 16:52:39 server01 kernel: [977784.908389] Node 0 Normal per-cpu:
Nov 16 16:52:39 server01 kernel: [977784.908392] cpu 0 hot: low 0, high 186, batch 31 used:42
Nov 16 16:52:39 server01 kernel: [977784.908394] cpu 0 cold: low 0, high 62, batch 15 used:35
Nov 16 16:52:39 server01 kernel: [977784.908396] cpu 1 hot: low 0, high 186, batch 31 used:47
Nov 16 16:52:39 server01 kernel: [977784.908398] cpu 1 cold: low 0, high 62, batch 15 used:51
Nov 16 16:52:39 server01 kernel: [977784.908401] cpu 2 hot: low 0, high 186, batch 31 used:2
Nov 16 16:52:39 server01 kernel: [977784.908403] cpu 2 cold: low 0, high 62, batch 15 used:38
Nov 16 16:52:39 server01 kernel: [977784.908405] cpu 3 hot: low 0, high 186, batch 31 used:12
Nov 16 16:52:39 server01 kernel: [977784.908407] cpu 3 cold: low 0, high 62, batch 15 used:25
Nov 16 16:52:39 server01 kernel: [977784.908409] Node 0 HighMem per-cpu: empty
Nov 16 16:52:39 server01 kernel: [977784.908414] Free pages:       23636kB (0kB HighMem)
Nov 16 16:52:39 server01 kernel: [977784.908417] Active:424365 inactive:387001 dirty:0 writeback:1729 unstable:0 free:5909 slab:61879 mapped:811615 pagetables:56272
Nov 16 16:52:39 server01 kernel: [977784.908420] Node 0 DMA free:12348kB min:20kB low:24kB high:28kB active:0kB inactive:0kB present:11992kB pages_scanned:26442 all_unreclaimable? yes
Nov 16 16:52:39 server01 kernel: [977784.908425] lowmem_reserve[]: 0 3251 4009 4009
Nov 16 16:52:39 server01 kernel: [977784.908428] Node 0 DMA32 free:9760kB min:6560kB low:8200kB high:9840kB active:1426736kB inactive:1219620kB present:3329568kB pages_scanned:3240097 all_unreclaimable? yes
Nov 16 16:52:39 server01 kernel: [977784.908434] lowmem_reserve[]: 0 0 757 757
Nov 16 16:52:39 server01 kernel: [977784.908437] Node 0 Normal free:1528kB min:1528kB low:1908kB high:2292kB active:270724kB inactive:328384kB present:775680kB pages_scanned:3189818 all_unreclaimable? yes
Nov 16 16:52:39 server01 kernel: [977784.908442] lowmem_reserve[]: 0 0 0 0
Nov 16 16:52:39 server01 kernel: [977784.908445] Node 0 HighMem free:0kB min:128kB low:128kB high:128kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
Nov 16 16:52:39 server01 kernel: [977784.908449] lowmem_reserve[]: 0 0 0 0
Nov 16 16:52:39 server01 kernel: [977784.908452] Node 0 DMA: 3*4kB 4*8kB 3*16kB 5*32kB 5*64kB 0*128kB 2*256kB 0*512kB 1*1024kB 1*2048kB 2*4096kB = 12348kB
Nov 16 16:52:39 server01 kernel: [977784.908460] Node 0 DMA32: 72*4kB 0*8kB 2*16kB 1*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 2*4096kB = 9760kB
Nov 16 16:52:39 server01 kernel: [977784.908468] Node 0 Normal: 42*4kB 2*8kB 0*16kB 6*32kB 0*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1528kB
Nov 16 16:52:39 server01 kernel: [977784.908476] Node 0 HighMem: empty
Nov 16 16:52:39 server01 kernel: [977784.908480] Swap cache: add 838704, delete 836758, find 139426/148155, race 0+60
Nov 16 16:52:39 server01 kernel: [977784.908482] Free swap  = 136280kB
Nov 16 16:52:39 server01 kernel: [977784.908483] Total swap = 2955952kB
Nov 16 16:52:39 server01 kernel: [977784.908485] Free swap:       136308kB
Nov 16 16:52:39 server01 kernel: [977784.944638] 1245184 pages of RAM
Nov 16 16:52:39 server01 kernel: [977784.944640] 233988 reserved pages
Nov 16 16:52:39 server01 kernel: [977784.944642] 1045199 pages shared
Nov 16 16:52:39 server01 kernel: [977784.944644] 1895 pages swap cached
Nov 16 16:52:39 server01 kernel: [977784.945229] 1245184 pages of RAM
Nov 16 16:52:39 server01 kernel: [977784.945231] 233988 reserved pages
Nov 16 16:52:39 server01 kernel: [977784.945233] 1045180 pages shared
Nov 16 16:52:39 server01 kernel: [977784.945234] 1910 pages swap cached
Nov 16 16:52:39 server01 kernel: [977784.951850] Out of Memory: Killed process 4157 (apache2).
Nov 16 16:52:39 server01 kernel: [977784.958954] Out of Memory: Killed process 4157 (apache2).
Nov 16 16:52:56 server01 kernel: [977805.454397] Shorewall:wan2all:DROP:IN=ppp0 OUT= MAC= SRC=60.190.49.244 DST=86.47.224.128 LEN=404 TOS=0x00 PREC=0x00 TTL=112 ID=26532 PROTO=UDP SPT=34924 DPT=1434 LEN=384 
Nov 16 16:53:20 server01 kernel: [977829.448978] Shorewall:wan2all:DROP:IN=ppp0 OUT= MAC= SRC=87.230.73.19 DST=86.47.224.128 LEN=48 TOS=0x00 PREC=0x00 TTL=121 ID=5945 DF PROTO=TCP SPT=18358 DPT=5938 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov 16 16:53:20 server01 kernel: [977829.451888] Shorewall:wan2all:DROP:IN=ppp0 OUT= MAC= SRC=87.230.73.19 DST=86.47.224.128 LEN=48 TOS=0x00 PREC=0x00 TTL=121 ID=5964 DF PROTO=TCP SPT=18358 DPT=5938 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov 16 16:53:23 server01 kernel: [977832.379178] Shorewall:wan2all:DROP:IN=ppp0 OUT= MAC= SRC=87.230.73.19 DST=86.47.224.128 LEN=48 TOS=0x00 PREC=0x00 TTL=121 ID=27638 DF PROTO=TCP SPT=18358 DPT=5938 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov 16 16:56:24 server01 kernel: [978012.687482] oom-killer: gfp_mask=0x201d2, order=0
Nov 16 16:56:27 server01 kernel: [978012.687488] Mem-info:
Nov 16 16:56:27 server01 kernel: [978012.687489] Node 0 DMA per-cpu:
Nov 16 16:56:27 server01 kernel: [978012.687493] cpu 0 hot: low 0, high 0, batch 1 used:0
Nov 16 16:56:27 server01 kernel: [978012.687495] cpu 0 cold: low 0, high 0, batch 1 used:0
Nov 16 16:56:27 server01 kernel: [978012.687498] cpu 1 hot: low 0, high 0, batch 1 used:0
Nov 16 16:56:27 server01 kernel: [978012.687500] cpu 1 cold: low 0, high 0, batch 1 used:0
Nov 16 16:56:27 server01 kernel: [978012.687502] cpu 2 hot: low 0, high 0, batch 1 used:0
Nov 16 16:56:27 server01 kernel: [978012.687504] cpu 2 cold: low 0, high 0, batch 1 used:0
Nov 16 16:56:27 server01 kernel: [978012.687506] cpu 3 hot: low 0, high 0, batch 1 used:0
Nov 16 16:56:27 server01 kernel: [978012.687508] cpu 3 cold: low 0, high 0, batch 1 used:0
Nov 16 16:56:27 server01 kernel: [978012.687510] Node 0 DMA32 per-cpu:
Nov 16 16:56:27 server01 kernel: [978012.687513] cpu 0 hot: low 0, high 186, batch 31 used:19
Nov 16 16:56:27 server01 kernel: [978012.687515] cpu 0 cold: low 0, high 62, batch 15 used:17
Nov 16 16:56:27 server01 kernel: [978012.687518] cpu 1 hot: low 0, high 186, batch 31 used:86
Nov 16 16:56:27 server01 kernel: [978012.687520] cpu 1 cold: low 0, high 62, batch 15 used:52
Nov 16 16:56:27 server01 kernel: [978012.687522] cpu 2 hot: low 0, high 186, batch 31 used:18
Nov 16 16:56:27 server01 kernel: [978012.687524] cpu 2 cold: low 0, high 62, batch 15 used:59
Nov 16 16:56:27 server01 kernel: [978012.687527] cpu 3 hot: low 0, high 186, batch 31 used:37
Nov 16 16:56:27 server01 kernel: [978012.687529] cpu 3 cold: low 0, high 62, batch 15 used:40
Nov 16 16:56:27 server01 kernel: [978012.687530] Node 0 Normal per-cpu:
Nov 16 16:56:27 server01 kernel: [978012.687533] cpu 0 hot: low 0, high 186, batch 31 used:32
Nov 16 16:56:27 server01 kernel: [978012.687535] cpu 0 cold: low 0, high 62, batch 15 used:7
Nov 16 16:56:27 server01 kernel: [978012.687538] cpu 1 hot: low 0, high 186, batch 31 used:98
Nov 16 16:56:27 server01 kernel: [978012.687540] cpu 1 cold: low 0, high 62, batch 15 used:26
Nov 16 16:56:27 server01 kernel: [978012.687543] cpu 2 hot: low 0, high 186, batch 31 used:39
Nov 16 16:56:27 server01 kernel: [978012.687545] cpu 2 cold: low 0, high 62, batch 15 used:60
Nov 16 16:56:27 server01 kernel: [978012.687547] cpu 3 hot: low 0, high 186, batch 31 used:33
Nov 16 16:56:27 server01 kernel: [978012.687549] cpu 3 cold: low 0, high 62, batch 15 used:50
Nov 16 16:56:27 server01 kernel: [978012.687551] Node 0 HighMem per-cpu: empty
Nov 16 16:56:27 server01 kernel: [978012.687556] Free pages:       23276kB (0kB HighMem)
Nov 16 16:56:28 server01 kernel: [978012.687559] Active:382887 inactive:400060 dirty:0 writeback:0 unstable:0 free:5819 slab:70659 mapped:784761 pagetables:64696
Nov 16 16:56:28 server01 kernel: [978012.687562] Node 0 DMA free:12348kB min:20kB low:24kB high:28kB active:0kB inactive:0kB present:11992kB pages_scanned:27024 all_unreclaimable? yes
Nov 16 16:56:28 server01 kernel: [978012.687566] lowmem_reserve[]: 0 3251 4009 4009
Nov 16 16:56:28 server01 kernel: [978012.687570] Node 0 DMA32 free:9560kB min:6560kB low:8200kB high:9840kB active:1279620kB inactive:1278812kB present:3329568kB pages_scanned:3796028 all_unreclaimable? yes
Nov 16 16:56:28 server01 kernel: [978012.687575] lowmem_reserve[]: 0 0 757 757
Nov 16 16:56:28 server01 kernel: [978012.687578] Node 0 Normal free:1368kB min:1528kB low:1908kB high:2292kB active:252056kB inactive:321316kB present:775680kB pages_scanned:1514880 all_unreclaimable? yes
Nov 16 16:56:28 server01 kernel: [978012.687584] lowmem_reserve[]: 0 0 0 0
Nov 16 16:56:28 server01 kernel: [978012.687586] Node 0 HighMem free:0kB min:128kB low:128kB high:128kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
Nov 16 16:56:28 server01 kernel: [978012.687591] lowmem_reserve[]: 0 0 0 0
Nov 16 16:56:28 server01 kernel: [978012.687593] Node 0 DMA: 3*4kB 4*8kB 3*16kB 5*32kB 5*64kB 0*128kB 2*256kB 0*512kB 1*1024kB 1*2048kB 2*4096kB = 12348kB
Nov 16 16:56:28 server01 kernel: [978012.687602] Node 0 DMA32: 124*4kB 19*8kB 1*16kB 0*32kB 1*64kB 1*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 2*4096kB = 9560kB
Nov 16 16:56:28 server01 kernel: [978012.687610] Node 0 Normal: 16*4kB 37*8kB 3*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1368kB
Nov 16 16:56:28 server01 kernel: [978012.687618] Node 0 HighMem: empty
Nov 16 16:56:28 server01 kernel: [978012.687621] Swap cache: add 1214015, delete 1213799, find 290121/311000, race 0+156
Nov 16 16:56:28 server01 kernel: [978012.687623] Free swap  = 0kB
Nov 16 16:56:28 server01 kernel: [978012.687625] Total swap = 2955952kB
Nov 16 16:56:28 server01 kernel: [978012.687627] Free swap:            0kB
Nov 16 16:56:28 server01 kernel: [978012.712919] 1245184 pages of RAM
Nov 16 16:56:28 server01 kernel: [978012.712922] 233988 reserved pages
Nov 16 16:56:28 server01 kernel: [978012.712924] 1206994 pages shared
Nov 16 16:56:28 server01 kernel: [978012.712925] 216 pages swap cached
Nov 16 16:56:28 server01 kernel: [978012.720971] Out of Memory: Killed process 14731 (mysqld).
Nov 16 16:56:28 server01 kernel: [978012.723290] oom-killer: gfp_mask=0x201d2, order=0
Nov 16 16:56:28 server01 kernel: [978012.723293] Mem-info:
Nov 16 16:56:28 server01 kernel: [978012.723295] Node 0 DMA per-cpu:
Nov 16 16:56:28 server01 kernel: [978012.723298] cpu 0 hot: low 0, high 0, batch 1 used:0
Nov 16 16:56:28 server01 kernel: [978012.723300] cpu 0 cold: low 0, high 0, batch 1 used:0
Nov 16 16:56:28 server01 kernel: [978012.723303] cpu 1 hot: low 0, high 0, batch 1 used:0
Nov 16 16:56:28 server01 kernel: [978012.723305] cpu 1 cold: low 0, high 0, batch 1 used:0
Nov 16 16:56:28 server01 kernel: [978012.723307] cpu 2 hot: low 0, high 0, batch 1 used:0
Nov 16 16:56:28 server01 kernel: [978012.723309] cpu 2 cold: low 0, high 0, batch 1 used:0
Nov 16 16:56:28 server01 kernel: [978012.723311] cpu 3 hot: low 0, high 0, batch 1 used:0
Nov 16 16:56:28 server01 kernel: [978012.723313] cpu 3 cold: low 0, high 0, batch 1 used:0
Nov 16 16:56:28 server01 kernel: [978012.723315] Node 0 DMA32 per-cpu:
Nov 16 16:56:28 server01 kernel: [978012.723318] cpu 0 hot: low 0, high 186, batch 31 used:19
Nov 16 16:56:28 server01 kernel: [978012.723320] cpu 0 cold: low 0, high 62, batch 15 used:17
Nov 16 16:56:28 server01 kernel: [978012.723322] cpu 1 hot: low 0, high 186, batch 31 used:86
Nov 16 16:56:28 server01 kernel: [978012.723325] cpu 1 cold: low 0, high 62, batch 15 used:52
Nov 16 16:56:28 server01 kernel: [978012.723327] cpu 2 hot: low 0, high 186, batch 31 used:18
Nov 16 16:56:28 server01 kernel: [978012.723329] cpu 2 cold: low 0, high 62, batch 15 used:59
Nov 16 16:56:28 server01 kernel: [978012.723331] cpu 3 hot: low 0, high 186, batch 31 used:37
Nov 16 16:56:28 server01 kernel: [978012.723334] cpu 3 cold: low 0, high 62, batch 15 used:40
Nov 16 16:56:28 server01 kernel: [978012.723335] Node 0 Normal per-cpu:
Nov 16 16:56:28 server01 kernel: [978012.723338] cpu 0 hot: low 0, high 186, batch 31 used:32
Nov 16 16:56:28 server01 kernel: [978012.723340] cpu 0 cold: low 0, high 62, batch 15 used:7
Nov 16 16:56:28 server01 kernel: [978012.723342] cpu 1 hot: low 0, high 186, batch 31 used:98
Nov 16 16:56:28 server01 kernel: [978012.723345] cpu 1 cold: low 0, high 62, batch 15 used:26
Nov 16 16:56:28 server01 kernel: [978012.723347] cpu 2 hot: low 0, high 186, batch 31 used:39
Nov 16 16:56:28 server01 kernel: [978012.723349] cpu 2 cold: low 0, high 62, batch 15 used:60
Nov 16 16:56:28 server01 kernel: [978012.723352] cpu 3 hot: low 0, high 186, batch 31 used:33
Nov 16 16:56:28 server01 kernel: [978012.723354] cpu 3 cold: low 0, high 62, batch 15 used:50
Nov 16 16:56:28 server01 kernel: [978012.723355] Node 0 HighMem per-cpu: empty
Nov 16 16:56:28 server01 kernel: [978012.723359] Free pages:       23276kB (0kB HighMem)
Nov 16 16:56:28 server01 kernel: [978012.723363] Active:403897 inactive:379054 dirty:0 writeback:0 unstable:0 free:5819 slab:70659 mapped:784761 pagetables:64696
Nov 16 16:56:28 server01 kernel: [978012.723365] Node 0 DMA free:12348kB min:20kB low:24kB high:28kB active:0kB inactive:0kB present:11992kB pages_scanned:27024 all_unreclaimable? yes
Nov 16 16:56:28 server01 kernel: [978012.723370] lowmem_reserve[]: 0 3251 4009 4009
Nov 16 16:56:28 server01 kernel: [978012.723373] Node 0 DMA32 free:9560kB min:6560kB low:8200kB high:9840kB active:1363276kB inactive:1195028kB present:3329568kB pages_scanned:3862548 all_unreclaimable? yes
Nov 16 16:56:28 server01 kernel: [978012.723379] lowmem_reserve[]: 0 0 757 757
Nov 16 16:56:28 server01 kernel: [978012.723382] Node 0 Normal free:1368kB min:1528kB low:1908kB high:2292kB active:252312kB inactive:321060kB present:775680kB pages_scanned:1514979 all_unreclaimable? yes
Nov 16 16:56:28 server01 kernel: [978012.723387] lowmem_reserve[]: 0 0 0 0
Nov 16 16:56:28 server01 kernel: [978012.723389] Node 0 HighMem free:0kB min:128kB low:128kB high:128kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
Nov 16 16:56:28 server01 kernel: [978012.723394] lowmem_reserve[]: 0 0 0 0
Nov 16 16:56:28 server01 kernel: [978012.723396] Node 0 DMA: 3*4kB 4*8kB 3*16kB 5*32kB 5*64kB 0*128kB 2*256kB 0*512kB 1*1024kB 1*2048kB 2*4096kB = 12348kB
Nov 16 16:56:28 server01 kernel: [978012.723405] Node 0 DMA32: 124*4kB 19*8kB 1*16kB 0*32kB 1*64kB 1*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 2*4096kB = 9560kB
Nov 16 16:56:28 server01 kernel: [978012.723413] Node 0 Normal: 16*4kB 37*8kB 3*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1368kB
Nov 16 16:56:28 server01 kernel: [978012.723420] Node 0 HighMem: empty
Nov 16 16:56:28 server01 kernel: [978012.723424] Swap cache: add 1214015, delete 1213799, find 290121/311000, race 0+156
Nov 16 16:56:28 server01 kernel: [978012.723454] Free swap  = 0kB
Nov 16 16:56:28 server01 kernel: [978012.723456] Total swap = 2955952kB
Nov 16 16:56:28 server01 kernel: [978012.723458] Free swap:            0kB
Nov 16 16:56:28 server01 kernel: [978012.749301] 1245184 pages of RAM
Nov 16 16:56:28 server01 kernel: [978012.749305] 233988 reserved pages
Nov 16 16:56:28 server01 kernel: [978012.749307] 1207000 pages shared
Nov 16 16:56:28 server01 kernel: [978012.749308] 216 pages swap cached
Nov 16 16:56:28 server01 kernel: [978012.757407] Out of Memory: Killed process 28386 (apache2).
Nov 16 17:00:40 server01 kernel: [978269.272664] oom-killer: gfp_mask=0x201d2, order=0
Nov 16 17:00:40 server01 kernel: [978269.272671] Mem-info:
Nov 16 17:00:40 server01 kernel: [978269.272672] Node 0 DMA per-cpu:
Nov 16 17:00:40 server01 kernel: [978269.272679] cpu 0 hot: low 0, high 0, batch 1 used:0
Nov 16 17:00:40 server01 kernel: [978269.272681] cpu 0 cold: low 0, high 0, batch 1 used:0
Nov 16 17:00:40 server01 kernel: [978269.272684] cpu 1 hot: low 0, high 0, batch 1 used:0
Nov 16 17:00:40 server01 kernel: [978269.272686] cpu 1 cold: low 0, high 0, batch 1 used:0
Nov 16 17:00:40 server01 kernel: [978269.272688] cpu 2 hot: low 0, high 0, batch 1 used:0
Nov 16 17:00:40 server01 kernel: [978269.272690] cpu 2 cold: low 0, high 0, batch 1 used:0
Nov 16 17:00:40 server01 kernel: [978269.272693] cpu 3 hot: low 0, high 0, batch 1 used:0
Nov 16 17:00:40 server01 kernel: [978269.272695] cpu 3 cold: low 0, high 0, batch 1 used:0
Nov 16 17:00:40 server01 kernel: [978269.272697] Node 0 DMA32 per-cpu:
Nov 16 17:00:40 server01 kernel: [978269.272700] cpu 0 hot: low 0, high 186, batch 31 used:16
Nov 16 17:00:40 server01 kernel: [978269.272702] cpu 0 cold: low 0, high 62, batch 15 used:60
Nov 16 17:00:40 server01 kernel: [978269.272704] cpu 1 hot: low 0, high 186, batch 31 used:137
Nov 16 17:00:40 server01 kernel: [978269.272707] cpu 1 cold: low 0, high 62, batch 15 used:55
Nov 16 17:00:40 server01 kernel: [978269.272709] cpu 2 hot: low 0, high 186, batch 31 used:174
Nov 16 17:00:40 server01 kernel: [978269.272711] cpu 2 cold: low 0, high 62, batch 15 used:24
Nov 16 17:00:40 server01 kernel: [978269.272714] cpu 3 hot: low 0, high 186, batch 31 used:156
Nov 16 17:00:40 server01 kernel: [978269.272716] cpu 3 cold: low 0, high 62, batch 15 used:44
Nov 16 17:00:40 server01 kernel: [978269.272718] Node 0 Normal per-cpu:
Nov 16 17:00:40 server01 kernel: [978269.272720] cpu 0 hot: low 0, high 186, batch 31 used:21
Nov 16 17:00:40 server01 kernel: [978269.272723] cpu 0 cold: low 0, high 62, batch 15 used:43
Nov 16 17:00:40 server01 kernel: [978269.272725] cpu 1 hot: low 0, high 186, batch 31 used:157
Nov 16 17:00:40 server01 kernel: [978269.272727] cpu 1 cold: low 0, high 62, batch 15 used:45
Nov 16 17:00:40 server01 kernel: [978269.272730] cpu 2 hot: low 0, high 186, batch 31 used:181
Nov 16 17:00:40 server01 kernel: [978269.272732] cpu 2 cold: low 0, high 62, batch 15 used:57
Nov 16 17:00:40 server01 kernel: [978269.272734] cpu 3 hot: low 0, high 186, batch 31 used:175
Nov 16 17:00:40 server01 kernel: [978269.272737] cpu 3 cold: low 0, high 62, batch 15 used:48
Nov 16 17:00:40 server01 kernel: [978269.272738] Node 0 HighMem per-cpu: empty
Nov 16 17:00:40 server01 kernel: [978269.272742] Free pages:       23612kB (0kB HighMem)
Nov 16 17:00:40 server01 kernel: [978269.272746] Active:366639 inactive:413882 dirty:0 writeback:0 unstable:0 free:5903 slab:70927 mapped:782433 pagetables:65182
Nov 16 17:00:40 server01 kernel: [978269.272748] Node 0 DMA free:12348kB min:20kB low:24kB high:28kB active:0kB inactive:0kB present:11992kB pages_scanned:27232 all_unreclaimable? yes
Nov 16 17:00:40 server01 kernel: [978269.272753] lowmem_reserve[]: 0 3251 4009 4009
Nov 16 17:00:40 server01 kernel: [978269.272756] Node 0 DMA32 free:9792kB min:6560kB low:8200kB high:9840kB active:1268196kB inactive:1283148kB present:3329568kB pages_scanned:3161074 all_unreclaimable? yes
Nov 16 17:00:40 server01 kernel: [978269.272762] lowmem_reserve[]: 0 0 757 757
Nov 16 17:00:40 server01 kernel: [978269.272765] Node 0 Normal free:1472kB min:1528kB low:1908kB high:2292kB active:198360kB inactive:372380kB present:775680kB pages_scanned:748022 all_unreclaimable? yes
Nov 16 17:00:40 server01 kernel: [978269.272770] lowmem_reserve[]: 0 0 0 0
Nov 16 17:00:40 server01 kernel: [978269.272773] Node 0 HighMem free:0kB min:128kB low:128kB high:128kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
Nov 16 17:00:40 server01 kernel: [978269.272777] lowmem_reserve[]: 0 0 0 0
Nov 16 17:00:40 server01 kernel: [978269.272780] Node 0 DMA: 3*4kB 4*8kB 3*16kB 5*32kB 5*64kB 0*128kB 2*256kB 0*512kB 1*1024kB 1*2048kB 2*4096kB = 12348kB
Nov 16 17:00:40 server01 kernel: [978269.272788] Node 0 DMA32: 88*4kB 18*8kB 25*16kB 0*32kB 1*64kB 1*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 2*4096kB = 9792kB
Nov 16 17:00:40 server01 kernel: [978269.272796] Node 0 Normal: 28*4kB 36*8kB 7*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1472kB
Nov 16 17:00:40 server01 kernel: [978269.272804] Node 0 HighMem: empty
Nov 16 17:00:40 server01 kernel: [978269.272808] Swap cache: add 1278651, delete 1278439, find 382269/408837, race 2+225
Nov 16 17:00:40 server01 kernel: [978269.272810] Free swap  = 0kB
Nov 16 17:00:40 server01 kernel: [978269.272812] Total swap = 2955952kB
Nov 16 17:00:40 server01 kernel: [978269.272813] Free swap:            0kB
Nov 16 17:00:40 server01 kernel: [978269.298454] 1245184 pages of RAM
Nov 16 17:00:40 server01 kernel: [978269.298458] 233988 reserved pages
Nov 16 17:00:40 server01 kernel: [978269.298460] 1215588 pages shared
Nov 16 17:00:40 server01 kernel: [978269.298461] 212 pages swap cached
Nov 16 17:00:40 server01 kernel: [978269.306868] Out of Memory: Killed process 4292 (apache2).
Nov 16 17:03:10 server01 kernel: [978419.093953] oom-killer: gfp_mask=0xd0, order=0
Nov 16 17:03:20 server01 kernel: [978419.093960] Mem-info:
Nov 16 17:03:20 server01 kernel: [978419.093962] Node 0 DMA per-cpu:
Nov 16 17:03:20 server01 kernel: [978419.093966] cpu 0 hot: low 0, high 0, batch 1 used:0
Nov 16 17:03:20 server01 kernel: [978419.093970] cpu 0 cold: low 0, high 0, batch 1 used:0
Nov 16 17:03:20 server01 kernel: [978419.093973] cpu 1 hot: low 0, high 0, batch 1 used:0
Nov 16 17:03:20 server01 kernel: [978419.093975] cpu 1 cold: low 0, high 0, batch 1 used:0
Nov 16 17:03:20 server01 kernel: [978419.093977] cpu 2 hot: low 0, high 0, batch 1 used:0
Nov 16 17:03:20 server01 kernel: [978419.093979] cpu 2 cold: low 0, high 0, batch 1 used:0
Nov 16 17:03:20 server01 kernel: [978419.093982] cpu 3 hot: low 0, high 0, batch 1 used:0
Nov 16 17:03:20 server01 kernel: [978419.093984] cpu 3 cold: low 0, high 0, batch 1 used:0
Nov 16 17:03:20 server01 kernel: [978419.093985] Node 0 DMA32 per-cpu:
Nov 16 17:03:20 server01 kernel: [978419.093988] cpu 0 hot: low 0, high 186, batch 31 used:29
Nov 16 17:03:20 server01 kernel: [978419.093990] cpu 0 cold: low 0, high 62, batch 15 used:36
Nov 16 17:03:20 server01 kernel: [978419.093994] cpu 1 hot: low 0, high 186, batch 31 used:155
Nov 16 17:03:20 server01 kernel: [978419.093996] cpu 1 cold: low 0, high 62, batch 15 used:18
Nov 16 17:03:20 server01 kernel: [978419.093999] cpu 2 hot: low 0, high 186, batch 31 used:32
Nov 16 17:03:20 server01 kernel: [978419.094001] cpu 2 cold: low 0, high 62, batch 15 used:54
Nov 16 17:03:20 server01 kernel: [978419.094003] cpu 3 hot: low 0, high 186, batch 31 used:21
Nov 16 17:03:20 server01 kernel: [978419.094006] cpu 3 cold: low 0, high 62, batch 15 used:28
Nov 16 17:03:20 server01 kernel: [978419.094007] Node 0 Normal per-cpu:
Nov 16 17:03:20 server01 kernel: [978419.094011] cpu 0 hot: low 0, high 186, batch 31 used:13
Nov 16 17:03:20 server01 kernel: [978419.094013] cpu 0 cold: low 0, high 62, batch 15 used:16
Nov 16 17:03:20 server01 kernel: [978419.094015] cpu 1 hot: low 0, high 186, batch 31 used:178
Nov 16 17:03:20 server01 kernel: [978419.094018] cpu 1 cold: low 0, high 62, batch 15 used:61
Nov 16 17:03:20 server01 kernel: [978419.094020] cpu 2 hot: low 0, high 186, batch 31 used:85
Nov 16 17:03:20 server01 kernel: [978419.094022] cpu 2 cold: low 0, high 62, batch 15 used:58
Nov 16 17:03:20 server01 kernel: [978419.094024] cpu 3 hot: low 0, high 186, batch 31 used:28
Nov 16 17:03:20 server01 kernel: [978419.094027] cpu 3 cold: low 0, high 62, batch 15 used:39
Nov 16 17:03:20 server01 kernel: [978419.094028] Node 0 HighMem per-cpu: empty
Nov 16 17:03:20 server01 kernel: [978419.094033] Free pages:       23308kB (0kB HighMem)
Nov 16 17:03:20 server01 kernel: [978419.094036] Active:425622 inactive:355431 dirty:0 writeback:0 unstable:0 free:5827 slab:70750 mapped:783493 pagetables:65031
Nov 16 17:03:20 server01 kernel: [978419.094039] Node 0 DMA free:12348kB min:20kB low:24kB high:28kB active:0kB inactive:0kB present:11992kB pages_scanned:27276 all_unreclaimable? yes
Nov 16 17:03:20 server01 kernel: [978419.094043] lowmem_reserve[]: 0 3251 4009 4009
Nov 16 17:03:20 server01 kernel: [978419.094047] Node 0 DMA32 free:9704kB min:6560kB low:8200kB high:9840kB active:1275000kB inactive:1276588kB present:3329568kB pages_scanned:4353183 all_unreclaimable? yes
Nov 16 17:03:20 server01 kernel: [978419.094053] lowmem_reserve[]: 0 0 757 757
Nov 16 17:03:20 server01 kernel: [978419.094056] Node 0 Normal free:1256kB min:1528kB low:1908kB high:2292kB active:427616kB inactive:145008kB present:775680kB pages_scanned:14186909 all_unreclaimable? yes
Nov 16 17:03:20 server01 kernel: [978419.094061] lowmem_reserve[]: 0 0 0 0
Nov 16 17:03:20 server01 kernel: [978419.094064] Node 0 HighMem free:0kB min:128kB low:128kB high:128kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
Nov 16 17:03:20 server01 kernel: [978419.094068] lowmem_reserve[]: 0 0 0 0
Nov 16 17:03:20 server01 kernel: [978419.094071] Node 0 DMA: 3*4kB 4*8kB 3*16kB 5*32kB 5*64kB 0*128kB 2*256kB 0*512kB 1*1024kB 1*2048kB 2*4096kB = 12348kB
Nov 16 17:03:20 server01 kernel: [978419.094079] Node 0 DMA32: 64*4kB 15*8kB 27*16kB 0*32kB 1*64kB 1*128kB 0*256kB 1*512kB 0*1024kB 0*2048kB 2*4096kB = 9704kB
Nov 16 17:03:20 server01 kernel: [978419.094087] Node 0 Normal: 0*4kB 21*8kB 8*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1256kB
Nov 16 17:03:20 server01 kernel: [978419.094095] Node 0 HighMem: empty
Nov 16 17:03:20 server01 kernel: [978419.094099] Swap cache: add 1290683, delete 1290448, find 392847/420583, race 2+230
Nov 16 17:03:20 server01 kernel: [978419.094101] Free swap  = 0kB
Nov 16 17:03:20 server01 kernel: [978419.094102] Total swap = 2955952kB
Nov 16 17:03:20 server01 kernel: [978419.094104] Free swap:            0kB
Nov 16 17:03:20 server01 kernel: [978419.119709] 1245184 pages of RAM
Nov 16 17:03:20 server01 kernel: [978419.119714] 233988 reserved pages
Nov 16 17:03:20 server01 kernel: [978419.119715] 1215099 pages shared
Nov 16 17:03:20 server01 kernel: [978419.119717] 235 pages swap cached
Nov 16 17:03:20 server01 kernel: [978419.128187] Out of Memory: Killed process 6962 (apache2).
Nov 16 17:06:45 server01 kernel: [978626.300800] oom-killer: gfp_mask=0x200d2, order=0
Nov 16 17:06:46 server01 kernel: [978626.300806] Mem-info:
Nov 16 17:06:47 server01 kernel: [978626.300808] Node 0 DMA per-cpu:
Nov 16 17:06:47 server01 kernel: [978626.300811] cpu 0 hot: low 0, high 0, batch 1 used:0
Nov 16 17:06:47 server01 kernel: [978626.300813] cpu 0 cold: low 0, high 0, batch 1 used:0
Nov 16 17:06:47 server01 kernel: [978626.300815] cpu 1 hot: low 0, high 0, batch 1 used:0
Nov 16 17:06:47 server01 kernel: [978626.300818] cpu 1 cold: low 0, high 0, batch 1 used:0
Nov 16 17:06:47 server01 kernel: [978626.300820] cpu 2 hot: low 0, high 0, batch 1 used:0
Nov 16 17:06:47 server01 kernel: [978626.300822] cpu 2 cold: low 0, high 0, batch 1 used:0
Nov 16 17:06:47 server01 kernel: [978626.300824] cpu 3 hot: low 0, high 0, batch 1 used:0
Nov 16 17:06:47 server01 kernel: [978626.300826] cpu 3 cold: low 0, high 0, batch 1 used:0
Nov 16 17:06:47 server01 kernel: [978626.300828] Node 0 DMA32 per-cpu:
Nov 16 17:07:10 server01 kernel: [978626.300831] cpu 0 hot: low 0, high 186, batch 31 used:104
Nov 16 17:09:57 server01 kernel: [978626.300833] cpu 0 cold: low 0, high 62, batch 15 used:16
Nov 16 17:10:54 server01 kernel: [978626.300835] cpu 1 hot: low 0, high 186, batch 31 used:35
Nov 16 17:10:54 server01 kernel: [978626.300837] cpu 1 cold: low 0, high 62, batch 15 used:57
Nov 16 17:10:54 server01 kernel: [978626.300840] cpu 2 hot: low 0, high 186, batch 31 used:33
Nov 16 17:10:56 server01 kernel: [978626.300842] cpu 2 cold: low 0, high 62, batch 15 used:42
Nov 16 17:14:11 server01 kernel: [978626.300844] cpu 3 hot: low 0, high 186, batch 31 used:35
Nov 16 17:14:12 server01 kernel: [978626.300846] cpu 3 cold: low 0, high 62, batch 15 used:59
Nov 16 17:14:12 server01 kernel: [978626.300848] Node 0 Normal per-cpu:
Nov 16 17:14:12 server01 kernel: [978626.300851] cpu 0 hot: low 0, high 186, batch 31 used:40
Nov 16 17:14:12 server01 kernel: [978626.300853] cpu 0 cold: low 0, high 62, batch 15 used:18 
```

---

### Post by uberamd on 2009-11-17
Probably not a super helpful answer for you, but on all of our severs at my work we run Munin. We have a master munin server and all of our other servers as nodes (insanely easy to setup, munin and munin-node are both in the repos).

The benefit to this is that it graphs memory use, processes, interrupts, etc over time and you can view them all over the web via the master munin server. You will then be able to actually see your server's memory filling up, and compare it to CPU load graph, interrupt graph, etc and track down **when** things start going wrong.

---

### Post by dca on 2009-11-17
Start it back up and run 'top', hit 'M' to sort by which is taking up the most mem to see...
 
Also, was this server upgraded by any chance?

The reason I ask, if you Google: *Out of Memory: Killed process (apache2)* you see some issues with those that have upgraded from one LTS release to the next or other issues...
 
[https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/224945](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/224945)

---

### Post by chrislynch8 on 2009-11-24
Found the issue - I ran the pppoeconf command from webmin and that caused the out of memory issue

---

