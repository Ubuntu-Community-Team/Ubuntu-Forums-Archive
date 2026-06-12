---
title: "server crashing once a day"
date: 2010-03-04
forum: Server Platforms
---

### Post by flipybcn on 2010-03-04
I've been running an ubuntu server for almost a year, and suddenly, since last week it started crashing once a day.
I've to power down and on to get the machine working again.
Taking a look a the logs I'm not able to see any kind of trouble, just how it runs out of memory and stop responding.

Server is ubuntu 9.04 x86_64 and has:
openldap
apache2
samba
dhcp3-server
bind9
mysql

This is an extract of the log:
```
Mar  4 21:54:31 venus kernel: [134949.882726] winbindd invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
Mar  4 21:54:31 venus kernel: [134949.882734] Pid: 3050, comm: winbindd Not tainted 2.6.28-18-server #59-Ubuntu
Mar  4 21:54:31 venus kernel: [134949.882736] Call Trace:
Mar  4 21:54:31 venus kernel: [134949.882757]  [<ffffffff802b3825>] oom_kill_process+0x95/0x240
Mar  4 21:54:31 venus kernel: [134949.882760]  [<ffffffff802b3fdf>] ? select_bad_process+0xef/0x130
Mar  4 21:54:31 venus kernel: [134949.882762]  [<ffffffff802b40d4>] out_of_memory+0xb4/0x150
Mar  4 21:54:31 venus kernel: [134949.882765]  [<ffffffff802b6c49>] __alloc_pages_internal+0x4a9/0x4f0
Mar  4 21:54:31 venus kernel: [134949.882770]  [<ffffffff802b9a7a>] __do_page_cache_readahead+0xda/0x210
Mar  4 21:54:31 venus kernel: [134949.882773]  [<ffffffff802b9c0e>] do_page_cache_readahead+0x5e/0x90
Mar  4 21:54:31 venus kernel: [134949.882775]  [<ffffffff802b201a>] filemap_fault+0x34a/0x430
Mar  4 21:54:31 venus kernel: [134949.882778]  [<ffffffff802c6010>] __do_fault+0x50/0x520
Mar  4 21:54:31 venus kernel: [134949.882789]  [<ffffffff8024a600>] ? default_wake_function+0x0/0x10
Mar  4 21:54:31 venus kernel: [134949.882791]  [<ffffffff802c7199>] handle_mm_fault+0x1e9/0x470
Mar  4 21:54:31 venus kernel: [134949.882798]  [<ffffffff802f7915>] ? set_fd_set+0x25/0x30
Mar  4 21:54:31 venus kernel: [134949.882800]  [<ffffffff802f8900>] ? core_sys_select+0x1e0/0x2a0
Mar  4 21:54:31 venus kernel: [134949.882811]  [<ffffffff8069e0d7>] do_page_fault+0x307/0x780
Mar  4 21:54:31 venus kernel: [134949.882833]  [<ffffffff802198f6>] ? read_tsc+0x16/0x40
Mar  4 21:54:31 venus kernel: [134949.882837]  [<ffffffff80270a39>] ? getnstimeofday+0x59/0xe0
Mar  4 21:54:31 venus kernel: [134949.882839]  [<ffffffff8026c6b9>] ? ktime_get_ts+0x59/0x60
Mar  4 21:54:31 venus kernel: [134949.882842]  [<ffffffff802f74b7>] ? poll_select_copy_remaining+0xf7/0x150
Mar  4 21:54:31 venus kernel: [134949.882844]  [<ffffffff802f8c2c>] ? sys_select+0x5c/0x110
Mar  4 21:54:31 venus kernel: [134949.882848]  [<ffffffff8069b6ba>] error_exit+0x0/0x70
Mar  4 21:54:31 venus kernel: [134949.882849] Mem-Info:
Mar  4 21:54:31 venus kernel: [134949.882851] DMA per-cpu:
Mar  4 21:54:31 venus kernel: [134949.882852] CPU    0: hi:    0, btch:   1 usd:   0
Mar  4 21:54:31 venus kernel: [134949.882853] CPU    1: hi:    0, btch:   1 usd:   0
Mar  4 21:54:31 venus kernel: [134949.882854] DMA32 per-cpu:
Mar  4 21:54:31 venus kernel: [134949.882855] CPU    0: hi:  186, btch:  31 usd: 163
Mar  4 21:54:31 venus kernel: [134949.882857] CPU    1: hi:  186, btch:  31 usd:  50
Mar  4 21:54:31 venus kernel: [134949.882859] Active_anon:366511 active_file:31 inactive_anon:122116
Mar  4 21:54:31 venus kernel: [134949.882862]  inactive_file:0 unevictable:0 dirty:0 writeback:0 unstable:0
Mar  4 21:54:31 venus kernel: [134949.882863]  free:3064 slab:4629 mapped:1 pagetables:6058 bounce:0
Mar  4 21:54:31 venus kernel: [134949.882865] DMA free:6644kB min:12kB low:12kB high:16kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB present:5588kB pages_scanned:0 all_unreclaimable? yes
Mar  4 21:54:31 venus kernel: [134949.882867] lowmem_reserve[]: 0 2004 2004 2004
Mar  4 21:54:31 venus kernel: [134949.882871] DMA32 free:5612kB min:5720kB low:7148kB high:8580kB active_anon:1466044kB inactive_anon:488464kB active_file:124kB inactive_file:0kB unevictable:0kB present:2052192kB pages_scanned:3540131 all_unreclaimable? yes
Mar  4 21:54:31 venus kernel: [134949.882873] lowmem_reserve[]: 0 0 0 0
Mar  4 21:54:31 venus kernel: [134949.882875] DMA: 3*4kB 3*8kB 3*16kB 3*32kB 3*64kB 1*128kB 2*256kB 1*512kB 1*1024kB 0*2048kB 1*4096kB = 6644kB
Mar  4 21:54:31 venus kernel: [134949.882881] DMA32: 57*4kB 1*8kB 4*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 1*4096kB = 5612kB
Mar  4 21:54:31 venus kernel: [134949.882886] 890 total pagecache pages
Mar  4 21:54:31 venus kernel: [134949.882887] 0 pages in swap cache
Mar  4 21:54:31 venus kernel: [134949.882888] Swap cache stats: add 0, delete 0, find 0/0
Mar  4 21:54:31 venus kernel: [134949.882889] Free swap  = 0kB
Mar  4 21:54:31 venus kernel: [134949.882890] Total swap = 0kB
Mar  4 21:54:31 venus kernel: [134949.888884] 524272 pages RAM
Mar  4 21:54:31 venus kernel: [134949.888886] 15612 pages reserved
Mar  4 21:54:31 venus kernel: [134949.888887] 56425 pages shared
Mar  4 21:54:31 venus kernel: [134949.888887] 501547 pages non-shared
Mar  4 21:54:31 venus kernel: [134949.888890] Out of memory: kill process 23304 (apache2) score 75991 or a child
Mar  4 21:54:31 venus kernel: [134949.889137] Killed process 23304 (apache2)
Mar  4 21:54:31 venus nrpe[23962]: Error: Could not complete SSL handshake. 5 
Mar  4 21:54:54 venus kernel: [134978.320235] ntpd invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=-17
Mar  4 21:54:54 venus kernel: [134978.320239] Pid: 2967, comm: ntpd Not tainted 2.6.28-18-server #59-Ubuntu
Mar  4 21:54:54 venus kernel: [134978.320240] Call Trace:
Mar  4 21:54:54 venus kernel: [134978.320248]  [<ffffffff802b3825>] oom_kill_process+0x95/0x240
Mar  4 21:54:54 venus kernel: [134978.320250]  [<ffffffff802b3fdf>] ? select_bad_process+0xef/0x130
Mar  4 21:54:54 venus kernel: [134978.320253]  [<ffffffff802b40d4>] out_of_memory+0xb4/0x150
Mar  4 21:54:54 venus kernel: [134978.320255]  [<ffffffff802b6c49>] __alloc_pages_internal+0x4a9/0x4f0
Mar  4 21:54:54 venus kernel: [134978.320258]  [<ffffffff802b9a7a>] __do_page_cache_readahead+0xda/0x210
Mar  4 21:54:54 venus kernel: [134978.320261]  [<ffffffff802b9c0e>] do_page_cache_readahead+0x5e/0x90
Mar  4 21:54:54 venus kernel: [134978.320263]  [<ffffffff802b201a>] filemap_fault+0x34a/0x430
Mar  4 21:54:54 venus kernel: [134978.320266]  [<ffffffff802c6010>] __do_fault+0x50/0x520
Mar  4 21:54:54 venus kernel: [134978.320270]  [<ffffffff8021b82a>] ? save_i387_xstate+0x1ba/0x1f0
Mar  4 21:54:54 venus kernel: [134978.320274]  [<ffffffff8024a600>] ? default_wake_function+0x0/0x10
Mar  4 21:54:54 venus kernel: [134978.320276]  [<ffffffff80211774>] ? __setup_rt_frame+0x94/0x520
Mar  4 21:54:54 venus kernel: [134978.320278]  [<ffffffff802c7199>] handle_mm_fault+0x1e9/0x470
Mar  4 21:54:54 venus kernel: [134978.320282]  [<ffffffff8069e0d7>] do_page_fault+0x307/0x780
Mar  4 21:54:54 venus kernel: [134978.320283]  [<ffffffff8021227b>] ? do_signal+0xbb/0x1e0
Mar  4 21:54:54 venus kernel: [134978.320286]  [<ffffffff8021b030>] ? init_fpu+0x60/0x150
Mar  4 21:54:54 venus kernel: [134978.320289]  [<ffffffff803d0bc1>] ? security_file_permission+0x11/0x20
Mar  4 21:54:54 venus kernel: [134978.320291]  [<ffffffff80211f0f>] ? do_rt_sigreturn+0x2df/0x2f0
Mar  4 21:54:54 venus kernel: [134978.320296]  [<ffffffff8069b6ba>] error_exit+0x0/0x70
Mar  4 21:54:54 venus kernel: [134978.320297] Mem-Info:
Mar  4 21:54:54 venus kernel: [134978.320298] DMA per-cpu:
Mar  4 21:54:54 venus kernel: [134978.320300] CPU    0: hi:    0, btch:   1 usd:   0
Mar  4 21:54:54 venus kernel: [134978.320301] CPU    1: hi:    0, btch:   1 usd:   0
Mar  4 21:54:54 venus kernel: [134978.320302] DMA32 per-cpu:
Mar  4 21:54:54 venus kernel: [134978.320303] CPU    0: hi:  186, btch:  31 usd: 181
Mar  4 21:54:54 venus kernel: [134978.320304] CPU    1: hi:  186, btch:  31 usd: 174
Mar  4 21:54:54 venus kernel: [134978.320306] Active_anon:366706 active_file:0 inactive_anon:122207
Mar  4 21:54:54 venus kernel: [134978.320307]  inactive_file:29 unevictable:0 dirty:0 writeback:0 unstable:0
Mar  4 21:54:54 venus kernel: [134978.320308]  free:3070 slab:4638 mapped:1 pagetables:5840 bounce:0
Mar  4 21:54:54 venus kernel: [134978.320310] DMA free:6644kB min:12kB low:12kB high:16kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB present:5588kB pages_scanned:0 all_unreclaimable? yes
Mar  4 21:54:54 venus kernel: [134978.320312] lowmem_reserve[]: 0 2004 2004 2004
Mar  4 21:54:54 venus kernel: [134978.320316] DMA32 free:5636kB min:5720kB low:7148kB high:8580kB active_anon:1466824kB inactive_anon:488828kB active_file:0kB inactive_file:116kB unevictable:0kB present:2052192kB pages_scanned:4308536 all_unreclaimable? no
Mar  4 21:54:54 venus kernel: [134978.320318] lowmem_reserve[]: 0 0 0 0
Mar  4 21:54:54 venus kernel: [134978.320320] DMA: 3*4kB 3*8kB 3*16kB 3*32kB 3*64kB 1*128kB 2*256kB 1*512kB 1*1024kB 0*2048kB 1*4096kB = 6644kB
Mar  4 21:54:54 venus kernel: [134978.320328] DMA32: 13*4kB 8*8kB 3*16kB 1*32kB 1*64kB 2*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 1*4096kB = 5636kB
Mar  4 21:54:54 venus kernel: [134978.320334] 897 total pagecache pages
Mar  4 21:54:54 venus kernel: [134978.320335] 0 pages in swap cache
Mar  4 21:54:54 venus kernel: [134978.320336] Swap cache stats: add 0, delete 0, find 0/0
Mar  4 21:54:54 venus kernel: [134978.320337] Free swap  = 0kB
Mar  4 21:54:54 venus kernel: [134978.320338] Total swap = 0kB
Mar  4 21:54:54 venus kernel: [134978.326258] 524272 pages RAM
Mar  4 21:54:54 venus kernel: [134978.326260] 15612 pages reserved
Mar  4 21:54:54 venus kernel: [134978.326261] 50901 pages shared
Mar  4 21:54:54 venus kernel: [134978.326262] 501635 pages non-shared
Mar  4 21:54:54 venus kernel: [134978.326264] Out of memory: kill process 23692 (apache2) score 75956 or a child
Mar  4 21:54:54 venus kernel: [134978.326501] Killed process 23692 (apache2)
Mar  4 21:55:01 venus kernel: [134985.202864] snmpd invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
Mar  4 21:55:01 venus kernel: [134985.202868] Pid: 3034, comm: snmpd Not tainted 2.6.28-18-server #59-Ubuntu
Mar  4 21:55:01 venus kernel: [134985.202869] Call Trace:
Mar  4 21:55:01 venus kernel: [134985.202876]  [<ffffffff802b3825>] oom_kill_process+0x95/0x240
Mar  4 21:55:01 venus kernel: [134985.202879]  [<ffffffff802b3fdf>] ? select_bad_process+0xef/0x130
Mar  4 21:55:01 venus kernel: [134985.202881]  [<ffffffff802b40d4>] out_of_memory+0xb4/0x150
Mar  4 21:55:01 venus kernel: [134985.202884]  [<ffffffff802b6c49>] __alloc_pages_internal+0x4a9/0x4f0
Mar  4 21:55:01 venus kernel: [134985.202887]  [<ffffffff802b9a7a>] __do_page_cache_readahead+0xda/0x210
Mar  4 21:55:01 venus kernel: [134985.202889]  [<ffffffff802b9c0e>] do_page_cache_readahead+0x5e/0x90
Mar  4 21:55:01 venus kernel: [134985.202892]  [<ffffffff802b201a>] filemap_fault+0x34a/0x430
Mar  4 21:55:01 venus kernel: [134985.202895]  [<ffffffff802c6010>] __do_fault+0x50/0x520
Mar  4 21:55:01 venus kernel: [134985.202899]  [<ffffffff8041e93d>] ? string+0x3d/0x100
Mar  4 21:55:01 venus kernel: [134985.202901]  [<ffffffff8041ee88>] ? vsnprintf+0x2e8/0x730
Mar  4 21:55:01 venus kernel: [134985.202903]  [<ffffffff802c7199>] handle_mm_fault+0x1e9/0x470
Mar  4 21:55:01 venus kernel: [134985.202907]  [<ffffffff802f7915>] ? set_fd_set+0x25/0x30
Mar  4 21:55:01 venus kernel: [134985.202908]  [<ffffffff802f8900>] ? core_sys_select+0x1e0/0x2a0
Mar  4 21:55:01 venus kernel: [134985.202912]  [<ffffffff8069e0d7>] do_page_fault+0x307/0x780
Mar  4 21:55:01 venus kernel: [134985.202916]  [<ffffffff802198f6>] ? read_tsc+0x16/0x40
Mar  4 21:55:01 venus kernel: [134985.202920]  [<ffffffff80270a39>] ? getnstimeofday+0x59/0xe0
Mar  4 21:55:01 venus kernel: [134985.202922]  [<ffffffff8026c6b9>] ? ktime_get_ts+0x59/0x60
Mar  4 21:55:01 venus kernel: [134985.202925]  [<ffffffff802f74b7>] ? poll_select_copy_remaining+0xf7/0x150
Mar  4 21:55:01 venus kernel: [134985.202927]  [<ffffffff802f8c2c>] ? sys_select+0x5c/0x110
Mar  4 21:55:01 venus kernel: [134985.202931]  [<ffffffff8069b6ba>] error_exit+0x0/0x70
Mar  4 21:55:01 venus kernel: [134985.202932] Mem-Info:
Mar  4 21:55:01 venus kernel: [134985.202933] DMA per-cpu:
Mar  4 21:55:01 venus kernel: [134985.202934] CPU    0: hi:    0, btch:   1 usd:   0
Mar  4 21:55:01 venus kernel: [134985.202936] CPU    1: hi:    0, btch:   1 usd:   0
Mar  4 21:55:01 venus kernel: [134985.202937] DMA32 per-cpu:
Mar  4 21:55:01 venus kernel: [134985.202938] CPU    0: hi:  186, btch:  31 usd: 117
Mar  4 21:55:01 venus kernel: [134985.202939] CPU    1: hi:  186, btch:  31 usd:  93
Mar  4 21:55:01 venus kernel: [134985.202941] Active_anon:367459 active_file:4 inactive_anon:122434
Mar  4 21:55:01 venus kernel: [134985.202942]  inactive_file:127 unevictable:0 dirty:0 writeback:0 unstable:0
Mar  4 21:55:01 venus kernel: [134985.202943]  free:3120 slab:4632 mapped:9 pagetables:6089 bounce:0
Mar  4 21:55:01 venus kernel: [134985.202945] DMA free:6644kB min:12kB low:12kB high:16kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB present:5588kB pages_scanned:0 all_unreclaimable? yes
Mar  4 21:55:01 venus kernel: [134985.202947] lowmem_reserve[]: 0 2004 2004 2004
Mar  4 21:55:01 venus kernel: [134985.202951] DMA32 free:5836kB min:5720kB low:7148kB high:8580kB active_anon:1469836kB inactive_anon:489736kB active_file:16kB inactive_file:508kB unevictable:0kB present:2052192kB pages_scanned:964 all_unreclaimable? no
Mar  4 21:55:01 venus kernel: [134985.202953] lowmem_reserve[]: 0 0 0 0
Mar  4 21:55:01 venus kernel: [134985.202955] DMA: 3*4kB 3*8kB 3*16kB 3*32kB 3*64kB 1*128kB 2*256kB 1*512kB 1*1024kB 0*2048kB 1*4096kB = 6644kB
Mar  4 21:55:01 venus kernel: [134985.202960] DMA32: 78*4kB 4*8kB 0*16kB 1*32kB 1*64kB 2*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 1*4096kB = 5816kB
Mar  4 21:55:01 venus kernel: [134985.202966] 1028 total pagecache pages
Mar  4 21:55:01 venus kernel: [134985.202967] 0 pages in swap cache
Mar  4 21:55:01 venus kernel: [134985.202968] Swap cache stats: add 0, delete 0, find 0/0
Mar  4 21:55:01 venus kernel: [134985.202969] Free swap  = 0kB
Mar  4 21:55:01 venus kernel: [134985.202970] Total swap = 0kB
Mar  4 21:55:01 venus kernel: [134985.209019] 524272 pages RAM
Mar  4 21:55:01 venus kernel: [134985.209020] 15612 pages reserved
Mar  4 21:55:01 venus kernel: [134985.209021] 53971 pages shared
Mar  4 21:55:01 venus kernel: [134985.209022] 502324 pages non-shared
Mar  4 21:55:01 venus kernel: [134985.209024] Out of memory: kill process 23551 (apache2) score 75217 or a child
Mar  4 21:55:01 venus kernel: [134985.209260] Killed process 23551 (apache2)
Mar  4 21:55:03 venus snmpd[3034]: Connection from UDP: [10.0.0.199]:33854 
Mar  4 21:55:03 venus kernel: [134986.946790] apache2 invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
Mar  4 21:55:03 venus kernel: [134986.946797] Pid: 23958, comm: apache2 Not tainted 2.6.28-18-server #59-Ubuntu
Mar  4 21:55:03 venus kernel: [134986.946799] Call Trace:
Mar  4 21:55:03 venus kernel: [134986.946806]  [<ffffffff802b3825>] oom_kill_process+0x95/0x240
Mar  4 21:55:03 venus kernel: [134986.946809]  [<ffffffff802b3fdf>] ? select_bad_process+0xef/0x130
Mar  4 21:55:03 venus kernel: [134986.946811]  [<ffffffff802b40d4>] out_of_memory+0xb4/0x150
Mar  4 21:55:03 venus kernel: [134986.946814]  [<ffffffff802b6c49>] __alloc_pages_internal+0x4a9/0x4f0
Mar  4 21:55:03 venus kernel: [134986.946817]  [<ffffffff802b9a7a>] __do_page_cache_readahead+0xda/0x210
Mar  4 21:55:03 venus kernel: [134986.946819]  [<ffffffff802b9c0e>] do_page_cache_readahead+0x5e/0x90
Mar  4 21:55:03 venus kernel: [134986.946821]  [<ffffffff802b201a>] filemap_fault+0x34a/0x430
Mar  4 21:55:03 venus kernel: [134986.946825]  [<ffffffff802c6010>] __do_fault+0x50/0x520
Mar  4 21:55:03 venus kernel: [134986.946827]  [<ffffffff802c7199>] handle_mm_fault+0x1e9/0x470
Mar  4 21:55:03 venus kernel: [134986.946830]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
Mar  4 21:55:03 venus kernel: [134986.946834]  [<ffffffff8069e0d7>] do_page_fault+0x307/0x780
Mar  4 21:55:03 venus kernel: [134986.946838]  [<ffffffff802e8753>] ? do_readv_writev+0x153/0x1e0
Mar  4 21:55:03 venus kernel: [134986.946841]  [<ffffffff80268970>] ? autoremove_wake_function+0x0/0x40
Mar  4 21:55:03 venus kernel: [134986.946845]  [<ffffffff802198f6>] ? read_tsc+0x16/0x40
Mar  4 21:55:03 venus kernel: [134986.946848]  [<ffffffff80270a39>] ? getnstimeofday+0x59/0xe0
Mar  4 21:55:03 venus kernel: [134986.946850]  [<ffffffff8026c6b9>] ? ktime_get_ts+0x59/0x60
Mar  4 21:55:03 venus kernel: [134986.946854]  [<ffffffff802f79a0>] ? poll_select_set_timeout+0x80/0x90
Mar  4 21:55:03 venus kernel: [134986.946859]  [<ffffffff8069b6ba>] error_exit+0x0/0x70
Mar  4 21:55:03 venus kernel: [134986.946860] Mem-Info:
Mar  4 21:55:03 venus kernel: [134986.946861] DMA per-cpu:
Mar  4 21:55:03 venus kernel: [134986.946863] CPU    0: hi:    0, btch:   1 usd:   0
Mar  4 21:55:03 venus kernel: [134986.946864] CPU    1: hi:    0, btch:   1 usd:   0
Mar  4 21:55:03 venus kernel: [134986.946865] DMA32 per-cpu:
Mar  4 21:55:03 venus kernel: [134986.946866] CPU    0: hi:  186, btch:  31 usd: 155
Mar  4 21:55:03 venus kernel: [134986.946867] CPU    1: hi:  186, btch:  31 usd: 154
Mar  4 21:55:03 venus kernel: [134986.946870] Active_anon:365592 active_file:780 inactive_anon:121846
Mar  4 21:55:03 venus kernel: [134986.946870]  inactive_file:1603 unevictable:0 dirty:0 writeback:0 unstable:0
Mar  4 21:55:03 venus kernel: [134986.946871]  free:3154 slab:4681 mapped:1190 pagetables:6302 bounce:0
Mar  4 21:55:03 venus kernel: [134986.946873] DMA free:6644kB min:12kB low:12kB high:16kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB present:5588kB pages_scanned:0 all_unreclaimable? yes
Mar  4 21:55:03 venus kernel: [134986.946875] lowmem_reserve[]: 0 2004 2004 2004
Mar  4 21:55:03 venus kernel: [134986.946879] DMA32 free:5972kB min:5720kB low:7148kB high:8580kB active_anon:1462368kB inactive_anon:487384kB active_file:3120kB inactive_file:6412kB unevictable:0kB present:2052192kB pages_scanned:929 all_unreclaimable? no
Mar  4 21:55:03 venus kernel: [134986.946881] lowmem_reserve[]: 0 0 0 0
Mar  4 21:55:03 venus kernel: [134986.946883] DMA: 3*4kB 3*8kB 3*16kB 3*32kB 3*64kB 1*128kB 2*256kB 1*512kB 1*1024kB 0*2048kB 1*4096kB = 6644kB
Mar  4 21:55:03 venus kernel: [134986.946889] DMA32: 77*4kB 1*8kB 4*16kB 4*32kB 1*64kB 2*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 1*4096kB = 5948kB
Mar  4 21:55:03 venus kernel: [134986.946894] 3261 total pagecache pages
Mar  4 21:55:03 venus kernel: [134986.946895] 0 pages in swap cache
Mar  4 21:55:03 venus kernel: [134986.946896] Swap cache stats: add 0, delete 0, find 0/0
Mar  4 21:55:03 venus kernel: [134986.946897] Free swap  = 0kB
Mar  4 21:55:03 venus kernel: [134986.946898] Total swap = 0kB
Mar  4 21:55:03 venus kernel: [134986.952888] 524272 pages RAM
Mar  4 21:55:03 venus kernel: [134986.952890] 15612 pages reserved
Mar  4 21:55:03 venus kernel: [134986.952890] 66175 pages shared
Mar  4 21:55:03 venus kernel: [134986.952891] 500976 pages non-shared
Mar  4 21:55:03 venus kernel: [134986.952893] Out of memory: kill process 23701 (apache2) score 74010 or a child
Mar  4 21:55:03 venus kernel: [134986.953127] Killed process 23701 (apache2)
Mar  4 21:55:03 venus snmpd[3034]: Connection from UDP: [10.0.0.199]:33854 
Mar  4 21:55:03 venus snmpd[3034]: Connection from UDP: [10.0.0.199]:54445 
Mar  4 21:55:03 venus snmpd[3034]: Connection from UDP: [10.0.0.199]:54545 
Mar  4 21:55:03 venus snmpd[3034]: Connection from UDP: [10.0.0.199]:38588 
Mar  4 21:55:03 venus snmpd[3034]: Connection from UDP: [10.0.0.199]:33781 
Mar  4 21:55:03 venus snmpd[3034]: Connection from UDP: [10.0.0.199]:48857 
Mar  4 21:55:03 venus snmpd[3034]: Connection from UDP: [10.0.0.199]:60150 
Mar  4 21:55:03 venus snmpd[3034]: Connection from UDP: [10.0.0.199]:57143 
Mar  4 21:55:03 venus snmpd[3034]: Connection from UDP: [10.0.0.199]:45600 
Mar  4 21:55:03 venus snmpd[3034]: Connection from UDP: [10.0.0.199]:35984 
Mar  4 21:55:03 venus snmpd[3034]: Connection from UDP: [10.0.0.199]:59124 
Mar  4 21:55:03 venus snmpd[3034]: Connection from UDP: [10.0.0.199]:55297 
Mar  4 21:55:03 venus snmpd[3034]: Connection from UDP: [10.0.0.199]:59703 
Mar  4 21:55:03 venus snmpd[3034]: Connection from UDP: [10.0.0.199]:33887 
Mar  4 21:55:06 venus kernel: [134989.510442] apache2 invoked oom-killer: gfp_mask=0x1280d2, order=0, oomkilladj=0
Mar  4 21:55:06 venus kernel: [134989.510446] Pid: 23922, comm: apache2 Not tainted 2.6.28-18-server #59-Ubuntu
Mar  4 21:55:06 venus kernel: [134989.510447] Call Trace:
Mar  4 21:55:06 venus kernel: [134989.510454]  [<ffffffff802b3825>] oom_kill_process+0x95/0x240
Mar  4 21:55:06 venus kernel: [134989.510457]  [<ffffffff802b3fdf>] ? select_bad_process+0xef/0x130
Mar  4 21:55:06 venus kernel: [134989.510459]  [<ffffffff802b40d4>] out_of_memory+0xb4/0x150
Mar  4 21:55:06 venus kernel: [134989.510461]  [<ffffffff802b6c49>] __alloc_pages_internal+0x4a9/0x4f0
Mar  4 21:55:06 venus kernel: [134989.510465]  [<ffffffff802c2a4e>] do_anonymous_page+0x4e/0x230
Mar  4 21:55:06 venus kernel: [134989.510467]  [<ffffffff802c7299>] handle_mm_fault+0x2e9/0x470
Mar  4 21:55:06 venus kernel: [134989.510470]  [<ffffffff8069e0d7>] do_page_fault+0x307/0x780
Mar  4 21:55:06 venus kernel: [134989.510474]  [<ffffffff8023dfff>] ? wake_affine+0xaf/0x240
Mar  4 21:55:06 venus kernel: [134989.510476]  [<ffffffff80242412>] ? enqueue_entity+0x122/0x2b0
Mar  4 21:55:06 venus kernel: [134989.510484]  [<ffffffff8024872d>] ? enqueue_task_fair+0x3d/0x80
Mar  4 21:55:06 venus kernel: [134989.510486]  [<ffffffff80249358>] ? check_preempt_wakeup+0x1d8/0x250
Mar  4 21:55:06 venus kernel: [134989.510488]  [<ffffffff8024a44c>] ? try_to_wake_up+0x12c/0x2e0
Mar  4 21:55:06 venus kernel: [134989.510493]  [<ffffffff8069b6ba>] error_exit+0x0/0x70
Mar  4 21:55:06 venus kernel: [134989.510495]  [<ffffffff802b0712>] ? file_read_actor+0x42/0x160
Mar  4 21:55:06 venus kernel: [134989.510497]  [<ffffffff802b2494>] do_generic_file_read+0x394/0x480
Mar  4 21:55:06 venus kernel: [134989.510499]  [<ffffffff802b06d0>] ? file_read_actor+0x0/0x160
Mar  4 21:55:06 venus kernel: [134989.510501]  [<ffffffff802b2649>] generic_file_aio_read+0xc9/0x1e0
Mar  4 21:55:06 venus kernel: [134989.510505]  [<ffffffff802e7ac1>] do_sync_read+0xf1/0x140
Mar  4 21:55:06 venus kernel: [134989.510509]  [<ffffffff80268970>] ? autoremove_wake_function+0x0/0x40
Mar  4 21:55:06 venus kernel: [134989.510513]  [<ffffffff803f6483>] ? apparmor_file_permission+0x23/0x30
Mar  4 21:55:06 venus kernel: [134989.510516]  [<ffffffff803d0bc1>] ? security_file_permission+0x11/0x20
Mar  4 21:55:06 venus kernel: [134989.510519]  [<ffffffff802e82a8>] vfs_read+0xc8/0x130
Mar  4 21:55:06 venus kernel: [134989.510521]  [<ffffffff802e8400>] sys_read+0x50/0x90
Mar  4 21:55:06 venus kernel: [134989.510523]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Mar  4 21:55:06 venus kernel: [134989.510525] Mem-Info:
Mar  4 21:55:06 venus kernel: [134989.510526] DMA per-cpu:
Mar  4 21:55:06 venus kernel: [134989.510527] CPU    0: hi:    0, btch:   1 usd:   0
Mar  4 21:55:06 venus kernel: [134989.510529] CPU    1: hi:    0, btch:   1 usd:   0
Mar  4 21:55:06 venus kernel: [134989.510530] DMA32 per-cpu:
Mar  4 21:55:06 venus kernel: [134989.510531] CPU    0: hi:  186, btch:  31 usd: 163
Mar  4 21:55:06 venus kernel: [134989.510532] CPU    1: hi:  186, btch:  31 usd: 176
Mar  4 21:55:06 venus kernel: [134989.510534] Active_anon:367224 active_file:32 inactive_anon:122446
Mar  4 21:55:06 venus kernel: [134989.510535]  inactive_file:179 unevictable:0 dirty:0 writeback:0 unstable:0
Mar  4 21:55:06 venus kernel: [134989.510536]  free:3152 slab:4677 mapped:39 pagetables:6266 bounce:0
Mar  4 21:55:06 venus kernel: [134989.510538] DMA free:6644kB min:12kB low:12kB high:16kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB present:5588kB pages_scanned:0 all_unreclaimable? yes
Mar  4 21:55:06 venus kernel: [134989.510540] lowmem_reserve[]: 0 2004 2004 2004
Mar  4 21:55:06 venus kernel: [134989.510544] DMA32 free:5964kB min:5720kB low:7148kB high:8580kB active_anon:1468896kB inactive_anon:489784kB active_file:128kB inactive_file:716kB unevictable:0kB present:2052192kB pages_scanned:0 all_unreclaimable? no
Mar  4 21:55:06 venus kernel: [134989.510546] lowmem_reserve[]: 0 0 0 0
Mar  4 21:55:06 venus kernel: [134989.510548] DMA: 3*4kB 3*8kB 3*16kB 3*32kB 3*64kB 1*128kB 2*256kB 1*512kB 1*1024kB 0*2048kB 1*4096kB = 6644kB
Mar  4 21:55:06 venus kernel: [134989.510553] DMA32: 124*4kB 10*8kB 3*16kB 1*32kB 1*64kB 2*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 1*4096kB = 6096kB
Mar  4 21:55:06 venus kernel: [134989.510559] 1093 total pagecache pages
Mar  4 21:55:06 venus kernel: [134989.510560] 0 pages in swap cache
Mar  4 21:55:06 venus kernel: [134989.510561] Swap cache stats: add 0, delete 0, find 0/0
Mar  4 21:55:06 venus kernel: [134989.510562] Free swap  = 0kB
Mar  4 21:55:06 venus kernel: [134989.510562] Total swap = 0kB
Mar  4 21:55:06 venus kernel: [134989.516559] 524272 pages RAM
Mar  4 21:55:06 venus kernel: [134989.516561] 15612 pages reserved
Mar  4 21:55:06 venus kernel: [134989.516562] 57357 pages shared
Mar  4 21:55:06 venus kernel: [134989.516562] 502786 pages non-shared
Mar  4 21:55:06 venus kernel: [134989.516565] Out of memory: kill process 23943 (apache2) score 74140 or a child
Mar  4 21:55:06 venus kernel: [134989.516799] Killed process 23943 (apache2)
Mar  4 21:55:16 venus kernel: [135000.400485] mysqld invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
Mar  4 21:55:16 venus kernel: [135000.400489] Pid: 21579, comm: mysqld Not tainted 2.6.28-18-server #59-Ubuntu
Mar  4 21:55:16 venus kernel: [135000.400491] Call Trace:
Mar  4 21:55:16 venus kernel: [135000.400498]  [<ffffffff802b3825>] oom_kill_process+0x95/0x240
Mar  4 21:55:16 venus kernel: [135000.400501]  [<ffffffff802b3fdf>] ? select_bad_process+0xef/0x130
Mar  4 21:55:16 venus kernel: [135000.400503]  [<ffffffff802b40d4>] out_of_memory+0xb4/0x150
Mar  4 21:55:16 venus kernel: [135000.400505]  [<ffffffff802b6c49>] __alloc_pages_internal+0x4a9/0x4f0
Mar  4 21:55:16 venus kernel: [135000.400508]  [<ffffffff802b9a7a>] __do_page_cache_readahead+0xda/0x210
Mar  4 21:55:16 venus kernel: [135000.400511]  [<ffffffff802b9c0e>] do_page_cache_readahead+0x5e/0x90
Mar  4 21:55:16 venus kernel: [135000.400513]  [<ffffffff802b201a>] filemap_fault+0x34a/0x430
Mar  4 21:55:16 venus kernel: [135000.400516]  [<ffffffff802c6010>] __do_fault+0x50/0x520
Mar  4 21:55:16 venus kernel: [135000.400519]  [<ffffffff802c7199>] handle_mm_fault+0x1e9/0x470
Mar  4 21:55:16 venus kernel: [135000.400523]  [<ffffffff8069959c>] ? thread_return+0x37/0x36b
Mar  4 21:55:16 venus kernel: [135000.400526]  [<ffffffff8069e0d7>] do_page_fault+0x307/0x780
Mar  4 21:55:16 venus kernel: [135000.400530]  [<ffffffff8025e70d>] ? __dequeue_signal+0xed/0x210
Mar  4 21:55:16 venus kernel: [135000.400532]  [<ffffffff8025eabb>] ? dequeue_signal+0x17b/0x180
Mar  4 21:55:16 venus kernel: [135000.400534]  [<ffffffff8025ebdd>] ? sys_rt_sigtimedwait+0x11d/0x290
Mar  4 21:55:16 venus kernel: [135000.400546]  [<ffffffff803d0bc1>] ? security_file_permission+0x11/0x20
Mar  4 21:55:16 venus kernel: [135000.400548]  [<ffffffff802556cc>] ? do_setitimer+0x37c/0x3b0
Mar  4 21:55:16 venus kernel: [135000.400551]  [<ffffffff8069b1c1>] ? _spin_lock_irq+0x11/0x20
Mar  4 21:55:16 venus kernel: [135000.400553]  [<ffffffff8025d251>] ? sigprocmask+0x91/0x110
Mar  4 21:55:16 venus kernel: [135000.400556]  [<ffffffff8069b6ba>] error_exit+0x0/0x70
Mar  4 21:55:16 venus kernel: [135000.400557] Mem-Info:
Mar  4 21:55:16 venus kernel: [135000.400559] DMA per-cpu:
Mar  4 21:55:16 venus kernel: [135000.400560] CPU    0: hi:    0, btch:   1 usd:   0
Mar  4 21:55:16 venus kernel: [135000.400561] CPU    1: hi:    0, btch:   1 usd:   0
Mar  4 21:55:16 venus kernel: [135000.400562] DMA32 per-cpu:
Mar  4 21:55:16 venus kernel: [135000.400564] CPU    0: hi:  186, btch:  31 usd: 176
Mar  4 21:55:16 venus kernel: [135000.400565] CPU    1: hi:  186, btch:  31 usd: 153
Mar  4 21:55:16 venus kernel: [135000.400567] Active_anon:366292 active_file:32 inactive_anon:122043
Mar  4 21:55:16 venus kernel: [135000.400568]  inactive_file:1 unevictable:0 dirty:0 writeback:0 unstable:0
Mar  4 21:55:16 venus kernel: [135000.400569]  free:3077 slab:4648 mapped:1 pagetables:6178 bounce:0
Mar  4 21:55:16 venus kernel: [135000.400571] DMA free:6644kB min:12kB low:12kB high:16kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB present:5588kB pages_scanned:0 all_unreclaimable? yes
Mar  4 21:55:16 venus kernel: [135000.400573] lowmem_reserve[]: 0 2004 2004 2004
Mar  4 21:55:16 venus kernel: [135000.400577] DMA32 free:5664kB min:5720kB low:7148kB high:8580kB active_anon:1465168kB inactive_anon:488172kB active_file:128kB inactive_file:4kB unevictable:0kB present:2052192kB pages_scanned:5902178 all_unreclaimable? yes
Mar  4 21:55:16 venus kernel: [135000.400579] lowmem_reserve[]: 0 0 0 0
Mar  4 21:55:16 venus kernel: [135000.400581] DMA: 3*4kB 3*8kB 3*16kB 3*32kB 3*64kB 1*128kB 2*256kB 1*512kB 1*1024kB 0*2048kB 1*4096kB = 6644kB
Mar  4 21:55:16 venus kernel: [135000.400586] DMA32: 10*4kB 15*8kB 2*16kB 1*32kB 1*64kB 2*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 1*4096kB = 5664kB
Mar  4 21:55:16 venus kernel: [135000.400591] 902 total pagecache pages
Mar  4 21:55:16 venus kernel: [135000.400593] 0 pages in swap cache
Mar  4 21:55:16 venus kernel: [135000.400594] Swap cache stats: add 0, delete 0, find 0/0
Mar  4 21:55:16 venus kernel: [135000.400595] Free swap  = 0kB
Mar  4 21:55:16 venus kernel: [135000.400595] Total swap = 0kB
Mar  4 21:55:16 venus kernel: [135000.406555] 524272 pages RAM
Mar  4 21:55:16 venus kernel: [135000.406557] 15612 pages reserved
Mar  4 21:55:16 venus kernel: [135000.406557] 57716 pages shared
Mar  4 21:55:16 venus kernel: [135000.406558] 501175 pages non-shared
Mar  4 21:55:16 venus kernel: [135000.406561] Out of memory: kill process 23729 (apache2) score 74827 or a child
Mar  4 21:55:16 venus kernel: [135000.406804] Killed process 23729 (apache2)
Mar  4 21:55:26 venus /USR/SBIN/CRON[24026]: (www-data) CMD ([ -f /usr/share/moodle/admin/cron.php ] && /usr/bin/php -f /usr/share/moodle/admin/cron.php > /dev/null)
Mar  4 21:55:52 venus kernel: [135018.680217] console-kit-dae invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
Mar  4 21:55:52 venus kernel: [135018.680221] Pid: 4435, comm: console-kit-dae Not tainted 2.6.28-18-server #59-Ubuntu
Mar  4 21:55:52 venus kernel: [135018.680223] Call Trace:
Mar  4 21:55:52 venus kernel: [135018.680230]  [<ffffffff802b3825>] oom_kill_process+0x95/0x240
Mar  4 21:55:52 venus kernel: [135018.680232]  [<ffffffff802b3fdf>] ? select_bad_process+0xef/0x130
Mar  4 21:55:52 venus kernel: [135018.680235]  [<ffffffff802b40d4>] out_of_memory+0xb4/0x150
Mar  4 21:55:52 venus kernel: [135018.680237]  [<ffffffff802b6c49>] __alloc_pages_internal+0x4a9/0x4f0
Mar  4 21:55:52 venus kernel: [135018.680240]  [<ffffffff802b9a7a>] __do_page_cache_readahead+0xda/0x210
Mar  4 21:55:52 venus kernel: [135018.680243]  [<ffffffff802b9c0e>] do_page_cache_readahead+0x5e/0x90
Mar  4 21:55:52 venus kernel: [135018.680245]  [<ffffffff802b201a>] filemap_fault+0x34a/0x430
Mar  4 21:55:52 venus kernel: [135018.680248]  [<ffffffff802c6010>] __do_fault+0x50/0x520
Mar  4 21:55:52 venus kernel: [135018.680251]  [<ffffffff80239932>] ? ptep_set_access_flags+0x42/0x60
Mar  4 21:55:52 venus kernel: [135018.680253]  [<ffffffff802c7199>] handle_mm_fault+0x1e9/0x470
Mar  4 21:55:52 venus kernel: [135018.680256]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
Mar  4 21:55:52 venus kernel: [135018.680260]  [<ffffffff8069e0d7>] do_page_fault+0x307/0x780
Mar  4 21:55:52 venus kernel: [135018.680262]  [<ffffffff802f954a>] ? __d_free+0x3a/0x60
Mar  4 21:55:52 venus kernel: [135018.680264]  [<ffffffff802f95c0>] ? d_free+0x50/0x60
Mar  4 21:55:52 venus kernel: [135018.680267]  [<ffffffff802198f6>] ? read_tsc+0x16/0x40
Mar  4 21:55:52 venus kernel: [135018.680272]  [<ffffffff80270a39>] ? getnstimeofday+0x59/0xe0
Mar  4 21:55:52 venus kernel: [135018.680274]  [<ffffffff8026c6b9>] ? ktime_get_ts+0x59/0x60
Mar  4 21:55:52 venus kernel: [135018.680278]  [<ffffffff802f79a0>] ? poll_select_set_timeout+0x80/0x90
Mar  4 21:55:52 venus kernel: [135018.680282]  [<ffffffff8069b6ba>] error_exit+0x0/0x70
Mar  4 21:55:52 venus kernel: [135018.680283] Mem-Info:
Mar  4 21:55:52 venus kernel: [135018.680285] DMA per-cpu:
Mar  4 21:55:52 venus kernel: [135018.680286] CPU    0: hi:    0, btch:   1 usd:   0
Mar  4 21:55:52 venus kernel: [135018.680287] CPU    1: hi:    0, btch:   1 usd:   0
Mar  4 21:55:52 venus kernel: [135018.680288] DMA32 per-cpu:
Mar  4 21:55:52 venus kernel: [135018.680289] CPU    0: hi:  186, btch:  31 usd: 184
Mar  4 21:55:52 venus kernel: [135018.680290] CPU    1: hi:  186, btch:  31 usd: 173
Mar  4 21:55:52 venus kernel: [135018.680293] Active_anon:366485 active_file:0 inactive_anon:122091
Mar  4 21:55:52 venus kernel: [135018.680300]  inactive_file:37 unevictable:0 dirty:0 writeback:0 unstable:0
Mar  4 21:55:52 venus kernel: [135018.680301]  free:3073 slab:4667 mapped:1 pagetables:6299 bounce:0
Mar  4 21:55:52 venus kernel: [135018.680303] DMA free:6644kB min:12kB low:12kB high:16kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB present:5588kB pages_scanned:0 all_unreclaimable? yes
Mar  4 21:55:52 venus kernel: [135018.680305] lowmem_reserve[]: 0 2004 2004 2004
Mar  4 21:55:52 venus kernel: [135018.680309] DMA32 free:5648kB min:5720kB low:7148kB high:8580kB active_anon:1465940kB inactive_anon:488364kB active_file:0kB inactive_file:148kB unevictable:0kB present:2052192kB pages_scanned:4617580 all_unreclaimable? yes
Mar  4 21:55:52 venus kernel: [135018.680312] lowmem_reserve[]: 0 0 0 0
Mar  4 21:55:52 venus kernel: [135018.680314] DMA: 3*4kB 3*8kB 3*16kB 3*32kB 3*64kB 1*128kB 2*256kB 1*512kB 1*1024kB 0*2048kB 1*4096kB = 6644kB
Mar  4 21:55:52 venus kernel: [135018.680319] DMA32: 2*4kB 13*8kB 4*16kB 1*32kB 1*64kB 2*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 1*4096kB = 5648kB
Mar  4 21:55:52 venus kernel: [135018.680325] 906 total pagecache pages
Mar  4 21:55:52 venus kernel: [135018.680326] 0 pages in swap cache
Mar  4 21:55:52 venus kernel: [135018.680327] Swap cache stats: add 0, delete 0, find 0/0
Mar  4 21:55:52 venus kernel: [135018.680328] Free swap  = 0kB
Mar  4 21:55:52 venus kernel: [135018.680329] Total swap = 0kB
Mar  4 21:55:52 venus kernel: [135018.686261] 524272 pages RAM
Mar  4 21:55:52 venus kernel: [135018.686263] 15612 pages reserved
Mar  4 21:55:52 venus kernel: [135018.686264] 57942 pages shared
Mar  4 21:55:52 venus kernel: [135018.686265] 501114 pages non-shared
Mar  4 21:55:52 venus kernel: [135018.686267] Out of memory: kill process 23877 (apache2) score 75573 or a child
Mar  4 21:55:52 venus kernel: [135018.686504] Killed process 23877 (apache2)
Mar  4 21:55:52 venus kernel: [135030.900265] snmpd invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
Mar  4 21:55:52 venus kernel: [135030.900269] Pid: 3034, comm: snmpd Not tainted 2.6.28-18-server #59-Ubuntu
Mar  4 21:55:52 venus kernel: [135030.900270] Call Trace:
Mar  4 21:55:52 venus kernel: [135030.900277]  [<ffffffff802b3825>] oom_kill_process+0x95/0x240
Mar  4 21:55:52 venus kernel: [135030.900280]  [<ffffffff802b3fdf>] ? select_bad_process+0xef/0x130
Mar  4 21:55:52 venus kernel: [135030.900282]  [<ffffffff802b40d4>] out_of_memory+0xb4/0x150
Mar  4 21:55:52 venus kernel: [135030.900285]  [<ffffffff802b6c49>] __alloc_pages_internal+0x4a9/0x4f0
Mar  4 21:55:52 venus kernel: [135030.900288]  [<ffffffff802b9a7a>] __do_page_cache_readahead+0xda/0x210
Mar  4 21:55:52 venus kernel: [135030.900290]  [<ffffffff802b9c0e>] do_page_cache_readahead+0x5e/0x90
Mar  4 21:55:52 venus kernel: [135030.900292]  [<ffffffff802b201a>] filemap_fault+0x34a/0x430
Mar  4 21:55:52 venus kernel: [135030.900296]  [<ffffffff802c6010>] __do_fault+0x50/0x520
Mar  4 21:55:52 venus kernel: [135030.900298]  [<ffffffff802c7199>] handle_mm_fault+0x1e9/0x470
Mar  4 21:55:52 venus kernel: [135030.900301]  [<ffffffff802f7915>] ? set_fd_set+0x25/0x30
Mar  4 21:55:52 venus kernel: [135030.900303]  [<ffffffff802f8900>] ? core_sys_select+0x1e0/0x2a0
Mar  4 21:55:52 venus kernel: [135030.900306]  [<ffffffff8069e0d7>] do_page_fault+0x307/0x780
Mar  4 21:55:52 venus kernel: [135030.900310]  [<ffffffff802198f6>] ? read_tsc+0x16/0x40
Mar  4 21:55:52 venus kernel: [135030.900314]  [<ffffffff80270a39>] ? getnstimeofday+0x59/0xe0
Mar  4 21:55:52 venus kernel: [135030.900315]  [<ffffffff8026c6b9>] ? ktime_get_ts+0x59/0x60
Mar  4 21:55:52 venus kernel: [135030.900318]  [<ffffffff802f74b7>] ? poll_select_copy_remaining+0xf7/0x150
Mar  4 21:55:52 venus kernel: [135030.900320]  [<ffffffff802f8c2c>] ? sys_select+0x5c/0x110
Mar  4 21:55:52 venus kernel: [135030.900323]  [<ffffffff8069b6ba>] error_exit+0x0/0x70
Mar  4 21:55:52 venus kernel: [135030.900324] Mem-Info:
Mar  4 21:55:52 venus kernel: [135030.900325] DMA per-cpu:
Mar  4 21:55:52 venus kernel: [135030.900327] CPU    0: hi:    0, btch:   1 usd:   0
Mar  4 21:55:52 venus kernel: [135030.900328] CPU    1: hi:    0, btch:   1 usd:   0
Mar  4 21:55:52 venus kernel: [135030.900329] DMA32 per-cpu:
Mar  4 21:55:52 venus kernel: [135030.900330] CPU    0: hi:  186, btch:  31 usd: 136
Mar  4 21:55:52 venus kernel: [135030.900331] CPU    1: hi:  186, btch:  31 usd: 150
Mar  4 21:55:52 venus kernel: [135030.900334] Active_anon:362660 active_file:1341 inactive_anon:120924
Mar  4 21:55:52 venus kernel: [135030.900334]  inactive_file:4561 unevictable:0 dirty:0 writeback:0 unstable:0
Mar  4 21:55:52 venus kernel: [135030.900335]  free:3101 slab:4695 mapped:1535 pagetables:6264 bounce:0
Mar  4 21:55:52 venus kernel: [135030.900337] DMA free:6644kB min:12kB low:12kB high:16kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB present:5588kB pages_scanned:0 all_unreclaimable? yes
Mar  4 21:55:52 venus kernel: [135030.900339] lowmem_reserve[]: 0 2004 2004 2004
Mar  4 21:55:52 venus kernel: [135030.900343] DMA32 free:5760kB min:5720kB low:7148kB high:8580kB active_anon:1450640kB inactive_anon:483696kB active_file:5364kB inactive_file:18244kB unevictable:0kB present:2052192kB pages_scanned:0 all_unreclaimable? no
Mar  4 21:55:52 venus kernel: [135030.900345] lowmem_reserve[]: 0 0 0 0
Mar  4 21:55:52 venus kernel: [135030.900347] DMA: 3*4kB 3*8kB 3*16kB 3*32kB 3*64kB 1*128kB 2*256kB 1*512kB 1*1024kB 0*2048kB 1*4096kB = 6644kB
Mar  4 21:55:52 venus kernel: [135030.900355] DMA32: 71*4kB 2*8kB 2*16kB 1*32kB 1*64kB 2*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 1*4096kB = 5804kB
Mar  4 21:55:52 venus kernel: [135030.900361] 6816 total pagecache pages
Mar  4 21:55:52 venus kernel: [135030.900362] 0 pages in swap cache
Mar  4 21:55:52 venus kernel: [135030.900363] Swap cache stats: add 0, delete 0, find 0/0
Mar  4 21:55:52 venus kernel: [135030.900364] Free swap  = 0kB
Mar  4 21:55:52 venus kernel: [135030.900364] Total swap = 0kB
Mar  4 21:55:52 venus kernel: [135030.906667] 524272 pages RAM
Mar  4 21:55:52 venus kernel: [135030.906669] 15612 pages reserved
Mar  4 21:55:52 venus kernel: [135030.906670] 67007 pages shared
Mar  4 21:55:52 venus kernel: [135030.906670] 499368 pages non-shared
Mar  4 21:55:52 venus kernel: [135030.906673] Out of memory: kill process 23921 (apache2) score 75262 or a child
Mar  4 21:55:52 venus kernel: [135030.906910] Killed process 23921 (apache2)
Mar  4 21:55:53 venus nrpe[24041]: Error: Could not complete SSL handshake. 5 
Mar  4 21:55:53 venus dhcpd: DHCPDISCOVER from 00:1c:10:b6:e7:f6 via 10.0.4.1
Mar  4 21:55:53 venus dhcpd: DHCPOFFER on 10.0.4.2 to 00:1c:10:b6:e7:f6 via 10.0.4.1
Mar  4 21:55:53 venus dhcpd: DHCPDISCOVER from 00:1c:10:b6:e7:f6 via 10.0.4.1
Mar  4 21:55:53 venus dhcpd: DHCPOFFER on 10.0.4.2 to 00:1c:10:b6:e7:f6 via 10.0.4.1
Mar  4 21:55:53 venus dhcpd: DHCPDISCOVER from 00:1c:10:b6:e7:f6 via 10.0.4.1
Mar  4 21:55:53 venus dhcpd: DHCPOFFER on 10.0.4.2 to 00:1c:10:b6:e7:f6 via 10.0.4.1
Mar  4 21:55:53 venus dhcpd: DHCPDISCOVER from 00:1c:10:b6:e7:f6 via 10.0.4.1
Mar  4 21:55:53 venus dhcpd: DHCPOFFER on 10.0.4.2 to 00:1c:10:b6:e7:f6 via 10.0.4.1
Mar  4 21:55:57 venus dhcpd: DHCPDISCOVER from 00:1c:10:b6:e7:f6 via 10.0.4.1
Mar  4 21:55:57 venus dhcpd: DHCPOFFER on 10.0.4.2 to 00:1c:10:b6:e7:f6 via 10.0.4.1

```

I can't see why this is happening.
I've tried to turn off swap to make the system more stable, but it didn't work.

Any hint?

Thanks

---

### Post by kanikilu on 2010-03-04
I was going to ask if you were up to date, but it looks like you are running the latest server kernel (linux-image-2.6.28-18-server), so there goes that suggestion ;)

This is a little over my head, but you said this happens with and without swap enabled, so I think my first inclination would be that there's an application that has a memory leak. Have you watched top/htop/[insert favorite process monitor here] to see what's eating up all your memory? Have you changed anything recently in regards to versions of the services you mentioned (e.g. mysqld, apache2, etc) or installed/updated/changed any related addons or modules to those services (such as an apache module)?

The easy part will be seeing what's chewing up memory and not freeing it since you said it happens so frequently...the hard part will be fixing it ;)

---

### Post by tgalati4 on 2010-03-04
man vmstat

---

### Post by flipybcn on 2010-03-05
> **kanikilu said:**
> I was going to ask if you were up to date, but it looks like you are running the latest server kernel (linux-image-2.6.28-18-server), so there goes that suggestion ;)

This is a little over my head, but you said this happens with and without swap enabled, so I think my first inclination would be that there's an application that has a memory leak. Have you watched top/htop/[insert favorite process monitor here] to see what's eating up all your memory? Have you changed anything recently in regards to versions of the services you mentioned (e.g. mysqld, apache2, etc) or installed/updated/changed any related addons or modules to those services (such as an apache module)?

The easy part will be seeing what's chewing up memory and not freeing it since you said it happens so frequently...the hard part will be fixing it ;)

Yes, but how can I monitor memory usage when it happens randomly?
I'll try to find out if top/htop/vmstat can output to some file.
And I didn't change anyhting. In fact, I've removed some other services (such as squid) to see if it helped.

Thanks for your answer!

---

### Post by KiLaHuRtZ on 2010-03-05
Is Apache running secure code?  Sounds to me like a fork bomb or some variant.  At various time intervals since boot, do you see the total number of processes increasing at all?

---

### Post by flipybcn on 2010-03-17
> **KiLaHuRtZ said:**
> Is Apache running secure code?  Sounds to me like a fork bomb or some variant.  At various time intervals since boot, do you see the total number of processes increasing at all?

Well, Apache2 works with its default configuration (I guess not with secure code).
And yes, it increases the number of apache processes, but I've thought they were requests from clients.

---

### Post by Zeosa on 2010-03-17
> **flipybcn said:**
> Yes, but how can I monitor memory usage when it happens randomly?




I use Munin for just this occasion, makes it pretty simple to go back in time (so to speak) and see what the condition of important system parameters were at the time of the fault.

---

### Post by flipybcn on 2010-03-17
Today crashed again.
This is the last top output I've had (I was using top -b -d 15 > output).

```
top - 16:40:41 up 2 days,  1:06,  1 user,  load average: 13.80, 4.46, 2.27
Tasks: 169 total,  23 running, 146 sleeping,   0 stopped,   0 zombie
Cpu(s): 64.4%us, 17.0%sy,  0.0%ni,  0.0%id, 18.2%wa,  0.1%hi,  0.3%si,  0.0%st
Mem:   3055772k total,  3041172k used,    14600k free,      128k buffers
Swap:   905208k total,   905208k used,        0k free,     8396k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 2695 mysql     20   0  418m  59m  176 D    9  2.0 120:46.39 mysqld                                                                                          
20333 www-data  20   0  307m 100m   36 R    9  3.4   0:02.33 apache2                                                                                         
20381 www-data  20   0  300m  94m   28 R    9  3.2   0:02.75 apache2                                                                                         
20538 www-data  20   0  293m  87m   24 R    9  2.9   0:01.67 apache2                                                                                         
20537 www-data  20   0  299m  93m   24 R    9  3.1   0:01.63 apache2                                                                                         
20522 www-data  20   0  294m  88m   24 R    8  3.0   0:01.54 apache2                                                                                         
20523 www-data  20   0  295m  88m   24 R    8  3.0   0:01.53 apache2                                                                                         
20398 www-data  20   0  299m  94m  492 R    8  3.2   0:05.75 apache2                                                                                         
20329 www-data  20   0  306m  97m  496 R    8  3.3   0:07.06 apache2                                                                                         
20400 www-data  20   0  294m  88m   24 R    8  3.0   0:06.23 apache2                                                                                         
20459 www-data  20   0  290m  85m   24 R    8  2.9   0:01.60 apache2                                                                                         
20467 www-data  20   0  302m  96m  492 R    8  3.2   0:01.54 apache2                                                                                         
20396 www-data  20   0  305m  96m  496 R    8  3.2   0:03.65 apache2                                                                                         
19241 www-data  20   0  304m  95m  504 R    8  3.2   0:11.32 apache2                                                                                         
20380 www-data  20   0  297m  92m  504 R    7  3.1   0:04.10 apache2                                                                                         
20539 www-data  20   0  293m  88m  492 R    7  3.0   0:01.27 apache2                                                                                         
20417 www-data  20   0  293m  88m  492 R    7  3.0   0:03.53 apache2                                                                                         
20414 www-data  20   0  280m  75m  492 R    5  2.5   0:05.04 apache2                                                                                         
20544 www-data  20   0  274m  68m  400 D    5  2.3   0:00.85 apache2                                                                                         
20542 www-data  20   0  272m  67m  488 D    5  2.3   0:00.81 apache2                                                                                         
   32 root      15  -5     0    0    0 R    3  0.0   0:08.08 kswapd0                                                                                         
20545 www-data  20   0  228m  24m  600 D    3  0.8   0:00.41 apache2                                                                                         
20301 www-data  20   0  230m  21m   48 S    1  0.7   0:11.55 apache2                                                                                         
20536 www-data  20   0  225m  21m  760 R    1  0.7   0:00.32 apache2                                                                                         
19711 www-data  20   0  237m  25m   32 S    1  0.9   0:28.20 apache2                                                                                         
20458 www-data  20   0  227m  22m  176 D    1  0.8   0:00.34 apache2                                                                                         
20328 www-data  20   0  214m 9108  164 D    0  0.3   0:12.90 apache2                                                                                         
20403 www-data  20   0  236m  28m   28 S    0  1.0   0:01.15 apache2                                                                                         
 3072 snmp      20   0 45644  580  108 R    0  0.0   0:20.49 snmpd                                                                                           
20395 www-data  20   0  212m 8148   36 S    0  0.3   0:04.62 apache2                                                                                         
   31 root      20   0     0    0    0 S    0  0.0   0:01.74 pdflush                                                                                         
    1 root      20   0  4104   40    4 S    0  0.0   0:03.22 init                                                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.10 migration/0                                                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:00.26 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.08 migration/1                                                                                     
    7 root      15  -5     0    0    0 S    0  0.0   0:00.74 ksoftirqd/1                                                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.24 events/0                                                                                        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.39 events/1                                                                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0                                                                                         
   13 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/1                                                                                         
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                                   
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                                                                                   
   16 root      15  -5     0    0    0 S    0  0.0   0:00.02 kblockd/0                                                                                       
   17 root      15  -5     0    0    0 S    0  0.0   0:00.02 kblockd/1                                                                                       
   18 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                          
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                    
   20 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue                                                                                          
   21 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/0                                                                                           
   22 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/1                                                                                           
   23 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                         
   24 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                   
   25 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                           
   26 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                         
   27 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmmcd                                                                                           
   28 root      15  -5     0    0    0 S    0  0.0   0:00.00 btaddconn                                                                                       
   29 root      15  -5     0    0    0 S    0  0.0   0:00.00 btdelconn                                                                                       
   30 root      20   0     0    0    0 S    0  0.0   0:01.43 pdflush                                                                                         
   33 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                           
   34 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                           
   35 root      15  -5     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                                                                 
   38 root      15  -5     0    0    0 S    0  0.0   0:00.00 pciehpd                                                                                         
   39 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                       
   40 root      15  -5     0    0    0 S    0  0.0   0:00.02 scsi_eh_1                                                                                       
   41 root      15  -5     0    0    0 S    0  0.0   0:00.00 kstriped                                                                                        
   42 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmpathd/0                                                                                       
   43 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmpathd/1                                                                                       
   44 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmpath_handlerd                                                                                 
   45 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksnapd                                                                                          
   46 root      15  -5     0    0    0 S    0  0.0   0:00.00 kondemand/0                                                                                     
   47 root      15  -5     0    0    0 S    0  0.0   0:00.00 kondemand/1                                                                                     
   48 root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd                                                                                        
  324 root      15  -5     0    0    0 S    0  0.0   0:00.01 mpt_poll_0                                                                                      
  765 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                                                       
  810 root      15  -5     0    0    0 S    0  0.0   0:00.00 kdmflush                                                                                        
  817 root      15  -5     0    0    0 S    0  0.0   0:00.00 kdmflush                                                                                        
  851 root      15  -5     0    0    0 S    0  0.0   0:07.14 kjournald2                                                                                      
  971 root      16  -4 10464    4    0 S    0  0.0   0:00.02 udevd                                                                                           
 1687 root      15  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                                                       
 2309 root      20   0  3944    8    4 S    0  0.0   0:00.00 getty                                                                                           
 2310 root      20   0  3944    8    4 S    0  0.0   0:00.00 getty                                                                                           
 2313 root      20   0  3944    8    4 S    0  0.0   0:00.00 getty                                                                                           
 2316 root      20   0  3944    8    4 S    0  0.0   0:00.01 getty                                                                                           
 2317 root      20   0  3944    8    4 S    0  0.0   0:00.00 getty                                                                                           
 2362 bind      20   0  196m 7792  136 S    0  0.3   0:11.33 named                                                                                           
 2490 root      20   0  3944    4    0 S    0  0.0   0:00.00 acpid                                                                                           
 2524 syslog    20   0 48164   96    4 S    0  0.0   0:01.59 syslogd                                                                                         
 2542 root      20   0  8204    8    4 S    0  0.0   0:00.05 dd                                                                                              
 2544 klog      20   0  6480    4    0 S    0  0.0   0:00.09 klogd                                                                                           
 2562 messageb  20   0 52944  148    4 S    0  0.0   0:00.67 dbus-daemon                                                                                     
 2605 root      20   0 44768   84    0 S    0  0.0   0:00.12 sshd                                                                                            
 2653 root      20   0  4024    8    4 S    0  0.0   0:00.00 mysqld_safe                                                                                     
 2696 root      20   0  3924    8    4 S    0  0.0   0:00.00 logger                                                                                          
 2923 root      20   0     0    0    0 S    0  0.0   0:10.38 vmmemctl                                                                                        
 2991 ntp       18  -2 25592  184   44 S    0  0.0   0:00.03 ntpd                                                                                            
 3039 root      20   0 17732  244   68 S    0  0.0   0:17.99 vmware-guestd                                                                                   
 3057 nagios    20   0 54308  124   68 S    0  0.0   0:01.35 nrpe                                                                                            
 3108 dhcpd     20   0 16276  480    4 S    0  0.0   0:02.44 dhcpd3                                                                                          
 3160 daemon    20   0 10196   12    0 S    0  0.0   0:00.00 atd                                                                                             
 3185 root      20   0 13644  108    4 S    0  0.0   0:00.09 cron                                                                                            
 3204 root      20   0  207m 3400  132 S    0  0.1   0:06.30 apache2                                                                                         
 3223 root      20   0  206m 2016   20 S    0  0.1   0:15.47 fail2ban-server                                                                                 
 3260 root      20   0  3944    8    4 S    0  0.0   0:00.00 getty                                                                                           
 3304 root      20   0  103m 1284    4 S    0  0.0   0:02.90 console-kit-dae                                                                                 
 3437 root      20   0 21176    8    4 S    0  0.0   0:00.00 screen.real                                                                                     
 3438 root      20   0  4024    8    4 S    0  0.0   0:00.00 motd+shell                                                                                      
 3465 root      20   0 13988    8    4 S    0  0.0   0:00.07 bash                                                                                            
 7056 root      20   0 99084   24    4 S    0  0.0   0:00.02 sshd                                                                                            
 7066 octavio   20   0 99220  332  208 S    0  0.0   0:00.02 sshd                                                                                            
 7067 octavio   20   0 55448    8    4 S    0  0.0   0:00.03 bash                                                                                            
 7506 root      20   0 54920  520  248 R    0  0.0   0:04.28 top                                                                                             
19216 www-data  20   0  240m 2072   36 S    0  0.1   0:25.65 apache2                                                                                         
19365 www-data  20   0  225m 2156   36 S    0  0.1   0:16.05 apache2                                                                                         
19367 www-data  20   0  226m 2168   36 S    0  0.1   0:06.81 apache2                                                                                         
19389 www-data  20   0  317m 102m   36 S    0  3.4   0:02.09 apache2                                                                                         
19413 www-data  20   0  223m 2316   28 S    0  0.1   0:34.03 apache2                                                                                         
19434 www-data  20   0  223m 2596   24 S    0  0.1   0:04.23 apache2                                                                                         
19453 www-data  20   0  239m 2164   28 S    0  0.1   0:16.03 apache2                                                                                         
19708 www-data  20   0  253m 2136   36 S    0  0.1   0:06.08 apache2                                                                                         
19720 www-data  20   0  223m 2808   28 S    0  0.1   0:00.25 apache2                                                                                         
19849 www-data  20   0  233m 2132   28 S    0  0.1   0:06.57 apache2                                                                                         
19866 www-data  20   0  319m  31m   96 D    0  1.1   0:08.25 apache2                                                                                         
19871 www-data  20   0  229m 2132   28 S    0  0.1   0:02.55 apache2                                                                                         
19919 www-data  20   0  325m 2268   72 D    0  0.1   0:11.94 apache2                                                                                         
19922 www-data  20   0  274m 2756   28 S    0  0.1   0:02.08 apache2                                                                                         
19924 www-data  20   0  237m  10m   32 S    0  0.4   0:09.04 apache2                                                                                         
19965 www-data  20   0  222m 3124   24 S    0  0.1   0:00.06 apache2                                                                                         
20086 www-data  20   0  222m 3128   24 S    0  0.1   0:00.08 apache2                                                                                         
20089 www-data  20   0  225m 2180   28 S    0  0.1   0:04.45 apache2                                                                                         
20139 www-data  20   0  245m  21m   44 S    0  0.7   0:16.33 apache2                                                                                         
20161 www-data  20   0  318m 104m   24 S    0  3.5   0:02.13 apache2                                                                                         
20163 www-data  20   0  232m 2044   28 S    0  0.1   0:01.25 apache2                                                                                         
20170 www-data  20   0  231m  22m   44 S    0  0.8   0:04.36 apache2                                                                                         
20177 www-data  20   0  225m 2368   28 S    0  0.1   0:06.25 apache2                                                                                         
20237 www-data  20   0  248m  20m   32 S    0  0.7   0:03.16 apache2                                                                                         
20239 www-data  20   0  321m  90m   36 S    0  3.0   0:04.23 apache2                                                                                         
20240 www-data  20   0  226m  17m   28 S    0  0.6   0:00.16 apache2                                                                                         
20242 www-data  20   0  226m  15m  144 R    0  0.5   0:04.89 apache2                                                                                         
20246 www-data  20   0  226m 8740   28 S    0  0.3   0:00.32 apache2                                                                                         
20247 www-data  20   0  238m  20m   28 S    0  0.7   0:03.46 apache2                                                                                         
20249 www-data  20   0  317m  20m   36 S    0  0.7   0:02.00 apache2                                                                                         
20293 www-data  20   0  222m  17m   24 S    0  0.6   0:00.06 apache2                                                                                         
20294 www-data  20   0  322m 112m   36 S    0  3.8   0:08.47 apache2                                                                                         
20305 www-data  20   0  225m  20m   36 S    0  0.7   0:02.40 apache2                                                                                         
20307 www-data  20   0  222m  16m   36 S    0  0.6   0:00.07 apache2                                                                                         
20311 www-data  20   0  225m  20m   36 S    0  0.7   0:02.38 apache2                                                                                         
20314 www-data  20   0  222m  17m   24 S    0  0.6   0:00.06 apache2                                                                                         
20315 www-data  20   0  233m  21m   36 S    0  0.7   0:02.45 apache2                                                                                         
20317 www-data  20   0  225m  20m   28 S    0  0.7   0:08.63 apache2                                                                                         
20325 www-data  20   0  236m  24m  252 D    0  0.8   0:04.93 apache2                                                                                         
20382 www-data  20   0  222m  18m   28 S    0  0.6   0:06.56 apache2                                                                                         
20388 www-data  20   0  226m  21m   28 S    0  0.7   0:04.65 apache2                                                                                         
20399 www-data  20   0  211m 7240  136 S    0  0.2   0:04.13 apache2                                                                                         
20406 www-data  20   0  219m  11m  132 S    0  0.4   0:00.60 apache2                                                                                         
20410 www-data  20   0  217m  11m  136 S    0  0.4   0:02.47 apache2                                                                                         
20415 www-data  20   0  233m  28m   32 S    0  1.0   0:02.76 apache2                                                                                         
20418 www-data  20   0  318m 112m   24 S    0  3.8   0:02.19 apache2                                                                                         
20419 www-data  20   0  223m  18m   24 S    0  0.6   0:02.34 apache2                                                                                         
20420 www-data  20   0  277m  70m   36 S    0  2.3   0:02.10 apache2                                                                                         
20457 www-data  20   0  220m  12m  184 D    0  0.4   0:00.25 apache2                                                                                         
20466 www-data  20   0  219m  13m  660 R    0  0.5   0:00.07 apache2                                                                                         
20468 www-data  20   0  209m 3824  180 S    0  0.1   0:00.03 apache2                                                                                         
20476 www-data  20   0  209m 3824  180 S    0  0.1   0:00.01 apache2                                                                                         
20547 www-data  20   0  209m 3504   12 S    0  0.1   0:00.00 apache2                                                                                         
20549 root      20   0  207m 3408   48 D    0  0.1   0:00.00 apache2                                                                                         
20550 nagios    20   0 54308  164   64 D    0  0.0   0:00.00 nrpe
```

So there are a lot of apache2 threads, but should be normal, doesn't it?

By the way, the first process to be killed in order to free memory was mysql.

---

### Post by KB1JWQ on 2010-03-17
Many processes, sure-- but not ones that are sucking up 200 MB apiece.

Check your httpd logs and see what the heck's going on there.

---

### Post by jrssystemsnet on 2010-03-17
Yeah, you've got some code available by way of Apache that's leaking memory / allocating massive amounts of memory.  Recently a client of mine had this happen on his server after some offshore programmers set the memory_size_limit to -1 in some PHP code.

I don't have a whole lot helpful for you on ways to isolate WHICH chunk of code is responsible... narrowing that down is a bit of a tricky process.  You might try looking for ridiculously frequent hits to a particular URL in your Apache logs, and/or looking for things under your website directories that "shouldn't be there".

---

### Post by tgalati4 on 2010-03-17
Rather than waiting for the server to crash, monitor the swap file.  When it passes some predetermined value (say 500 MB) then start pruning processes and examining log files.

Write a script that examines your swap file every 10 minutes.  If it exceeds 500 MB then dump some vmstat data and send an email or wall message to take action.

cat /proc/swaps

man gawk

cat /proc/swaps | gawk  '/sda3/ {print $4}'

If above expression is greater than 500 MB then do something.  Your swap device will be different than mine (sda3).

echo "My server is about to crash!!" | wall

---

### Post by flipybcn on 2010-03-18
First, thanks for all your tips/suggestions.

It keeps crashing, no matter what I do. It is pretty unusable since I can't login to it (neither remotely nor local).

Looking at the logs the only thing I see for all the sites we're hosting is a bunch of "file does not exist", but that shouldn't hurt, right?

However, looking at the php configuration I've found that the variable *memory_limit* was set to 128M. I've never used such a high value before, so it must have been a suggestion from a client. I've decided to change it to a safer value (32M).

Since this is pretty critical, I'll try to deploy a HA Cluster with 2 servers.
But, if the error is caused by some code, it will be useless.

I'll keep monitoring this week, checking swap and log files (I'd love to find the problem, but seems that is not going to happen...).

Thanks!

---

### Post by ploum on 2010-03-23
I've exactly the same problem. I monitor swap and memory and nothing special happens. It's very very sudden as I can see on graphs.

So not a leak but more like a fork-bomb.

It's completely random but not once-a-day. More 3 times a week then nothing for one month.

No idea of what it could be.

My log :


Mar 23 16:56:41 localhost kernel: Out of memory: kill process 16678 (apache2) score 17006 or a child
Mar 23 16:56:41 localhost kernel: Killed process 8674 (apache2)
Mar 23 16:56:41 localhost kernel: fail2ban-server invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
Mar 23 16:56:41 localhost kernel: fail2ban-server cpuset=/ mems_allowed=0
Mar 23 16:56:41 localhost kernel: Pid: 22547, comm: fail2ban-server Not tainted 2.6.32.2-xxxx-std-ipv4-32 #1
Mar 23 16:56:41 localhost kernel: Call Trace:
Mar 23 16:56:41 localhost kernel: [] oom_kill_process+0xa0/0x2b0
Mar 23 16:56:41 localhost kernel: [] ? select_bad_process+0xab/0xe0
Mar 23 16:56:41 localhost kernel: [] __out_of_memory+0x4e/0xb0
Mar 23 16:56:41 localhost kernel: [] out_of_memory+0x52/0xa0
Mar 23 16:56:41 localhost kernel: [] __alloc_pages_nodemask+0x527/0x540
Mar 23 16:56:41 localhost kernel: [] __do_page_cache_readahead+0xd2/0x1d0
Mar 23 16:56:41 localhost kernel: [] ra_submit+0x28/0x40
Mar 23 16:56:41 localhost kernel: [] filemap_fault+0x3b0/0x3c0
Mar 23 16:56:41 localhost kernel: [] __do_fault+0x4c/0x460
Mar 23 16:56:41 localhost kernel: [] ? filemap_fault+0x0/0x3c0
Mar 23 16:56:41 localhost kernel: [] handle_mm_fault+0x13c/0x7f0
Mar 23 16:56:41 localhost kernel: [] ? finish_task_switch+0x3a/0xb0
Mar 23 16:56:41 localhost kernel: [] ? ktime_get_ts+0xed/0x110
Mar 23 16:56:41 localhost kernel: [] ? poll_select_copy_remaining+0xc7/0x110
Mar 23 16:56:41 localhost kernel: [] do_page_fault+0x121/0x300
Mar 23 16:56:41 localhost kernel: [] ? sys_select+0x3d/0xb0
Mar 23 16:56:41 localhost kernel: [] ? do_page_fault+0x0/0x300
Mar 23 16:56:41 localhost kernel: [] error_code+0x66/0x6c
Mar 23 16:56:41 localhost kernel: [] ? do_page_fault+0x0/0x300
Mar 23 16:56:41 localhost kernel: Mem-Info:
Mar 23 16:56:41 localhost kernel: DMA per-cpu:
Mar 23 16:56:41 localhost kernel: CPU 0: hi: 0, btch: 1 usd: 0
Mar 23 16:56:41 localhost kernel: CPU 1: hi: 0, btch: 1 usd: 0
Mar 23 16:56:41 localhost kernel: Normal per-cpu:
Mar 23 16:56:41 localhost kernel: CPU 0: hi: 186, btch: 31 usd: 61
Mar 23 16:56:41 localhost kernel: CPU 1: hi: 186, btch: 31 usd: 87
Mar 23 16:56:41 localhost kernel: HighMem per-cpu:
Mar 23 16:56:41 localhost kernel: CPU 0: hi: 42, btch: 7 usd: 27
Mar 23 16:56:41 localhost kernel: CPU 1: hi: 42, btch: 7 usd: 13
Mar 23 16:56:41 localhost kernel: active_anon:113730 inactive_anon:113864 isolated_anon:0
Mar 23 16:56:41 localhost kernel: active_file:555 inactive_file:749 isolated_file:0

---

### Post by ploum on 2010-04-19
It looks like I was simply targetted by some slowloris bots.

Installing libapache2-mod-antiloris allowed me to not reboot anymore.

---

### Post by jhetrick62 on 2010-06-04
Looks to me like you are running zoneminder, possible?  I'm having the same issues so the zoneminder code may be the issue, I haven't found it yet though.

Jeff

---

### Post by tgalati4 on 2010-06-04
Yea, zoneminder is not exactly enterprise-class code.  If you are running zoneminder, then move it another machine or stop it for a month.  If a camera stream gets interrupted, zoneminder (or the video modules) don't exit gracefully--kernel panics!

---

