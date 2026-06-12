---
title: "Kernel Errors"
date: 2011-01-28
forum: Server Platforms
---

### Post by capspecialk on 2011-01-28
I am running a headless Ubuntu 10.04 server with the 2.6.32-28-generic kernel.  For what I can figure out no single direct cause I get a high load average and the following syslog output at random intervals.  Generally the load average will drop back down to normal however the kernel errors will still continue.   What little I have been able to find has pointed to memory issues.  I am not totaly convinced this is the cause as the server will be showing >50% free when the errors are happening.

Any thoughts?

Thanks,
Karl

```
Jan 28 08:25:03 VPN kernel: [  770.957643] __ratelimit: 15 callbacks suppressed
Jan 28 08:25:03 VPN kernel: [  770.957649] java: page allocation failure. order:4, mode:0xc0d0
Jan 28 08:25:03 VPN kernel: [  770.957655] Pid: 1427, comm: java Tainted: P           2.6.32-28-generic #55-Ubuntu
Jan 28 08:25:03 VPN kernel: [  770.957659] Call Trace:
Jan 28 08:25:03 VPN kernel: [  770.957671]  [<c058bf3e>] ? printk+0x1d/0x1f
Jan 28 08:25:03 VPN kernel: [  770.957693]  [<c01d0c6b>] __alloc_pages_slowpath+0x3ab/0x4a0
Jan 28 08:25:03 VPN kernel: [  770.957698]  [<c01d0e9a>] __alloc_pages_nodemask+0x13a/0x170
Jan 28 08:25:03 VPN kernel: [  770.957703]  [<c01d0eec>] __get_free_pages+0x1c/0x30
Jan 28 08:25:03 VPN kernel: [  770.957729]  [<f097a7ba>] hiddev_open+0x5a/0x1a0 [usbhid]
Jan 28 08:25:03 VPN kernel: [  770.957735]  [<c021bf11>] ? dput+0x91/0x130
Jan 28 08:25:03 VPN kernel: [  770.957753]  [<c044f102>] usb_open+0xc2/0x1c0
Jan 28 08:25:03 VPN kernel: [  770.957758]  [<c020c3c4>] ? cdev_get+0x24/0xc0
Jan 28 08:25:03 VPN kernel: [  770.957763]  [<c020c9c5>] chrdev_open+0xf5/0x200
Jan 28 08:25:03 VPN kernel: [  770.957770]  [<c02075a5>] __dentry_open+0xe5/0x290
Jan 28 08:25:03 VPN kernel: [  770.957777]  [<c02f764d>] ? security_inode_permission+0x1d/0x30
Jan 28 08:25:03 VPN kernel: [  770.957783]  [<c021253e>] ? inode_permission+0x9e/0xb0
Jan 28 08:25:03 VPN kernel: [  770.957798]  [<c020784d>] nameidata_to_filp+0x5d/0x70
Jan 28 08:25:03 VPN kernel: [  770.957802]  [<c020c8d0>] ? chrdev_open+0x0/0x200
Jan 28 08:25:03 VPN kernel: [  770.957806]  [<c0215f02>] do_filp_open+0x4d2/0x990
Jan 28 08:25:03 VPN kernel: [  770.957811]  [<c012fcfc>] ? flush_tlb_page+0x3c/0x90
Jan 28 08:25:03 VPN kernel: [  770.957815]  [<c012f309>] ? ptep_set_access_flags+0x59/0x60
Jan 28 08:25:03 VPN kernel: [  770.957820]  [<c01307cc>] ? kmap_atomic_prot+0x4c/0xf0
Jan 28 08:25:03 VPN kernel: [  770.957825]  [<c0207305>] do_sys_open+0x55/0x160
Jan 28 08:25:03 VPN kernel: [  770.957829]  [<c020747e>] sys_open+0x2e/0x40
Jan 28 08:25:03 VPN kernel: [  770.957834]  [<c01033ec>] syscall_call+0x7/0xb
Jan 28 08:25:03 VPN kernel: [  770.957837] Mem-Info:
Jan 28 08:25:03 VPN kernel: [  770.957839] DMA per-cpu:
Jan 28 08:25:03 VPN kernel: [  770.957842] CPU    0: hi:    0, btch:   1 usd:   0
Jan 28 08:25:03 VPN kernel: [  770.957844] Normal per-cpu:
Jan 28 08:25:03 VPN kernel: [  770.957847] CPU    0: hi:  186, btch:  31 usd:   0
Jan 28 08:25:03 VPN kernel: [  770.957854] active_anon:33162 inactive_anon:36870 isolated_anon:1
Jan 28 08:25:03 VPN kernel: [  770.957855]  active_file:32600 inactive_file:74537 isolated_file:0
Jan 28 08:25:03 VPN kernel: [  770.957857]  unevictable:0 dirty:29118 writeback:4580 unstable:0
Jan 28 08:25:03 VPN kernel: [  770.957858]  free:2918 slab_reclaimable:2376 slab_unreclaimable:3860
Jan 28 08:25:03 VPN kernel: [  770.957860]  mapped:23801 shmem:2919 pagetables:1483 bounce:0
Jan 28 08:25:03 VPN kernel: [  770.957869] DMA free:3036kB min:68kB low:84kB high:100kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:5396kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15804kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:52kB slab_unreclaimable:20kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Jan 28 08:25:03 VPN kernel: [  770.957876] lowmem_reserve[]: 0 746 746 746
Jan 28 08:25:03 VPN kernel: [  770.957887] Normal free:8636kB min:3460kB low:4324kB high:5188kB active_anon:132648kB inactive_anon:147480kB active_file:130400kB inactive_file:292752kB unevictable:0kB isolated(anon):4kB isolated(file):0kB present:763968kB mlocked:0kB dirty:116472kB writeback:18320kB mapped:95204kB shmem:11676kB slab_reclaimable:9452kB slab_unreclaimable:15420kB kernel_stack:3080kB pagetables:5932kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Jan 28 08:25:03 VPN kernel: [  770.957895] lowmem_reserve[]: 0 0 0 0
Jan 28 08:25:03 VPN kernel: [  770.957899] DMA: 1*4kB 0*8kB 2*16kB 2*32kB 4*64kB 5*128kB 6*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 3044kB
Jan 28 08:25:03 VPN kernel: [  770.957911] Normal: 1373*4kB 321*8kB 32*16kB 0*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 8636kB
Jan 28 08:25:03 VPN kernel: [  770.957922] 110496 total pagecache pages
Jan 28 08:25:03 VPN kernel: [  770.957924] 447 pages in swap cache
Jan 28 08:25:03 VPN kernel: [  770.957927] Swap cache stats: add 472, delete 25, find 53/53
Jan 28 08:25:03 VPN kernel: [  770.957929] Free swap  = 881708kB
Jan 28 08:25:03 VPN kernel: [  770.957931] Total swap = 883532kB
Jan 28 08:25:03 VPN kernel: [  770.966540] 196576 pages RAM
Jan 28 08:25:03 VPN kernel: [  770.966544] 0 pages HighMem
Jan 28 08:25:03 VPN kernel: [  770.966546] 4699 pages reserved
Jan 28 08:25:03 VPN kernel: [  770.966548] 146843 pages shared
Jan 28 08:25:03 VPN kernel: [  770.966550] 121202 pages non-shared

```

---

### Post by Vegan on 2011-01-28
RAM prices have fallen, so its less painful to upgrade.

---

### Post by datamove on 2011-01-28
Be generous allocating swap space. Matching swap space to amount of RAM won't hurt. It's true that linux doesn't need this swap disk space for operation, but swap counts as virtual memory and a lot of processes need to allocate virtual memory even they consume less than allocated. Java is one of them. You should also pay attention to your java heap settings. I believe any java allocation errors are due to inability to allocate virtual memory.

---

