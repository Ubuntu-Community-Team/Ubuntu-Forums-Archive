---
title: "Xen virtualized ubuntu and out of memory problem"
date: 2009-01-26
forum: Server Platforms
---

### Post by iler on 2009-01-26
I've been running a Ubuntu 8.04.1 64 bit server as a xen domU at my service providers systems succesfully until resent weeks. Now my server is crashing now and then I have to boot it up through a web page. Today I found these lines from syslog:

> Jan 26 17:43:08 i28 kernel: oom-killer: gfp_mask=0x201d2, order=0
Jan 26 17:43:08 i28 kernel: 
Jan 26 17:43:08 i28 kernel: Call Trace:
Jan 26 17:43:08 i28 kernel:  [<ffffffff8022a159>] printk_ratelimit+0x15/0x17
Jan 26 17:43:08 i28 kernel:  [<ffffffff80257aa1>] out_of_memory+0x37/0x186
Jan 26 17:43:08 i28 kernel:  [<ffffffff802593af>] __alloc_pages+0x237/0x2be
Jan 26 17:43:08 i28 kernel:  [<ffffffff8025aa9e>] __do_page_cache_readahead+0x154/0x323
Jan 26 17:43:08 i28 kernel:  [<ffffffff804382e0>] io_schedule+0x28/0x36
Jan 26 17:43:08 i28 kernel:  [<ffffffff8043861e>] __wait_on_bit_lock+0x67/0x79
Jan 26 17:43:08 i28 kernel:  [<ffffffff802542ee>] sync_page+0x0/0x43
Jan 26 17:43:08 i28 kernel:  [<ffffffff8025afe4>] do_page_cache_readahead+0x51/0x5e
Jan 26 17:43:08 i28 kernel:  [<ffffffff80256f4d>] filemap_nopage+0x154/0x337
Jan 26 17:43:08 i28 kernel:  [<ffffffff80263337>] __handle_mm_fault+0x74c/0x1050
Jan 26 17:43:08 i28 kernel:  [<ffffffff803363b3>] strncpy_from_user+0x3a/0x43
Jan 26 17:43:08 i28 kernel:  [<ffffffff80287818>] path_release+0x29/0x30
Jan 26 17:43:08 i28 kernel:  [<ffffffff80333752>] __up_read+0x90/0x9b
Jan 26 17:43:08 i28 kernel:  [<ffffffff80214b2d>] do_page_fault+0xe0b/0x1272
Jan 26 17:43:08 i28 kernel:  [<ffffffff80283849>] sys_newlstat+0x31/0x3c
Jan 26 17:43:08 i28 kernel:  [<ffffffff8020a877>] error_exit+0x0/0x71
Jan 26 17:43:08 i28 kernel: 
Jan 26 17:43:08 i28 kernel: Mem-info:
Jan 26 17:43:08 i28 kernel: DMA per-cpu:
Jan 26 17:43:08 i28 kernel: cpu 0 hot: high 186, batch 31 used:12
Jan 26 17:43:08 i28 kernel: cpu 0 cold: high 62, batch 15 used:44
Jan 26 17:43:08 i28 kernel: DMA32 per-cpu: empty
Jan 26 17:43:08 i28 kernel: Normal per-cpu: empty
Jan 26 17:43:08 i28 kernel: HighMem per-cpu: empty
Jan 26 17:43:08 i28 kernel: Free pages:        3328kB (0kB HighMem)
Jan 26 17:43:08 i28 kernel: Active:52613 inactive:59296 dirty:0 writeback:0 unstable:0 free:832 slab:3551 mapped:39 pagetables:7386
Jan 26 17:43:08 i28 kernel: DMA free:3328kB min:2916kB low:3644kB high:4372kB active:210452kB inactive:237184kB present:532480kB pages_scanned:5143 all_unreclaimable? no
Jan 26 17:43:08 i28 kernel: lowmem_reserve[]: 0 0 0 0
Jan 26 17:43:08 i28 kernel: DMA32 free:0kB min:0kB low:0kB high:0kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
Jan 26 17:43:08 i28 kernel: lowmem_reserve[]: 0 0 0 0
Jan 26 17:43:08 i28 kernel: Normal free:0kB min:0kB low:0kB high:0kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
Jan 26 17:43:08 i28 kernel: lowmem_reserve[]: 0 0 0 0
Jan 26 17:43:08 i28 kernel: HighMem free:0kB min:128kB low:128kB high:128kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
Jan 26 17:43:08 i28 kernel: lowmem_reserve[]: 0 0 0 0
Jan 26 17:43:08 i28 kernel: DMA: 104*4kB 12*8kB 2*16kB 1*32kB 1*64kB 1*128kB 0*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 3328kB
Jan 26 17:43:08 i28 kernel: DMA32: empty
Jan 26 17:43:08 i28 kernel: Normal: empty
Jan 26 17:43:08 i28 kernel: HighMem: empty
Jan 26 17:43:08 i28 kernel: Swap cache: add 677008, delete 676968, find 278549/335435, race 0+25
Jan 26 17:43:08 i28 kernel: Free swap  = 0kB
Jan 26 17:43:08 i28 kernel: Total swap = 525304kB
Jan 26 17:43:08 i28 kernel: Free swap:            0kB
Jan 26 17:43:08 i28 kernel: 133120 pages of RAM
Jan 26 17:43:08 i28 kernel: 3665 reserved pages
Jan 26 17:43:08 i28 kernel: 7176 pages shared
Jan 26 17:43:08 i28 kernel: 40 pages swap cached
Jan 26 17:43:08 i28 kernel: Out of Memory: Kill process 6350 (apache2) score 82992 and children.
Jan 26 17:43:08 i28 kernel: Out of memory: Killed process 6350 (apache2).


It seems that apache2 is running out of memory but I really don't know why. I have 512MB memory and 512MB swap on my server and it should be enough to run six minor sites. Only one site tops over 200 visitors per day, others are under 100. I have similar setup at home, Ubuntu 8.04.1 64bit running as both dom0 and domU but don't have similar problems. All my systems are up to date. So is there some kind of problem with memory leaks in apache2 or is it something other?

---

### Post by windependence on 2009-01-26
Apache isn't your problem. You just don't have enough memory, especially if this is all the memory you have on the entire box. Xen takes a good amount by itself. Even if this is what you have allocated to the VM, it's marginal. Do you also have MySQL and PHP running on the box? Any other programs running? A GUI desktop?

-Tim

---

### Post by iler on 2009-01-26
Not enough? I'm not talking about dom0 server here. 512MB of memory for a xen domU server is enough. I have run several xen domU servers with 512MB of memory with success (lamp etc running.) My friend has several xen domU web servers running with 384MB to 512MB of memory and those are several times more occupied than my server and he has no problems. No, the amount of memory is not a problem here :) Or how could you explain that my server worked like a charm for 2 months and now suddenly I don't have enough memory?

---

### Post by aimeesonfl on 2011-01-12
> **iler said:**
> I've been running a Ubuntu 8.04.1 64 bit server as a xen domU at my service providers systems succesfully until resent weeks. Now my server is crashing now and then I have to boot it up through a web page. Today I found these lines from syslog: ] printk_ratelimit+0x15/0x17Jan 26 17:43:08 i28 kernel: [] out_of_memory+0x37/0x186Jan 26 17:43:08 i28 kernel: [] __alloc_pages+0x237/0x2beJan 26 17:43:08 i28 kernel: [] __do_page_cache_readahead+0x154/0x323Jan 26 17:43:08 i28 kernel: [] io_schedule+0x28/0x36Jan 26 17:43:08 i28 kernel: [] __wait_on_bit_lock+0x67/0x79Jan 26 17:43:08 i28 kernel: [] sync_page+0x0/0x43Jan 26 17:43:08 i28 kernel: [] do_page_cache_readahead+0x51/0x5eJan 26 17:43:08 i28 kernel: [] filemap_nopage+0x154/0x337Jan 26 17:43:08 i28 kernel: [] __handle_mm_fault+0x74c/0x1050Jan 26 17:43:08 i28 kernel: [] strncpy_from_user+0x3a/0x43Jan 26 17:43:08 i28 kernel: [] path_release+0x29/0x30Jan 26 17:43:08 i28 kernel: [] __up_read+0x90/0x9bJan 26 17:43:08 i28 kernel: [] do_page_fault+0xe0b/0x1272Jan 26 17:43:08 i28 kernel: [] sys_newlstat+0x31/0x3cJan 26 17:43:08 i28 kernel: [] error_exit+0x0/0x71Jan 26 17:43:08 i28 kernel: Jan 26 17:43:08 i28 kernel: Mem-info:Jan 26 17:43:08 i28 kernel: DMA per-cpu:Jan 26 17:43:08 i28 kernel: cpu 0 hot: high 186, batch 31 used:12Jan 26 17:43:08 i28 kernel: cpu 0 cold: high 62, batch 15 used:44Jan 26 17:43:08 i28 kernel: DMA32 per-cpu: emptyJan 26 17:43:08 i28 kernel: Normal per-cpu: emptyJan 26 17:43:08 i28 kernel: HighMem per-cpu: emptyJan 26 17:43:08 i28 kernel: Free pages: [[COLOR=#000000]3328kB[/COLOR]](http://www.****************.com/apple-tv-video-format/convert-mkv-video-to-apple-tv-format.html) (0kB HighMem)Jan 26 17:43:08 i28 kernel: Active:52613 inactive:59296 dirty:0 writeback:0 unstable:0 free:832 slab:3551 mapped:39 pagetables:7386Jan 26 17:43:08 i28 kernel: DMA free:3328kB min:2916kB low:3644kB high:4372kB active:210452kB inactive:237184kB present:532480kB pages_scanned:5143 all_unreclaimable? noJan 26 17:43:08 i28 kernel: lowmem_reserve[]: 0 0 0 0Jan 26 17:43:08 i28 kernel: DMA32 free:0kB min:0kB low:0kB high:0kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? noJan 26 17:43:08 i28 kernel: lowmem_reserve[]: 0 0 0 0Jan 26 17:43:08 i28 kernel: Normal free:0kB min:0kB low:0kB high:0kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? noJan 26 17:43:08 i28 kernel: lowmem_reserve[]: 0 0 0 0Jan 26 17:43:08 i28 kernel: HighMem free:0kB min:128kB low:128kB high:128kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? noJan 26 17:43:08 i28 kernel: lowmem_reserve[]: 0 0 0 0Jan 26 17:43:08 i28 kernel: DMA: 104*4kB 12*8kB 2*16kB 1*32kB 1*64kB 1*128kB 0*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB=3328kBJan 26 17:43:08 i28 kernel: DMA32: emptyJan 26 17:43:08 i28 kernel: Normal: emptyJan 26 17:43:08 i28 kernel: HighMem: emptyJan 26 17:43:08 i28 kernel: Swap cache: add 677008, delete 676968, find 278549/335435, race 0+25Jan 26 17:43:08 i28 kernel: Free swap=0kBJan 26 17:43:08 i28 kernel: Total swap=525304kBJan 26 17:43:08 i28 kernel: Free swap: 0kBJan 26 17:43:08 i28 kernel: 133120 pages of RAMJan 26 17:43:08 i28 kernel: 3665 reserved pagesJan 26 17:43:08 i28 kernel: 7176 pages sharedJan 26 17:43:08 i28 kernel: 40 pages swap cachedJan 26 17:43:08 i28 kernel: Out of Memory: Kill process 6350 (apache2) score 82992 and children.Jan 26 17:43:08 i28 kernel: Out of memory: Killed process 6350 (apache2).   It seems that apache2 is running out of memory but I really don't know why. I have 512MB memory and 512MB swap on my server and it should be enough to run six minor sites. Only one site tops over 200 visitors per day, others are under 100. I have similar setup at home, Ubuntu 8.04.1 64bit running as both dom0 and domU but don't have similar problems. All my systems are up to date. So is there some kind of problem with memory leaks in apache2 or is it something other?Thanks for your effort! Now I got it, It's good for reference.

---

