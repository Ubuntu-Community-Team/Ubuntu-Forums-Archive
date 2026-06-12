---
title: "[ufw block]"
date: 2009-11-27
forum: Security
---

### Post by tomas12 on 2009-11-27
today  my pc froze for about 2 minutes and when i looked at the logs i found this:

```
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288600] Pid: 2587, comm: chromium-browse Tainted: P           2.6.31-15-generic #50-Ubuntu
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288602] Call Trace:
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288612]  [<ffffffff810a27a8>] ? cpuset_print_task_mems_allowed+0x98/0xa0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288618]  [<ffffffff810dd7de>] oom_kill_process+0xce/0x290
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288621]  [<ffffffff810ddd4a>] ? select_bad_process+0xea/0x120
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288625]  [<ffffffff810dddd0>] __out_of_memory+0x50/0xb0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288629]  [<ffffffff810ddf56>] out_of_memory+0x126/0x1a0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288634]  [<ffffffff81529a09>] ? _spin_lock+0x9/0x10
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288639]  [<ffffffff810e0818>] __alloc_pages_slowpath+0x498/0x4e0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288643]  [<ffffffff810e09ae>] __alloc_pages_nodemask+0x14e/0x150
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288648]  [<ffffffff8110ceb2>] alloc_pages_current+0x82/0xd0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288651]  [<ffffffff810da93f>] __page_cache_alloc+0x5f/0x70
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288656]  [<ffffffff810e4611>] __do_page_cache_readahead+0xc1/0x160
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288660]  [<ffffffff810e46cc>] ra_submit+0x1c/0x20
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288664]  [<ffffffff810da43b>] do_sync_mmap_readahead+0x9b/0xd0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288667]  [<ffffffff810dc5a4>] filemap_fault+0x314/0x3c0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288671]  [<ffffffff810f424f>] __do_fault+0x4f/0x4e0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288675]  [<ffffffff810f89e7>] handle_mm_fault+0x1a7/0x3c0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288680]  [<ffffffff81036419>] ? default_spin_lock_flags+0x9/0x10
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288685]  [<ffffffff8152c5aa>] do_page_fault+0x16a/0x370
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.288689]  [<ffffffff81529f25>] page_fault+0x25/0x30
```

and 

```
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496334] Pid: 2003, comm: gconfd-2 Tainted: P           2.6.31-15-generic #50-Ubuntu
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496337] Call Trace:
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496346]  [<ffffffff810a27a8>] ? cpuset_print_task_mems_allowed+0x98/0xa0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496352]  [<ffffffff810dd7de>] oom_kill_process+0xce/0x290
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496356]  [<ffffffff810ddd4a>] ? select_bad_process+0xea/0x120
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496359]  [<ffffffff810dddd0>] __out_of_memory+0x50/0xb0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496363]  [<ffffffff810ddf56>] out_of_memory+0x126/0x1a0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496369]  [<ffffffff81529a09>] ? _spin_lock+0x9/0x10
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496373]  [<ffffffff810e0818>] __alloc_pages_slowpath+0x498/0x4e0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496377]  [<ffffffff810e09ae>] __alloc_pages_nodemask+0x14e/0x150
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496382]  [<ffffffff8110ceb2>] alloc_pages_current+0x82/0xd0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496386]  [<ffffffff810da93f>] __page_cache_alloc+0x5f/0x70
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496391]  [<ffffffff8104a87e>] ? __wake_up+0x4e/0x70
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496395]  [<ffffffff810e4611>] __do_page_cache_readahead+0xc1/0x160
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496399]  [<ffffffff810e46cc>] ra_submit+0x1c/0x20
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496403]  [<ffffffff810da43b>] do_sync_mmap_readahead+0x9b/0xd0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496406]  [<ffffffff810dc5a4>] filemap_fault+0x314/0x3c0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496410]  [<ffffffff810f424f>] __do_fault+0x4f/0x4e0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496414]  [<ffffffff810f89e7>] handle_mm_fault+0x1a7/0x3c0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496419]  [<ffffffff81036419>] ? default_spin_lock_flags+0x9/0x10
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496423]  [<ffffffff8152c5aa>] do_page_fault+0x16a/0x370
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.496427]  [<ffffffff81529f25>] page_fault+0x25/0x30
```

and

```
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706325] Call Trace:
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706336]  [<ffffffff810a27a8>] ? cpuset_print_task_mems_allowed+0x98/0xa0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706344]  [<ffffffff810dd7de>] oom_kill_process+0xce/0x290
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706349]  [<ffffffff810ddd4a>] ? select_bad_process+0xea/0x120
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706354]  [<ffffffff810dddd0>] __out_of_memory+0x50/0xb0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706359]  [<ffffffff810ddf56>] out_of_memory+0x126/0x1a0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706365]  [<ffffffff81529a09>] ? _spin_lock+0x9/0x10
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706369]  [<ffffffff810e0818>] __alloc_pages_slowpath+0x498/0x4e0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706374]  [<ffffffff810e09ae>] __alloc_pages_nodemask+0x14e/0x150
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706378]  [<ffffffff8110ceb2>] alloc_pages_current+0x82/0xd0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706382]  [<ffffffff810da93f>] __page_cache_alloc+0x5f/0x70
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706387]  [<ffffffff810e4611>] __do_page_cache_readahead+0xc1/0x160
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706391]  [<ffffffff810e46cc>] ra_submit+0x1c/0x20
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706394]  [<ffffffff810da43b>] do_sync_mmap_readahead+0x9b/0xd0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706398]  [<ffffffff810dc5a4>] filemap_fault+0x314/0x3c0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706402]  [<ffffffff810f424f>] __do_fault+0x4f/0x4e0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706405]  [<ffffffff810f89e7>] handle_mm_fault+0x1a7/0x3c0
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706411]  [<ffffffff81036419>] ? default_spin_lock_flags+0x9/0x10
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706415]  [<ffffffff8152c5aa>] do_page_fault+0x16a/0x370
Nov 27 19:36:08 tomas-desktop kernel: [ 7817.706419]  [<ffffffff81529f25>] page_fault+0x25/0x30
```

but thats not really what worries me what worries me is this entry:

```
Nov 27 19:37:27 tomas-desktop acpid: client 1251[0:0] has disconnected
Nov 27 19:37:27 tomas-desktop acpid: client 1251[0:0] has disconnected
Nov 27 19:37:27 tomas-desktop acpid: client connected from 1251[0:0]
Nov 27 19:37:27 tomas-desktop acpid: client connected from 1251[0:0]
```

i was worried that it was someone trying to connect to this pc, so i decided to install a firewall. so i install gufw and enabled the firewall. when i did that the syslog got filled by messages like this:

```
Nov 27 19:47:11 tomas-desktop kernel: [ 8481.520129] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=98.14.43.224 DST=10.0.0.10 LEN=64 TOS=0x00 PREC=0x00 TTL=111 ID=11332 DF PROTO=TCP SPT=8167 DPT=43914 WINDOW=65535 RES=0x00 ACK URGP=0 
Nov 27 19:47:11 tomas-desktop kernel: [ 8481.520498] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=98.14.43.224 DST=10.0.0.10 LEN=64 TOS=0x00 PREC=0x00 TTL=111 ID=11370 DF PROTO=TCP SPT=8167 DPT=43914 WINDOW=65535 RES=0x00 ACK URGP=0 
Nov 27 19:47:12 tomas-desktop kernel: [ 8481.823313] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=196.205.144.11 DST=10.0.0.10 LEN=87 TOS=0x00 PREC=0x00 TTL=111 ID=14361 DF PROTO=TCP SPT=6889 DPT=60649 WINDOW=16872 RES=0x00 ACK PSH URGP=0 
Nov 27 19:47:12 tomas-desktop kernel: [ 8482.216172] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=196.205.144.11 DST=10.0.0.10 LEN=87 TOS=0x00 PREC=0x00 TTL=111 ID=14430 DF PROTO=TCP SPT=6889 DPT=60649 WINDOW=16872 RES=0x00 ACK PSH URGP=0 
Nov 27 19:47:12 tomas-desktop kernel: [ 8482.450429] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=85.170.168.101 DST=10.0.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=116 ID=13609 DF PROTO=TCP SPT=49532 DPT=45128 WINDOW=65493 RES=0x00 ACK URGP=0 
Nov 27 19:47:13 tomas-desktop kernel: [ 8483.294002] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=196.205.144.11 DST=10.0.0.10 LEN=87 TOS=0x00 PREC=0x00 TTL=111 ID=14573 DF PROTO=TCP SPT=6889 DPT=60649 WINDOW=16872 RES=0x00 ACK PSH URGP=0 
Nov 27 19:47:13 tomas-desktop kernel: [ 8483.393757] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=85.175.146.237 DST=10.0.0.10 LEN=64 TOS=0x00 PREC=0x00 TTL=110 ID=30680 DF PROTO=TCP SPT=16500 DPT=57023 WINDOW=64167 RES=0x00 ACK URGP=0 
Nov 27 19:47:13 tomas-desktop kernel: [ 8483.746196] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=85.175.146.237 DST=10.0.0.10 LEN=64 TOS=0x00 PREC=0x00 TTL=110 ID=30692 DF PROTO=TCP SPT=16500 DPT=57023 WINDOW=64167 RES=0x00 ACK URGP=0 
Nov 27 19:47:14 tomas-desktop kernel: [ 8484.564995] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=93.136.71.200 DST=10.0.0.10 LEN=61 TOS=0x00 PREC=0x00 TTL=111 ID=33885 DF PROTO=TCP SPT=11607 DPT=53549 WINDOW=65535 RES=0x00 ACK PSH URGP=0 
Nov 27 19:47:15 tomas-desktop kernel: [ 8484.970154] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=96.48.60.207 DST=10.0.0.10 LEN=232 TOS=0x00 PREC=0x00 TTL=111 ID=22293 DF PROTO=TCP SPT=44239 DPT=46088 WINDOW=64478 RES=0x00 ACK PSH URGP=0 
Nov 27 19:47:25 tomas-desktop kernel: [ 8494.770127] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=212.66.87.9 DST=10.0.0.10 LEN=264 TOS=0x00 PREC=0x00 TTL=116 ID=13350 DF PROTO=TCP SPT=52508 DPT=35499 WINDOW=64 RES=0x00 ACK PSH FIN URGP=0 
Nov 27 19:47:28 tomas-desktop kernel: [ 8498.525848] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=85.170.168.101 DST=10.0.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=116 ID=31751 DF PROTO=TCP SPT=49532 DPT=45128 WINDOW=65493 RES=0x00 ACK FIN URGP=0 
Nov 27 19:47:29 tomas-desktop kernel: [ 8498.980133] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=85.170.168.101 DST=10.0.0.10 LEN=205 TOS=0x00 PREC=0x00 TTL=116 ID=32218 DF PROTO=TCP SPT=49532 DPT=45128 WINDOW=65493 RES=0x00 ACK PSH FIN URGP=0 
Nov 27 19:47:30 tomas-desktop kernel: [ 8499.985813] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=85.170.168.101 DST=10.0.0.10 LEN=205 TOS=0x00 PREC=0x00 TTL=116 ID=33094 DF PROTO=TCP SPT=49532 DPT=45128 WINDOW=65493 RES=0x00 ACK PSH FIN URGP=0 
Nov 27 19:47:31 tomas-desktop kernel: [ 8501.643528] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=82.40.208.94 DST=10.0.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=113 ID=8449 DF PROTO=TCP SPT=25060 DPT=42293 WINDOW=17382 RES=0x00 ACK URGP=0 
Nov 27 19:47:32 tomas-desktop kernel: [ 8501.973955] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=85.170.168.101 DST=10.0.0.10 LEN=205 TOS=0x00 PREC=0x00 TTL=116 ID=34568 PROTO=TCP SPT=49532 DPT=45128 WINDOW=65493 RES=0x00 ACK PSH FIN URGP=0 
Nov 27 19:47:34 tomas-desktop kernel: [ 8503.957371] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=85.170.168.101 DST=10.0.0.10 LEN=205 TOS=0x00 PREC=0x00 TTL=116 ID=35903 PROTO=TCP SPT=49532 DPT=45128 WINDOW=65493 RES=0x00 ACK PSH FIN URGP=0 
Nov 27 19:47:36 tomas-desktop kernel: [ 8505.989117] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=85.170.168.101 DST=10.0.0.10 LEN=205 TOS=0x00 PREC=0x00 TTL=116 ID=37891 DF PROTO=TCP SPT=49532 DPT=45128 WINDOW=65493 RES=0x00 ACK PSH FIN URGP=0 
Nov 27 19:47:40 tomas-desktop kernel: [ 8509.835995] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=82.40.208.94 DST=10.0.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=113 ID=9451 DF PROTO=TCP SPT=25060 DPT=42293 WINDOW=17382 RES=0x00 ACK FIN URGP=0 
Nov 27 19:47:40 tomas-desktop kernel: [ 8509.989475] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=85.170.168.101 DST=10.0.0.10 LEN=205 TOS=0x00 PREC=0x00 TTL=116 ID=42165 DF PROTO=TCP SPT=49532 DPT=45128 WINDOW=65493 RES=0x00 ACK PSH FIN URGP=0 
Nov 27 19:47:40 tomas-desktop kernel: [ 8510.261640] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=82.40.208.94 DST=10.0.0.10 LEN=241 TOS=0x00 PREC=0x00 TTL=113 ID=9499 DF PROTO=TCP SPT=25060 DPT=42293 WINDOW=17382 RES=0x00 ACK PSH FIN URGP=0 
Nov 27 19:47:45 tomas-desktop kernel: [ 8515.288156] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=82.40.208.94 DST=10.0.0.10 LEN=241 TOS=0x00 PREC=0x00 TTL=113 ID=10149 PROTO=TCP SPT=25060 DPT=42293 WINDOW=17382 RES=0x00 ACK PSH FIN URGP=0 
Nov 27 19:47:52 tomas-desktop kernel: [ 8521.785698] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=91.189.89.31 DST=10.0.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=TCP SPT=80 DPT=51634 WINDOW=54 RES=0x00 ACK URGP=0 
Nov 27 19:48:06 tomas-desktop kernel: [ 8536.067985] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=212.66.87.9 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=116 ID=16382 DF PROTO=TCP SPT=52508 DPT=35499 WINDOW=0 RES=0x00 ACK RST URGP=0 
Nov 27 19:48:15 tomas-desktop kernel: [ 8545.139776] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=87.182.115.24 DST=10.0.0.10 LEN=151 TOS=0x00 PREC=0x00 TTL=113 ID=964 DF PROTO=TCP SPT=55274 DPT=34142 WINDOW=65535 RES=0x00 ACK PSH URGP=0 
Nov 27 19:48:25 tomas-desktop kernel: [ 8554.839894] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=82.128.184.16 DST=10.0.0.10 LEN=94 TOS=0x00 PREC=0x00 TTL=50 ID=45575 DF PROTO=TCP SPT=30568 DPT=59083 WINDOW=490 RES=0x00 ACK PSH FIN URGP=0 
Nov 27 19:48:34 tomas-desktop kernel: [ 8563.818289] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=24.164.140.192 DST=10.0.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=111 ID=9885 DF PROTO=TCP SPT=46843 DPT=51068 WINDOW=257 RES=0x00 ACK URGP=0 
Nov 27 19:49:00 tomas-desktop kernel: [ 8589.736672] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=190.43.129.197 DST=10.0.0.10 LEN=277 TOS=0x00 PREC=0x00 TTL=105 ID=22860 DF PROTO=TCP SPT=50049 DPT=38340 WINDOW=17074 RES=0x00 ACK PSH FIN URGP=0 
Nov 27 19:49:11 tomas-desktop kernel: [ 8601.164108] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.77.18 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=41616 PROTO=TCP SPT=443 DPT=48282 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:49:28 tomas-desktop kernel: [ 8618.161097] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.77.18 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=10234 PROTO=TCP SPT=443 DPT=48282 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:49:29 tomas-desktop kernel: [ 8618.853512] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=190.43.129.197 DST=10.0.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=105 ID=27217 DF PROTO=TCP SPT=50049 DPT=38340 WINDOW=17074 RES=0x00 ACK URGP=0 
Nov 27 19:49:45 tomas-desktop kernel: [ 8635.463388] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.77.18 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=60981 PROTO=TCP SPT=443 DPT=48282 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:50:20 tomas-desktop kernel: [ 8669.985167] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.77.18 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=36134 PROTO=TCP SPT=443 DPT=48282 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:50:48 tomas-desktop kernel: [ 8698.685972] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=190.43.129.197 DST=10.0.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=105 ID=5816 DF PROTO=TCP SPT=50049 DPT=38340 WINDOW=17074 RES=0x00 ACK URGP=0 
Nov 27 19:50:58 tomas-desktop kernel: [ 8707.959420] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=190.43.129.197 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=105 ID=7176 DF PROTO=TCP SPT=50049 DPT=38340 WINDOW=0 RES=0x00 ACK RST URGP=0 
Nov 27 19:53:00 tomas-desktop kernel: [ 8830.274914] [UFW BLOCK] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:15:f2:1b:66:f9:08:00 SRC=10.0.0.3 DST=10.0.0.255 LEN=237 TOS=0x00 PREC=0x00 TTL=128 ID=25568 PROTO=UDP SPT=138 DPT=138 LEN=217 
Nov 27 19:53:22 tomas-desktop kernel: [ 8852.455467] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=98.207.128.7 DST=10.0.0.10 LEN=56 TOS=0x00 PREC=0x20 TTL=103 ID=18369 DF PROTO=TCP SPT=2248 DPT=47649 WINDOW=8192 RES=0x00 ACK SYN URGP=0 
Nov 27 19:53:25 tomas-desktop kernel: [ 8855.446393] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=98.207.128.7 DST=10.0.0.10 LEN=56 TOS=0x00 PREC=0x20 TTL=103 ID=19025 DF PROTO=TCP SPT=2248 DPT=47649 WINDOW=8192 RES=0x00 ACK SYN URGP=0 
Nov 27 19:53:31 tomas-desktop kernel: [ 8861.440735] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=98.207.128.7 DST=10.0.0.10 LEN=56 TOS=0x00 PREC=0x20 TTL=103 ID=21141 DF PROTO=TCP SPT=2248 DPT=47649 WINDOW=8192 RES=0x00 ACK SYN URGP=0 
Nov 27 19:53:43 tomas-desktop kernel: [ 8873.429650] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=98.207.128.7 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x20 TTL=103 ID=25097 DF PROTO=TCP SPT=2248 DPT=47649 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:54:12 tomas-desktop kernel: [ 8902.286660] [UFW BLOCK] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:15:f2:1b:66:f9:08:00 SRC=10.0.0.3 DST=10.0.0.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=26986 PROTO=UDP SPT=138 DPT=138 LEN=209 
Nov 27 19:57:23 tomas-desktop kernel: [ 9092.834219] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.79.18 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=3162 PROTO=TCP SPT=443 DPT=48791 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:57:23 tomas-desktop kernel: [ 9092.834718] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.77.99 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=49225 PROTO=TCP SPT=80 DPT=44264 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:57:23 tomas-desktop kernel: [ 9093.101252] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.79.18 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=3163 PROTO=TCP SPT=443 DPT=48791 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:57:23 tomas-desktop kernel: [ 9093.101612] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.77.99 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=49226 PROTO=TCP SPT=80 DPT=44264 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:57:24 tomas-desktop kernel: [ 9093.668128] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.79.18 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=3164 PROTO=TCP SPT=443 DPT=48791 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:57:24 tomas-desktop kernel: [ 9093.668440] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.77.99 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=49227 PROTO=TCP SPT=80 DPT=44264 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:57:25 tomas-desktop kernel: [ 9094.801189] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.79.18 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=3165 PROTO=TCP SPT=443 DPT=48791 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:57:25 tomas-desktop kernel: [ 9094.801546] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.77.99 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=49228 PROTO=TCP SPT=80 DPT=44264 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:57:27 tomas-desktop kernel: [ 9097.031726] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.77.99 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=49229 PROTO=TCP SPT=80 DPT=44264 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:57:27 tomas-desktop kernel: [ 9097.032042] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.79.18 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=3166 PROTO=TCP SPT=443 DPT=48791 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:57:58 tomas-desktop kernel: [ 9128.368139] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.79.18 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=36050 PROTO=TCP SPT=443 DPT=48791 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:58:34 tomas-desktop kernel: [ 9164.226637] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.79.18 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=17955 PROTO=TCP SPT=443 DPT=48791 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:58:34 tomas-desktop kernel: [ 9164.227427] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=74.125.77.99 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=47749 PROTO=TCP SPT=80 DPT=44264 WINDOW=0 RES=0x00 RST URGP=0 
Nov 27 19:58:52 tomas-desktop kernel: [ 9181.735725] [UFW BLOCK] IN=eth0 OUT= MAC=FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF:FF SRC=85.167.21.133 DST=10.0.0.10 LEN=40 TOS=0x00 PREC=0x00 TTL=119 ID=15199 DF PROTO=TCP SPT=28943 DPT=37526 WINDOW=0 RES=0x00 ACK RST URGP=0 
```

and new messages appered about every 10 second. so i reboot my pc and after that nothing else has happened. so what im wondering is was my pc compromised? and if not can someone explain what the messages mean.

note: sorry if my english is a little broken, English is not my native language.
note2: the MAC part of the udf block originally show my MAC address i just replaced it with FF in this post, to avoid anyone misusing my MAC address

---

