---
title: "[ubuntu] Something crashes (forcedeth?)"
date: 2010-04-19
forum: Server Platforms
---

### Post by BuryAlex on 2010-04-19
```
Apr 19 10:40:39 revo kernel: [34790.236803] swapper: page allocation failure. order:0, mode:0x4020
Apr 19 10:40:39 revo kernel: [34790.236812] Pid: 0, comm: swapper Not tainted 2.6.32-21-server #32-Ubuntu
Apr 19 10:40:39 revo kernel: [34790.236818] Call Trace:
Apr 19 10:40:39 revo kernel: [34790.236823]  <IRQ>  [<ffffffff810f97de>] __alloc_pages_slowpath+0x56e/0x580
Apr 19 10:40:39 revo kernel: [34790.236849]  [<ffffffff8105a49d>] ? scheduler_tick+0x18d/0x260
Apr 19 10:40:39 revo kernel: [34790.236860]  [<ffffffff8102ed7d>] ? lapic_next_event+0x1d/0x30
Apr 19 10:40:39 revo kernel: [34790.236870]  [<ffffffff81092a94>] ? clockevents_program_event+0x54/0xa0
Apr 19 10:40:39 revo kernel: [34790.236879]  [<ffffffff810f9961>] __alloc_pages_nodemask+0x171/0x180
Apr 19 10:40:39 revo kernel: [34790.236888]  [<ffffffff810940ca>] ? tick_program_event+0x2a/0x30
Apr 19 10:40:39 revo kernel: [34790.236899]  [<ffffffff81088bd0>] ? hrtimer_interrupt+0x130/0x220
Apr 19 10:40:39 revo kernel: [34790.236910]  [<ffffffff8112c597>] alloc_pages_current+0x87/0xd0
Apr 19 10:40:39 revo kernel: [34790.236919]  [<ffffffff81132547>] new_slab+0x2f7/0x310
Apr 19 10:40:39 revo kernel: [34790.236928]  [<ffffffff81013cb3>] ? apic_timer_interrupt+0x13/0x20
Apr 19 10:40:39 revo kernel: [34790.236936]  [<ffffffff81134dc1>] __slab_alloc+0x201/0x2d0
Apr 19 10:40:39 revo kernel: [34790.236946]  [<ffffffff8146687d>] ? dev_alloc_skb+0x1d/0x40
Apr 19 10:40:39 revo kernel: [34790.236955]  [<ffffffff81135d9f>] __kmalloc_node_track_caller+0xaf/0x160
Apr 19 10:40:39 revo kernel: [34790.236963]  [<ffffffff8146687d>] ? dev_alloc_skb+0x1d/0x40
Apr 19 10:40:39 revo kernel: [34790.236971]  [<ffffffff81466590>] __alloc_skb+0x80/0x190
Apr 19 10:40:39 revo kernel: [34790.236979]  [<ffffffff8146687d>] dev_alloc_skb+0x1d/0x40
Apr 19 10:40:39 revo kernel: [34790.237008]  [<ffffffffa0005f27>] nv_alloc_rx_optimized+0x197/0x270 [forcedeth]
Apr 19 10:40:39 revo kernel: [34790.237020]  [<ffffffffa0005237>] ? T.935+0x137/0x2a0 [forcedeth]
Apr 19 10:40:39 revo kernel: [34790.237032]  [<ffffffffa000709c>] nv_nic_irq_optimized+0xdc/0x330 [forcedeth]
Apr 19 10:40:39 revo kernel: [34790.237042]  [<ffffffff810c4880>] handle_IRQ_event+0x60/0x170
Apr 19 10:40:39 revo kernel: [34790.237051]  [<ffffffff810c6dc9>] handle_fasteoi_irq+0x89/0x100
Apr 19 10:40:39 revo kernel: [34790.237060]  [<ffffffff81015d12>] handle_irq+0x22/0x30
Apr 19 10:40:39 revo kernel: [34790.237069]  [<ffffffff8155c60c>] do_IRQ+0x6c/0xf0
Apr 19 10:40:39 revo kernel: [34790.237077]  [<ffffffff81013b13>] ret_from_intr+0x0/0x11
Apr 19 10:40:39 revo kernel: [34790.237082]  <EOI>  [<ffffffff8101b551>] ? mwait_idle+0x71/0xd0
Apr 19 10:40:39 revo kernel: [34790.237098]  [<ffffffff8155a2ea>] ? atomic_notifier_call_chain+0x1a/0x20
Apr 19 10:40:39 revo kernel: [34790.237108]  [<ffffffff81011e63>] ? cpu_idle+0xb3/0x110
Apr 19 10:40:39 revo kernel: [34790.237117]  [<ffffffff8154f580>] ? start_secondary+0xa8/0xaa
Apr 19 10:40:39 revo kernel: [34790.237123] Mem-Info:
Apr 19 10:40:39 revo kernel: [34790.237127] Node 0 DMA per-cpu:
Apr 19 10:40:39 revo kernel: [34790.237134] CPU    0: hi:    0, btch:   1 usd:   0
Apr 19 10:40:39 revo kernel: [34790.237139] CPU    1: hi:    0, btch:   1 usd:   0
Apr 19 10:40:39 revo kernel: [34790.237144] CPU    2: hi:    0, btch:   1 usd:   0
Apr 19 10:40:39 revo kernel: [34790.237150] CPU    3: hi:    0, btch:   1 usd:   0
Apr 19 10:40:39 revo kernel: [34790.237154] Node 0 DMA32 per-cpu:
Apr 19 10:40:39 revo kernel: [34790.237160] CPU    0: hi:  186, btch:  31 usd: 183
Apr 19 10:40:39 revo kernel: [34790.237166] CPU    1: hi:  186, btch:  31 usd: 166
Apr 19 10:40:39 revo kernel: [34790.237171] CPU    2: hi:  186, btch:  31 usd: 187
Apr 19 10:40:39 revo kernel: [34790.237177] CPU    3: hi:  186, btch:  31 usd: 155
Apr 19 10:40:39 revo kernel: [34790.237188] active_anon:7894 inactive_anon:8308 isolated_anon:0
Apr 19 10:40:39 revo kernel: [34790.237191]  active_file:22961 inactive_file:23707 isolated_file:0
Apr 19 10:40:39 revo kernel: [34790.237194]  unevictable:0 dirty:1892 writeback:3829 unstable:0
Apr 19 10:40:39 revo kernel: [34790.237197]  free:1212 slab_reclaimable:2570 slab_unreclaimable:11981
Apr 19 10:40:39 revo kernel: [34790.237200]  mapped:31681 shmem:2 pagetables:2295 bounce:0
Apr 19 10:40:39 revo kernel: [34790.237206] Node 0 DMA free:3488kB min:64kB low:80kB high:96kB active_anon:1616kB inactive_anon:1828kB active_file:3364kB inactive_file:3344kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15300kB mlocked:0kB dirty:0kB writeback:0kB mapped:3408kB shmem:0kB slab_reclaimable:160kB slab_unreclaimable:1860kB kernel_stack:32kB pagetables:92kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Apr 19 10:40:39 revo kernel: [34790.237232] lowmem_reserve[]: 0 867 867 867
Apr 19 10:40:39 revo kernel: [34790.237241] Node 0 DMA32 free:1360kB min:3732kB low:4664kB high:5596kB active_anon:29960kB inactive_anon:31404kB active_file:88480kB inactive_file:91484kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:888356kB mlocked:0kB dirty:7568kB writeback:15316kB mapped:123316kB shmem:8kB slab_reclaimable:10120kB slab_unreclaimable:46064kB kernel_stack:1256kB pagetables:9088kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Apr 19 10:40:39 revo kernel: [34790.237268] lowmem_reserve[]: 0 0 0 0
Apr 19 10:40:39 revo kernel: [34790.237277] Node 0 DMA: 46*4kB 21*8kB 60*16kB 10*32kB 1*64kB 0*128kB 1*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 3488kB
Apr 19 10:40:39 revo kernel: [34790.237302] Node 0 DMA32: 244*4kB 6*8kB 13*16kB 0*32kB 0*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1360kB
Apr 19 10:40:39 revo kernel: [34790.237327] 52409 total pagecache pages
Apr 19 10:40:39 revo kernel: [34790.237331] 5650 pages in swap cache
Apr 19 10:40:39 revo kernel: [34790.237337] Swap cache stats: add 133154, delete 127504, find 43272/63078
Apr 19 10:40:39 revo kernel: [34790.237341] Free swap  = 885556kB
Apr 19 10:40:39 revo kernel: [34790.237345] Total swap = 979924kB
Apr 19 10:40:39 revo kernel: [34790.245446] 229248 pages RAM
Apr 19 10:40:39 revo kernel: [34790.245451] 6310 pages reserved
Apr 19 10:40:39 revo kernel: [34790.245455] 73507 pages shared
Apr 19 10:40:39 revo kernel: [34790.245459] 183113 pages non-shared
Apr 19 10:40:39 revo kernel: [34790.245467] SLUB: Unable to allocate memory on node -1 (gfp=0x20)
Apr 19 10:40:39 revo kernel: [34790.245475]   cache: kmalloc-4096, object size: 4096, buffer size: 4096, default order: 3, min order: 0
Apr 19 10:40:39 revo kernel: [34790.245482]   node 0: slabs: 1912, objs: 5069, free: 0

```
What's that?

P.S. Ubuntu Server (Lucid Lynx) @ Revo R3600 (1G RAM + 1G Swap). Main proccess eating memory is rtorrent. On previous version of Ubuntu (Karmic Koala) there were no problems

```
user@revo:~$ top
top - 12:04:24 up 11:03,  2 users,  load average: 1.07, 1.17, 1.33
Tasks: 146 total,   1 running, 145 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.8%us,  2.1%sy,  0.0%ni, 77.8%id, 17.7%wa,  0.2%hi,  0.5%si,  0.0%st
Mem:    891752k total,   879800k used,    11952k free,     1504k buffers
Swap:   979924k total,    77000k used,   902924k free,   189432k cached
```

---

