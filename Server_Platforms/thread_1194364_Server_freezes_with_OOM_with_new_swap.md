---
title: "Server freezes with OOM with new swap"
date: 2009-06-22
forum: Server Platforms
---

### Post by omael on 2009-06-22
My server (Ubuntu 8.10LTS server) recently had a power failure and after that it started having problems, it started freezing with OOM killer failures. I checked the swap and found that it wasn't big enough to hold the ram (by a couple of MBs). So i added another SATA disk, made a 16GB swap partition and issued mkswap over it, the server booted normally and was stable, but after 36 hours it resumed the oom errors (i've tried disabling the origianl swap partition).
After a couple of tests i found out that the server wasn't using the swap partition, when i checked "free" it reported that almost all 4GB of ram where used, and none of the swap was.
What should i do?

Here's my output for free:
> 
omael@www:~$ free
             total       used       free     shared    buffers     cached
Mem:       4139756     996752    3143004          0      99324     523764
-/+ buffers/cache:     373664    3766092
Swap:     16787884          0   16787884


Here are some of the error messages from /var/log/messages/

```

Jun 22 13:34:15 www kernel: [134351.592241] Swap cache: add 0, delete 0, find 0/0, race 0+0
Jun 22 13:34:15 www kernel: [134351.592244] Free swap  = 0kB
Jun 22 13:34:15 www kernel: [134351.592244] Total swap = 0kB
Jun 22 13:34:15 www kernel: [134351.592245] Free swap:            0kB
Jun 22 13:34:15 www kernel: [134351.601534] 1245184 pages of RAM
Jun 22 13:34:15 www kernel: [134351.601538] 1015808 pages of HIGHMEM
Jun 22 13:34:15 www kernel: [134351.601539] 210245 reserved pages
Jun 22 13:34:15 www kernel: [134351.601540] 66823 pages shared
Jun 22 13:34:15 www kernel: [134351.601543] 0 pages swap cached
Jun 22 13:34:15 www kernel: [134351.601546] 9 pages dirty
Jun 22 13:34:15 www kernel: [134351.601546] 0 pages writeback
Jun 22 13:34:15 www kernel: [134351.601547] 7997 pages mapped
Jun 22 13:34:15 www kernel: [134351.601550] 190598 pages slab
Jun 22 13:34:15 www kernel: [134351.601550] 680 pages pagetables
Jun 22 13:34:15 www kernel: [134351.653463] apache2 invoked oom-killer: gfp_mask=0x40d0, order=1, oomkilladj=-17
Jun 22 13:34:15 www kernel: [134351.653469] Pid: 18726, comm: apache2 Not tainted 2.6.24-19-server #1
Jun 22 13:34:15 www kernel: [134351.653482]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Jun 22 13:34:15 www kernel: [134351.653500]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
Jun 22 13:34:15 www kernel: [134351.653507]  [agpgart:__alloc_pages+0x34c/0x380] __alloc_pages+0x34c/0x380
Jun 22 13:34:15 www kernel: [134351.653512]  [__slab_alloc+0x186/0x4a0] __slab_alloc+0x186/0x4a0
Jun 22 13:34:15 www kernel: [134351.653520]  [ext3:kmem_cache_alloc+0xad/0xc0] kmem_cache_alloc+0xad/0xc0
Jun 22 13:34:15 www kernel: [134351.653524]  [getname+0x28/0xe0] getname+0x28/0xe0
Jun 22 13:34:15 www kernel: [134351.653530]  [getname+0x28/0xe0] getname+0x28/0xe0
Jun 22 13:34:15 www kernel: [134351.653533]  [__user_walk_fd+0x1e/0x60] __user_walk_fd+0x1e/0x60
Jun 22 13:34:15 www kernel: [134351.653537]  [vfs_stat_fd+0x22/0x60] vfs_stat_fd+0x22/0x60
Jun 22 13:34:15 www kernel: [134351.653543]  [<c0145fc0>] autoremove_wake_function+0x0/0x40
Jun 22 13:34:15 www kernel: [134351.653550]  [sock_aio_write+0x0/0x120] sock_aio_write+0x0/0x120
Jun 22 13:34:15 www kernel: [134351.653560]  [sys_stat64+0xf/0x30] sys_stat64+0xf/0x30
Jun 22 13:34:15 www kernel: [134351.653566]  [ieee1394:do_gettimeofday+0x34/0xdac0] do_gettimeofday+0x34/0xe0
Jun 22 13:34:15 www kernel: [134351.653573]  [sys_gettimeofday+0x28/0x80] sys_gettimeofday+0x28/0x80
Jun 22 13:34:15 www kernel: [134351.653579]  [sysenter_past_esp+0x6b/0xa1] sysenter_past_esp+0x6b/0xa1
Jun 22 13:34:15 www kernel: [134351.653589]  =======================
Jun 22 13:34:15 www kernel: [134351.653592] Mem-info:
Jun 22 13:34:15 www kernel: [134351.653594] DMA per-cpu:
Jun 22 13:34:15 www kernel: [134351.653596] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:15 www kernel: [134351.653599] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:15 www kernel: [134351.653603] CPU    2: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:15 www kernel: [134351.653606] CPU    3: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:15 www kernel: [134351.653611] Normal per-cpu:
Jun 22 13:34:15 www kernel: [134351.653612] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:15 www kernel: [134351.653616] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:15 www kernel: [134351.653619] CPU    2: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:15 www kernel: [134351.653623] CPU    3: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:15 www kernel: [134351.653626] HighMem per-cpu:
Jun 22 13:34:15 www kernel: [134351.653627] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:15 www kernel: [134351.653631] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:15 www kernel: [134351.653634] CPU    2: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:15 www kernel: [134351.653637] CPU    3: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:15 www kernel: [134351.653641] Active:59937 inactive:35237 dirty:9 writeback:0 unstable:0
Jun 22 13:34:15 www kernel: [134351.653642]  free:744884 slab:190598 mapped:7997 pagetables:680 bounce:0
Jun 22 13:34:15 www kernel: [134351.653645] DMA free:3548kB min:68kB low:84kB high:100kB active:0kB inactive:0kB present:16256kB pages_scanned:0 all_unreclaimable? no
Jun 22 13:34:15 www kernel: [134351.653648] lowmem_reserve[]: 0 873 4810 4810
Jun 22 13:34:15 www kernel: [134351.653654] Normal free:95708kB min:3744kB low:4680kB high:5616kB active:180kB inactive:68kB present:894080kB pages_scanned:0 all_unreclaimable? no
Jun 22 13:34:15 www kernel: [134351.653657] lowmem_reserve[]: 0 0 31496 31496
Jun 22 13:34:15 www kernel: [134351.653664] HighMem free:2880280kB min:512kB low:4736kB high:8960kB active:239568kB inactive:140880kB present:4031488kB pages_scanned:0 all_unreclaimable? no
Jun 22 13:34:15 www kernel: [134351.653667] lowmem_reserve[]: 0 0 0 0
Jun 22 13:34:15 www kernel: [134351.653673] DMA: 355*4kB 10*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 3548kB
Jun 22 13:34:15 www kernel: [134351.653688] Normal: 23478*4kB 14*8kB 3*16kB 1*32kB 1*64kB 1*128kB 0*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 95832kB
Jun 22 13:34:15 www kernel: [134351.653702] HighMem: 116*4kB 4234*8kB 12079*16kB 6674*32kB 2728*64kB 1014*128kB 337*256kB 213*512kB 62*1024kB 34*2048kB 441*4096kB = 2880336kB
Jun 22 13:34:15 www kernel: [134351.653717] Swap cache: add 0, delete 0, find 0/0, race 0+0
Jun 22 13:34:15 www kernel: [134351.653719] Free swap  = 0kB
Jun 22 13:34:15 www kernel: [134351.653720] Total swap = 0kB
Jun 22 13:34:15 www kernel: [134351.653722] Free swap:            0kB
Jun 22 13:34:15 www kernel: [134351.662865] 1245184 pages of RAM
Jun 22 13:34:15 www kernel: [134351.662869] 1015808 pages of HIGHMEM
Jun 22 13:34:15 www kernel: [134351.662870] 210245 reserved pages
Jun 22 13:34:15 www kernel: [134351.662872] 66583 pages shared
Jun 22 13:34:15 www kernel: [134351.662875] 0 pages swap cached
Jun 22 13:34:15 www kernel: [134351.662877] 9 pages dirty
Jun 22 13:34:15 www kernel: [134351.662878] 0 pages writeback
Jun 22 13:34:15 www kernel: [134351.662878] 7997 pages mapped
Jun 22 13:34:15 www kernel: [134351.662881] 190598 pages slab
Jun 22 13:34:15 www kernel: [134351.662882] 680 pages pagetables
Jun 22 13:34:16 www kernel: [134352.415759] courierpop3logi invoked oom-killer: gfp_mask=0x40d0, order=1, oomkilladj=0
Jun 22 13:34:16 www kernel: [134352.415769] Pid: 18734, comm: courierpop3logi Not tainted 2.6.24-19-server #1
Jun 22 13:34:16 www kernel: [134352.415781]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Jun 22 13:34:16 www kernel: [134352.415791]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
Jun 22 13:34:16 www kernel: [134352.415797]  [agpgart:__alloc_pages+0x34c/0x380] __alloc_pages+0x34c/0x380
Jun 22 13:34:16 www kernel: [134352.415803]  [__slab_alloc+0x186/0x4a0] __slab_alloc+0x186/0x4a0
Jun 22 13:34:16 www kernel: [134352.415807]  [snd_pcm:schedule_timeout+0x75/0x2c0] schedule_timeout+0x75/0xc0
Jun 22 13:34:16 www kernel: [134352.415813]  [ext3:kmem_cache_alloc+0xad/0xc0] kmem_cache_alloc+0xad/0xc0
Jun 22 13:34:16 www kernel: [134352.415816]  [pgd_alloc+0x13f/0x210] pgd_alloc+0x13f/0x210
Jun 22 13:34:16 www kernel: [134352.415822]  [pgd_alloc+0x13f/0x210] pgd_alloc+0x13f/0x210
Jun 22 13:34:16 www kernel: [134352.415828]  [mm_init+0xa2/0xd0] mm_init+0xa2/0xd0
Jun 22 13:34:16 www kernel: [134352.415832]  [bprm_mm_init+0x1f/0x170] bprm_mm_init+0x1f/0x170
Jun 22 13:34:16 www kernel: [134352.415837]  [do_execve+0x66/0x1d0] do_execve+0x66/0x1d0
Jun 22 13:34:16 www kernel: [134352.415842]  [sys_execve+0x2f/0x80] sys_execve+0x2f/0x80
Jun 22 13:34:16 www kernel: [134352.415846]  [sysenter_past_esp+0x6b/0xa1] sysenter_past_esp+0x6b/0xa1
Jun 22 13:34:16 www kernel: [134352.415853]  =======================
Jun 22 13:34:16 www kernel: [134352.415855] Mem-info:
Jun 22 13:34:16 www kernel: [134352.415856] DMA per-cpu:
Jun 22 13:34:16 www kernel: [134352.415858] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:16 www kernel: [134352.415861] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:16 www kernel: [134352.415864] CPU    2: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:16 www kernel: [134352.415867] CPU    3: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:16 www kernel: [134352.415869] Normal per-cpu:
Jun 22 13:34:16 www kernel: [134352.415871] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   2
Jun 22 13:34:16 www kernel: [134352.415873] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.415876] CPU    2: Hot: hi:  186, btch:  31 usd:  30   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.415879] CPU    3: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.415881] HighMem per-cpu:
Jun 22 13:34:16 www kernel: [134352.415883] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.415885] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.415888] CPU    2: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.415891] CPU    3: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.415894] Active:60067 inactive:35227 dirty:24 writeback:0 unstable:0
Jun 22 13:34:16 www kernel: [134352.415895]  free:744628 slab:190591 mapped:7997 pagetables:686 bounce:0
Jun 22 13:34:16 www kernel: [134352.415898] DMA free:3548kB min:68kB low:84kB high:100kB active:0kB inactive:0kB present:16256kB pages_scanned:0 all_unreclaimable? yes
Jun 22 13:34:16 www kernel: [134352.415901] lowmem_reserve[]: 0 873 4810 4810
Jun 22 13:34:16 www kernel: [134352.415906] Normal free:95524kB min:3744kB low:4680kB high:5616kB active:248kB inactive:60kB present:894080kB pages_scanned:104 all_unreclaimable? no
Jun 22 13:34:16 www kernel: [134352.415909] lowmem_reserve[]: 0 0 31496 31496
Jun 22 13:34:16 www kernel: [134352.415914] HighMem free:2879440kB min:512kB low:4736kB high:8960kB active:240020kB inactive:140848kB present:4031488kB pages_scanned:0 all_unreclaimable? no
Jun 22 13:34:16 www kernel: [134352.415916] lowmem_reserve[]: 0 0 0 0
Jun 22 13:34:16 www kernel: [134352.415919] DMA: 355*4kB 10*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 3548kB
Jun 22 13:34:16 www kernel: [134352.415928] Normal: 23451*4kB 0*8kB 3*16kB 1*32kB 1*64kB 1*128kB 0*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 95612kB
Jun 22 13:34:16 www kernel: [134352.415936] HighMem: 55*4kB 4179*8kB 12079*16kB 6677*32kB 2728*64kB 1014*128kB 337*256kB 213*512kB 62*1024kB 34*2048kB 441*4096kB = 2879748kB
Jun 22 13:34:16 www kernel: [134352.415946] Swap cache: add 0, delete 0, find 0/0, race 0+0
Jun 22 13:34:16 www kernel: [134352.415947] Free swap  = 0kB
Jun 22 13:34:16 www kernel: [134352.415949] Total swap = 0kB
Jun 22 13:34:16 www kernel: [134352.415950] Free swap:            0kB
Jun 22 13:34:16 www kernel: [134352.427109] 1245184 pages of RAM
Jun 22 13:34:16 www kernel: [134352.427113] 1015808 pages of HIGHMEM
Jun 22 13:34:16 www kernel: [134352.427114] 210245 reserved pages
Jun 22 13:34:16 www kernel: [134352.427115] 67397 pages shared
Jun 22 13:34:16 www kernel: [134352.427117] 0 pages swap cached
Jun 22 13:34:16 www kernel: [134352.427118] 24 pages dirty
Jun 22 13:34:16 www kernel: [134352.427119] 0 pages writeback
Jun 22 13:34:16 www kernel: [134352.427121] 7997 pages mapped
Jun 22 13:34:16 www kernel: [134352.427122] 190591 pages slab
Jun 22 13:34:16 www kernel: [134352.427123] 686 pages pagetables
Jun 22 13:34:16 www kernel: [134352.524220] mysqld invoked oom-killer: gfp_mask=0x40d0, order=1, oomkilladj=-17
Jun 22 13:34:16 www kernel: [134352.524225] Pid: 17486, comm: mysqld Not tainted 2.6.24-19-server #1
Jun 22 13:34:16 www kernel: [134352.524239]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Jun 22 13:34:16 www kernel: [134352.524249]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
Jun 22 13:34:16 www kernel: [134352.524256]  [agpgart:__alloc_pages+0x34c/0x380] __alloc_pages+0x34c/0x380
Jun 22 13:34:16 www kernel: [134352.524264]  [__slab_alloc+0x186/0x4a0] __slab_alloc+0x186/0x4a0
Jun 22 13:34:16 www kernel: [134352.524271]  [ext3:kmem_cache_alloc+0xad/0xc0] kmem_cache_alloc+0xad/0xc0
Jun 22 13:34:16 www kernel: [134352.524275]  [getname+0x28/0xe0] getname+0x28/0xe0
Jun 22 13:34:16 www kernel: [134352.524281]  [getname+0x28/0xe0] getname+0x28/0xe0
Jun 22 13:34:16 www kernel: [134352.524284]  [__user_walk_fd+0x1e/0x60] __user_walk_fd+0x1e/0x60
Jun 22 13:34:16 www kernel: [134352.524287]  [sys_faccessat+0x97/0x160] sys_faccessat+0x97/0x160
Jun 22 13:34:16 www kernel: [134352.524293]  [recalc_sigpending+0xb/0x40] recalc_sigpending+0xb/0x40
Jun 22 13:34:16 www kernel: [134352.524300]  [fuse:sigprocmask+0x65/0x1220] sigprocmask+0x65/0x110
Jun 22 13:34:16 www kernel: [134352.524302]  [do_fcntl+0x25a/0x320] do_fcntl+0x25a/0x320
Jun 22 13:34:16 www kernel: [134352.524308]  [sys_access+0x1f/0x30] sys_access+0x1f/0x30
Jun 22 13:34:16 www kernel: [134352.524311]  [sysenter_past_esp+0x6b/0xa1] sysenter_past_esp+0x6b/0xa1
Jun 22 13:34:16 www kernel: [134352.524318]  [snd_hda_intel:_spin_lock_irqsave+0x10/0x50] _spin_lock_irqsave+0x10/0x50
Jun 22 13:34:16 www kernel: [134352.524326]  =======================
Jun 22 13:34:16 www kernel: [134352.524329] Mem-info:
Jun 22 13:34:16 www kernel: [134352.524330] DMA per-cpu:
Jun 22 13:34:16 www kernel: [134352.524333] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:16 www kernel: [134352.524336] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:16 www kernel: [134352.524339] CPU    2: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:16 www kernel: [134352.524342] CPU    3: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:16 www kernel: [134352.524345] Normal per-cpu:
Jun 22 13:34:16 www kernel: [134352.524346] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.524350] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.524353] CPU    2: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.524357] CPU    3: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.524360] HighMem per-cpu:
Jun 22 13:34:16 www kernel: [134352.524361] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.524364] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.524368] CPU    2: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.524371] CPU    3: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.524375] Active:60258 inactive:35221 dirty:24 writeback:0 unstable:0
Jun 22 13:34:16 www kernel: [134352.524376]  free:744517 slab:190591 mapped:7997 pagetables:686 bounce:0
Jun 22 13:34:16 www kernel: [134352.524380] DMA free:3548kB min:68kB low:84kB high:100kB active:0kB inactive:0kB present:16256kB pages_scanned:0 all_unreclaimable? no
Jun 22 13:34:16 www kernel: [134352.524383] lowmem_reserve[]: 0 873 4810 4810
Jun 22 13:34:16 www kernel: [134352.524389] Normal free:95524kB min:3744kB low:4680kB high:5616kB active:132kB inactive:36kB present:894080kB pages_scanned:0 all_unreclaimable? no
Jun 22 13:34:16 www kernel: [134352.524392] lowmem_reserve[]: 0 0 31496 31496
Jun 22 13:34:16 www kernel: [134352.524400] HighMem free:2878996kB min:512kB low:4736kB high:8960kB active:240900kB inactive:140848kB present:4031488kB pages_scanned:0 all_unreclaimable? no
Jun 22 13:34:16 www kernel: [134352.524402] lowmem_reserve[]: 0 0 0 0
Jun 22 13:34:16 www kernel: [134352.524409] DMA: 355*4kB 10*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 3548kB
Jun 22 13:34:16 www kernel: [134352.524422] Normal: 23463*4kB 14*8kB 3*16kB 1*32kB 1*64kB 1*128kB 0*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 95772kB
Jun 22 13:34:16 www kernel: [134352.524437] HighMem: 44*4kB 4098*8kB 12082*16kB 6678*32kB 2728*64kB 1014*128kB 337*256kB 213*512kB 62*1024kB 34*2048kB 441*4096kB = 2879136kB
Jun 22 13:34:16 www kernel: [134352.524452] Swap cache: add 0, delete 0, find 0/0, race 0+0
Jun 22 13:34:16 www kernel: [134352.524455] Free swap  = 0kB
Jun 22 13:34:16 www kernel: [134352.524457] Total swap = 0kB
Jun 22 13:34:16 www kernel: [134352.524458] Free swap:            0kB
Jun 22 13:34:16 www kernel: [134352.534056] 1245184 pages of RAM
Jun 22 13:34:16 www kernel: [134352.534060] 1015808 pages of HIGHMEM
Jun 22 13:34:16 www kernel: [134352.534061] 210245 reserved pages
Jun 22 13:34:16 www kernel: [134352.534063] 67085 pages shared
Jun 22 13:34:16 www kernel: [134352.534064] 0 pages swap cached
Jun 22 13:34:16 www kernel: [134352.534067] 24 pages dirty
Jun 22 13:34:16 www kernel: [134352.534067] 0 pages writeback
Jun 22 13:34:16 www kernel: [134352.534070] 7997 pages mapped
Jun 22 13:34:16 www kernel: [134352.534071] 190591 pages slab
Jun 22 13:34:16 www kernel: [134352.534073] 686 pages pagetables
Jun 22 13:34:16 www kernel: [134352.725318] courierpop3d invoked oom-killer: gfp_mask=0x40d0, order=1, oomkilladj=0
Jun 22 13:34:16 www kernel: [134352.725323] Pid: 18732, comm: courierpop3d Not tainted 2.6.24-19-server #1
Jun 22 13:34:16 www kernel: [134352.725336]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Jun 22 13:34:16 www kernel: [134352.725346]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
Jun 22 13:34:16 www kernel: [134352.725355]  [agpgart:__alloc_pages+0x34c/0x380] __alloc_pages+0x34c/0x380
Jun 22 13:34:16 www kernel: [134352.725362]  [__slab_alloc+0x186/0x4a0] __slab_alloc+0x186/0x4a0
Jun 22 13:34:16 www kernel: [134352.725369]  [ext3:kmem_cache_alloc+0xad/0xc0] kmem_cache_alloc+0xad/0xc0
Jun 22 13:34:16 www kernel: [134352.725373]  [getname+0x28/0xe0] getname+0x28/0xe0
Jun 22 13:34:16 www kernel: [134352.725378]  [getname+0x28/0xe0] getname+0x28/0xe0
Jun 22 13:34:16 www kernel: [134352.725383]  [do_sys_open+0x1e/0xe0] do_sys_open+0x1e/0xe0
Jun 22 13:34:16 www kernel: [134352.725391]  [sys_open+0x1c/0x20] sys_open+0x1c/0x20
Jun 22 13:34:16 www kernel: [134352.725393]  [sysenter_past_esp+0x6b/0xa1] sysenter_past_esp+0x6b/0xa1
Jun 22 13:34:16 www kernel: [134352.725403]  =======================
Jun 22 13:34:16 www kernel: [134352.725406] Mem-info:
Jun 22 13:34:16 www kernel: [134352.725407] DMA per-cpu:
Jun 22 13:34:16 www kernel: [134352.725410] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:16 www kernel: [134352.725414] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:16 www kernel: [134352.725418] CPU    2: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:16 www kernel: [134352.725421] CPU    3: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:16 www kernel: [134352.725424] Normal per-cpu:
Jun 22 13:34:16 www kernel: [134352.725425] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.725428] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.725432] CPU    2: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.725435] CPU    3: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.725439] HighMem per-cpu:
Jun 22 13:34:16 www kernel: [134352.725440] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.725443] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.725448] CPU    2: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.725451] CPU    3: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:16 www kernel: [134352.725454] Active:60235 inactive:35223 dirty:21 writeback:1 unstable:0
Jun 22 13:34:16 www kernel: [134352.725455]  free:744620 slab:190599 mapped:7989 pagetables:682 bounce:0
Jun 22 13:34:16 www kernel: [134352.725458] DMA free:3548kB min:68kB low:84kB high:100kB active:0kB inactive:0kB present:16256kB pages_scanned:0 all_unreclaimable? yes
Jun 22 13:34:16 www kernel: [134352.725462] lowmem_reserve[]: 0 873 4810 4810
Jun 22 13:34:16 www kernel: [134352.725469] Normal free:95616kB min:3744kB low:4680kB high:5616kB active:208kB inactive:0kB present:894080kB pages_scanned:337 all_unreclaimable? yes
Jun 22 13:34:16 www kernel: [134352.725473] lowmem_reserve[]: 0 0 31496 31496
Jun 22 13:34:16 www kernel: [134352.725480] HighMem free:2879316kB min:512kB low:4736kB high:8960kB active:240604kB inactive:140904kB present:4031488kB pages_scanned:0 all_unreclaimable? no
Jun 22 13:34:16 www kernel: [134352.725483] lowmem_reserve[]: 0 0 0 0
Jun 22 13:34:16 www kernel: [134352.725487] DMA: 355*4kB 10*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 3548kB
Jun 22 13:34:16 www kernel: [134352.725500] Normal: 23461*4kB 20*8kB 3*16kB 1*32kB 1*64kB 1*128kB 0*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 95812kB
Jun 22 13:34:16 www kernel: [134352.725515] HighMem: 120*4kB 4096*8kB 12082*16kB 6678*32kB 2728*64kB 1014*128kB 337*256kB 213*512kB 62*1024kB 34*2048kB 441*4096kB = 2879424kB
Jun 22 13:34:16 www kernel: [134352.725530] Swap cache: add 0, delete 0, find 0/0, race 0+0
Jun 22 13:34:16 www kernel: [134352.725532] Free swap  = 0kB
Jun 22 13:34:16 www kernel: [134352.725534] Total swap = 0kB
Jun 22 13:34:16 www kernel: [134352.725535] Free swap:            0kB
Jun 22 13:34:16 www kernel: [134352.734701] 1245184 pages of RAM
Jun 22 13:34:16 www kernel: [134352.734704] 1015808 pages of HIGHMEM
Jun 22 13:34:16 www kernel: [134352.734705] 210245 reserved pages
Jun 22 13:34:16 www kernel: [134352.734708] 66761 pages shared
Jun 22 13:34:16 www kernel: [134352.734709] 0 pages swap cached
Jun 22 13:34:16 www kernel: [134352.734713] 21 pages dirty
Jun 22 13:34:16 www kernel: [134352.734714] 1 pages writeback
Jun 22 13:34:16 www kernel: [134352.734715] 7989 pages mapped
Jun 22 13:34:16 www kernel: [134352.734717] 190599 pages slab
Jun 22 13:34:16 www kernel: [134352.734719] 682 pages pagetables
Jun 22 13:34:25 www kernel: [134362.070968] printk: 2 messages suppressed.
Jun 22 13:34:25 www kernel: [134362.070979] apache2 invoked oom-killer: gfp_mask=0x40d0, order=1, oomkilladj=-17
Jun 22 13:34:25 www kernel: [134362.070982] Pid: 18733, comm: apache2 Not tainted 2.6.24-19-server #1
Jun 22 13:34:26 www kernel: [134362.070994]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Jun 22 13:34:26 www kernel: [134362.071003]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
Jun 22 13:34:26 www kernel: [134362.071007]  [agpgart:__alloc_pages+0x34c/0x380] __alloc_pages+0x34c/0x380
Jun 22 13:34:26 www kernel: [134362.071011]  [__slab_alloc+0x186/0x4a0] __slab_alloc+0x186/0x4a0
Jun 22 13:34:26 www kernel: [134362.071015]  [ext3:kmem_cache_alloc+0xad/0xc0] kmem_cache_alloc+0xad/0xc0
Jun 22 13:34:26 www kernel: [134362.071019]  [getname+0x28/0xe0] getname+0x28/0xe0
Jun 22 13:34:26 www kernel: [134362.071023]  [getname+0x28/0xe0] getname+0x28/0xe0
Jun 22 13:34:26 www kernel: [134362.071027]  [__user_walk_fd+0x1e/0x60] __user_walk_fd+0x1e/0x60
Jun 22 13:34:26 www kernel: [134362.071030]  [sys_faccessat+0x97/0x160] sys_faccessat+0x97/0x160
Jun 22 13:34:26 www kernel: [134362.071036]  [vfs_read+0x115/0x160] vfs_read+0x115/0x160
Jun 22 13:34:26 www kernel: [134362.071040]  [sys_access+0x1f/0x30] sys_access+0x1f/0x30
Jun 22 13:34:26 www kernel: [134362.071044]  [sysenter_past_esp+0x6b/0xa1] sysenter_past_esp+0x6b/0xa1
Jun 22 13:34:26 www kernel: [134362.071052]  =======================
Jun 22 13:34:26 www kernel: [134362.071053] Mem-info:
Jun 22 13:34:26 www kernel: [134362.071054] DMA per-cpu:
Jun 22 13:34:26 www kernel: [134362.071056] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:26 www kernel: [134362.071058] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:26 www kernel: [134362.071061] CPU    2: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:26 www kernel: [134362.071064] CPU    3: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:26 www kernel: [134362.071067] Normal per-cpu:
Jun 22 13:34:26 www kernel: [134362.071068] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:26 www kernel: [134362.071071] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:26 www kernel: [134362.071074] CPU    2: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:26 www kernel: [134362.071076] CPU    3: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:26 www kernel: [134362.071079] HighMem per-cpu:
Jun 22 13:34:26 www kernel: [134362.071080] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:26 www kernel: [134362.071084] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:26 www kernel: [134362.071086] CPU    2: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:26 www kernel: [134362.071090] CPU    3: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:26 www kernel: [134362.071094] Active:61078 inactive:35121 dirty:0 writeback:24 unstable:0
Jun 22 13:34:26 www kernel: [134362.071095]  free:743749 slab:190636 mapped:7885 pagetables:754 bounce:10
Jun 22 13:34:26 www kernel: [134362.071099] DMA free:3564kB min:68kB low:84kB high:100kB active:0kB inactive:0kB present:16256kB pages_scanned:0 all_unreclaimable? no
Jun 22 13:34:26 www kernel: [134362.071102] lowmem_reserve[]: 0 873 4810 4810
Jun 22 13:34:26 www kernel: [134362.071106] Normal free:95520kB min:3744kB low:4680kB high:5616kB active:104kB inactive:120kB present:894080kB pages_scanned:0 all_unreclaimable? no
Jun 22 13:34:26 www kernel: [134362.071109] lowmem_reserve[]: 0 0 31496 31496
Jun 22 13:34:26 www kernel: [134362.071113] HighMem free:2875912kB min:512kB low:4736kB high:8960kB active:244208kB inactive:140364kB present:4031488kB pages_scanned:0 all_unreclaimable? no
Jun 22 13:34:26 www kernel: [134362.071116] lowmem_reserve[]: 0 0 0 0
Jun 22 13:34:26 www kernel: [134362.071119] DMA: 355*4kB 12*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 3564kB
Jun 22 13:34:26 www kernel: [134362.071131] Normal: 23422*4kB 11*8kB 6*16kB 1*32kB 1*64kB 1*128kB 0*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 95632kB
Jun 22 13:34:26 www kernel: [134362.071141] HighMem: 102*4kB 3675*8kB 12081*16kB 6679*32kB 2728*64kB 1014*128kB 337*256kB 213*512kB 62*1024kB 34*2048kB 441*4096kB = 2876000kB
Jun 22 13:34:26 www kernel: [134362.071153] Swap cache: add 0, delete 0, find 0/0, race 0+0
Jun 22 13:34:26 www kernel: [134362.071155] Free swap  = 0kB
Jun 22 13:34:26 www kernel: [134362.071156] Total swap = 0kB
Jun 22 13:34:26 www kernel: [134362.071157] Free swap:            0kB
Jun 22 13:34:26 www kernel: [134362.080622] 1245184 pages of RAM
Jun 22 13:34:26 www kernel: [134362.080627] 1015808 pages of HIGHMEM
Jun 22 13:34:26 www kernel: [134362.080628] 210245 reserved pages
Jun 22 13:34:26 www kernel: [134362.080631] 73829 pages shared
Jun 22 13:34:26 www kernel: [134362.080632] 0 pages swap cached
Jun 22 13:34:26 www kernel: [134362.080635] 0 pages dirty
Jun 22 13:34:26 www kernel: [134362.080636] 24 pages writeback
Jun 22 13:34:26 www kernel: [134362.080638] 7885 pages mapped
Jun 22 13:34:26 www kernel: [134362.080640] 190636 pages slab
Jun 22 13:34:26 www kernel: [134362.080641] 754 pages pagetables
Jun 22 13:34:26 www kernel: [134362.315636] syslogd invoked oom-killer: gfp_mask=0x40d0, order=1, oomkilladj=0
Jun 22 13:34:26 www kernel: [134362.315641] Pid: 4431, comm: syslogd Not tainted 2.6.24-19-server #1
Jun 22 13:34:26 www kernel: [134362.315655]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Jun 22 13:34:26 www kernel: [134362.315671]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
Jun 22 13:34:26 www kernel: [134362.315679]  [agpgart:__alloc_pages+0x34c/0x380] __alloc_pages+0x34c/0x380
Jun 22 13:34:26 www kernel: [134362.315687]  [__slab_alloc+0x186/0x4a0] __slab_alloc+0x186/0x4a0
Jun 22 13:34:26 www kernel: [134362.315693]  [ext3:kmem_cache_alloc+0xad/0xc0] kmem_cache_alloc+0xad/0xc0
Jun 22 13:34:26 www kernel: [134362.315698]  [getname+0x28/0xe0] getname+0x28/0xe0
Jun 22 13:34:26 www kernel: [134362.315703]  [getname+0x28/0xe0] getname+0x28/0xe0
Jun 22 13:34:26 www kernel: [134362.315707]  [__user_walk_fd+0x1e/0x60] __user_walk_fd+0x1e/0x60
Jun 22 13:34:26 www kernel: [134362.315710]  [cp_new_stat64+0xf9/0x110] cp_new_stat64+0xf9/0x110
Jun 22 13:34:26 www kernel: [134362.315715]  [vfs_stat_fd+0x22/0x60] vfs_stat_fd+0x22/0x60
Jun 22 13:34:26 www kernel: [134362.315724]  [sys_stat64+0xf/0x30] sys_stat64+0xf/0x30
Jun 22 13:34:26 www kernel: [134362.315727]  [sys_socketcall+0x1a6/0x2b0] sys_socketcall+0x1a6/0x2b0
Jun 22 13:34:26 www kernel: [134362.315734]  [recalc_sigpending+0xb/0x40] recalc_sigpending+0xb/0x40
Jun 22 13:34:26 www kernel: [134362.315739]  [fuse:sigprocmask+0x65/0x1220] sigprocmask+0x65/0x110
Jun 22 13:34:26 www kernel: [134362.315745]  [sys_rt_sigprocmask+0xed/0x110] sys_rt_sigprocmask+0xed/0x110
Jun 22 13:34:26 www kernel: [134362.315750]  [sys_time+0xa/0x30] sys_time+0xa/0x30
Jun 22 13:34:26 www kernel: [134362.315752]  [sysenter_past_esp+0x6b/0xa1] sysenter_past_esp+0x6b/0xa1
Jun 22 13:34:26 www kernel: [134362.315760]  =======================
Jun 22 13:34:26 www kernel: [134362.315761] Mem-info:
Jun 22 13:34:26 www kernel: [134362.315764] DMA per-cpu:
Jun 22 13:34:26 www kernel: [134362.315766] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:26 www kernel: [134362.315769] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:26 www kernel: [134362.315772] CPU    2: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:26 www kernel: [134362.315776] CPU    3: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Jun 22 13:34:26 www kernel: [134362.315779] Normal per-cpu:
Jun 22 13:34:26 www kernel: [134362.315781] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:26 www kernel: [134362.315784] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:26 www kernel: [134362.315788] CPU    2: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:26 www kernel: [134362.315791] CPU    3: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:26 www kernel: [134362.315794] HighMem per-cpu:
Jun 22 13:34:26 www kernel: [134362.315796] CPU    0: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:26 www kernel: [134362.315800] CPU    1: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:26 www kernel: [134362.315802] CPU    2: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:26 www kernel: [134362.315806] CPU    3: Hot: hi:  186, btch:  31 usd:   0   Cold: hi:   62, btch:  15 usd:   0
Jun 22 13:34:26 www kernel: [134362.315810] Active:61066 inactive:35142 dirty:12 writeback:0 unstable:0
Jun 22 13:34:26 www kernel: [134362.315811]  free:743749 slab:190631 mapped:7795 pagetables:749 bounce:0
Jun 22 13:34:26 www kernel: [134362.315814] DMA free:3564kB min:68kB low:84kB high:100kB active:0kB inactive:0kB present:16256kB pages_scanned:0 all_unreclaimable? no
Jun 22 13:34:26 www kernel: [134362.315817] lowmem_reserve[]: 0 873 4810 4810
Jun 22 13:34:26 www kernel: [134362.315822] Normal free:95372kB min:3744kB low:4680kB high:5616kB active:168kB inactive:136kB present:894080kB pages_scanned:87 all_unreclaimable? no
Jun 22 13:34:26 www kernel: [134362.315825] lowmem_reserve[]: 0 0 31496 31496
Jun 22 13:34:26 www kernel: [134362.315830] HighMem free:2876060kB min:512kB low:4736kB high:8960kB active:244096kB inactive:140432kB present:4031488kB pages_scanned:0 all_unreclaimable? no
Jun 22 13:34:26 www kernel: [134362.315833] lowmem_reserve[]: 0 0 0 0



```

---

### Post by windependence on 2009-06-23
Your free output is perfectly normal. Linux != Windows. Linux memory management will use ALL the memory available to it. It is not an indication it is out of memory at all. On most modern systems, swap is not even technically necessary. IMHO you have other issues here.

-Tim

---

