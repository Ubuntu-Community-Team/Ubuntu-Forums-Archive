---
title: "Ubuntu 15.04 and Hyper-V dynamic memory doesn't work (properly)"
date: 2015-05-06
forum: Virtualisation
---

### Post by gijs007 on 2015-05-06
I've enabled dynamic memory for my Ubuntu virtual machine and noticed that the memory never increases above the default of 2048..

It appears that this causes some errors because in my syslog file I found the following:
```
May  6 13:18:01 www kernel: [772095.801933] php5-fpm invoked oom-killer: gfp_mask=0x201da, order=0, oom_score_adj=0
May  6 13:18:01 www kernel: [772095.801936] php5-fpm cpuset=/ mems_allowed=0
May  6 13:18:01 www kernel: [772095.801941] CPU: 5 PID: 19217 Comm: php5-fpm Tainted: G         C     3.19.0-15-generic #15-Ubuntu
May  6 13:18:01 www kernel: [772095.801943] Hardware name: Microsoft Corporation Virtual Machine/Virtual Machine, BIOS Hyper-V UEFI Release v1.0 11/26/2012
May  6 13:18:01 www kernel: [772095.801944]  0000000000000000 ffff88007a42b898 ffffffff817c2205 0000000000000007
May  6 13:18:01 www kernel: [772095.801947]  ffff88007b5409d0 ffff88007a42b918 ffffffff817bfc73 ffff88007a42b8f8
May  6 13:18:01 www kernel: [772095.801949]  ffffffff810d57f4 ffff88007c0b4278 ffff880009aa58b8 ffff880079d875c0
May  6 13:18:01 www kernel: [772095.801951] Call Trace:
May  6 13:18:01 www kernel: [772095.801958]  [<ffffffff817c2205>] dump_stack+0x45/0x57
May  6 13:18:01 www kernel: [772095.801961]  [<ffffffff817bfc73>] dump_header+0x7f/0x1e7
May  6 13:18:01 www kernel: [772095.801965]  [<ffffffff810d57f4>] ? rcu_oom_notify+0xd4/0xf0
May  6 13:18:01 www kernel: [772095.801969]  [<ffffffff8117d04b>] oom_kill_process+0x22b/0x390
May  6 13:18:01 www kernel: [772095.801973]  [<ffffffff8107eabe>] ? has_capability_noaudit+0x1e/0x30
May  6 13:18:01 www kernel: [772095.801975]  [<ffffffff8117d5bd>] out_of_memory+0x24d/0x500
May  6 13:18:01 www kernel: [772095.801978]  [<ffffffff8118350a>] __alloc_pages_nodemask+0xaba/0xba0
May  6 13:18:01 www kernel: [772095.801983]  [<ffffffff811c9821>] alloc_pages_current+0x91/0x110
May  6 13:18:01 www kernel: [772095.801985]  [<ffffffff81179567>] __page_cache_alloc+0xa7/0xd0
May  6 13:18:01 www kernel: [772095.801988]  [<ffffffff8117bc7f>] filemap_fault+0x1af/0x400
May  6 13:18:01 www kernel: [772095.801991]  [<ffffffff811a64fd>] __do_fault+0x3d/0xc0
May  6 13:18:01 www kernel: [772095.801994]  [<ffffffff817c8f42>] ? _raw_spin_lock+0x32/0x80
May  6 13:18:01 www kernel: [772095.801996]  [<ffffffff811a8daf>] do_read_fault.isra.55+0x1df/0x2f0
May  6 13:18:01 www kernel: [772095.801998]  [<ffffffff811aac7e>] handle_mm_fault+0x86e/0xff0
May  6 13:18:01 www kernel: [772095.802001]  [<ffffffff810b6386>] ? autoremove_wake_function+0x16/0x40
May  6 13:18:01 www kernel: [772095.802004]  [<ffffffff81062bdd>] __do_page_fault+0x1dd/0x5b0
May  6 13:18:01 www kernel: [772095.802006]  [<ffffffff810b5f28>] ? __wake_up+0x48/0x60
May  6 13:18:01 www kernel: [772095.802008]  [<ffffffff810d547f>] ? wake_nocb_leader+0x4f/0x60
May  6 13:18:01 www kernel: [772095.802010]  [<ffffffff810d5567>] ? __call_rcu_nocb_enqueue+0xd7/0xe0
May  6 13:18:01 www kernel: [772095.802012]  [<ffffffff81062fe1>] do_page_fault+0x31/0x70
May  6 13:18:01 www kernel: [772095.802015]  [<ffffffff817cb4a8>] page_fault+0x28/0x30
May  6 13:18:01 www kernel: [772095.802016] Mem-Info:
May  6 13:18:01 www /etc/init.d/mysql[1002]: /usr/bin/mysqld_safe: line 182:  6502 Killed                  nohup /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --log-error=/var/log/mysql/error.log --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306 < /dev/null >> /var/log/mysql/error.log 2>&1 >> /var/log/mysql/error.log 2>&1 >> /var/log/mysql/error.log 2>&1
May  6 13:18:01 www kernel: [772095.802018] Node 0 DMA per-cpu:
May  6 13:18:01 www kernel: [772095.802020] CPU    0: hi:    0, btch:   1 usd:   0
May  6 13:18:01 www kernel: [772095.802021] CPU    1: hi:    0, btch:   1 usd:   0
May  6 13:18:01 www kernel: [772095.802022] CPU    2: hi:    0, btch:   1 usd:   0
May  6 13:18:01 www kernel: [772095.802023] CPU    3: hi:    0, btch:   1 usd:   0
May  6 13:18:01 www kernel: [772095.802024] CPU    4: hi:    0, btch:   1 usd:   0
May  6 13:18:01 www kernel: [772095.802025] CPU    5: hi:    0, btch:   1 usd:   0
May  6 13:18:01 www kernel: [772095.802026] CPU    6: hi:    0, btch:   1 usd:   0
May  6 13:18:01 www kernel: [772095.802027] CPU    7: hi:    0, btch:   1 usd:   0
May  6 13:18:01 www kernel: [772095.802028] Node 0 DMA32 per-cpu:
May  6 13:18:01 www kernel: [772095.802029] CPU    0: hi:  186, btch:  31 usd: 178
May  6 13:18:01 www kernel: [772095.802031] CPU    1: hi:  186, btch:  31 usd:   0
May  6 13:18:01 www kernel: [772095.802032] CPU    2: hi:  186, btch:  31 usd:  60
May  6 13:18:01 www kernel: [772095.802033] CPU    3: hi:  186, btch:  31 usd:  54
May  6 13:18:01 www kernel: [772095.802035] CPU    4: hi:  186, btch:  31 usd:  28
May  6 13:18:01 www kernel: [772095.802036] CPU    5: hi:  186, btch:  31 usd:  30
May  6 13:18:01 www kernel: [772095.802037] CPU    6: hi:  186, btch:  31 usd:  65
May  6 13:18:01 www kernel: [772095.802039] CPU    7: hi:  186, btch:  31 usd:  24
May  6 13:18:01 www kernel: [772095.802043] active_anon:340700 inactive_anon:120128 isolated_anon:0
May  6 13:18:01 www kernel: [772095.802043]  active_file:392 inactive_file:417 isolated_file:0
May  6 13:18:01 www kernel: [772095.802043]  unevictable:0 dirty:0 writeback:0 unstable:0
May  6 13:18:01 www kernel: [772095.802043]  free:13235 slab_reclaimable:5457 slab_unreclaimable:9083
May  6 13:18:01 www kernel: [772095.802043]  mapped:7181 shmem:17909 pagetables:4132 bounce:0
May  6 13:18:01 www kernel: [772095.802043]  free_cma:0
May  6 13:18:01 www kernel: [772095.802046] Node 0 DMA free:8240kB min:348kB low:432kB high:520kB active_anon:2724kB inactive_anon:2992kB active_file:4kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15996kB managed:15904kB mlocked:0kB dirty:0kB writeback:0kB mapped:1356kB shmem:1400kB slab_reclaimable:216kB slab_unreclaimable:232kB kernel_stack:112kB pagetables:952kB unstable:0kB bounce:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
May  6 13:18:01 www kernel: [772095.802050] lowmem_reserve[]: 0 1973 1973 1973
May  6 13:18:01 www kernel: [772095.802053] Node 0 DMA32 free:44700kB min:44704kB low:55880kB high:67056kB active_anon:1360076kB inactive_anon:477520kB active_file:1564kB inactive_file:1672kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:2078120kB managed:2022304kB mlocked:0kB dirty:0kB writeback:0kB mapped:27368kB shmem:70236kB slab_reclaimable:21612kB slab_unreclaimable:36100kB kernel_stack:6080kB pagetables:15576kB unstable:0kB bounce:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:20192 all_unreclaimable? yes
May  6 13:18:01 www kernel: [772095.802056] lowmem_reserve[]: 0 0 0 0
May  6 13:18:01 www kernel: [772095.802058] Node 0 DMA: 4*4kB (EM) 1*8kB (U) 2*16kB (E) 4*32kB (UEM) 6*64kB (EM) 4*128kB (UEM) 2*256kB (UM) 3*512kB (UEM) 3*1024kB (UEM) 1*2048kB (R) 0*4096kB = 8248kB
May  6 13:18:01 www kernel: [772095.802068] Node 0 DMA32: 68*4kB (UE) 172*8kB (UEM) 240*16kB (UEM) 168*32kB (UEM) 100*64kB (UEM) 81*128kB (UEM) 33*256kB (UEM) 11*512kB (UEM) 3*1024kB (E) 0*2048kB 0*4096kB = 44784kB
May  6 13:18:01 www kernel: [772095.802078] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
May  6 13:18:01 www kernel: [772095.802079] 19281 total pagecache pages
May  6 13:18:01 www kernel: [772095.802080] 444 pages in swap cache
May  6 13:18:01 www kernel: [772095.802082] Swap cache stats: add 1751872, delete 1751428, find 211702/239528
May  6 13:18:01 www kernel: [772095.802082] Free swap  = 0kB
May  6 13:18:01 www kernel: [772095.802083] Total swap = 2097148kB
May  6 13:18:01 www kernel: [772095.802084] 523529 pages RAM
May  6 13:18:01 www kernel: [772095.802085] 0 pages HighMem/MovableOnly
May  6 13:18:01 www kernel: [772095.802086] 13977 pages reserved
May  6 13:18:01 www kernel: [772095.802087] 0 pages cma reserved
May  6 13:18:01 www kernel: [772095.802087] 0 pages hwpoisoned
May  6 13:18:01 www kernel: [772095.802088] [ pid ]   uid  tgid total_vm      rss nr_ptes swapents oom_score_adj name
May  6 13:18:01 www kernel: [772095.802094] [  332]     0   332     7259       30      17       51             0 systemd-journal
May  6 13:18:01 www kernel: [772095.802135] [  716]     0   716     4795        6      14       38             0 atd
May  6 13:18:01 www kernel: [772095.802137] [  725]     0   725    14910       28      33      142         -1000 sshd
May  6 13:18:01 www kernel: [772095.802139] [  732]     0   732    71163      111      41      135             0 accounts-daemon
May  6 13:18:01 www kernel: [772095.802141] [  738]     0   738     7233       22      20       47             0 cron
May  6 13:18:01 www kernel: [772095.802143] [  746]   104   746    64071     5874      40     1288             0 rsyslogd
May  6 13:18:01 www kernel: [772095.802145] [  770]   105   770    10629       74      26       97          -900 dbus-daemon
May  6 13:18:01 www kernel: [772095.802146] [  771]     0   771     4860       19      15       35             0 irqbalance
May  6 13:18:01 www kernel: [772095.802148] [  783]     0   783    69671       82      38      633             0 polkitd
May  6 13:18:01 www kernel: [772095.802150] [  787]     0   787     3964        2      13       38             0 agetty
May  6 13:18:01 www kernel: [772095.802151] [  789]   110   789    96965    13755      95     6417             0 memcached
May  6 13:18:01 www kernel: [772095.802153] [ 1001]     0  1001     5274        2      15      115             0 mysqld_safe
May  6 13:18:01 www kernel: [772095.802155] [ 1002]     0  1002     5753        0      17       57             0 logger
May  6 13:18:01 www kernel: [772095.802156] [ 1238]     0  1238    41946      717      85       67             0 apache2
May  6 13:18:01 www kernel: [772095.802159] [44370]     0 44370    10392        2      22      109         -1000 systemd-udevd
May  6 13:18:01 www kernel: [772095.802161] [52446]     0 52446     7136       42      18       39             0 systemd-logind
May  6 13:18:01 www kernel: [772095.802162] [52468]   100 52468    24553       14      18       45             0 systemd-timesyn
May  6 13:18:01 www kernel: [772095.802164] [ 6502]   109  6502  1822125   377586    1867   508631             0 mysqld
May  6 13:18:01 www kernel: [772095.802167] [17021]     0 17021   175597      358      87      772             0 php5-fpm
May  6 13:18:01 www kernel: [772095.802169] [17691]    33 17691   194238     6448      97      428             0 php5-fpm
May  6 13:18:01 www kernel: [772095.802170] [17694]    33 17694   194539     5548      96      428             0 php5-fpm
May  6 13:18:01 www kernel: [772095.802172] [17695]    33 17695   177602     6060      95      438             0 php5-fpm
May  6 13:18:01 www kernel: [772095.802174] [17696]    33 17696   178000     4497      95      437             0 php5-fpm
May  6 13:18:01 www kernel: [772095.802175] [17697]    33 17697   194122     4019      95      437             0 php5-fpm
May  6 13:18:01 www kernel: [772095.802177] [18352]    33 18352    28731      634      53       87             0 apache2
May  6 13:18:01 www kernel: [772095.802179] [18360]    33 18360   619660     9663     161       65             0 apache2
May  6 13:18:01 www kernel: [772095.802180] [18361]    33 18361   618093     9077     159       65             0 apache2
May  6 13:18:01 www kernel: [772095.802182] [18362]    33 18362   617558     9244     158       70             0 apache2
May  6 13:18:01 www kernel: [772095.802184] [19209]    33 19209   192691     3182      82      455             0 php5-fpm
May  6 13:18:01 www kernel: [772095.802186] [19210]    33 19210   175955     1746      76      530             0 php5-fpm
May  6 13:18:01 www kernel: [772095.802188] [19211]    33 19211   192080     1682      78      460             0 php5-fpm
May  6 13:18:01 www kernel: [772095.802190] [19214]    33 19214   193001     4453      85      447             0 php5-fpm
May  6 13:18:01 www kernel: [772095.802192] [19215]    33 19215   175955     1862      76      530             0 php5-fpm
May  6 13:18:01 www kernel: [772095.802194] [19216]    33 19216   175858     1545      75      546             0 php5-fpm
May  6 13:18:01 www kernel: [772095.802196] [19217]    33 19217   192242     2590      80      457             0 php5-fpm
May  6 13:18:01 www kernel: [772095.802198] [19218]    33 19218   175597      367      66      763             0 php5-fpm
May  6 13:18:01 www kernel: [772095.802200] Out of memory: Kill process 6502 (mysqld) score 859 or sacrifice child
May  6 13:18:01 www kernel: [772095.802235] Killed process 6502 (mysqld) total-vm:7288500kB, anon-rss:1510344kB, file-rss:0kB
```

I've now set the default startup memory tot 4096 for this VM and did a dist-upgrade to update the kernel.
Just after the startup (~1-2 minutes) the VM is already using ~10GB and this increases to ~11GB after another minute or two.
I've looked at the memory usage in phpmyadmin and it appears that 9.4 GB is currently free, which makes me wonder why this is happening.

It appears to me that the dynamic memory function is not working correctly, since at first it wasn't allocating enough memory and had to kill processes and now (after the dist-upgrade) it's allocating to much memory.

---

