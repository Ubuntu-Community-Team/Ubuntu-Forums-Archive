---
title: "oom-killer kills without reason"
date: 2013-06-08
forum: Server Platforms
---

### Post by shimie on 2013-06-08
[COLOR=#000000][FONT=verdana]Hello,
to night Qemu killed my VM and some Minecraft-Servers, dmesg:

[/FONT][/COLOR]```
[So Jun  9 01:03:02 2013] qemu-system-x86 invoked oom-killer: gfp_mask=0xd0, order=0, oom_adj=0, oom_score_adj=0
[So Jun  9 01:03:02 2013] qemu-system-x86 cpuset=/ mems_allowed=0
[So Jun  9 01:03:02 2013] Pid: 22140, comm: qemu-system-x86 Tainted: G         C   3.2.0-36-generic #57-Ubuntu
[So Jun  9 01:03:02 2013] Call Trace:
[So Jun  9 01:03:02 2013]  [<ffffffff810c0f1d>] ? cpuset_print_task_mems_allowed+0x9d/0xb0
[So Jun  9 01:03:02 2013]  [<ffffffff8111beb1>] dump_header+0x91/0xe0
[So Jun  9 01:03:02 2013]  [<ffffffff8111c235>] oom_kill_process+0x85/0xb0
[So Jun  9 01:03:02 2013]  [<ffffffff8111c5da>] out_of_memory+0xfa/0x220
[So Jun  9 01:03:02 2013]  [<ffffffff81121fdc>] __alloc_pages_nodemask+0x8dc/0x8f0
[So Jun  9 01:03:02 2013]  [<ffffffff81159076>] alloc_pages_current+0xb6/0x120
[So Jun  9 01:03:02 2013]  [<ffffffff8111d05e>] __get_free_pages+0xe/0x40
[So Jun  9 01:03:02 2013]  [<ffffffffa039027c>] mmu_topup_memory_caches+0xdc/0x110 [kvm]
[So Jun  9 01:03:02 2013]  [<ffffffffa0395dc6>] tdp_page_fault+0x46/0x200 [kvm]
[So Jun  9 01:03:02 2013]  [<ffffffffa0390937>] kvm_mmu_page_fault+0x37/0xb0 [kvm]
[So Jun  9 01:03:02 2013]  [<ffffffffa03da066>] handle_ept_violation+0x76/0x160 [kvm_intel]
[So Jun  9 01:03:02 2013]  [<ffffffffa03de0b1>] vmx_handle_exit+0xb1/0x260 [kvm_intel]
[So Jun  9 01:03:02 2013]  [<ffffffffa0389893>] vcpu_enter_guest+0x1e3/0x590 [kvm]
[So Jun  9 01:03:02 2013]  [<ffffffffa038a1c8>] __vcpu_run+0x158/0x2d0 [kvm]
[So Jun  9 01:03:02 2013]  [<ffffffffa038a3be>] kvm_arch_vcpu_ioctl_run+0x7e/0x150 [kvm]
[So Jun  9 01:03:02 2013]  [<ffffffffa0373192>] kvm_vcpu_ioctl+0x4e2/0x780 [kvm]
[So Jun  9 01:03:02 2013]  [<ffffffffa0373dbb>] ? kvm_vm_ioctl+0x10b/0x300 [kvm]
[So Jun  9 01:03:02 2013]  [<ffffffff8105702d>] ? set_next_entity+0xad/0xd0
[So Jun  9 01:03:02 2013]  [<ffffffff8118b76a>] do_vfs_ioctl+0x8a/0x340
[So Jun  9 01:03:02 2013]  [<ffffffff81115f2d>] ? fire_user_return_notifiers+0x3d/0x50
[So Jun  9 01:03:02 2013]  [<ffffffff8118bab1>] sys_ioctl+0x91/0xa0
[So Jun  9 01:03:02 2013]  [<ffffffff81665a02>] system_call_fastpath+0x16/0x1b
[So Jun  9 01:03:02 2013] Mem-Info:
[So Jun  9 01:03:02 2013] Node 0 DMA per-cpu:
[So Jun  9 01:03:02 2013] CPU    0: hi:    0, btch:   1 usd:   0
[So Jun  9 01:03:02 2013] CPU    1: hi:    0, btch:   1 usd:   0
[So Jun  9 01:03:02 2013] CPU    2: hi:    0, btch:   1 usd:   0
[So Jun  9 01:03:02 2013] CPU    3: hi:    0, btch:   1 usd:   0
[So Jun  9 01:03:02 2013] CPU    4: hi:    0, btch:   1 usd:   0
[So Jun  9 01:03:02 2013] CPU    5: hi:    0, btch:   1 usd:   0
[So Jun  9 01:03:02 2013] CPU    6: hi:    0, btch:   1 usd:   0
[So Jun  9 01:03:02 2013] CPU    7: hi:    0, btch:   1 usd:   0
[So Jun  9 01:03:02 2013] Node 0 DMA32 per-cpu:
[So Jun  9 01:03:02 2013] CPU    0: hi:  186, btch:  31 usd:   0
[So Jun  9 01:03:02 2013] CPU    1: hi:  186, btch:  31 usd:   0
[So Jun  9 01:03:02 2013] CPU    2: hi:  186, btch:  31 usd:   0
[So Jun  9 01:03:02 2013] CPU    3: hi:  186, btch:  31 usd:   0
[So Jun  9 01:03:02 2013] CPU    4: hi:  186, btch:  31 usd:   0
[So Jun  9 01:03:02 2013] CPU    5: hi:  186, btch:  31 usd:   0
[So Jun  9 01:03:02 2013] CPU    6: hi:  186, btch:  31 usd:   0
[So Jun  9 01:03:02 2013] CPU    7: hi:  186, btch:  31 usd:   0
[So Jun  9 01:03:02 2013] Node 0 Normal per-cpu:
[So Jun  9 01:03:02 2013] CPU    0: hi:  186, btch:  31 usd:   0
[So Jun  9 01:03:02 2013] CPU    1: hi:  186, btch:  31 usd:   0
[So Jun  9 01:03:02 2013] CPU    2: hi:  186, btch:  31 usd:   0
[So Jun  9 01:03:02 2013] CPU    3: hi:  186, btch:  31 usd:   0
[So Jun  9 01:03:02 2013] CPU    4: hi:  186, btch:  31 usd:   0
[So Jun  9 01:03:02 2013] CPU    5: hi:  186, btch:  31 usd:   0
[So Jun  9 01:03:02 2013] CPU    6: hi:  186, btch:  31 usd:   0
[So Jun  9 01:03:02 2013] CPU    7: hi:  186, btch:  31 usd:   0
[So Jun  9 01:03:02 2013] active_anon:7262474 inactive_anon:654968 isolated_anon:0
[So Jun  9 01:03:02 2013]  active_file:0 inactive_file:0 isolated_file:0
[So Jun  9 01:03:02 2013]  unevictable:31209 dirty:1 writeback:0 unstable:0
[So Jun  9 01:03:02 2013]  free:49492 slab_reclaimable:22931 slab_unreclaimable:72211
[So Jun  9 01:03:02 2013]  mapped:1492 shmem:1955634 pagetables:18657 bounce:0
[So Jun  9 01:03:02 2013] Node 0 DMA free:15904kB min:32kB low:40kB high:48kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15648kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
[So Jun  9 01:03:02 2013] lowmem_reserve[]: 0 3438 32140 32140
[So Jun  9 01:03:02 2013] Node 0 DMA32 free:121820kB min:7224kB low:9028kB high:10836kB active_anon:3293876kB inactive_anon:51240kB active_file:8kB inactive_file:68kB unevictable:9184kB isolated(anon):0kB isolated(file):0kB present:3520768kB mlocked:9184kB dirty:0kB writeback:0kB mapped:8kB shmem:551152kB slab_reclaimable:5768kB slab_unreclaimable:18684kB kernel_stack:312kB pagetables:6544kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:6134 all_unreclaimable? yes
[So Jun  9 01:03:02 2013] lowmem_reserve[]: 0 0 28702 28702
[So Jun  9 01:03:02 2013] Node 0 Normal free:60244kB min:60324kB low:75404kB high:90484kB active_anon:25756020kB inactive_anon:2568632kB active_file:0kB inactive_file:0kB unevictable:115652kB isolated(anon):0kB isolated(file):0kB present:29391264kB mlocked:115652kB dirty:4kB writeback:0kB mapped:5960kB shmem:7271384kB slab_reclaimable:85956kB slab_unreclaimable:270160kB kernel_stack:6024kB pagetables:68084kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:24 all_unreclaimable? yes
[So Jun  9 01:03:02 2013] lowmem_reserve[]: 0 0 0 0
[So Jun  9 01:03:02 2013] Node 0 DMA: 0*4kB 0*8kB 0*16kB 1*32kB 2*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 3*4096kB = 15904kB
[So Jun  9 01:03:02 2013] Node 0 DMA32: 656*4kB 693*8kB 316*16kB 232*32kB 177*64kB 127*128kB 94*256kB 56*512kB 17*1024kB 0*2048kB 1*4096kB = 122472kB
[So Jun  9 01:03:02 2013] Node 0 Normal: 14274*4kB 29*8kB 1*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 1*4096kB = 61440kB
[So Jun  9 01:03:02 2013] 1956817 total pagecache pages
[So Jun  9 01:03:02 2013] 0 pages in swap cache
[So Jun  9 01:03:02 2013] Swap cache stats: add 0, delete 0, find 0/0
[So Jun  9 01:03:02 2013] Free swap  = 0kB
[So Jun  9 01:03:02 2013] Total swap = 0kB
[So Jun  9 01:03:02 2013] 8381936 pages RAM
[So Jun  9 01:03:02 2013] 167864 pages reserved
[So Jun  9 01:03:02 2013] 504497 pages shared
[So Jun  9 01:03:02 2013] 7900203 pages non-shared
[So Jun  9 01:03:02 2013] [ pid ]   uid  tgid total_vm      rss cpu oom_adj oom_score_adj name
[So Jun  9 01:03:02 2013] [  584]     0   584     4308      105   3       0             0 upstart-udev-br
[So Jun  9 01:03:02 2013] [  592]     0   592     5450      345   5     -17         -1000 udevd
[So Jun  9 01:03:02 2013] [  619]     0   619     6385      161   3       0             0 rpc.idmapd
[So Jun  9 01:03:02 2013] [  826]   110   826     6244      425   1       0             0 dbus-daemon
[So Jun  9 01:03:02 2013] [  898]     0   898     5297      176   4       0             0 bluetoothd
[So Jun  9 01:03:02 2013] [  903]     0   903    26040      421   1       0             0 cupsd
[So Jun  9 01:03:02 2013] [  909]     0   909     3797       75   1       0             0 upstart-socket-
[So Jun  9 01:03:02 2013] [  912]     0   912     4800      201   0       0             0 rpcbind
[So Jun  9 01:03:02 2013] [ 1019]   105  1019     5376      270   0       0             0 rpc.statd
[So Jun  9 01:03:02 2013] [ 1050]     0  1050    12508      336   1     -17         -1000 sshd
[So Jun  9 01:03:02 2013] [ 1090]     0  1090    19760      359   6       0             0 modem-manager
[So Jun  9 01:03:02 2013] [ 1118]     0  1118    39031      459   5       0             0 NetworkManager
[So Jun  9 01:03:02 2013] [ 1122]     0  1122    48868      428   2       0             0 polkitd
[So Jun  9 01:03:02 2013] [ 1215]     0  1215     3935      206   0       0             0 getty
[So Jun  9 01:03:02 2013] [ 1221]     0  1221     3935      205   5       0             0 getty
[So Jun  9 01:03:02 2013] [ 1262]     0  1262     3935      205   0       0             0 getty
[So Jun  9 01:03:02 2013] [ 1263]     0  1263     3935      205   1       0             0 getty
[So Jun  9 01:03:02 2013] [ 1267]     0  1267     3935      207   0       0             0 getty
[So Jun  9 01:03:02 2013] [ 1278]     0  1278     1115      199   1       0             0 acpid
[So Jun  9 01:03:02 2013] [ 1279]     0  1279    31382      254   3       0             0 gdm-binary
[So Jun  9 01:03:02 2013] [ 1296]     0  1296     4358      217   3       0             0 dovecot
[So Jun  9 01:03:02 2013] [ 1301]     0  1301     4778      208   2       0             0 cron
[So Jun  9 01:03:02 2013] [ 1341]   106  1341  1103101   550992   3       0             0 mysqld
[So Jun  9 01:03:02 2013] [ 1434]     0  1434    34860      361   0       0             0 gdm-simple-slav
[So Jun  9 01:03:02 2013] [ 1455]   119  1455    50091      535   0       0             0 whoopsie
[So Jun  9 01:03:02 2013] [ 1565]     0  1565    29645     1521   0       0             0 Xorg
[So Jun  9 01:03:02 2013] [ 1585]   108  1585     2238      170   0       0             0 anvil
[So Jun  9 01:03:02 2013] [ 1586]     0  1586     2269      179   2       0             0 log
[So Jun  9 01:03:02 2013] [ 1659]   126  1659    11005      421   0       0             0 freshclam
[So Jun  9 01:03:02 2013] [ 1984]     0  1984  1047219      487   7       0             0 console-kit-dae
[So Jun  9 01:03:02 2013] [ 2191]  1000  2191     6037      205   2       0             0 screen
[So Jun  9 01:03:02 2013] [ 2208]  1000  2208     9527     1471   3       0             0 python
[So Jun  9 01:03:02 2013] [ 2214]  1000  2214     1100      133   6       0             0 sh
[So Jun  9 01:03:02 2013] [ 2226]  1000  2226  1975776    79486   2       0             0 java
[So Jun  9 01:03:02 2013] [ 2290]  1000  2290     6037      245   0       0             0 screen
[So Jun  9 01:03:02 2013] [ 2292]  1000  2292     9527     1468   3       0             0 python
[So Jun  9 01:03:02 2013] [ 2300]  1000  2300     1100      133   5       0             0 sh
[So Jun  9 01:03:02 2013] [ 2302]  1000  2302  1678311    94465   0       0             0 java
[So Jun  9 01:03:02 2013] [ 2393]   114  2393     6117      220   0       0             0 dbus-daemon
[So Jun  9 01:03:02 2013] [ 2397]   114  2397    97981      759   0       0             0 gnome-session
[So Jun  9 01:03:02 2013] [ 2585]   114  2585    12771      622   0       0             0 gconfd-2
[So Jun  9 01:03:02 2013] [ 2635]   114  2635   211945     1473   0       0             0 gnome-settings-
[So Jun  9 01:03:02 2013] [ 2832]     0  2832    54975      368   0       0             0 upowerd
[So Jun  9 01:03:02 2013] [ 3034]   102  3034     9443      340   5       0             0 ntpd
[So Jun  9 01:03:02 2013] [ 3150]  1000  3150     6037      245   2       0             0 screen
[So Jun  9 01:03:02 2013] [ 3151]  1000  3151     9528     1472   3       0             0 python
[So Jun  9 01:03:02 2013] [ 3199]  1000  3199     1100      132   4       0             0 sh
[So Jun  9 01:03:02 2013] [ 3201]  1000  3201  3929764   130552   1       0             0 java
[So Jun  9 01:03:02 2013] [ 3237]   114  3237     9224      218   5       0             0 gvfsd
[So Jun  9 01:03:02 2013] [ 3310]   114  3310    86914      300   5       0             0 at-spi-bus-laun
[So Jun  9 01:03:02 2013] [ 3314]   114  3314     5987      261   3       0             0 dbus-daemon
[So Jun  9 01:03:02 2013] [ 3317]   114  3317    31141      300   7       0             0 at-spi2-registr
[So Jun  9 01:03:02 2013] [ 3365]   114  3365   145223     1014   1       0             0 metacity
[So Jun  9 01:03:02 2013] [ 3367]   112  3367   125037      917   6       0             0 colord
[So Jun  9 01:03:02 2013] [ 3396]   114  3396    64350      468   2       0             0 pulseaudio
[So Jun  9 01:03:02 2013] [ 3398]   117  3398    42218      223   4       0             0 rtkit-daemon
[So Jun  9 01:03:02 2013] [ 3405]   114  3405    25558      326   2       0             0 gconf-helper
[So Jun  9 01:03:02 2013] [ 3465]   114  3465   105070     1420   1       0             0 gdm-simple-gree
[So Jun  9 01:03:02 2013] [ 3477]     0  3477    11407      287   1       0             0 gdm-session-wor
[So Jun  9 01:03:02 2013] [ 3492]     0  3492    30384      297   2       0             0 accounts-daemon
[So Jun  9 01:03:02 2013] [ 4538]  1004  4538   544013     3735   0       0             0 ts3server_linux
[So Jun  9 01:03:02 2013] [ 5201]     0  5201     7080      296   0       0             0 rpc.mountd
[So Jun  9 01:03:02 2013] [ 5252]   132  5252   149286     9240   5       0             0 ntop
[So Jun  9 01:03:02 2013] [ 5279]     0  5279    44338      932   3       0             0 php5-fpm
[So Jun  9 01:03:02 2013] [ 5280]    33  5280    44338      857   6       0             0 php5-fpm
[So Jun  9 01:03:02 2013] [ 5281]    33  5281    44338      858   4       0             0 php5-fpm
[So Jun  9 01:03:02 2013] [ 5282]    33  5282    44338      858   5       0             0 php5-fpm
[So Jun  9 01:03:02 2013] [ 5283]    33  5283    44338      858   6       0             0 php5-fpm
[So Jun  9 01:03:02 2013] [ 5392]     0  5392     6277      264   6       0             0 master
[So Jun  9 01:03:02 2013] [ 5397]   104  5397     6834      220   1       0             0 qmgr
[So Jun  9 01:03:02 2013] [ 5433]   133  5433     1077      124   3       0             0 uml_switch
[So Jun  9 01:03:02 2013] [ 5457]     0  5457     1852      151   0       0             0 vnstatd
[So Jun  9 01:03:02 2013] [ 5491]     0  5491     3340      148   0       0             0 mdadm
[So Jun  9 01:03:02 2013] [ 5541]     0  5541    58947     1821   4       0             0 apache2
[So Jun  9 01:03:02 2013] [ 5577]     0  5577   307170     1683   0       0             0 fail2ban-server
[So Jun  9 01:03:02 2013] [ 5580]     0  5580     5632      255   2       0             0 gam_server
[So Jun  9 01:03:02 2013] [ 5657]     0  5657     3935      207   2       0             0 getty
[So Jun  9 01:03:02 2013] [ 6545]     0  6545     6746      274   0       0             0 screen
[So Jun  9 01:03:02 2013] [ 6546]     0  6546  2210800   757026   5       0             0 qemu-system-x86
[So Jun  9 01:03:02 2013] [ 8740]  1000  8740     6816      315   0       0             0 screen
[So Jun  9 01:03:02 2013] [ 8741]  1000  8741    64243     1195   4       0             0 python
[So Jun  9 01:03:02 2013] [10678]  1000 10678     6746      278   1       0             0 screen
[So Jun  9 01:03:02 2013] [10679]  1000 10679    86971     2112   4       0             0 python
[So Jun  9 01:03:02 2013] [29607]    33 29607    58969     1630   7       0             0 apache2
[So Jun  9 01:03:02 2013] [29608]    33 29608    58969     1630   5       0             0 apache2
[So Jun  9 01:03:02 2013] [29609]    33 29609    58969     1630   7       0             0 apache2
[So Jun  9 01:03:02 2013] [29610]    33 29610    58969     1646   0       0             0 apache2
[So Jun  9 01:03:02 2013] [29611]    33 29611    58961     1649   2       0             0 apache2
[So Jun  9 01:03:02 2013] [ 5049]     0  5049    13037     2087   3       0             0 /usr/sbin/munin
[So Jun  9 01:03:02 2013] [16729]   130 16729  2203211   461488   3       0             0 kvm
[So Jun  9 01:03:02 2013] [  879]   101   879    62416      579   0       0             0 rsyslogd
[So Jun  9 01:03:02 2013] [21629]  1003 21629     6746      266   4       0             0 screen
[So Jun  9 01:03:02 2013] [21631]  1003 21631  2973114   204758   0       0             0 java
[So Jun  9 01:03:02 2013] [ 1494]     0  1494     5449      231   0     -17         -1000 udevd
[So Jun  9 01:03:02 2013] [22113]     0 22113     6037      265   3       0             0 screen
[So Jun  9 01:03:02 2013] [22114]     0 22114  2791480  1598471   3       0             0 qemu-system-x86
[So Jun  9 01:03:02 2013] [ 1208]     0  1208   150247      695   2       0             0 libvirtd
[So Jun  9 01:03:02 2013] [ 1284]   131  1284     6493      154   2       0             0 dnsmasq
[So Jun  9 01:03:02 2013] [ 1373]     0  1373     5449      254   4     -17         -1000 udevd
[So Jun  9 01:03:02 2013] [11084]  1000 11084     6037      206   6       0             0 screen
[So Jun  9 01:03:02 2013] [11085]  1000 11085     6037      216   2       0             0 screen
[So Jun  9 01:03:02 2013] [11092]  1000 11092     9528     1473   4       0             0 python
[So Jun  9 01:03:02 2013] [11093]  1000 11093     9528     1473   1       0             0 python
[So Jun  9 01:03:02 2013] [11103]  1000 11103     6037      267   1       0             0 screen
[So Jun  9 01:03:02 2013] [11105]  1000 11105     9528     1473   0       0             0 python
[So Jun  9 01:03:02 2013] [11117]  1000 11117     1100      133   4       0             0 sh
[So Jun  9 01:03:02 2013] [11122]  1000 11122     1100      132   4       0             0 sh
[So Jun  9 01:03:02 2013] [11134]  1000 11134     1100      133   0       0             0 sh
[So Jun  9 01:03:02 2013] [11152]  1000 11152  1740347   127439   4       0             0 java
[So Jun  9 01:03:02 2013] [11153]  1000 11153  1728464   243080   2       0             0 java
[So Jun  9 01:03:02 2013] [11154]  1000 11154  2178942   124074   0       0             0 java
[So Jun  9 01:03:02 2013] [11239]  1000 11239     6037      239   0       0             0 screen
[So Jun  9 01:03:02 2013] [11240]  1000 11240     9528     1472   1       0             0 python
[So Jun  9 01:03:02 2013] [11267]  1000 11267     1100      133   7       0             0 sh
[So Jun  9 01:03:02 2013] [11269]  1000 11269  4111079  1997249   5       0             0 java
[So Jun  9 01:03:02 2013] [28252]     0 28252    35314    31173   5       0             0 atop
[So Jun  9 01:03:02 2013] [22688]     0 22688    22045      446   2       0             0 sshd
[So Jun  9 01:03:02 2013] [22819]  1000 22819    22084      407   0       0             0 sshd
[So Jun  9 01:03:02 2013] [22820]  1000 22820     3266      266   3       0             0 sftp-server
[So Jun  9 01:03:02 2013] [16696]     0 16696    22045      447   0       0             0 sshd
[So Jun  9 01:03:02 2013] [16879]  1000 16879    22045      362   0       0             0 sshd
[So Jun  9 01:03:02 2013] [16880]  1000 16880     5275      380   2       0             0 bash
[So Jun  9 01:03:02 2013] [20215]     0 20215    22045      444   4       0             0 sshd
[So Jun  9 01:03:02 2013] [20397]  1000 20397    22045      273   1       0             0 sshd
[So Jun  9 01:03:02 2013] [20399]  1000 20399     4565      365   0       0             0 bash
[So Jun  9 01:03:02 2013] [20621]     0 20621    22542     1019   0       0             0 sshd
[So Jun  9 01:03:02 2013] [20625]  1000 20625     5799      507   0       0             0 htop
[So Jun  9 01:03:02 2013] [20808]     0 20808     5303      400   1       0             0 bash
[So Jun  9 01:03:02 2013] [22758]   104 22758     6793      232   4       0             0 pickup
[So Jun  9 01:03:02 2013] [24801]     0 24801    22045      446   0       0             0 sshd
[So Jun  9 01:03:02 2013] [24962]  1000 24962    22082      309   1       0             0 sshd
[So Jun  9 01:03:02 2013] [24963]  1000 24963     3226      200   2       0             0 sftp-server
[So Jun  9 01:03:02 2013] [25451]     0 25451    22045      445   0       0             0 sshd
[So Jun  9 01:03:02 2013] [25617]  1000 25617    22045      310   3       0             0 sshd
[So Jun  9 01:03:02 2013] [25630]  1000 25630     3194      171   2       0             0 sftp-server
[So Jun  9 01:03:02 2013] [ 9994]   104  9994     6852      254   2       0             0 cleanup
[So Jun  9 01:03:02 2013] [ 9996]   104  9996     6796      194   3       0             0 trivial-rewrite
[So Jun  9 01:03:02 2013] [ 9998]   104  9998     6792      225   2       0             0 error
[So Jun  9 01:03:02 2013] [ 9999]   104  9999     6801      198   3       0             0 bounce
[So Jun  9 01:03:02 2013] [17068]     0 17068    22045      388   1       0             0 sshd
[So Jun  9 01:03:02 2013] [17133]     0 17133       82        1   5       0             0 udev-acl.ck
[So Jun  9 01:03:02 2013] Out of memory: Kill process 11269 (java) score 243 or sacrifice child
[So Jun  9 01:03:02 2013] Killed process 11269 (java) total-vm:16444316kB, anon-rss:7988996kB, file-rss:0kB



```[COLOR=#000000][FONT=verdana]

[/FONT][/COLOR]i don't know why it happens because on the system were 10 GB of Ram free.
Has anyone i idea, how i can prevent the oom killer that it kill without real reason?

---

