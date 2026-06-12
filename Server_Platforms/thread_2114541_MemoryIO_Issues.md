---
title: "Memory/IO Issues"
date: 2013-02-10
forum: Server Platforms
---

### Post by ndstate on 2013-02-10
Hello,

Every few nights something is using up all of my server memory and I have some huge disk IO issues.  Would anyone be able to tell me how to beging figuring out what is causing the issues?

I have posted part of the syslog from about 20 minutes before to the out of memory issues around 0630. I am running Ubuntu 12.04.2 on a Linode 512


Thanks in advance!

```
Feb 10 06:10:17 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=96.3.106.43 DST=96.126.122.212 LEN=64 TOS=0x00 PREC=0x00 TTL=37 ID=26291 DF PROTO=TCP SPT=3335 DPT=135 WINDOW=53760 RES=0x00 SYN URGP=0 
Feb 10 06:10:20 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=96.3.106.43 DST=96.126.122.212 LEN=64 TOS=0x00 PREC=0x00 TTL=37 ID=27619 DF PROTO=TCP SPT=3335 DPT=135 WINDOW=53760 RES=0x00 SYN URGP=0 
Feb 10 06:11:04 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.188.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=21811 PROTO=UDP SPT=53 DPT=49929 LEN=52 
Feb 10 06:11:22 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.188.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=21812 PROTO=UDP SPT=53 DPT=52422 LEN=52 
Feb 10 06:13:11 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=96.3.106.43 DST=96.126.122.212 LEN=64 TOS=0x00 PREC=0x00 TTL=37 ID=37399 DF PROTO=TCP SPT=2932 DPT=135 WINDOW=53760 RES=0x00 SYN URGP=0 
Feb 10 06:13:13 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=96.3.106.43 DST=96.126.122.212 LEN=64 TOS=0x00 PREC=0x00 TTL=37 ID=38837 DF PROTO=TCP SPT=2932 DPT=135 WINDOW=53760 RES=0x00 SYN URGP=0 
Feb 10 06:13:32 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.179.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=6955 PROTO=UDP SPT=53 DPT=54885 LEN=52 
Feb 10 06:13:33 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.188.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=21813 PROTO=UDP SPT=53 DPT=52422 LEN=52 
Feb 10 06:13:44 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.179.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=6956 PROTO=UDP SPT=53 DPT=42390 LEN=52 
Feb 10 06:13:58 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.179.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=6973 PROTO=UDP SPT=53 DPT=47018 LEN=52 
Feb 10 06:14:06 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.179.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=7001 PROTO=UDP SPT=53 DPT=42390 LEN=52 
Feb 10 06:14:07 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.179.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=7002 PROTO=UDP SPT=53 DPT=47018 LEN=52 
Feb 10 06:15:01 bison CRON[10545]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Feb 10 06:15:29 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.179.5 DST=96.126.122.212 LEN=73 TOS=0x00 PREC=0x00 TTL=63 ID=7003 PROTO=UDP SPT=53 DPT=54228 LEN=53 
Feb 10 06:16:49 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.188.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=21814 PROTO=UDP SPT=53 DPT=45327 LEN=52 
Feb 10 06:17:01 bison CRON[10587]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 10 06:17:38 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.188.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=21815 PROTO=UDP SPT=53 DPT=45327 LEN=52 
Feb 10 06:17:49 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.179.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=7007 PROTO=UDP SPT=53 DPT=56378 LEN=52 
Feb 10 06:17:56 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.179.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=7008 PROTO=UDP SPT=53 DPT=56378 LEN=52 
Feb 10 06:18:25 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.188.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=21816 PROTO=UDP SPT=53 DPT=50327 LEN=52 
Feb 10 06:21:15 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.188.5 DST=96.126.122.212 LEN=73 TOS=0x00 PREC=0x00 TTL=63 ID=21817 PROTO=UDP SPT=53 DPT=60396 LEN=53 
Feb 10 06:22:07 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.179.5 DST=96.126.122.212 LEN=73 TOS=0x00 PREC=0x00 TTL=63 ID=7053 PROTO=UDP SPT=53 DPT=54228 LEN=53 
Feb 10 06:22:14 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.188.5 DST=96.126.122.212 LEN=73 TOS=0x00 PREC=0x00 TTL=63 ID=21818 PROTO=UDP SPT=53 DPT=60396 LEN=53 
Feb 10 06:25:01 bison CRON[10671]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Feb 10 06:25:01 bison CRON[10672]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Feb 10 06:25:42 bison drupal: http://www.campusdakota.com|1360499142|throttle|94.181.130.244|http://www.campusdakota.com/node/414|http://www.campusdakota.com/node/414#comment-1622+++++++++++++++++Result:+%E8%F1%EF%EE%EB%FC%E7%EE%E2%E0%ED+%ED%E8%EA%ED%E5%E9%EC+%22Oceadaydavy%22;+ReCaptcha+%E4%E5%F8%E8%F4%F0%EE%E2%E0%ED%E0;+%F3%F1%EF%E5%F5+%28%F1+%EF%E5%F0%E2%EE%E9+%F1%F2%F0%E0%ED%E8%F6%FB%29;|0||Throttle: 61 guests accessing site; throttle enabled.
Feb 10 06:26:33 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.179.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=7104 PROTO=UDP SPT=53 DPT=52601 LEN=52 
Feb 10 06:27:04 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=96.3.106.43 DST=96.126.122.212 LEN=64 TOS=0x00 PREC=0x00 TTL=37 ID=14328 DF PROTO=TCP SPT=4371 DPT=135 WINDOW=53760 RES=0x00 SYN URGP=0 
Feb 10 06:27:07 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=96.3.106.43 DST=96.126.122.212 LEN=64 TOS=0x00 PREC=0x00 TTL=37 ID=15669 DF PROTO=TCP SPT=4371 DPT=135 WINDOW=53760 RES=0x00 SYN URGP=0 
Feb 10 06:28:23 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.188.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=21819 PROTO=UDP SPT=53 DPT=49398 LEN=52 
Feb 10 06:28:23 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.188.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=21820 PROTO=UDP SPT=53 DPT=49398 LEN=52 
Feb 10 06:29:08 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.179.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=7148 PROTO=UDP SPT=53 DPT=49943 LEN=52 
Feb 10 06:29:13 bison kernel: apache2 invoked oom-killer: gfp_mask=0x200da, order=0, oom_adj=0, oom_score_adj=0
Feb 10 06:29:13 bison kernel: apache2 cpuset=/ mems_allowed=0
Feb 10 06:29:13 bison kernel: Pid: 10666, comm: apache2 Not tainted 3.5.2-linode45 #1
Feb 10 06:29:13 bison kernel: Call Trace:
Feb 10 06:29:13 bison kernel: [<c019c3ed>] ? T.681+0x7d/0x1b0
Feb 10 06:29:13 bison kernel: [<c072dd71>] ? _raw_spin_unlock_irqrestore+0x11/0x20
Feb 10 06:29:13 bison kernel: [<c04a6a77>] ? ___ratelimit+0x97/0x110
Feb 10 06:29:13 bison kernel: [<c018d644>] ? __delayacct_freepages_end+0x24/0x30
Feb 10 06:29:13 bison kernel: [<c019c778>] ? T.680+0x258/0x290
Feb 10 06:29:13 bison kernel: [<c0452d64>] ? security_capable_noaudit+0x14/0x20
Feb 10 06:29:13 bison kernel: [<c0138a4b>] ? has_ns_capability_noaudit+0xb/0x20
Feb 10 06:29:13 bison kernel: [<c019ca21>] ? out_of_memory+0x271/0x320
Feb 10 06:29:13 bison kernel: [<c01a0523>] ? __alloc_pages_nodemask+0x6b3/0x6d0
Feb 10 06:29:13 bison kernel: [<c01c1517>] ? read_swap_cache_async+0xb7/0xf0
Feb 10 06:29:13 bison kernel: [<c01c15b7>] ? swapin_readahead+0x67/0xa0
Feb 10 06:29:13 bison kernel: [<c01b459f>] ? do_swap_page+0x4af/0x610
Feb 10 06:29:13 bison kernel: [<c0106738>] ? xen_vcpuop_set_next_event+0x48/0x80
Feb 10 06:29:13 bison kernel: [<c010413f>] ? pte_mfn_to_pfn+0x8f/0xf0
Feb 10 06:29:13 bison kernel: [<c01b52dc>] ? handle_pte_fault+0x23c/0x2f0
Feb 10 06:29:13 bison kernel: [<c01b5485>] ? handle_mm_fault+0xf5/0x1b0
Feb 10 06:29:13 bison kernel: [<c0122821>] ? do_page_fault+0x101/0x3a0
Feb 10 06:29:13 bison kernel: [<c04c45a0>] ? evtchn_from_irq+0x10/0x40
Feb 10 06:29:13 bison kernel: [<c0189221>] ? handle_percpu_irq+0x31/0x50
Feb 10 06:29:13 bison kernel: [<c04c3d2e>] ? __xen_evtchn_do_upcall+0x1ce/0x210
Feb 10 06:29:13 bison kernel: [<c0103828>] ? xen_mc_flush+0x78/0x110
Feb 10 06:29:13 bison kernel: [<c0109e60>] ? math_state_restore+0xf0/0xf0
Feb 10 06:29:13 bison kernel: [<c0102eb4>] ? xen_clts+0x44/0x50
Feb 10 06:29:13 bison kernel: [<c0109d90>] ? math_state_restore+0x20/0xf0
Feb 10 06:29:13 bison kernel: [<c0122720>] ? mm_fault_error+0x160/0x160
Feb 10 06:29:13 bison kernel: [<c072e582>] ? error_code+0x5a/0x60
Feb 10 06:29:13 bison kernel: [<c0720000>] ? sctp_v6_get_saddr+0x40/0x40
Feb 10 06:29:13 bison kernel: [<c0122720>] ? mm_fault_error+0x160/0x160
Feb 10 06:29:13 bison kernel: Mem-Info:
Feb 10 06:29:13 bison kernel: DMA per-cpu:
Feb 10 06:29:13 bison kernel: CPU    0: hi:    0, btch:   1 usd:   0
Feb 10 06:29:14 bison kernel: CPU    1: hi:    0, btch:   1 usd:   0
Feb 10 06:29:14 bison kernel: CPU    2: hi:    0, btch:   1 usd:   0
Feb 10 06:29:14 bison kernel: CPU    3: hi:    0, btch:   1 usd:   0
Feb 10 06:29:14 bison kernel: Normal per-cpu:
Feb 10 06:29:14 bison kernel: CPU    0: hi:  186, btch:  31 usd:  18
Feb 10 06:29:14 bison kernel: CPU    1: hi:  186, btch:  31 usd:  48
Feb 10 06:29:14 bison kernel: CPU    2: hi:  186, btch:  31 usd:  48
Feb 10 06:29:14 bison kernel: CPU    3: hi:  186, btch:  31 usd:  33
Feb 10 06:29:14 bison kernel: active_anon:58545 inactive_anon:58760 isolated_anon:42
Feb 10 06:29:14 bison kernel: active_file:82 inactive_file:207 isolated_file:0
Feb 10 06:29:14 bison kernel: unevictable:0 dirty:0 writeback:120 unstable:0
Feb 10 06:29:14 bison kernel: free:1301 slab_reclaimable:1105 slab_unreclaimable:2613
Feb 10 06:29:14 bison kernel: mapped:82 shmem:141 pagetables:1166 bounce:0
Feb 10 06:29:14 bison kernel: DMA free:2080kB min:84kB low:104kB high:124kB active_anon:1892kB inactive_anon:2480kB active_file:4kB inactive_file:40kB unevictable:0kB isolated(anon):8kB isolated(file):0kB present:15808kB mlocked:0kB dirty:0kB writeback:12kB mapped:0kB shmem:456kB slab_reclaimable:28kB slab_unreclaimable:52kB kernel_stack:136kB pagetables:12kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:198 all_unreclaimable? yes
Feb 10 06:29:14 bison kernel: lowmem_reserve[]: 0 500 500 500
Feb 10 06:29:14 bison kernel: Normal free:3124kB min:2816kB low:3520kB high:4224kB active_anon:232288kB inactive_anon:232560kB active_file:324kB inactive_file:788kB unevictable:0kB isolated(anon):160kB isolated(file):0kB present:512064kB mlocked:0kB dirty:0kB writeback:468kB mapped:328kB shmem:108kB slab_reclaimable:4392kB slab_unreclaimable:10400kB kernel_stack:1488kB pagetables:4652kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:2961 all_unreclaimable? yes
Feb 10 06:29:14 bison kernel: lowmem_reserve[]: 0 0 0 0
Feb 10 06:29:14 bison kernel: DMA: 3*4kB 10*8kB 67*16kB 29*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 2092kB
Feb 10 06:29:14 bison kernel: Normal: 573*4kB 94*8kB 5*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 3124kB
Feb 10 06:29:14 bison kernel: 3926 total pagecache pages
Feb 10 06:29:14 bison kernel: 3461 pages in swap cache
Feb 10 06:29:14 bison kernel: Swap cache stats: add 28450693, delete 28447232, find 488109270/490658208
Feb 10 06:29:14 bison kernel: Free swap  = 0kB
Feb 10 06:29:14 bison kernel: Total swap = 262140kB
Feb 10 06:29:14 bison kernel: 133104 pages RAM
Feb 10 06:29:14 bison kernel: 0 pages HighMem
Feb 10 06:29:14 bison kernel: 5960 pages reserved
Feb 10 06:29:14 bison kernel: 4546 pages shared
Feb 10 06:29:14 bison kernel: 124681 pages non-shared
Feb 10 06:29:14 bison kernel: [ pid ]   uid  tgid total_vm      rss cpu oom_adj oom_score_adj name
Feb 10 06:29:14 bison kernel: [ 1975]     0  1975      712        0   0       0             0 upstart-socket-
Feb 10 06:29:14 bison kernel: [ 2088]     0  2088      733        0   0       0             0 dhclient3
Feb 10 06:29:14 bison kernel: [ 2098]     0  2098     1672        0   3     -17         -1000 sshd
Feb 10 06:29:14 bison kernel: [ 2147]   101  2147     8071       10   0       0             0 rsyslogd
Feb 10 06:29:14 bison kernel: [ 2162]   102  2162      816        0   2       0             0 dbus-daemon
Feb 10 06:29:14 bison kernel: [ 2199]     0  2199      619        0   0       0             0 atd
Feb 10 06:29:14 bison kernel: [ 2205]     0  2205      656       13   0       0             0 cron
Feb 10 06:29:14 bison kernel: [ 2351]   103  2351     6110        0   0       0             0 whoopsie
Feb 10 06:29:14 bison kernel: [ 3446]   106  3446     1434       12   0       0             0 ntpd
Feb 10 06:29:14 bison kernel: [ 4003]     0  4003     7349      168   0       0             0 fail2ban-server
Feb 10 06:29:14 bison kernel: [ 4005]     0  4005     1001       42   2       0             0 gam_server
Feb 10 06:29:14 bison kernel: [ 4264]     0  4264      602        0   2       0             0 getty
Feb 10 06:29:14 bison kernel: [21506]     0 21506      710        0   2       0             0 upstart-udev-br
Feb 10 06:29:14 bison kernel: [21508]     0 21508      738        0   1     -17         -1000 udevd
Feb 10 06:29:14 bison kernel: [21743]     0 21743     1146        9   1       0             0 master
Feb 10 06:29:14 bison kernel: [ 9715]     0  9715      646        0   0       0             0 jsvc
Feb 10 06:29:14 bison kernel: [23232]   108 23232    12555       26   2     -13          -900 postgres
Feb 10 06:29:14 bison kernel: [23234]   108 23234    12555       13   1       0             0 postgres
Feb 10 06:29:14 bison kernel: [23235]   108 23235    12555        7   0       0             0 postgres
Feb 10 06:29:14 bison kernel: [23236]   108 23236    12719      100   1       0             0 postgres
Feb 10 06:29:14 bison kernel: [23237]   108 23237     5180       61   0       0             0 postgres
Feb 10 06:29:14 bison kernel: [12598]   109 12598   108047      214   0       0             0 jsvc
Feb 10 06:29:14 bison kernel: [26544]     0 26544     4809      160   1       0             0 miniserv.pl
Feb 10 06:29:14 bison kernel: [14506]     0 14506    10419       21   1       0             0 apache2
Feb 10 06:29:14 bison kernel: [32716]   110 32716     1187       13   0       0             0 qmgr
Feb 10 06:29:14 bison kernel: [31733]    33 31733    67067       79   0       0             0 apache2
Feb 10 06:29:14 bison kernel: [ 6447]    33  6447    65247       18   0       0             0 apache2
Feb 10 06:29:14 bison kernel: [ 6536]   107  6536    78962     2566   0       0             0 mysqld
Feb 10 06:29:14 bison kernel: [10666]    33 10666    21571     9423   0       0             0 apache2
Feb 10 06:29:14 bison kernel: [10667]   110 10667     1151        0   0       0             0 pickup
Feb 10 06:29:14 bison kernel: [10669]     0 10669      753        0   1       0             0 cron
Feb 10 06:29:14 bison kernel: [10671]     0 10671      560        0   1       0             0 sh
Feb 10 06:29:14 bison kernel: [10673]     0 10673      537        0   2       0             0 run-parts
Feb 10 06:29:14 bison kernel: [10678]     0 10678      560        0   1       0             0 apt
Feb 10 06:29:14 bison kernel: [10712]     0 10712     1051        0   0       0             0 sleep
Feb 10 06:29:14 bison kernel: [10730]    33 10730    21599    10733   2       0             0 apache2
Feb 10 06:29:14 bison kernel: [10757]    33 10757    20228     9476   1       0             0 apache2
Feb 10 06:29:14 bison kernel: [10760]    33 10760    19692     9438   3       0             0 apache2
Feb 10 06:29:14 bison kernel: [10767]    33 10767    19629     9407   2       0             0 apache2
Feb 10 06:29:14 bison kernel: [10770]    33 10770    19698     9348   3       0             0 apache2
Feb 10 06:29:14 bison kernel: [10771]    33 10771    19690     9295   1       0             0 apache2
Feb 10 06:29:14 bison kernel: [10773]    33 10773    21034     8960   0       0             0 apache2
Feb 10 06:29:14 bison kernel: [10774]    33 10774    21034     9142   2       0             0 apache2
Feb 10 06:29:14 bison kernel: [10775]    33 10775    21034     9563   1       0             0 apache2
Feb 10 06:29:14 bison kernel: [10777]    33 10777    13390     3311   3       0             0 apache2
Feb 10 06:29:14 bison kernel: [10778]    33 10778    13390     3274   0       0             0 apache2
Feb 10 06:29:14 bison kernel: [10779]    33 10779    12225     1872   2       0             0 apache2
Feb 10 06:29:14 bison kernel: [10784]    33 10784    13390     3215   2       0             0 apache2
Feb 10 06:29:14 bison kernel: [10785]    33 10785    13390     3376   2       0             0 apache2
Feb 10 06:29:14 bison kernel: [10787]    33 10787    13390     3381   2       0             0 apache2
Feb 10 06:29:14 bison kernel: [10789]    33 10789    10723      407   3       0             0 apache2
Feb 10 06:29:14 bison kernel: [10790]    33 10790    10495       82   2       0             0 apache2
Feb 10 06:29:14 bison kernel: [10791]   108 10791    12555       43   2       0             0 postgres
Feb 10 06:29:14 bison kernel: [10792]    33 10792    10495       82   3       0             0 apache2
Feb 10 06:29:14 bison kernel: [10793]    33 10793    10496       80   0       0             0 apache2
Feb 10 06:29:14 bison kernel: Out of memory: Kill process 6536 (mysqld) score 88 or sacrifice child
Feb 10 06:29:14 bison kernel: Killed process 6536 (mysqld) total-vm:315848kB, anon-rss:10264kB, file-rss:0kB
Feb 10 06:29:14 bison kernel: apache2 invoked oom-killer: gfp_mask=0x200da, order=0, oom_adj=0, oom_score_adj=0
Feb 10 06:29:14 bison kernel: apache2 cpuset=/ mems_allowed=0
Feb 10 06:29:14 bison kernel: Pid: 10774, comm: apache2 Not tainted 3.5.2-linode45 #1
Feb 10 06:29:14 bison kernel: Call Trace:
Feb 10 06:29:14 bison kernel: [<c019c3ed>] ? T.681+0x7d/0x1b0
Feb 10 06:29:14 bison kernel: [<c072dd71>] ? _raw_spin_unlock_irqrestore+0x11/0x20
Feb 10 06:29:14 bison kernel: [<c04a6a77>] ? ___ratelimit+0x97/0x110
Feb 10 06:29:14 bison kernel: [<c018d644>] ? __delayacct_freepages_end+0x24/0x30
Feb 10 06:29:14 bison kernel: [<c019c778>] ? T.680+0x258/0x290
Feb 10 06:29:14 bison kernel: [<c0452d64>] ? security_capable_noaudit+0x14/0x20
Feb 10 06:29:14 bison kernel: [<c0138a4b>] ? has_ns_capability_noaudit+0xb/0x20
Feb 10 06:29:14 bison kernel: [<c019ca21>] ? out_of_memory+0x271/0x320
Feb 10 06:29:14 bison kernel: [<c01a0523>] ? __alloc_pages_nodemask+0x6b3/0x6d0
Feb 10 06:29:14 bison kernel: [<c01c1517>] ? read_swap_cache_async+0xb7/0xf0
Feb 10 06:29:14 bison kernel: [<c01c15b7>] ? swapin_readahead+0x67/0xa0
Feb 10 06:29:14 bison kernel: [<c01b459f>] ? do_swap_page+0x4af/0x610
Feb 10 06:29:14 bison kernel: [<c01b52dc>] ? handle_pte_fault+0x23c/0x2f0
Feb 10 06:29:14 bison kernel: [<c01b5485>] ? handle_mm_fault+0xf5/0x1b0
Feb 10 06:29:14 bison kernel: [<c0122821>] ? do_page_fault+0x101/0x3a0
Feb 10 06:29:14 bison kernel: [<c04c45a0>] ? evtchn_from_irq+0x10/0x40
Feb 10 06:29:14 bison kernel: [<c0189221>] ? handle_percpu_irq+0x31/0x50
Feb 10 06:29:14 bison kernel: [<c04c3d2e>] ? __xen_evtchn_do_upcall+0x1ce/0x210
Feb 10 06:29:14 bison kernel: [<c010aea2>] ? do_softirq+0x42/0xb0
Feb 10 06:29:14 bison kernel: [<c018d2f2>] ? rcu_irq_exit+0x52/0xa0
Feb 10 06:29:14 bison kernel: [<c0122720>] ? mm_fault_error+0x160/0x160
Feb 10 06:29:14 bison kernel: [<c072e582>] ? error_code+0x5a/0x60
Feb 10 06:29:14 bison kernel: [<c0720000>] ? sctp_v6_get_saddr+0x40/0x40
Feb 10 06:29:14 bison kernel: [<c0122720>] ? mm_fault_error+0x160/0x160
Feb 10 06:29:14 bison kernel: Mem-Info:
Feb 10 06:29:14 bison kernel: DMA per-cpu:
Feb 10 06:29:14 bison kernel: CPU    0: hi:    0, btch:   1 usd:   0
Feb 10 06:29:14 bison kernel: CPU    1: hi:    0, btch:   1 usd:   0
Feb 10 06:29:14 bison kernel: CPU    2: hi:    0, btch:   1 usd:   0
Feb 10 06:29:14 bison kernel: CPU    3: hi:    0, btch:   1 usd:   0
Feb 10 06:29:14 bison kernel: Normal per-cpu:
Feb 10 06:29:14 bison kernel: CPU    0: hi:  186, btch:  31 usd:   0
Feb 10 06:29:14 bison kernel: CPU    1: hi:  186, btch:  31 usd:   0
Feb 10 06:29:14 bison kernel: CPU    2: hi:  186, btch:  31 usd:   0
Feb 10 06:29:14 bison kernel: CPU    3: hi:  186, btch:  31 usd:   0
Feb 10 06:29:14 bison kernel: active_anon:58645 inactive_anon:58808 isolated_anon:66
Feb 10 06:29:14 bison kernel: active_file:158 inactive_file:314 isolated_file:0
Feb 10 06:29:14 bison kernel: unevictable:0 dirty:0 writeback:148 unstable:0
Feb 10 06:29:14 bison kernel: free:1224 slab_reclaimable:1105 slab_unreclaimable:2613
Feb 10 06:29:14 bison kernel: mapped:194 shmem:141 pagetables:1166 bounce:0
Feb 10 06:29:14 bison kernel: DMA free:2080kB min:84kB low:104kB high:124kB active_anon:1892kB inactive_anon:2480kB active_file:4kB inactive_file:40kB unevictable:0kB isolated(anon):8kB isolated(file):0kB present:15808kB mlocked:0kB dirty:0kB writeback:12kB mapped:0kB shmem:456kB slab_reclaimable:28kB slab_unreclaimable:52kB kernel_stack:136kB pagetables:12kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:276 all_unreclaimable? yes
Feb 10 06:29:14 bison kernel: lowmem_reserve[]: 0 500 500 500
Feb 10 06:29:14 bison kernel: Normal free:2816kB min:2816kB low:3520kB high:4224kB active_anon:232688kB inactive_anon:232752kB active_file:628kB inactive_file:1216kB unevictable:0kB isolated(anon):256kB isolated(file):0kB present:512064kB mlocked:0kB dirty:0kB writeback:580kB mapped:776kB shmem:108kB slab_reclaimable:4392kB slab_unreclaimable:10400kB kernel_stack:1488kB pagetables:4652kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:10005 all_unreclaimable? yes
Feb 10 06:29:14 bison kernel: lowmem_reserve[]: 0 0 0 0
Feb 10 06:29:14 bison kernel: DMA: 3*4kB 10*8kB 67*16kB 29*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 2092kB
Feb 10 06:29:14 bison kernel: Normal: 544*4kB 77*8kB 3*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 2840kB
Feb 10 06:29:14 bison kernel: 4290 total pagecache pages
Feb 10 06:29:14 bison kernel: 3607 pages in swap cache
Feb 10 06:29:14 bison kernel: Swap cache stats: add 28450895, delete 28447288, find 488109298/490658257
Feb 10 06:29:14 bison kernel: Free swap  = 0kB
Feb 10 06:29:14 bison kernel: Total swap = 262140kB
Feb 10 06:29:14 bison kernel: 133104 pages RAM
Feb 10 06:29:14 bison kernel: 0 pages HighMem
Feb 10 06:29:15 bison kernel: 5960 pages reserved
Feb 10 06:29:15 bison kernel: 4929 pages shared
Feb 10 06:29:15 bison kernel: 124761 pages non-shared
Feb 10 06:29:15 bison kernel: [ pid ]   uid  tgid total_vm      rss cpu oom_adj oom_score_adj name
Feb 10 06:29:15 bison kernel: [ 1975]     0  1975      712        0   0       0             0 upstart-socket-
Feb 10 06:29:15 bison kernel: [ 2088]     0  2088      733        0   0       0             0 dhclient3
Feb 10 06:29:15 bison kernel: [ 2098]     0  2098     1672        0   3     -17         -1000 sshd
Feb 10 06:29:15 bison kernel: [ 2147]   101  2147     8071       21   0       0             0 rsyslogd
Feb 10 06:29:15 bison kernel: [ 2162]   102  2162      816        0   2       0             0 dbus-daemon
Feb 10 06:29:15 bison kernel: [ 2199]     0  2199      619        0   0       0             0 atd
Feb 10 06:29:15 bison kernel: [ 2205]     0  2205      656       13   0       0             0 cron
Feb 10 06:29:15 bison kernel: [ 2351]   103  2351     6110        0   0       0             0 whoopsie
Feb 10 06:29:15 bison kernel: [ 3446]   106  3446     1434       12   1       0             0 ntpd
Feb 10 06:29:15 bison kernel: [ 4003]     0  4003     7349      168   0       0             0 fail2ban-server
Feb 10 06:29:15 bison kernel: [ 4005]     0  4005     1001       42   2       0             0 gam_server
Feb 10 06:29:15 bison kernel: [ 4264]     0  4264      602        0   2       0             0 getty
Feb 10 06:29:15 bison kernel: [21506]     0 21506      710        0   2       0             0 upstart-udev-br
Feb 10 06:29:15 bison kernel: [21508]     0 21508      738        0   1     -17         -1000 udevd
Feb 10 06:29:15 bison kernel: [21743]     0 21743     1146        9   1       0             0 master
Feb 10 06:29:15 bison kernel: [ 9715]     0  9715      646        0   0       0             0 jsvc
Feb 10 06:29:15 bison kernel: [23232]   108 23232    12555       26   2     -13          -900 postgres
Feb 10 06:29:15 bison kernel: [23234]   108 23234    12555       13   0       0             0 postgres
Feb 10 06:29:15 bison kernel: [23235]   108 23235    12555        7   0       0             0 postgres
Feb 10 06:29:15 bison kernel: [23236]   108 23236    12719      100   0       0             0 postgres
Feb 10 06:29:15 bison kernel: [23237]   108 23237     5180       61   0       0             0 postgres
Feb 10 06:29:15 bison kernel: [12598]   109 12598   108047      214   0       0             0 jsvc
Feb 10 06:29:15 bison kernel: [26544]     0 26544     4809      160   1       0             0 miniserv.pl
Feb 10 06:29:15 bison kernel: [14506]     0 14506    10419       21   1       0             0 apache2
Feb 10 06:29:15 bison kernel: [32716]   110 32716     1187       13   2       0             0 qmgr
Feb 10 06:29:15 bison kernel: [31733]    33 31733    67067       79   0       0             0 apache2
Feb 10 06:29:15 bison kernel: [ 6447]    33  6447    65247       18   0       0             0 apache2
Feb 10 06:29:15 bison kernel: [10783]   107  6536    78962     2692   3       0             0 mysqld
Feb 10 06:29:15 bison kernel: [10666]    33 10666    21571     9423   0       0             0 apache2
Feb 10 06:29:15 bison kernel: [10667]   110 10667     1151        0   0       0             0 pickup
Feb 10 06:29:15 bison kernel: [10669]     0 10669      753        0   1       0             0 cron
Feb 10 06:29:15 bison kernel: [10671]     0 10671      560        0   1       0             0 sh
Feb 10 06:29:15 bison kernel: [10673]     0 10673      537        0   2       0             0 run-parts
Feb 10 06:29:15 bison kernel: [10678]     0 10678      560        0   1       0             0 apt
Feb 10 06:29:15 bison kernel: [10712]     0 10712     1051        0   0       0             0 sleep
Feb 10 06:29:15 bison kernel: [10730]    33 10730    21599    10733   0       0             0 apache2
Feb 10 06:29:15 bison kernel: [10757]    33 10757    20228     9529   1       0             0 apache2
Feb 10 06:29:15 bison kernel: [10760]    33 10760    19692     9438   1       0             0 apache2
Feb 10 06:29:15 bison kernel: [10767]    33 10767    19629     9407   0       0             0 apache2
Feb 10 06:29:15 bison kernel: [10770]    33 10770    19698     9395   0       0             0 apache2
Feb 10 06:29:15 bison kernel: [10771]    33 10771    19690     9310   0       0             0 apache2
Feb 10 06:29:15 bison kernel: [10773]    33 10773    21034     8957   2       0             0 apache2
Feb 10 06:29:15 bison kernel: [10774]    33 10774    21034     9119   1       0             0 apache2
Feb 10 06:29:15 bison kernel: [10775]    33 10775    21034     9588   2       0             0 apache2
Feb 10 06:29:15 bison kernel: [10777]    33 10777    13390     3311   0       0             0 apache2
Feb 10 06:29:15 bison kernel: [10778]    33 10778    13390     3322   1       0             0 apache2
Feb 10 06:29:15 bison kernel: [10779]    33 10779    12225     1872   2       0             0 apache2
Feb 10 06:29:15 bison kernel: [10784]    33 10784    13390     3215   0       0             0 apache2
Feb 10 06:29:15 bison kernel: [10785]    33 10785    13390     3376   0       0             0 apache2
Feb 10 06:29:15 bison kernel: [10787]    33 10787    13390     3381   1       0             0 apache2
Feb 10 06:29:15 bison kernel: [10789]    33 10789    10723      407   0       0             0 apache2
Feb 10 06:29:15 bison kernel: [10790]    33 10790    10495       82   2       0             0 apache2
Feb 10 06:29:15 bison kernel: [10791]   108 10791    12555       43   2       0             0 postgres
Feb 10 06:29:15 bison kernel: [10792]    33 10792    10495       82   1       0             0 apache2
Feb 10 06:29:15 bison kernel: [10793]    33 10793    10495      109   0       0             0 apache2
Feb 10 06:29:15 bison kernel: Out of memory: Kill process 10783 (mysqld) score 88 or sacrifice child
Feb 10 06:29:15 bison kernel: Killed process 10783 (mysqld) total-vm:315848kB, anon-rss:10768kB, file-rss:0kB
Feb 10 06:29:29 bison kernel: which invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0, oom_score_adj=0
Feb 10 06:29:29 bison kernel: which cpuset=/ mems_allowed=0
Feb 10 06:29:29 bison kernel: Pid: 10798, comm: which Not tainted 3.5.2-linode45 #1
Feb 10 06:29:29 bison kernel: Call Trace:
Feb 10 06:29:29 bison kernel: [<c019c3ed>] ? T.681+0x7d/0x1b0
Feb 10 06:29:29 bison kernel: [<c072dd71>] ? _raw_spin_unlock_irqrestore+0x11/0x20
Feb 10 06:29:29 bison kernel: [<c04a6a77>] ? ___ratelimit+0x97/0x110
Feb 10 06:29:29 bison kernel: [<c018d644>] ? __delayacct_freepages_end+0x24/0x30
Feb 10 06:29:29 bison kernel: [<c019c778>] ? T.680+0x258/0x290
Feb 10 06:29:29 bison kernel: [<c0452d64>] ? security_capable_noaudit+0x14/0x20
Feb 10 06:29:29 bison kernel: [<c0138a4b>] ? has_ns_capability_noaudit+0xb/0x20
Feb 10 06:29:29 bison kernel: [<c019ca21>] ? out_of_memory+0x271/0x320
Feb 10 06:29:29 bison kernel: [<c01a0523>] ? __alloc_pages_nodemask+0x6b3/0x6d0
Feb 10 06:29:29 bison kernel: [<c019b232>] ? filemap_fault+0x1f2/0x3c0
Feb 10 06:29:29 bison kernel: [<c01b1b55>] ? __do_fault+0x75/0x550
Feb 10 06:29:29 bison kernel: [<c01b5140>] ? handle_pte_fault+0xa0/0x2f0
Feb 10 06:29:29 bison kernel: [<c0103106>] ? load_TLS_descriptor+0x36/0x70
Feb 10 06:29:29 bison kernel: [<c01b5485>] ? handle_mm_fault+0xf5/0x1b0
Feb 10 06:29:29 bison kernel: [<c0122821>] ? do_page_fault+0x101/0x3a0
Feb 10 06:29:29 bison kernel: [<c0112ea3>] ? do_set_thread_area+0xd3/0xe0
Feb 10 06:29:29 bison kernel: [<c0122720>] ? mm_fault_error+0x160/0x160
Feb 10 06:29:29 bison kernel: [<c072e582>] ? error_code+0x5a/0x60
Feb 10 06:29:29 bison kernel: [<c0122720>] ? mm_fault_error+0x160/0x160
Feb 10 06:29:29 bison kernel: Mem-Info:
Feb 10 06:29:29 bison kernel: DMA per-cpu:
Feb 10 06:29:29 bison kernel: CPU    0: hi:    0, btch:   1 usd:   0
Feb 10 06:29:29 bison kernel: CPU    1: hi:    0, btch:   1 usd:   0
Feb 10 06:29:29 bison kernel: CPU    2: hi:    0, btch:   1 usd:   0
Feb 10 06:29:29 bison kernel: CPU    3: hi:    0, btch:   1 usd:   0
Feb 10 06:29:29 bison kernel: Normal per-cpu:
Feb 10 06:29:29 bison kernel: CPU    0: hi:  186, btch:  31 usd:  55
Feb 10 06:29:29 bison kernel: CPU    1: hi:  186, btch:  31 usd:  22
Feb 10 06:29:29 bison kernel: CPU    2: hi:  186, btch:  31 usd:  38
Feb 10 06:29:29 bison kernel: CPU    3: hi:  186, btch:  31 usd:   3
Feb 10 06:29:29 bison kernel: active_anon:58627 inactive_anon:58677 isolated_anon:32
Feb 10 06:29:29 bison kernel: active_file:251 inactive_file:401 isolated_file:0
Feb 10 06:29:29 bison kernel: unevictable:0 dirty:3 writeback:118 unstable:0
Feb 10 06:29:29 bison kernel: free:1215 slab_reclaimable:1098 slab_unreclaimable:2506
Feb 10 06:29:29 bison kernel: mapped:298 shmem:213 pagetables:1156 bounce:0
Feb 10 06:29:29 bison kernel: DMA free:2080kB min:84kB low:104kB high:124kB active_anon:2180kB inactive_anon:2304kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15808kB mlocked:0kB dirty:0kB writeback:0kB mapped:24kB shmem:448kB slab_reclaimable:28kB slab_unreclaimable:20kB kernel_stack:136kB pagetables:12kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Feb 10 06:29:29 bison kernel: lowmem_reserve[]: 0 500 500 500
Feb 10 06:29:29 bison kernel: Normal free:2780kB min:2816kB low:3520kB high:4224kB active_anon:232328kB inactive_anon:232404kB active_file:1004kB inactive_file:1608kB unevictable:0kB isolated(anon):128kB isolated(file):0kB present:512064kB mlocked:0kB dirty:12kB writeback:472kB mapped:1168kB shmem:404kB slab_reclaimable:4364kB slab_unreclaimable:10004kB kernel_stack:1280kB pagetables:4612kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:4195 all_unreclaimable? yes
Feb 10 06:29:29 bison kernel: lowmem_reserve[]: 0 0 0 0
Feb 10 06:29:29 bison kernel: DMA: 0*4kB 5*8kB 68*16kB 30*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 2088kB
Feb 10 06:29:29 bison kernel: Normal: 671*4kB 13*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 2788kB
Feb 10 06:29:29 bison kernel: 9737 total pagecache pages
Feb 10 06:29:29 bison kernel: 8742 pages in swap cache
Feb 10 06:29:29 bison kernel: Swap cache stats: add 28475081, delete 28466339, find 488113770/490663845
Feb 10 06:29:29 bison kernel: Free swap  = 0kB
Feb 10 06:29:29 bison kernel: Total swap = 262140kB
Feb 10 06:29:29 bison kernel: 133104 pages RAM
Feb 10 06:29:29 bison kernel: 0 pages HighMem
Feb 10 06:29:29 bison kernel: 5960 pages reserved
Feb 10 06:29:29 bison kernel: 6381 pages shared
Feb 10 06:29:29 bison kernel: 124616 pages non-shared
Feb 10 06:29:29 bison kernel: [ pid ]   uid  tgid total_vm      rss cpu oom_adj oom_score_adj name
Feb 10 06:29:29 bison kernel: [ 1975]     0  1975      712       12   0       0             0 upstart-socket-
Feb 10 06:29:29 bison kernel: [ 2088]     0  2088      733        0   0       0             0 dhclient3
Feb 10 06:29:29 bison kernel: [ 2098]     0  2098     1672        0   3     -17         -1000 sshd
Feb 10 06:29:29 bison kernel: [ 2147]   101  2147     8071       26   0       0             0 rsyslogd
Feb 10 06:29:29 bison kernel: [ 2162]   102  2162      816       23   0       0             0 dbus-daemon
Feb 10 06:29:29 bison kernel: [ 2199]     0  2199      619        0   0       0             0 atd
Feb 10 06:29:29 bison kernel: [ 2205]     0  2205      656        8   0       0             0 cron
Feb 10 06:29:29 bison kernel: [ 2351]   103  2351     6110       28   1       0             0 whoopsie
Feb 10 06:29:29 bison kernel: [ 3446]   106  3446     1434       53   0       0             0 ntpd
Feb 10 06:29:29 bison kernel: [ 4003]     0  4003     7349      166   0       0             0 fail2ban-server
Feb 10 06:29:29 bison kernel: [ 4005]     0  4005     1001       53   3       0             0 gam_server
Feb 10 06:29:29 bison kernel: [ 4264]     0  4264      602        0   2       0             0 getty
Feb 10 06:29:29 bison kernel: [21506]     0 21506      710       11   0       0             0 upstart-udev-br
Feb 10 06:29:29 bison kernel: [21508]     0 21508      738        0   1     -17         -1000 udevd
Feb 10 06:29:29 bison kernel: [21743]     0 21743     1146       24   1       0             0 master
Feb 10 06:29:29 bison kernel: [ 9715]     0  9715      646        0   0       0             0 jsvc
Feb 10 06:29:29 bison kernel: [23232]   108 23232    12555       25   0     -13          -900 postgres
Feb 10 06:29:29 bison kernel: [23234]   108 23234    12555       13   0       0             0 postgres
Feb 10 06:29:29 bison kernel: [23235]   108 23235    12555        7   0       0             0 postgres
Feb 10 06:29:29 bison kernel: [23236]   108 23236    12719      125   0       0             0 postgres
Feb 10 06:29:29 bison kernel: [23237]   108 23237     5180       68   0       0             0 postgres
Feb 10 06:29:29 bison kernel: [12598]   109 12598   108047      210   0       0             0 jsvc
Feb 10 06:29:29 bison kernel: [26544]     0 26544     4809      148   0       0             0 miniserv.pl
Feb 10 06:29:29 bison kernel: [14506]     0 14506    10419       21   0       0             0 apache2
Feb 10 06:29:29 bison kernel: [32716]   110 32716     1187       20   0       0             0 qmgr
Feb 10 06:29:29 bison kernel: [31733]    33 31733    67067       73   0       0             0 apache2
Feb 10 06:29:29 bison kernel: [ 6447]    33  6447    65247       12   0       0             0 apache2
Feb 10 06:29:29 bison kernel: [10666]    33 10666    21571     7927   0       0             0 apache2
Feb 10 06:29:29 bison kernel: [10667]   110 10667     1151        0   0       0             0 pickup
Feb 10 06:29:29 bison kernel: [10669]     0 10669      753        0   1       0             0 cron
Feb 10 06:29:29 bison kernel: [10671]     0 10671      560        0   1       0             0 sh
Feb 10 06:29:29 bison kernel: [10673]     0 10673      537        0   2       0             0 run-parts
Feb 10 06:29:29 bison kernel: [10678]     0 10678      560        3   0       0             0 apt
Feb 10 06:29:29 bison kernel: [10730]    33 10730    20211     7622   2       0             0 apache2
Feb 10 06:29:29 bison kernel: [10757]    33 10757    20223     9443   2       0             0 apache2
Feb 10 06:29:29 bison kernel: [10760]    33 10760    19692     9531   3       0             0 apache2
Feb 10 06:29:29 bison kernel: [10767]    33 10767    19629     9486   2       0             0 apache2
Feb 10 06:29:29 bison kernel: [10770]    33 10770    19708     9449   2       0             0 apache2
Feb 10 06:29:29 bison kernel: [10771]    33 10771    19690     9331   0       0             0 apache2
Feb 10 06:29:29 bison kernel: [10773]    33 10773    21034     8655   3       0             0 apache2
Feb 10 06:29:29 bison kernel: [10774]    33 10774    21034     9005   0       0             0 apache2
Feb 10 06:29:29 bison kernel: [10775]    33 10775    21034     5733   2       0             0 apache2
Feb 10 06:29:29 bison kernel: [10777]    33 10777    15043     3674   0       0             0 apache2
Feb 10 06:29:29 bison kernel: [10778]    33 10778    15385     4099   3       0             0 apache2
Feb 10 06:29:29 bison kernel: [10779]    33 10779    12162     1827   0       0             0 apache2
Feb 10 06:29:29 bison kernel: [10784]    33 10784    14122     2678   0       0             0 apache2
Feb 10 06:29:29 bison kernel: [10785]    33 10785    15383     3734   1       0             0 apache2
Feb 10 06:29:29 bison kernel: [10787]    33 10787    15385     3781   0       0             0 apache2
Feb 10 06:29:29 bison kernel: [10789]    33 10789    11548     1501   3       0             0 apache2
Feb 10 06:29:29 bison kernel: [10790]    33 10790    11548     1566   3       0             0 apache2
Feb 10 06:29:29 bison kernel: [10792]    33 10792    11548     1572   2       0             0 apache2
Feb 10 06:29:29 bison kernel: [10793]    33 10793    11548     1568   1       0             0 apache2
Feb 10 06:29:29 bison kernel: [10794]   108 10794    12555       38   2       0             0 postgres
Feb 10 06:29:29 bison kernel: [10795]     0 10795      535       38   0       0             0 sh
Feb 10 06:29:29 bison kernel: [10796]    33 10796      535       38   1       0             0 sh
Feb 10 06:29:29 bison kernel: [10797]     0 10797    10423       63   0       0             0 apache2
Feb 10 06:29:29 bison kernel: [10798]     0 10798      535       14   3       0             0 which
Feb 10 06:29:29 bison kernel: Out of memory: Kill process 10666 (apache2) score 61 or sacrifice child
Feb 10 06:29:29 bison kernel: Killed process 10666 (apache2) total-vm:86284kB, anon-rss:31600kB, file-rss:108kB
Feb 10 06:30:14 bison postfix/pickup[10667]: 6FCC210388: uid=33 from=<www-data>
Feb 10 06:30:25 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.179.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=7149 PROTO=UDP SPT=53 DPT=52601 LEN=52 
Feb 10 06:30:25 bison kernel: whoopsie invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0, oom_score_adj=0
Feb 10 06:30:25 bison kernel: whoopsie cpuset=/ mems_allowed=0
Feb 10 06:30:25 bison kernel: Pid: 2351, comm: whoopsie Not tainted 3.5.2-linode45 #1
Feb 10 06:30:25 bison kernel: Call Trace:
Feb 10 06:30:25 bison kernel: [<c019c3ed>] ? T.681+0x7d/0x1b0
Feb 10 06:30:25 bison kernel: [<c072dd71>] ? _raw_spin_unlock_irqrestore+0x11/0x20
Feb 10 06:30:25 bison kernel: [<c04a6a77>] ? ___ratelimit+0x97/0x110
Feb 10 06:30:25 bison kernel: [<c018d644>] ? __delayacct_freepages_end+0x24/0x30
Feb 10 06:30:25 bison kernel: [<c019c778>] ? T.680+0x258/0x290
Feb 10 06:30:25 bison kernel: [<c0452d64>] ? security_capable_noaudit+0x14/0x20
Feb 10 06:30:25 bison kernel: [<c0138a4b>] ? has_ns_capability_noaudit+0xb/0x20
Feb 10 06:30:25 bison kernel: [<c019ca21>] ? out_of_memory+0x271/0x320
Feb 10 06:30:25 bison kernel: [<c01a0523>] ? __alloc_pages_nodemask+0x6b3/0x6d0
Feb 10 06:30:25 bison kernel: [<c019b232>] ? filemap_fault+0x1f2/0x3c0
Feb 10 06:30:25 bison kernel: [<c0104e6e>] ? xen_batched_set_pte+0x1e/0xf0
Feb 10 06:30:25 bison kernel: [<c0103ed5>] ? pte_pfn_to_mfn+0xb5/0xd0
Feb 10 06:30:25 bison kernel: [<c01b1b55>] ? __do_fault+0x75/0x550
Feb 10 06:30:25 bison kernel: [<c01b5140>] ? handle_pte_fault+0xa0/0x2f0
Feb 10 06:30:25 bison kernel: [<c01b5485>] ? handle_mm_fault+0xf5/0x1b0
Feb 10 06:30:25 bison kernel: [<c0122821>] ? do_page_fault+0x101/0x3a0
Feb 10 06:30:25 bison kernel: [<c01898ab>] ? handle_edge_irq+0x6b/0xf0
Feb 10 06:30:25 bison kernel: [<c04c3d2e>] ? __xen_evtchn_do_upcall+0x1ce/0x210
Feb 10 06:30:25 bison kernel: [<c0103828>] ? xen_mc_flush+0x78/0x110
Feb 10 06:30:25 bison kernel: [<c0109e60>] ? math_state_restore+0xf0/0xf0
Feb 10 06:30:25 bison kernel: [<c0102eb4>] ? xen_clts+0x44/0x50
Feb 10 06:30:25 bison kernel: [<c0109d90>] ? math_state_restore+0x20/0xf0
Feb 10 06:30:25 bison kernel: [<c0122720>] ? mm_fault_error+0x160/0x160
Feb 10 06:30:25 bison kernel: [<c072e582>] ? error_code+0x5a/0x60
Feb 10 06:30:25 bison kernel: [<c0720000>] ? sctp_v6_get_saddr+0x40/0x40
Feb 10 06:30:25 bison kernel: [<c0122720>] ? mm_fault_error+0x160/0x160
Feb 10 06:30:25 bison kernel: Mem-Info:
Feb 10 06:30:25 bison kernel: DMA per-cpu:
Feb 10 06:30:25 bison kernel: CPU    0: hi:    0, btch:   1 usd:   0
Feb 10 06:30:25 bison kernel: CPU    1: hi:    0, btch:   1 usd:   0
Feb 10 06:30:25 bison kernel: CPU    2: hi:    0, btch:   1 usd:   0
Feb 10 06:30:25 bison kernel: CPU    3: hi:    0, btch:   1 usd:   0
Feb 10 06:30:25 bison kernel: Normal per-cpu:
Feb 10 06:30:25 bison kernel: CPU    0: hi:  186, btch:  31 usd:  30
Feb 10 06:30:25 bison kernel: CPU    1: hi:  186, btch:  31 usd:   0
Feb 10 06:30:25 bison kernel: CPU    2: hi:  186, btch:  31 usd:   0
Feb 10 06:30:25 bison kernel: CPU    3: hi:  186, btch:  31 usd:  13
Feb 10 06:30:25 bison kernel: active_anon:58437 inactive_anon:58560 isolated_anon:32
Feb 10 06:30:25 bison kernel: active_file:347 inactive_file:421 isolated_file:0
Feb 10 06:30:25 bison kernel: unevictable:0 dirty:0 writeback:15 unstable:0
Feb 10 06:30:25 bison kernel: free:1203 slab_reclaimable:1089 slab_unreclaimable:2518
Feb 10 06:30:25 bison kernel: mapped:342 shmem:232 pagetables:1291 bounce:0
Feb 10 06:30:25 bison kernel: DMA free:2080kB min:84kB low:104kB high:124kB active_anon:2008kB inactive_anon:2184kB active_file:8kB inactive_file:28kB unevictable:0kB isolated(anon):128kB isolated(file):0kB present:15808kB mlocked:0kB dirty:0kB writeback:4kB mapped:16kB shmem:116kB slab_reclaimable:28kB slab_unreclaimable:36kB kernel_stack:240kB pagetables:36kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:228 all_unreclaimable? yes
Feb 10 06:30:25 bison kernel: lowmem_reserve[]: 0 500 500 500
Feb 10 06:30:25 bison kernel: Normal free:2732kB min:2816kB low:3520kB high:4224kB active_anon:231740kB inactive_anon:232056kB active_file:1380kB inactive_file:1656kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:512064kB mlocked:0kB dirty:0kB writeback:56kB mapped:1352kB shmem:812kB slab_reclaimable:4328kB slab_unreclaimable:10036kB kernel_stack:1256kB pagetables:5128kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:4945 all_unreclaimable? yes
Feb 10 06:30:25 bison kernel: lowmem_reserve[]: 0 0 0 0
Feb 10 06:30:25 bison kernel: DMA: 1*4kB 48*8kB 82*16kB 12*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 2084kB
Feb 10 06:30:25 bison kernel: Normal: 672*4kB 17*8kB 1*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 2840kB
Feb 10 06:30:25 bison kernel: 2796 total pagecache pages
Feb 10 06:30:25 bison kernel: 1706 pages in swap cache
Feb 10 06:30:25 bison kernel: Swap cache stats: add 28528159, delete 28526453, find 488128047/490683323
Feb 10 06:30:25 bison kernel: Free swap  = 0kB
Feb 10 06:30:25 bison kernel: Total swap = 262140kB
Feb 10 06:30:25 bison kernel: 133104 pages RAM
Feb 10 06:30:25 bison kernel: 0 pages HighMem
Feb 10 06:30:25 bison kernel: 5960 pages reserved
Feb 10 06:30:25 bison kernel: 4581 pages shared
Feb 10 06:30:25 bison kernel: 124682 pages non-shared
Feb 10 06:30:25 bison kernel: [ pid ]   uid  tgid total_vm      rss cpu oom_adj oom_score_adj name
Feb 10 06:30:25 bison kernel: [ 1975]     0  1975      712       19   2       0             0 upstart-socket-
Feb 10 06:30:25 bison kernel: [ 2088]     0  2088      733        0   0       0             0 dhclient3
Feb 10 06:30:25 bison kernel: [ 2098]     0  2098     1672        0   3     -17         -1000 sshd
Feb 10 06:30:25 bison kernel: [ 2147]   101  2147     8071       76   0       0             0 rsyslogd
Feb 10 06:30:25 bison kernel: [ 2162]   102  2162      816       23   3       0             0 dbus-daemon
Feb 10 06:30:25 bison kernel: [ 2199]     0  2199      619        0   0       0             0 atd
Feb 10 06:30:25 bison kernel: [ 2205]     0  2205      656       15   0       0             0 cron
Feb 10 06:30:25 bison kernel: [ 2351]   103  2351     6110       31   1       0             0 whoopsie
Feb 10 06:30:25 bison kernel: [ 3446]   106  3446     1434       35   1       0             0 ntpd
Feb 10 06:30:25 bison kernel: [ 4003]     0  4003     7349      188   0       0             0 fail2ban-server
Feb 10 06:30:25 bison kernel: [ 4005]     0  4005     1001       43   0       0             0 gam_server
Feb 10 06:30:25 bison kernel: [ 4264]     0  4264      602        0   2       0             0 getty
Feb 10 06:30:25 bison kernel: [21506]     0 21506      710       16   1       0             0 upstart-udev-br
Feb 10 06:30:25 bison kernel: [21508]     0 21508      738        0   1     -17         -1000 udevd
Feb 10 06:30:25 bison kernel: [21743]     0 21743     1146       28   3       0             0 master
Feb 10 06:30:25 bison kernel: [ 9715]     0  9715      646        0   0       0             0 jsvc
Feb 10 06:30:25 bison kernel: [23232]   108 23232    12555       26   0     -13          -900 postgres
Feb 10 06:30:25 bison kernel: [23234]   108 23234    12555       31   0       0             0 postgres
Feb 10 06:30:25 bison kernel: [23235]   108 23235    12555        7   1       0             0 postgres
Feb 10 06:30:25 bison kernel: [23236]   108 23236    12719       93   1       0             0 postgres
Feb 10 06:30:25 bison kernel: [23237]   108 23237     5180       61   0       0             0 postgres
Feb 10 06:30:25 bison kernel: [12598]   109 12598   108047      274   0       0             0 jsvc
Feb 10 06:30:25 bison kernel: [26544]     0 26544     4809      163   0       0             0 miniserv.pl
Feb 10 06:30:25 bison kernel: [14506]     0 14506    10419       19   1       0             0 apache2
Feb 10 06:30:25 bison kernel: [32716]   110 32716     1187       18   0       0             0 qmgr
Feb 10 06:30:25 bison kernel: [31733]    33 31733    67067      359   0       0             0 apache2
Feb 10 06:30:25 bison kernel: [ 6447]    33  6447    65247      294   0       0             0 apache2
Feb 10 06:30:25 bison kernel: [10667]   110 10667     1151       37   2       0             0 pickup
Feb 10 06:30:25 bison kernel: [10669]     0 10669      753        0   1       0             0 cron
Feb 10 06:30:25 bison kernel: [10671]     0 10671      560        0   1       0             0 sh
Feb 10 06:30:25 bison kernel: [10673]     0 10673      537        0   2       0             0 run-parts
Feb 10 06:30:25 bison kernel: [10678]     0 10678      560       19   1       0             0 apt
Feb 10 06:30:25 bison kernel: [10730]    33 10730    20211     6895   1       0             0 apache2
Feb 10 06:30:25 bison kernel: [10757]    33 10757    20223     7098   0       0             0 apache2
Feb 10 06:30:25 bison kernel: [10760]    33 10760    19701     7006   0       0             0 apache2
Feb 10 06:30:25 bison kernel: [10767]    33 10767    19629     8125   2       0             0 apache2
Feb 10 06:30:25 bison kernel: [10770]    33 10770    19693     8281   3       0             0 apache2
Feb 10 06:30:25 bison kernel: [10771]    33 10771    19690     7921   0       0             0 apache2
Feb 10 06:30:25 bison kernel: [10773]    33 10773    19690     9080   3       0             0 apache2
Feb 10 06:30:25 bison kernel: [10774]    33 10774    19690     8568   3       0             0 apache2
Feb 10 06:30:25 bison kernel: [10775]    33 10775    21034     9216   0       0             0 apache2
Feb 10 06:30:25 bison kernel: [10777]    33 10777    17579     5862   3       0             0 apache2
Feb 10 06:30:25 bison kernel: [10778]    33 10778    18641     7057   1       0             0 apache2
Feb 10 06:30:25 bison kernel: [10779]    33 10779    12163     1368   2       0             0 apache2
Feb 10 06:30:25 bison kernel: [10784]    33 10784    17579     5983   3       0             0 apache2
Feb 10 06:30:25 bison kernel: [10785]    33 10785    18641     6774   1       0             0 apache2
Feb 10 06:30:25 bison kernel: [10787]    33 10787    18457     6566   2       0             0 apache2
Feb 10 06:30:25 bison kernel: [10789]    33 10789    11554     1428   1       0             0 apache2
Feb 10 06:30:25 bison kernel: [10790]    33 10790    11554     1474   0       0             0 apache2
Feb 10 06:30:25 bison kernel: [10792]    33 10792    11554     1532   1       0             0 apache2
Feb 10 06:30:25 bison kernel: [10793]    33 10793    11554     1523   3       0             0 apache2
Feb 10 06:30:25 bison kernel: [10797]    33 10797    10768      457   0       0             0 apache2
Feb 10 06:30:25 bison kernel: [10801]    33 10801    11548     1404   2       0             0 apache2
Feb 10 06:30:25 bison kernel: [10802]    33 10802    11208      984   0       0             0 apache2
Feb 10 06:30:25 bison kernel: [10816]     0 10816      560       19   3       0             0 apt-key
Feb 10 06:30:25 bison kernel: [10819]     0 10819     5870      223   2       0             0 mysqld
Feb 10 06:30:25 bison kernel: [10820]   108 10820    12727      281   0       0             0 postgres
Feb 10 06:30:25 bison kernel: [10821]     0 10821     1689       66   0       0             0 apt-config
Feb 10 06:30:25 bison kernel: [10822]     0 10822      560       19   3       0             0 sh
Feb 10 06:30:25 bison kernel: [10826]   108 10826    12761      299   1       0             0 postgres
Feb 10 06:30:25 bison kernel: [10828]    33 10828    10633      291   2       0             0 apache2
Feb 10 06:30:25 bison kernel: [10829]   110 10829     1174       59   0       0             0 cleanup
Feb 10 06:30:25 bison kernel: [10830]     0 10830     4809      270   2       0             0 /usr/share/webm
Feb 10 06:30:25 bison kernel: [10831]    33 10831    10633      300   3       0             0 apache2
Feb 10 06:30:25 bison kernel: [10842]     0 10842     1086       51   3       0             0 trivial-rewrite
Feb 10 06:30:25 bison kernel: [10843]     0 10843      130        2   0       0             0 status
Feb 10 06:30:25 bison kernel: Out of memory: Kill process 10775 (apache2) score 61 or sacrifice child
Feb 10 06:30:25 bison kernel: Killed process 10775 (apache2) total-vm:84136kB, anon-rss:36780kB, file-rss:84kB
Feb 10 06:30:31 bison postfix/cleanup[10829]: 6FCC210388: message-id=<20130210123006.6FCC210388@>
Feb 10 06:30:32 bison postfix/qmgr[32716]: 6FCC210388: from=<www-data@.>, size=539, nrcpt=1 (queue active)
Feb 10 06:30:43 bison kernel: apache2 invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0, oom_score_adj=0
Feb 10 06:30:43 bison kernel: apache2 cpuset=/ mems_allowed=0
Feb 10 06:30:43 bison kernel: Pid: 10802, comm: apache2 Not tainted 3.5.2-linode45 #1
Feb 10 06:30:43 bison kernel: Call Trace:
Feb 10 06:30:43 bison kernel: [<c019c3ed>] ? T.681+0x7d/0x1b0
Feb 10 06:30:43 bison kernel: [<c072dd71>] ? _raw_spin_unlock_irqrestore+0x11/0x20
Feb 10 06:30:43 bison kernel: [<c04a6a77>] ? ___ratelimit+0x97/0x110
Feb 10 06:30:43 bison kernel: [<c018d644>] ? __delayacct_freepages_end+0x24/0x30
Feb 10 06:30:43 bison kernel: [<c019c778>] ? T.680+0x258/0x290
Feb 10 06:30:43 bison kernel: [<c0452d64>] ? security_capable_noaudit+0x14/0x20
Feb 10 06:30:43 bison kernel: [<c0138a4b>] ? has_ns_capability_noaudit+0xb/0x20
Feb 10 06:30:43 bison kernel: [<c019ca21>] ? out_of_memory+0x271/0x320
Feb 10 06:30:43 bison kernel: [<c01a0523>] ? __alloc_pages_nodemask+0x6b3/0x6d0
Feb 10 06:30:43 bison kernel: [<c019b232>] ? filemap_fault+0x1f2/0x3c0
Feb 10 06:30:43 bison kernel: [<c0104e6e>] ? xen_batched_set_pte+0x1e/0xf0
Feb 10 06:30:43 bison kernel: [<c01b1b55>] ? __do_fault+0x75/0x550
Feb 10 06:30:43 bison kernel: [<c01b5140>] ? handle_pte_fault+0xa0/0x2f0
Feb 10 06:30:43 bison kernel: [<c04e77be>] ? add_interrupt_randomness+0x2e/0x160
Feb 10 06:30:43 bison kernel: [<c01b5485>] ? handle_mm_fault+0xf5/0x1b0
Feb 10 06:30:43 bison kernel: [<c0122821>] ? do_page_fault+0x101/0x3a0
Feb 10 06:30:43 bison kernel: [<c01898ab>] ? handle_edge_irq+0x6b/0xf0
Feb 10 06:30:43 bison kernel: [<c04c3d2e>] ? __xen_evtchn_do_upcall+0x1ce/0x210
Feb 10 06:30:43 bison kernel: [<c018d2f2>] ? rcu_irq_exit+0x52/0xa0
Feb 10 06:30:43 bison kernel: [<c0122720>] ? mm_fault_error+0x160/0x160
Feb 10 06:30:43 bison kernel: [<c072e582>] ? error_code+0x5a/0x60
Feb 10 06:30:43 bison kernel: [<c0122720>] ? mm_fault_error+0x160/0x160
Feb 10 06:30:43 bison kernel: Mem-Info:
Feb 10 06:30:43 bison kernel: DMA per-cpu:
Feb 10 06:30:43 bison kernel: CPU    0: hi:    0, btch:   1 usd:   0
Feb 10 06:30:43 bison kernel: CPU    1: hi:    0, btch:   1 usd:   0
Feb 10 06:30:43 bison kernel: CPU    2: hi:    0, btch:   1 usd:   0
Feb 10 06:30:43 bison kernel: CPU    3: hi:    0, btch:   1 usd:   0
Feb 10 06:30:43 bison kernel: Normal per-cpu:
Feb 10 06:30:43 bison kernel: CPU    0: hi:  186, btch:  31 usd:   0
Feb 10 06:30:43 bison kernel: CPU    1: hi:  186, btch:  31 usd:   0
Feb 10 06:30:43 bison kernel: CPU    2: hi:  186, btch:  31 usd:   0
Feb 10 06:30:43 bison kernel: CPU    3: hi:  186, btch:  31 usd:   0
Feb 10 06:30:43 bison kernel: active_anon:58405 inactive_anon:58464 isolated_anon:32
Feb 10 06:30:43 bison kernel: active_file:379 inactive_file:501 isolated_file:0
Feb 10 06:30:43 bison kernel: unevictable:0 dirty:3 writeback:24 unstable:0
Feb 10 06:30:43 bison kernel: free:1224 slab_reclaimable:1086 slab_unreclaimable:2526
Feb 10 06:30:43 bison kernel: mapped:448 shmem:227 pagetables:1270 bounce:0
Feb 10 06:30:43 bison kernel: DMA free:2080kB min:84kB low:104kB high:124kB active_anon:2072kB inactive_anon:2160kB active_file:8kB inactive_file:152kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15808kB mlocked:0kB dirty:4kB writeback:4kB mapped:12kB shmem:104kB slab_reclaimable:28kB slab_unreclaimable:40kB kernel_stack:224kB pagetables:40kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:256 all_unreclaimable? yes
Feb 10 06:30:43 bison kernel: lowmem_reserve[]: 0 500 500 500
Feb 10 06:30:43 bison kernel: Normal free:2816kB min:2816kB low:3520kB high:4224kB active_anon:231548kB inactive_anon:231696kB active_file:1508kB inactive_file:1852kB unevictable:0kB isolated(anon):128kB isolated(file):0kB present:512064kB mlocked:0kB dirty:8kB writeback:92kB mapped:1780kB shmem:804kB slab_reclaimable:4316kB slab_unreclaimable:10064kB kernel_stack:1272kB pagetables:5040kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:67188 all_unreclaimable? yes
Feb 10 06:30:43 bison kernel: lowmem_reserve[]: 0 0 0 0
Feb 10 06:30:43 bison kernel: DMA: 0*4kB 56*8kB 90*16kB 6*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 2080kB
Feb 10 06:30:43 bison kernel: Normal: 698*4kB 10*8kB 1*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 2888kB
Feb 10 06:30:43 bison kernel: 5883 total pagecache pages
Feb 10 06:30:43 bison kernel: 4730 pages in swap cache
Feb 10 06:30:43 bison kernel: Swap cache stats: add 28544819, delete 28540089, find 488132575/490689523
Feb 10 06:30:43 bison kernel: Free swap  = 0kB
Feb 10 06:30:43 bison kernel: Total swap = 262140kB
Feb 10 06:30:43 bison kernel: 133104 pages RAM
Feb 10 06:30:43 bison kernel: 0 pages HighMem
Feb 10 06:30:43 bison kernel: 5960 pages reserved
Feb 10 06:30:43 bison kernel: 7124 pages shared
Feb 10 06:30:43 bison kernel: 124327 pages non-shared
Feb 10 06:30:43 bison kernel: [ pid ]   uid  tgid total_vm      rss cpu oom_adj oom_score_adj name
Feb 10 06:30:43 bison kernel: [ 1975]     0  1975      712       18   2       0             0 upstart-socket-
Feb 10 06:30:43 bison kernel: [ 2088]     0  2088      733        0   0       0             0 dhclient3
Feb 10 06:30:43 bison kernel: [ 2098]     0  2098     1672        0   3     -17         -1000 sshd
Feb 10 06:30:43 bison kernel: [ 2147]   101  2147     8071       77   2       0             0 rsyslogd
Feb 10 06:30:43 bison kernel: [ 2162]   102  2162      816       23   3       0             0 dbus-daemon
Feb 10 06:30:43 bison kernel: [ 2199]     0  2199      619        0   0       0             0 atd
Feb 10 06:30:43 bison kernel: [ 2205]     0  2205      656       11   0       0             0 cron
Feb 10 06:30:43 bison kernel: [ 2351]   103  2351     6110       30   0       0             0 whoopsie
Feb 10 06:30:43 bison kernel: [ 3446]   106  3446     1434       35   0       0             0 ntpd
Feb 10 06:30:43 bison kernel: [ 4003]     0  4003     7349      187   1       0             0 fail2ban-server
Feb 10 06:30:43 bison kernel: [ 4005]     0  4005     1001       44   0       0             0 gam_server
Feb 10 06:30:43 bison kernel: [ 4264]     0  4264      602        0   2       0             0 getty
Feb 10 06:30:43 bison kernel: [21506]     0 21506      710       14   1       0             0 upstart-udev-br
Feb 10 06:30:43 bison kernel: [21508]     0 21508      738        0   1     -17         -1000 udevd
Feb 10 06:30:43 bison kernel: [21743]     0 21743     1146       26   0       0             0 master
Feb 10 06:30:43 bison kernel: [ 9715]     0  9715      646        0   0       0             0 jsvc
Feb 10 06:30:43 bison kernel: [23232]   108 23232    12555       27   0     -13          -900 postgres
Feb 10 06:30:43 bison kernel: [23234]   108 23234    12555       24   0       0             0 postgres
Feb 10 06:30:43 bison kernel: [23235]   108 23235    12555       16   0       0             0 postgres
Feb 10 06:30:43 bison kernel: [23236]   108 23236    12719      119   0       0             0 postgres
Feb 10 06:30:43 bison kernel: [23237]   108 23237     5180       61   2       0             0 postgres
Feb 10 06:30:43 bison kernel: [12598]   109 12598   108047      279   0       0             0 jsvc
Feb 10 06:30:43 bison kernel: [26544]     0 26544     4809      158   0       0             0 miniserv.pl
Feb 10 06:30:43 bison kernel: [14506]     0 14506    10419       20   2       0             0 apache2
Feb 10 06:30:43 bison kernel: [32716]   110 32716     1187       32   0       0             0 qmgr
Feb 10 06:30:43 bison kernel: [31733]    33 31733    67067      588   0       0             0 apache2
Feb 10 06:30:43 bison kernel: [ 6447]    33  6447    65247      481   0       0             0 apache2
Feb 10 06:30:43 bison kernel: [10667]   110 10667     1151       33   0       0             0 pickup
Feb 10 06:30:43 bison kernel: [10669]     0 10669      753        0   1       0             0 cron
Feb 10 06:30:43 bison kernel: [10671]     0 10671      560        0   1       0             0 sh
Feb 10 06:30:43 bison kernel: [10673]     0 10673      537        0   2       0             0 run-parts
Feb 10 06:30:43 bison kernel: [10678]     0 10678      560       19   1       0             0 apt
Feb 10 06:30:43 bison kernel: [10730]    33 10730    20211     6904   0       0             0 apache2
Feb 10 06:30:43 bison kernel: [10757]    33 10757    20252     7765   0       0             0 apache2
Feb 10 06:30:43 bison kernel: [10760]    33 10760    19701     7193   3       0             0 apache2
Feb 10 06:30:43 bison kernel: [10767]    33 10767    19637     8107   0       0             0 apache2
Feb 10 06:30:43 bison kernel: [10770]    33 10770    19693     7685   2       0             0 apache2
Feb 10 06:30:43 bison kernel: [10771]    33 10771    19690     7371   3       0             0 apache2
Feb 10 06:30:43 bison kernel: [10773]    33 10773    19690     9137   3       0             0 apache2
Feb 10 06:30:43 bison kernel: [10774]    33 10774    19690     8712   2       0             0 apache2
Feb 10 06:30:43 bison kernel: [10777]    33 10777    18443     6537   0       0             0 apache2
Feb 10 06:30:43 bison kernel: [10778]    33 10778    19827     8041   0       0             0 apache2
Feb 10 06:30:43 bison kernel: [10779]    33 10779    12034     1701   0       0             0 apache2
Feb 10 06:30:43 bison kernel: [10784]    33 10784    18251     6560   2       0             0 apache2
Feb 10 06:30:43 bison kernel: [10785]    33 10785    19827     7878   2       0             0 apache2
Feb 10 06:30:43 bison kernel: [10787]    33 10787    19827     7693   3       0             0 apache2
Feb 10 06:30:43 bison kernel: [10789]    33 10789    11810     1832   2       0             0 apache2
Feb 10 06:30:43 bison kernel: [10790]    33 10790    11554     1462   0       0             0 apache2
Feb 10 06:30:43 bison kernel: [10792]    33 10792    11810     1910   0       0             0 apache2
Feb 10 06:30:43 bison kernel: [10793]    33 10793    11810     1867   3       0             0 apache2
Feb 10 06:30:43 bison kernel: [10797]    33 10797    10768      447   0       0             0 apache2
Feb 10 06:30:43 bison kernel: [10801]    33 10801    11806     1801   0       0             0 apache2
Feb 10 06:30:43 bison kernel: [10802]    33 10802    11226     1133   0       0             0 apache2
Feb 10 06:30:43 bison kernel: [10816]     0 10816      560       23   0       0             0 apt-key
Feb 10 06:30:43 bison kernel: [10819]   107 10819    10996     1196   0       0             0 mysqld
Feb 10 06:30:43 bison kernel: [10822]     0 10822      560       19   2       0             0 sh
Feb 10 06:30:43 bison kernel: [10828]    33 10828    10764      493   0       0             0 apache2
Feb 10 06:30:43 bison kernel: [10829]   110 10829     1174       49   2       0             0 cleanup
Feb 10 06:30:43 bison kernel: [10830]     0 10830     4809      630   0       0             0 /usr/share/webm
Feb 10 06:30:43 bison kernel: [10831]    33 10831    10764      490   2       0             0 apache2
Feb 10 06:30:43 bison kernel: [10842]   110 10842     1153       56   0       0             0 trivial-rewrite
Feb 10 06:30:43 bison kernel: [10844]     0 10844     1689       46   3       0             0 apt-config
Feb 10 06:30:43 bison kernel: [10845]    33 10845    10632      362   1       0             0 apache2
Feb 10 06:30:43 bison kernel: [10848]   108 10848    12693      249   1       0             0 postgres
Feb 10 06:30:43 bison kernel: [10854]     0 10854     1725       74   2       0             0 smtp
Feb 10 06:30:43 bison kernel: [10857]     0 10857      238       13   0       0             0 status
Feb 10 06:30:43 bison kernel: Out of memory: Kill process 31733 (apache2) score 59 or sacrifice child
Feb 10 06:30:43 bison kernel: Killed process 31733 (apache2) total-vm:268268kB, anon-rss:2352kB, file-rss:0kB
Feb 10 06:30:52 bison kernel: iptables denied: IN=eth0 OUT= MAC=f2:3c:91:ae:bd:2b:c8:4c:75:f5:c4:ff:08:00 SRC=72.14.188.5 DST=96.126.122.212 LEN=72 TOS=0x00 PREC=0x00 TTL=63 ID=21821 PROTO=UDP SPT=53 DPT=37651 LEN=52 
Feb 10 06:31:08 bison postfix/smtp[10854]: 6FCC210388: to=<webmaster@campusdakota.com>, relay=ASPMX.L.GOOGLE.com[2607:f8b0:400e:c03::1a]:25, delay=77, delays=41/21/13/1.7, dsn=2.0.0, status=sent (250 2.0.0 OK 1360499467 f9si47168256paw.314 - gsmtp)
Feb 10 06:31:09 bison postfix/qmgr[32716]: 6FCC210388: removed
Feb 10 06:31:15 bison kernel: postgres invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0, oom_score_adj=0
Feb 10 06:31:15 bison kernel: postgres cpuset=/ mems_allowed=0
Feb 10 06:31:15 bison kernel: Pid: 23235, comm: postgres Not tainted 3.5.2-linode45 #1
Feb 10 06:31:15 bison kernel: Call Trace:
Feb 10 06:31:15 bison kernel: [<c019c3ed>] ? T.681+0x7d/0x1b0
Feb 10 06:31:15 bison kernel: [<c072dd71>] ? _raw_spin_unlock_irqrestore+0x11/0x20
Feb 10 06:31:15 bison kernel: [<c04a6a77>] ? ___ratelimit+0x97/0x110
Feb 10 06:31:15 bison kernel: [<c018d644>] ? __delayacct_freepages_end+0x24/0x30
Feb 10 06:31:15 bison kernel: [<c019c778>] ? T.680+0x258/0x290
Feb 10 06:31:15 bison kernel: [<c0452d64>] ? security_capable_noaudit+0x14/0x20
Feb 10 06:31:15 bison kernel: [<c0138a4b>] ? has_ns_capability_noaudit+0xb/0x20
Feb 10 06:31:15 bison kernel: [<c019ca21>] ? out_of_memory+0x271/0x320
Feb 10 06:31:15 bison kernel: [<c01a0523>] ? __alloc_pages_nodemask+0x6b3/0x6d0
Feb 10 06:31:15 bison kernel: [<c019b232>] ? filemap_fault+0x1f2/0x3c0
Feb 10 06:31:15 bison kernel: [<c01520f2>] ? __wake_up+0x42/0x60
Feb 10 06:31:15 bison kernel: [<c01b1b55>] ? __do_fault+0x75/0x550
Feb 10 06:31:15 bison kernel: [<c01b5140>] ? handle_pte_fault+0xa0/0x2f0
Feb 10 06:31:15 bison kernel: [<c01b5485>] ? handle_mm_fault+0xf5/0x1b0
Feb 10 06:31:15 bison kernel: [<c0122821>] ? do_page_fault+0x101/0x3a0
Feb 10 06:31:15 bison kernel: [<c01dd7e0>] ? sys_select+0x40/0xb0
Feb 10 06:31:15 bison kernel: [<c0122720>] ? mm_fault_error+0x160/0x160
Feb 10 06:31:15 bison kernel: [<c072e582>] ? error_code+0x5a/0x60
Feb 10 06:31:15 bison kernel: [<c0720000>] ? sctp_v6_get_saddr+0x40/0x40
Feb 10 06:31:15 bison kernel: [<c0122720>] ? mm_fault_error+0x160/0x160
Feb 10 06:31:15 bison kernel: Mem-Info:
Feb 10 06:31:15 bison kernel: DMA per-cpu:
Feb 10 06:31:15 bison kernel: CPU    0: hi:    0, btch:   1 usd:   0
Feb 10 06:31:15 bison kernel: CPU    1: hi:    0, btch:   1 usd:   0
Feb 10 06:31:15 bison kernel: CPU    2: hi:    0, btch:   1 usd:   0
Feb 10 06:31:15 bison kernel: CPU    3: hi:    0, btch:   1 usd:   0
Feb 10 06:31:15 bison kernel: Normal per-cpu:
Feb 10 06:31:15 bison kernel: CPU    0: hi:  186, btch:  31 usd:  22
Feb 10 06:31:15 bison kernel: CPU    1: hi:  186, btch:  31 usd:   2
Feb 10 06:31:15 bison kernel: CPU    2: hi:  186, btch:  31 usd:   0
Feb 10 06:31:15 bison kernel: CPU    3: hi:  186, btch:  31 usd:  47
Feb 10 06:31:15 bison kernel: active_anon:58553 inactive_anon:58613 isolated_anon:32
Feb 10 06:31:15 bison kernel: active_file:243 inactive_file:419 isolated_file:0
Feb 10 06:31:15 bison kernel: unevictable:0 dirty:3 writeback:25 unstable:0
Feb 10 06:31:15 bison kernel: free:1203 slab_reclaimable:1086 slab_unreclaimable:2533
Feb 10 06:31:15 bison kernel: mapped:331 shmem:246 pagetables:1260 bounce:0
Feb 10 06:31:15 bison kernel: DMA free:2080kB min:84kB low:104kB high:124kB active_anon:2016kB inactive_anon:2084kB active_file:36kB inactive_file:76kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15808kB mlocked:0kB dirty:0kB writeback:4kB mapped:52kB shmem:72kB slab_reclaimable:28kB slab_unreclaimable:48kB kernel_stack:376kB pagetables:32kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:274 all_unreclaimable? yes
Feb 10 06:31:15 bison kernel: lowmem_reserve[]: 0 500 500 500
Feb 10 06:31:15 bison kernel: Normal free:2732kB min:2816kB low:3520kB high:4224kB active_anon:232196kB inactive_anon:232368kB active_file:936kB inactive_file:1600kB unevictable:0kB isolated(anon):128kB isolated(file):0kB present:512064kB mlocked:0kB dirty:12kB writeback:96kB mapped:1272kB shmem:912kB slab_reclaimable:4316kB slab_unreclaimable:10084kB kernel_stack:1112kB pagetables:5008kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:4029 all_unreclaimable? yes
Feb 10 06:31:15 bison kernel: lowmem_reserve[]: 0 0 0 0
Feb 10 06:31:15 bison kernel: DMA: 3*4kB 75*8kB 92*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 2084kB
Feb 10 06:31:15 bison kernel: Normal: 669*4kB 7*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 2732kB
Feb 10 06:31:15 bison kernel: 9824 total pagecache pages
Feb 10 06:31:15 bison kernel: 8839 pages in swap cache
Feb 10 06:31:15 bison kernel: Swap cache stats: add 28576970, delete 28568131, find 488138957/490698470
Feb 10 06:31:15 bison kernel: Free swap  = 0kB
Feb 10 06:31:15 bison kernel: Total swap = 262140kB
Feb 10 06:31:15 bison kernel: 133104 pages RAM
Feb 10 06:31:15 bison kernel: 0 pages HighMem
Feb 10 06:31:15 bison kernel: 5960 pages reserved
Feb 10 06:31:15 bison kernel: 8244 pages shared
Feb 10 06:31:15 bison kernel: 124033 pages non-shared
Feb 10 06:31:15 bison kernel: [ pid ]   uid  tgid total_vm      rss cpu oom_adj oom_score_adj name
Feb 10 06:31:15 bison kernel: [ 1975]     0  1975      712       19   0       0             0 upstart-socket-
Feb 10 06:31:15 bison kernel: [ 2088]     0  2088      733        0   0       0             0 dhclient3
Feb 10 06:31:15 bison kernel: [ 2098]     0  2098     1672        0   3     -17         -1000 sshd
Feb 10 06:31:15 bison kernel: [ 2147]   101  2147     8071       83   0       0             0 rsyslogd
Feb 10 06:31:15 bison kernel: [ 2162]   102  2162      816       25   0       0             0 dbus-daemon
Feb 10 06:31:15 bison kernel: [ 2199]     0  2199      619        0   0       0             0 atd
Feb 10 06:31:15 bison kernel: [ 2205]     0  2205      656       13   2       0             0 cron
Feb 10 06:31:15 bison kernel: [ 2351]   103  2351     6110       31   0       0             0 whoopsie
Feb 10 06:31:15 bison kernel: [ 3446]   106  3446     1434       35   0       0             0 ntpd
Feb 10 06:31:15 bison kernel: [ 4003]     0  4003     7349      188   1       0             0 fail2ban-server
Feb 10 06:31:15 bison kernel: [ 4005]     0  4005     1001       44   1       0             0 gam_server
Feb 10 06:31:15 bison kernel: [ 4264]     0  4264      602        0   2       0             0 getty
Feb 10 06:31:15 bison kernel: [21506]     0 21506      710       16   1       0             0 upstart-udev-br
Feb 10 06:31:15 bison kernel: [21508]     0 21508      738        0   1     -17         -1000 udevd
Feb 10 06:31:15 bison kernel: [21743]     0 21743     1146       27   1       0             0 master
Feb 10 06:31:15 bison kernel: [ 9715]     0  9715      646        0   0       0             0 jsvc
Feb 10 06:31:15 bison kernel: [23232]   108 23232    12555       29   1     -13          -900 postgres
Feb 10 06:31:15 bison kernel: [23234]   108 23234    12555       15   2       0             0 postgres
Feb 10 06:31:15 bison kernel: [23235]   108 23235    12555        7   0       0             0 postgres
Feb 10 06:31:15 bison kernel: [23236]   108 23236    12719      143   3       0             0 postgres
Feb 10 06:31:15 bison kernel: [23237]   108 23237     5180       61   1       0             0 postgres
Feb 10 06:31:15 bison kernel: [12598]   109 12598   108047      273   0       0             0 jsvc
Feb 10 06:31:15 bison kernel: [26544]     0 26544     4809      182   1       0             0 miniserv.pl
Feb 10 06:31:15 bison kernel: [14506]     0 14506    10419       26   1       0             0 apache2
Feb 10 06:31:15 bison kernel: [32716]   110 32716     1187       32   3       0             0 qmgr
Feb 10 06:31:15 bison kernel: [ 6447]    33  6447    65247      870   0       0             0 apache2
Feb 10 06:31:15 bison kernel: [10667]   110 10667     1151       33   0       0             0 pickup
Feb 10 06:31:15 bison kernel: [10669]     0 10669      753        0   1       0             0 cron
Feb 10 06:31:15 bison kernel: [10671]     0 10671      560        0   1       0             0 sh
Feb 10 06:31:15 bison kernel: [10673]     0 10673      537        0   2       0             0 run-parts
Feb 10 06:31:15 bison kernel: [10678]     0 10678      560        7   1       0             0 apt
Feb 10 06:31:15 bison kernel: [10730]    33 10730    20211     6649   3       0             0 apache2
Feb 10 06:31:15 bison kernel: [10757]    33 10757    20227     8039   2       0             0 apache2
Feb 10 06:31:15 bison kernel: [10760]    33 10760    19701     7080   0       0             0 apache2
Feb 10 06:31:15 bison kernel: [10767]    33 10767    19637     8076   1       0             0 apache2
Feb 10 06:31:15 bison kernel: [10770]    33 10770    19722     5103   3       0             0 apache2
Feb 10 06:31:15 bison kernel: [10771]    33 10771    19701     5088   3       0             0 apache2
Feb 10 06:31:15 bison kernel: [10773]    33 10773    19690     8478   3       0             0 apache2
Feb 10 06:31:15 bison kernel: [10774]    33 10774    19692     7792   2       0             0 apache2
Feb 10 06:31:15 bison kernel: [10777]    33 10777    20019     7374   1       0             0 apache2
Feb 10 06:31:15 bison kernel: [10778]    33 10778    20211     7597   3       0             0 apache2
Feb 10 06:31:15 bison kernel: [10779]    33 10779    11651     1660   1       0             0 apache2
Feb 10 06:31:15 bison kernel: [10784]    33 10784    20019     7642   2       0             0 apache2
Feb 10 06:31:15 bison kernel: [10785]    33 10785    20083     7012   3       0             0 apache2
Feb 10 06:31:15 bison kernel: [10787]    33 10787    20147     7514   2       0             0 apache2
Feb 10 06:31:15 bison kernel: [10789]    33 10789    11554     1572   2       0             0 apache2
Feb 10 06:31:15 bison kernel: [10790]    33 10790    11554     1301   0       0             0 apache2
Feb 10 06:31:15 bison kernel: [10792]    33 10792    11563     1733   3       0             0 apache2
Feb 10 06:31:15 bison kernel: [10793]    33 10793    11554     1649   0       0             0 apache2
Feb 10 06:31:15 bison kernel: [10797]    33 10797    11554     1730   2       0             0 apache2
Feb 10 06:31:15 bison kernel: [10801]    33 10801    11554     1674   3       0             0 apache2
Feb 10 06:31:15 bison kernel: [10802]    33 10802    11209     1340   2       0             0 apache2
Feb 10 06:31:15 bison kernel: [10816]     0 10816      560       21   0       0             0 apt-key
Feb 10 06:31:15 bison kernel: [10828]    33 10828    11554     1734   2       0             0 apache2
Feb 10 06:31:15 bison kernel: [10829]   110 10829     1174       45   2       0             0 cleanup
Feb 10 06:31:15 bison kernel: [10830]     0 10830     4842     1132   1       0             0 /usr/share/webm
Feb 10 06:31:15 bison kernel: [10831]    33 10831    11554     1733   3       0             0 apache2
Feb 10 06:31:15 bison kernel: [10842]   110 10842     1153       53   2       0             0 trivial-rewrite
Feb 10 06:31:15 bison kernel: [10845]    33 10845    10768      498   0       0             0 apache2
Feb 10 06:31:15 bison kernel: [10854]   110 10854     1784      107   0       0             0 smtp
Feb 10 06:31:15 bison kernel: [10859]    33 10859    43519      473   1       0             0 apache2
Feb 10 06:31:15 bison kernel: [10860]   108 10860    12727      336   2       0             0 postgres
Feb 10 06:31:15 bison kernel: [10867]     0 10867     4809      363   1       0             0 /usr/share/webm
Feb 10 06:31:15 bison kernel: [10870]   108 10870    12693      249   1       0             0 postgres
Feb 10 06:31:15 bison kernel: [10894]     0 10894      560       32   1       0             0 which
Feb 10 06:31:15 bison kernel: [10895]     0 10895      880      133   3       0             0 init
Feb 10 06:31:15 bison kernel: Out of memory: Kill process 10787 (apache2) score 57 or sacrifice child
Feb 10 06:31:15 bison kernel: Killed process 10787 (apache2) total-vm:80588kB, anon-rss:29744kB, file-rss:312kB
```

The errors are also posted at [http://pastebin.com/ZDKW9tCx](http://pastebin.com/ZDKW9tCx)
Thanks

---

### Post by GordThompson on 2013-02-11
One thing to check would be to look in the Apache access logs and see if there are a very large number of connections. I investigated a similar problem on one of my servers and found that some bots were establishing several dozen simultaneous connections and trying to download the whole site at once. I don't believe that it was intended to be a DOS attack, but that was the result: the server was overwhelmed and completely locked up.

(I resolved the issue by using mod_limitipconn to keep those greedy bots at bay.)

---

### Post by Vegan on 2013-02-11
to deal with google et al, i found it was expedient to use a more powerful rig for a web sever appliance.

---

### Post by GordThompson on 2013-02-11
> **Vegan said:**
> to deal with google et al, i found it was expedient to use a more powerful rig for a web sever appliance.
More horsepower is always a good thing, but just to be clear: I wasn't referring to reputable bots from Google or Bing, I was talking about really obnoxious bots that apparently have little regard for the other visitors to the site, let alone the server itself.

---

### Post by Doug S on 2013-02-11
I have never tried to read an OOM dump before and had some troubles.
I might be wrong, but I don't think you are acutally running out of memory, but rather the memory has become fragmented and is unable to fill a requests for continuous blocks of memory. Your Apache tasks are all taking large amounts of memory, and I wonder why. On my server I tried, via clients, to get even one apache task to take more memory and couldn't. I agree with previous suggestions, have a look at your apache log files. Perhaps you also tell us more about your application.
 
Your disk I/O is likely because the system is swapping in and out of the swap space lots.

---

### Post by ndstate on 2013-02-13
Hello everyone,

Thanks so much for your help.  I have two Drupal website that are not too active (and dont have many modules).  I have another Drupal site that is set to offline (this is a huge site that uses tons of memory, hence its offline).  I have many other html sites and a wiki.

You can see the /var/log/apache2/other_vhosts_access.log log at:

[http://pastie.org/6148090](http://pastie.org/6148090) (about an hour of logs today, I know the site was down at 6:30 

[http://dl.dropbox.com/u/1243306/other/log.txt](http://dl.dropbox.com/u/1243306/other/log.txt) (is about a day long log, it was too long to post on pastebin type websites)

It appears that there are a lot of bot connections, perhaps those are causing the issues?  I assume they wont listen to robots, should I IP ban them?

Thanks! :)

---

### Post by GordThompson on 2013-02-13
> **pmp6nl said:**
> It appears that there are a lot of bot connections, perhaps those are causing the issues?  I assume they wont listen to robots, should I IP ban them?
That's where I would start, mainly to see if banning some of the most persistent bot traffic helps alleviate the out-of-memory problem in the short term.

---

### Post by Doug S on 2013-02-13
I do not think the bot traffic is causing your problems. It looks pretty tame to me. However, yes try to eliminate them, as a test case. All the ones I noticed in your log obey the robots.txt, but give it a couple of days. I can not recall which one it is, but one bot only checks robots.txt every few days.
 
Otherwise, sorry but you will have to do the work of looking through log files and trying to correlate with OOM events. "6:30" is not an exact enough time reference., but maybe look here:```
ndsugsa.com:80 159.224.218.28 - - [11/Feb/2013:06:30:01 -0600] "GET /comment/reply/5+...
```Suggest to watch your memory use starting from a fresh boot. Do the apache taaks continue to grow and grow in memory? I.E. might there be a memory leak?
 
While it doesn't explain why you are having OOM issues, you do appear to have annoying issues from China and Russia. If you don't care about potential collateral damage (dropping legitamate IP addresses within the range), perhaps DROP all packets from 110.85.103.0/24 (or 110.85.0.0/16, if you like) and 27.159.0.0/16 and 5.167.177.131/32. Have a look into, and consider dropping 96.47.0.0/16. But keep watching, as they will try from other IP addresses.

---

