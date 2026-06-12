---
title: "Random crashes"
date: 2010-01-18
forum: Server Platforms
---

### Post by dmalcomd on 2010-01-18
I've a 8.04 in production environment with kernel 2.6.24-23-xen on dom0.
At the moment my domU suddendly crashes (about every 20-30 days). 
I've tried another release of kernel (2.6.18 i think, i don't remember well ) but it was MUCH MORE unstable :(

This is a dump i've taken after xm console the domU

> 20 00 40 01 00 00 00 ff ff ff ff 94 4d a0 c1 00 00 00 00 60
[41906.545029] EIP: [<c1a2cbc0>] 0xc1a2cbc0 SS:ESP 0069:dc0d5ec4
[41906.545037] ---[ end trace 298670a673aeb1b0 ]---
[61989.204987] Bad page state in process 'kswapd0'
[61989.204988] page:c16cba00 flags:0x40090008 mapping:00000000 mapcount:0 count:                     0
[61989.204989] Trying to fix it up, but a reboot is needed
[61989.204990] Backtrace:
[61989.205002] Pid: 95, comm: kswapd0 Tainted: G      D 2.6.24-23-xen #1
[61989.205012]  [<c0161c33>] bad_page+0x63/0xa0
[61989.205023]  [<c0162418>] free_hot_cold_page+0x208/0x220
[61989.205028]  [<c0162456>] __pagevec_free+0x26/0x30
[61989.205034]  [<c01658c8>] release_pages+0x68/0x160
[61989.205043]  [<c0166055>] __pagevec_release+0x15/0x20
[61989.205047]  [<c016672a>] __invalidate_mapping_pages+0xfa/0x130
[61989.205054]  [<c016676f>] invalidate_mapping_pages+0xf/0x20
[61989.205059]  [<c0199dfa>] shrink_icache_memory+0x24a/0x260
[61989.205068]  [<c0168317>] shrink_slab+0x117/0x170
[61989.205074]  [<c01686f0>] kswapd+0x300/0x490
[61989.205081]  [<c013bac0>] autoremove_wake_function+0x0/0x40
[61989.205090]  [<c011e260>] complete+0x40/0x60
[61989.205096]  [<c01683f0>] kswapd+0x0/0x490
[61989.205100]  [<c013b802>] kthread+0x42/0x70
[61989.205105]  [<c013b7c0>] kthread+0x0/0x70
[61989.205110]  [<c0105bb7>] kernel_thread_helper+0x7/0x10
[61989.205118]  =======================
[61989.205121] Bad page state in process 'kswapd0'
[61989.205122] page:c17e82c0 flags:0x40090008 mapping:00000000 mapcount:0 count:                     0
[61989.205123] Trying to fix it up, but a reboot is needed
[61989.205124] Backtrace:
[61989.205131] Pid: 95, comm: kswapd0 Tainted: G    B D 2.6.24-23-xen #1
[61989.205134]  [<c0161c33>] bad_page+0x63/0xa0
[61989.205141]  [<c0162418>] free_hot_cold_page+0x208/0x220
[61989.205148]  [<c0162456>] __pagevec_free+0x26/0x30
[61989.205154]  [<c01658c8>] release_pages+0x68/0x160
[61989.205160]  [<c0166055>] __pagevec_release+0x15/0x20
[61989.205166]  [<c016672a>] __invalidate_mapping_pages+0xfa/0x130
[61989.205173]  [<c016676f>] invalidate_mapping_pages+0xf/0x20
[61989.205179]  [<c0199dfa>] shrink_icache_memory+0x24a/0x260
[61989.205186]  [<c0168317>] shrink_slab+0x117/0x170
[61989.205193]  [<c01686f0>] kswapd+0x300/0x490
[61989.205199]  [<c013bac0>] autoremove_wake_function+0x0/0x40
[61989.205205]  [<c011e260>] complete+0x40/0x60
[61989.205211]  [<c01683f0>] kswapd+0x0/0x490
[61989.205216]  [<c013b802>] kthread+0x42/0x70
[61989.205219]  [<c013b7c0>] kthread+0x0/0x70
[61989.205226]  [<c0105bb7>] kernel_thread_helper+0x7/0x10
[61989.205230]  =======================
[63668.089880] Bad page state in process 'apache2'
[63668.089882] page:c17e82c0 flags:0x40000824 mapping:df802d94 mapcount:0 count:                     2
[63668.089883] Trying to fix it up, but a reboot is needed
[63668.089884] Backtrace:
[63668.089902] Pid: 31246, comm: apache2 Tainted: G    B D 2.6.24-23-xen #1
[63668.089917]  [<c0161c33>] bad_page+0x63/0xa0
[63668.089934]  [<c0162c73>] get_page_from_freelist+0x3d3/0x4b0
[63668.089941]  [<c0162e40>] __alloc_pages+0x60/0x390
[63668.089946]  [<c01788cd>] anon_vma_prepare+0x1d/0xe0
[63668.089951]  [<c0165a9a>] __pagevec_lru_add_active+0xda/0x100
[63668.089956]  [<c017130c>] handle_mm_fault+0x89c/0x1350
[63668.089970]  [<c015d080>] file_read_actor+0x0/0x100
[63668.089977]  [<c0173d2b>] vma_adjust+0x10b/0x440
[63668.089984]  [<c03298c6>] do_page_fault+0x366/0xe90
[63668.089991]  [<c01744d4>] vma_merge+0x144/0x1d0
[63668.089998]  [<c0174a75>] do_brk+0x195/0x240
[63668.090005]  [<c0185e5c>] vfs_read+0x11c/0x170
[63668.090011]  [<c0175026>] sys_brk+0xb6/0xf0
[63668.090016]  [<c0329560>] do_page_fault+0x0/0xe90
[63668.090020]  [<c0328205>] error_code+0x35/0x40
[63668.090028]  [<c0320000>] vcc_ioctl+0x1e0/0x2d0
[63668.090034]  =======================
[70807.536352] BUG: unable to handle kernel NULL pointer dereference at virtual                      address 0000003a
[70807.536364] printing eip: c01618b6
[70807.536369] 1726d000 -> *pde = 00000000:02680001
[70807.536372] 1e8d1000 -> *pme = 00000000:00000000
[70807.536376] Oops: 0002 [#2] SMP
[70807.536381] Modules linked in: xt_multiport iptable_filter ip_tables x_tables                      quota_v1 ipv6 evdev ext3 jbd mbcache raid10 raid456 async_xor async_memcpy asyn                     c_tx xor raid1 raid0 multipath linear md_mod fuse
[70807.536405]
[70807.536408] Pid: 1556, comm: apache2 Tainted: G    B D (2.6.24-23-xen #1)
[70807.536411] EIP: 0061:[<c01618b6>] EFLAGS: 00210087 CPU: 0
[70807.536422] EIP is at __rmqueue_smallest+0x76/0x130
[70807.536425] EAX: dfc07200 EBX: 00000001 ECX: 00000036 EDX: c03fdcc0
[70807.536428] ESI: c03fdcb0 EDI: 00000000 EBP: c03fd800 ESP: c7759d40
[70807.536430]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0069
[70807.536433] Process apache2 (pid: 1556, ti=c7758000 task=df0df290 task.ti=c77                     58000)
[70807.536435] Stack: 00000010 00000002 00000000 dfc071e8 00000002 c03fd800 0000                     0000 c03fd800
[70807.536445]        c016198e 80000000 c1a04f40 c1a04f40 00000000 c011958c 0000                     0063 c1a04f40
[70807.536454]        c1a04f60 dfc035e0 c03fd800 0000001b 0000001f c0161b95 0000                     0000 00000018
[70807.536463] Call Trace:
[70807.536468]  [<c016198e>] __rmqueue+0x1e/0x1f0
[70807.536472]  [<c011958c>] kmap_atomic+0x1c/0x30
[70807.536478]  [<c0161b95>] rmqueue_bulk+0x35/0x70
[70807.536483]  [<c0162c9c>] get_page_from_freelist+0x3fc/0x4b0
[70807.536489]  [<c0162e40>] __alloc_pages+0x60/0x390
[70807.536494]  [<c01788cd>] anon_vma_prepare+0x1d/0xe0
[70807.536497]  [<c0165a9a>] __pagevec_lru_add_active+0xda/0x100
[70807.536502]  [<c017130c>] handle_mm_fault+0x89c/0x1350
[70807.536507]  [<c0109030>] timer_interrupt+0x3a0/0x770
[70807.536514]  [<c013eaea>] hrtimer_run_queues+0xda/0x1e0
[70807.536519]  [<c0173d2b>] vma_adjust+0x10b/0x440
[70807.536524]  [<c03298c6>] do_page_fault+0x366/0xe90
[70807.536529]  [<c01744d4>] vma_merge+0x144/0x1d0
[70807.536533]  [<c0174a75>] do_brk+0x195/0x240
[70807.536538]  [<c0175026>] sys_brk+0xb6/0xf0
[70807.536542]  [<c0329560>] do_page_fault+0x0/0xe90
[70807.536546]  [<c0328205>] error_code+0x35/0x40
[70807.536551]  [<c0320000>] vcc_ioctl+0x1e0/0x2d0
[70807.536555]  =======================
[70807.536557] Code: fb 0b 75 e7 c7 44 24 0c 00 00 00 00 8b 44 24 0c 83 c4 10 5b                      5e 5f 5d c3 8b 54 24 04 8b 04 d6 8d 48 e8 89 4c 24 0c 8b 08 8b 50 04 <89> 51 04                      89 0a c7 40 04 00 02 20 00 c7 00 00 01 10 00 0f ba 70
[70807.536606] EIP: [<c01618b6>] __rmqueue_smallest+0x76/0x130 SS:ESP 0069:c7759                     d40
[70807.536615] ---[ end trace 298670a673aeb1b0 ]---

---

### Post by tgalati4 on 2010-01-22
What is the hardware that you are running?  Bad swap looks like an OS problem, possibly a xen problem, but it could also be a failing motherboard/IO subsystem or bad RAM.

You need to take the machine offline and run a liveCD for a month to determine uptime stability with the production hardy kernel.  If you can't benchmark the machine's performance, then trying to trace stability issues becomes difficult.

For Dell poweredge servers, there is a package called openmanage server administrator that can drill down through the hardware and read back hardware errors that are captured in the BIOS.  Do you have any hardware monitor data?

The stack dump isn't helpful (beyond the fact that a bad page was fetched) which corrupted running processes--requiring a reboot.

There are a lot of things that can cause a bad page fetch.  Most of them hardware related.

---

