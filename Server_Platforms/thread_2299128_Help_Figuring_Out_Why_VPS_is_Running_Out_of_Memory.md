---
title: "Help Figuring Out Why VPS is Running Out of Memory Occasionally"
date: 2015-10-15
forum: Server Platforms
---

### Post by dave-davemackey on 2015-10-15
I have a VPS running LAMP which occasionally craps out on me.

Specifically, it runs out of memory and begins killing off processes - which at some point includes MySQL which of course kills all the database driven websites. I'm wondering if anyone can help me figure out why this is occurring? The VPS is 2 GB RAM and 20 GB SSD and I'm running Ubuntu Server 14.04.3 LTS.


Here are what I think are the relevant records from the syslog:

```
Oct 15 03:10:13 localhost rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="508" x-info="http://www.rsyslog.com"] rsyslogd was HUPedOct 15 03:10:37 localhost tripwire[2034]: Integrity Check Complete: /var/lib/tripwire/nameofserver.twd TWReport nameofserver 20151015031015 V:23172 S:100 A:4870 R:4845 C:13457
Oct 15 03:10:37 localhost anacron[892]: Job `cron.daily' terminated (exit status: 1) (mailing output)
Oct 15 03:10:38 localhost anacron[892]: Normal exit (1 job run)
Oct 15 03:17:01 localhost CRON[2106]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 15 03:39:01 localhost CRON[2236]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Oct 15 04:06:25 localhost kernel: [ 3676.842344] hrtimer: interrupt took 13978039 ns
Oct 15 04:09:01 localhost CRON[2360]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Oct 15 04:17:01 localhost CRON[2387]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 15 04:39:01 localhost CRON[2458]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Oct 15 05:09:01 localhost CRON[2585]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Oct 15 05:17:01 localhost CRON[2617]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 15 05:39:01 localhost CRON[2640]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Oct 15 06:09:01 localhost CRON[2732]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Oct 15 06:17:01 localhost CRON[2751]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 15 06:25:01 localhost CRON[2763]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Oct 15 06:39:01 localhost CRON[2866]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Oct 15 07:09:01 localhost CRON[2985]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Oct 15 07:17:01 localhost CRON[3008]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 15 07:30:01 localhost CRON[3093]: (root) CMD (start -q anacron || :)
Oct 15 07:30:01 localhost anacron[3096]: Anacron 2.3 started on 2015-10-15
Oct 15 07:30:01 localhost anacron[3096]: Normal exit (0 jobs run)
Oct 15 07:39:01 localhost CRON[3127]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Oct 15 08:09:01 localhost CRON[3326]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Oct 15 08:17:01 localhost CRON[3416]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 15 08:39:01 localhost CRON[3453]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Oct 15 09:09:01 localhost CRON[3566]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Oct 15 09:17:01 localhost CRON[3653]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 15 09:39:01 localhost CRON[3702]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Oct 15 09:56:13 localhost kernel: [24664.232509] apache2 invoked oom-killer: gfp_mask=0x280da, order=0, oom_score_adj=0
Oct 15 09:56:13 localhost kernel: [24664.232536] apache2 cpuset=/ mems_allowed=0
Oct 15 09:56:13 localhost kernel: [24664.232547] Pid: 3858, comm: apache2 Tainted: GF            3.8.0-19-generic #30-Ubuntu
Oct 15 09:56:13 localhost kernel: [24664.232572] Call Trace:
Oct 15 09:56:13 localhost kernel: [24664.232632]  [<ffffffff816bfc4a>] dump_header+0x80/0x1c3
Oct 15 09:56:13 localhost kernel: [24664.232639]  [<ffffffff81132b67>] oom_kill_process+0x1b7/0x320
Oct 15 09:56:13 localhost kernel: [24664.232655]  [<ffffffff81065845>] ? has_ns_capability_noaudit+0x15/0x20
Oct 15 09:56:13 localhost kernel: [24664.232658]  [<ffffffff81065867>] ? has_capability_noaudit+0x17/0x20
Oct 15 09:56:13 localhost kernel: [24664.232660]  [<ffffffff811332a7>] out_of_memory+0x417/0x450
Oct 15 09:56:13 localhost kernel: [24664.232664]  [<ffffffff81138849>] __alloc_pages_nodemask+0x7f9/0x940
Oct 15 09:56:13 localhost kernel: [24664.232669]  [<ffffffff811753e5>] alloc_pages_vma+0xa5/0x150
Oct 15 09:56:13 localhost kernel: [24664.232675]  [<ffffffff811583a9>] handle_pte_fault+0x2d9/0x450
Oct 15 09:56:13 localhost kernel: [24664.232677]  [<ffffffff81158e79>] handle_mm_fault+0x299/0x670
Oct 15 09:56:13 localhost kernel: [24664.232680]  [<ffffffff8115f5c5>] ? mmap_region+0x2d5/0x640
Oct 15 09:56:13 localhost kernel: [24664.232685]  [<ffffffff816cee3d>] __do_page_fault+0x18d/0x500
Oct 15 09:56:13 localhost kernel: [24664.232688]  [<ffffffff8115fb7d>] ? do_mmap_pgoff+0x24d/0x340
Oct 15 09:56:13 localhost kernel: [24664.232693]  [<ffffffff8114b438>] ? vm_mmap_pgoff+0x88/0xb0
Oct 15 09:56:13 localhost kernel: [24664.232695]  [<ffffffff816cf1be>] do_page_fault+0xe/0x10
Oct 15 09:56:13 localhost kernel: [24664.232697]  [<ffffffff816ce935>] do_async_page_fault+0x35/0x90
Oct 15 09:56:13 localhost kernel: [24664.232700]  [<ffffffff816cb808>] async_page_fault+0x28/0x30
Oct 15 09:56:13 localhost kernel: [24664.232705] Mem-Info:
Oct 15 09:56:13 localhost kernel: [24664.232709] Node 0 DMA per-cpu:
Oct 15 09:56:13 localhost kernel: [24664.232714] CPU    0: hi:    0, btch:   1 usd:   0
Oct 15 09:56:13 localhost kernel: [24664.232715] CPU    1: hi:    0, btch:   1 usd:   0
Oct 15 09:56:13 localhost kernel: [24664.232716] Node 0 DMA32 per-cpu:
Oct 15 09:56:13 localhost kernel: [24664.232731] CPU    0: hi:  186, btch:  31 usd:  58
Oct 15 09:56:13 localhost kernel: [24664.232733] CPU    1: hi:  186, btch:  31 usd: 119
Oct 15 09:56:13 localhost kernel: [24664.232736] active_anon:350785 inactive_anon:117568 isolated_anon:0
Oct 15 09:56:13 localhost kernel: [24664.232736]  active_file:33 inactive_file:106 isolated_file:0
Oct 15 09:56:13 localhost kernel: [24664.232736]  unevictable:0 dirty:0 writeback:0 unstable:0
Oct 15 09:56:13 localhost kernel: [24664.232736]  free:13333 slab_reclaimable:2694 slab_unreclaimable:6700
Oct 15 09:56:13 localhost kernel: [24664.232736]  mapped:136 shmem:467 pagetables:15416 bounce:0
Oct 15 09:56:13 localhost kernel: [24664.232736]  free_cma:0
Oct 15 09:56:13 localhost kernel: [24664.232739] Node 0 DMA free:8328kB min:340kB low:424kB high:508kB active_anon:3580kB inactive_anon:3656kB active_file:0kB inactive_file:44kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15652kB managed:15908kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:80kB slab_unreclaimable:4kB kernel_stack:0kB pagetables:80kB unstable:0kB bounce:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Oct 15 09:56:13 localhost kernel: [24664.232747] lowmem_reserve[]: 0 2000 2000 2000
Oct 15 09:56:13 localhost kernel: [24664.232755] Node 0 DMA32 free:45004kB min:44712kB low:55888kB high:67068kB active_anon:1399560kB inactive_anon:466616kB active_file:132kB inactive_file:380kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:2048248kB managed:2027300kB mlocked:0kB dirty:0kB writeback:0kB mapped:544kB shmem:1868kB slab_reclaimable:10696kB slab_unreclaimable:26796kB kernel_stack:2424kB pagetables:61584kB unstable:0kB bounce:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:495 all_unreclaimable? yes
Oct 15 09:56:13 localhost kernel: [24664.232759] lowmem_reserve[]: 0 0 0 0
Oct 15 09:56:13 localhost kernel: [24664.232762] Node 0 DMA: 2*4kB (M) 11*8kB (EM) 7*16kB (UEM) 1*32kB (E) 5*64kB (UE) 1*128kB (U) 2*256kB (UM) 2*512kB (EM) 2*1024kB (UE) 2*2048kB (ER) 0*4096kB = 8368kB
Oct 15 09:56:13 localhost kernel: [24664.232782] Node 0 DMA32: 173*4kB (EM) 227*8kB (UEM) 180*16kB (UEM) 114*32kB (EM) 60*64kB (UEM) 37*128kB (UEM) 31*256kB (UE) 10*512kB (UE) 6*1024kB (E) 2*2048kB (UE) 1*4096kB (R) = 45004kB
Oct 15 09:56:13 localhost kernel: [24664.232792] 1224 total pagecache pages
Oct 15 09:56:13 localhost kernel: [24664.232794] 597 pages in swap cache
Oct 15 09:56:13 localhost kernel: [24664.232797] Swap cache stats: add 171048, delete 170451, find 15984/19723
Oct 15 09:56:13 localhost kernel: [24664.232799] Free swap  = 0kB
Oct 15 09:56:13 localhost kernel: [24664.232799] Total swap = 524284kB
Oct 15 09:56:13 localhost kernel: [24664.239560] 524270 pages RAM
Oct 15 09:56:13 localhost kernel: [24664.239563] 11487 pages reserved
Oct 15 09:56:13 localhost kernel: [24664.239564] 579411 pages shared
Oct 15 09:56:13 localhost kernel: [24664.239565] 498000 pages non-shared
Oct 15 09:56:13 localhost kernel: [24664.239567] [ pid ]   uid  tgid total_vm      rss nr_ptes swapents oom_score_adj name
Oct 15 09:56:13 localhost kernel: [24664.239574] [  333]     0   333     5915        1      16       59             0 cgmanager
Oct 15 09:56:13 localhost kernel: [24664.239577] [  407]     0   407     4901        0      14       77             0 upstart-udev-br
Oct 15 09:56:13 localhost kernel: [24664.239579] [  412]     0   412    12412        1      28      156         -1000 systemd-udevd
Oct 15 09:56:13 localhost kernel: [24664.239582] [  476]   102   476     9778       30      23       62             0 dbus-daemon
Oct 15 09:56:13 localhost kernel: [24664.239584] [  497]     0   497     8754        0      23       78             0 systemd-logind
Oct 15 09:56:13 localhost kernel: [24664.239586] [  508]   101   508    63960        0      28      120             0 rsyslogd
Oct 15 09:56:13 localhost kernel: [24664.239588] [  807]     0   807     3983       30      14      190             0 upstart-file-br
Oct 15 09:56:13 localhost kernel: [24664.239590] [  821]     0   821     3847       28      12       74             0 upstart-socket-
Oct 15 09:56:13 localhost kernel: [24664.239592] [  837]     0   837     3954        1      13       41             0 getty
Oct 15 09:56:13 localhost kernel: [24664.239595] [  839]     0   839     3954        1      14       41             0 getty
Oct 15 09:56:13 localhost kernel: [24664.239597] [  845]     0   845     3954        1      13       39             0 getty
Oct 15 09:56:13 localhost kernel: [24664.239598] [  846]     0   846     3954        1      13       38             0 getty
Oct 15 09:56:13 localhost kernel: [24664.239601] [  850]     0   850     3954        1      12       41             0 getty
Oct 15 09:56:13 localhost kernel: [24664.239603] [  886]     0   886    15341        0      34      170         -1000 sshd
Oct 15 09:56:13 localhost kernel: [24664.239604] [  893]     0   893     1091        0       8       33             0 acpid
Oct 15 09:56:13 localhost kernel: [24664.239606] [  899]     0   899     5913       23      17       41             0 cron
Oct 15 09:56:13 localhost kernel: [24664.239608] [  900]     0   900     4784        2      13       39             0 atd
Oct 15 09:56:13 localhost kernel: [24664.239611] [ 1104]   110  1104     7051        0      17       61             0 dnsmasq
Oct 15 09:56:13 localhost kernel: [24664.239613] [ 1143]   105  1143   339331    14485     149    15854             0 mysqld
Oct 15 09:56:13 localhost kernel: [24664.239629] [ 1260]   106  1260    13554        6      27      120             0 exim4
Oct 15 09:56:13 localhost kernel: [24664.239632] [ 1341]     0  1341    99848      609     130     1161             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239634] [ 1406]     0  1406    66390      600      32     1173             0 fail2ban-server
Oct 15 09:56:13 localhost kernel: [24664.239636] [ 1469]     0  1469     3954        1      13       39             0 getty
Oct 15 09:56:13 localhost kernel: [24664.239639] [ 3723]    33  3723   112417     6467     172     6961             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239641] [ 3726]    33  3726   106466     7338     158     1132             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239643] [ 3727]    33  3727   107103     7134     159     2014             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239645] [ 3728]    33  3728   106405     7142     169     1247             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239647] [ 3729]    33  3729   106213     6981     158     1250             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239649] [ 3730]    33  3730   105456     6174     156     1211             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239651] [ 3731]    33  3731   105832     6665     167     1199             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239653] [ 3732]    33  3732   107082     6787     161     1248             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239654] [ 3733]    33  3733   110436     7306     149     5163             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239656] [ 3735]    33  3735   109345     6439     176     3928             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239658] [ 3747]    33  3747   105321     6050     137     1119             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239660] [ 3749]    33  3749   105474     6299     138     1084             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239662] [ 3750]    33  3750   105203     5871     137     1112             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239664] [ 3751]    33  3751   104196     5035     135     1108             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239666] [ 3752]    33  3752   103916     4747     135     1119             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239668] [ 3753]    33  3753   106181     6928     139     1089             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239670] [ 3754]    33  3754   103916     4813     135     1110             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239672] [ 3755]    33  3755   100898     1607     129     1300             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239674] [ 3756]    33  3756   105019     1655     135     5313             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239676] [ 3757]    33  3757   100962     1735     129     1195             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239678] [ 3758]    33  3758   102367     1619     132     2751             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239679] [ 3759]    33  3759   105011     1439     135     5507             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239681] [ 3760]    33  3760   105011     1569     135     5433             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239683] [ 3761]    33  3761   105011     1540     135     5411             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239685] [ 3762]    33  3762   105016     1605     135     5382             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239687] [ 3763]    33  3763   109008     5512     143     5313             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239689] [ 3764]    33  3764   109209     5404     144     5601             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239690] [ 3765]    33  3765   108932     5777     143     4994             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239692] [ 3766]    33  3766   108999     5436     143     5375             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239694] [ 3767]    33  3767   109008     5426     143     5352             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239696] [ 3768]    33  3768   108999     4872     143     5890             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239698] [ 3769]    33  3769   103242     4067     131      979             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239700] [ 3770]    33  3770   102581     3503     132      974             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239702] [ 3771]    33  3771   103395     4207     131      995             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239704] [ 3772]    33  3772   102528     3476     129      979             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239706] [ 3773]    33  3773   101978     2919     128      983             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239708] [ 3774]    33  3774   103802     4690     135      998             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239710] [ 3775]    33  3775   102918     3811     130      975             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239711] [ 3776]    33  3776   102702     3615     129      966             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239713] [ 3777]    33  3777   108169     4858     142     5166             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239715] [ 3778]    33  3778   109209     5496     144     5456             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239726] [ 3787]    33  3787   106849     6248     139     2414             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239728] [ 3788]    33  3788   106659     6200     139     2293             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239730] [ 3789]    33  3789   106665     6084     139     2335             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239732] [ 3790]    33  3790   101964     2810     131      979             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239734] [ 3792]    33  3792   106849     6461     139     2232             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239736] [ 3793]    33  3793   106310     5999     138     2179             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239738] [ 3794]    33  3794   101299     2190     127      972             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239740] [ 3796]    33  3796   101365     2279     127      974             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239742] [ 3797]    33  3797   106493     6231     138     2017             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239744] [ 3798]    33  3798   101212     2171     126      954             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239746] [ 3799]    33  3799   100674     1544     126      955             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239748] [ 3800]    33  3800   106659     6831     139     1696             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239749] [ 3801]    33  3801   106273     6264     138     1843             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239751] [ 3802]    33  3802   101477     2465     127      950             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239753] [ 3803]    33  3803   100941     1902     126      955             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239755] [ 3804]    33  3804   100944     1908     126      954             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239757] [ 3805]    33  3805   101234     2180     126      951             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239759] [ 3806]    33  3806   105958     6425     137     1373             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239761] [ 3807]    33  3807   105888     6363     137     1386             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239763] [ 3808]    33  3808   105689     6310     136     1313             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239765] [ 3809]    33  3809   105689     6377     136     1249             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239767] [ 3811]    33  3811   105104     5749     135     1324             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239769] [ 3813]    33  3813   105560     6223     136     1235             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239771] [ 3815]    33  3815   105690     6455     136     1174             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239773] [ 3816]    33  3816   105689     6553     136     1112             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239774] [ 3817]    33  3817   105625     6468     136     1135             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239776] [ 3818]    33  3818   105104     5765     135     1280             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239778] [ 3819]    33  3819   105364     6176     136     1081             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239780] [ 3820]    33  3820   105429     6259     136     1123             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239782] [ 3821]    33  3821   105104     6029     135      996             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239784] [ 3838]    33  3838   105419     6338     135      949             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239786] [ 3839]    33  3839   105482     6289     135      980             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239788] [ 3840]    33  3840   105669     6536     136      979             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239790] [ 3841]    33  3841   105417     6326     135      955             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239792] [ 3845]    33  3845   105547     6489     136      947             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239794] [ 3848]    33  3848   104936     5790     134     1008             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239796] [ 3849]    33  3849   103876     4806     131      938             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239798] [ 3850]    33  3850   105089     5921     134     1001             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239800] [ 3851]    33  3851   105482     6350     135      958             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239802] [ 3852]    33  3852   104112     5082     136      951             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239803] [ 3853]    33  3853   105360     6221     135      965             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239805] [ 3854]    33  3854   104929     5808     134      985             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239807] [ 3855]    33  3855   104189     5135     136      954             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239809] [ 3856]    33  3856   104194     5094     136      957             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239820] [ 3858]    33  3858   104736     5622     134      949             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239822] [ 3859]    33  3859   104775     5641     134      946             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239824] [ 3865]    33  3865   103344     4296     133      949             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239826] [ 3867]    33  3867   103611     4529     135      955             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239828] [ 3868]    33  3868   103516     4548     135      961             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239830] [ 3872]    33  3872   103409     4421     134      944             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239832] [ 3873]    33  3873   102880     3817     133      945             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239834] [ 3876]    33  3876   103241     4218     133      953             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239836] [ 3884]    33  3884   103716     4648     135      978             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239838] [ 3885]    33  3885   103918     4906     135      942             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239840] [ 3886]    33  3886   103519     4515     135      939             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239842] [ 3887]    33  3887   102555     3560     132      946             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239844] [ 3891]    33  3891   102492     3452     132      951             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239846] [ 3892]    33  3892   103017     3938     130      947             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239847] [ 3893]    33  3893   102883     3814     133      957             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239849] [ 3894]    33  3894   103439     4444     134      950             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239852] [ 3919]    33  3919   100385     1240     124      979             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239854] [ 3922]    33  3922   100034      835     122     1038             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239856] [ 3923]    33  3923   100065      841     123     1036             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239858] [ 3931]    33  3931   100027      811     122     1041             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239860] [ 3932]    33  3932    99866      594     121     1138             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239862] [ 3934]    33  3934    99866      603     121     1129             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239864] [ 3937]    33  3937    99866      604     121     1128             0 apache2
Oct 15 09:56:13 localhost kernel: [24664.239866] Out of memory: Kill process 1143 (mysqld) score 47 or sacrifice child
Oct 15 09:56:13 localhost kernel: [24664.240138] Killed process 1143 (mysqld) total-vm:1357324kB, anon-rss:57940kB, file-rss:0kB
Oct 15 09:56:14 localhost kernel: [24665.189481] init: mysql main process (1143) killed by KILL signal
Oct 15 09:56:14 localhost kernel: [24665.189517] init: mysql main process ended, respawning
Oct 15 09:56:14 localhost kernel: [24665.259212] audit_printk_skb: 27 callbacks suppressed
Oct 15 09:56:14 localhost kernel: [24665.259218] type=1400 audit(1444902974.278:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3947 comm="apparmor_parser"
Oct 15 09:56:14 localhost kernel: [24665.409266] init: mysql main process (3959) terminated with status 1
Oct 15 09:56:14 localhost kernel: [24665.409309] init: mysql main process ended, respawning
Oct 15 09:56:15 localhost kernel: [24666.445568] init: mysql post-start process (3961) terminated with status 1
Oct 15 09:56:15 localhost kernel: [24666.560676] type=1400 audit(1444902975.582:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=3983 comm="apparmor_parser"
Oct 15 09:56:17 localhost kernel: [24668.188461] init: mysql main process (3995) terminated with status 1
Oct 15 09:56:17 localhost kernel: [24668.188505] init: mysql respawning too fast, stopped
Oct 15 09:56:26 localhost kernel: [24675.488106] fail2ban-server invoked oom-killer: gfp_mask=0x201da, order=0, oom_score_adj=0
Oct 15 09:56:34 localhost kernel: [24675.488128] fail2ban-server cpuset=/ mems_allowed=0
Oct 15 09:56:35 localhost kernel: [24675.488139] Pid: 1428, comm: fail2ban-server Tainted: GF            3.8.0-19-generic #30-Ubuntu
Oct 15 09:56:36 localhost kernel: [24675.488148] Call Trace:
Oct 15 09:56:36 localhost kernel: [24675.488175]  [<ffffffff816bfc4a>] dump_header+0x80/0x1c3
Oct 15 09:56:36 localhost kernel: [24675.488181]  [<ffffffff81132b67>] oom_kill_process+0x1b7/0x320
Oct 15 09:56:36 localhost kernel: [24675.488188]  [<ffffffff81065845>] ? has_ns_capability_noaudit+0x15/0x20
Oct 15 09:56:36 localhost kernel: [24675.488190]  [<ffffffff81065867>] ? has_capability_noaudit+0x17/0x20
Oct 15 09:56:36 localhost kernel: [24675.488193]  [<ffffffff811332a7>] out_of_memory+0x417/0x450
Oct 15 09:56:36 localhost kernel: [24675.488196]  [<ffffffff81138849>] __alloc_pages_nodemask+0x7f9/0x940
Oct 15 09:56:36 localhost kernel: [24675.488201]  [<ffffffff81173628>] alloc_pages_current+0xb8/0x180
Oct 15 09:56:36 localhost kernel: [24675.488203]  [<ffffffff8112f3bf>] __page_cache_alloc+0xaf/0xd0
Oct 15 09:56:36 localhost kernel: [24675.488205]  [<ffffffff81131962>] filemap_fault+0x2a2/0x470
Oct 15 09:56:36 localhost kernel: [24675.488209]  [<ffffffff81154aaf>] __do_fault+0x6f/0x510
Oct 15 09:56:36 localhost kernel: [24675.488227]  [<ffffffff81158165>] handle_pte_fault+0x95/0x450
Oct 15 09:56:36 localhost kernel: [24675.488232]  [<ffffffff81158e79>] handle_mm_fault+0x299/0x670
Oct 15 09:56:36 localhost kernel: [24675.488237]  [<ffffffff816cee3d>] __do_page_fault+0x18d/0x500
Oct 15 09:56:36 localhost kernel: [24675.488247]  [<ffffffff81043c0f>] ? kvm_clock_read+0x1f/0x30
Oct 15 09:56:36 localhost kernel: [24675.488250]  [<ffffffff81043c29>] ? kvm_clock_get_cycles+0x9/0x10
Oct 15 09:56:36 localhost kernel: [24675.488256]  [<ffffffff810abf08>] ? ktime_get_ts+0x48/0xe0
Oct 15 09:56:36 localhost kernel: [24675.488261]  [<ffffffff811a68d5>] ? poll_select_copy_remaining+0xf5/0x150
Oct 15 09:56:36 localhost kernel: [24675.488265]  [<ffffffff816cf1be>] do_page_fault+0xe/0x10
Oct 15 09:56:36 localhost kernel: [24675.488268]  [<ffffffff816ce935>] do_async_page_fault+0x35/0x90
Oct 15 09:56:36 localhost kernel: [24675.488272]  [<ffffffff816cb808>] async_page_fault+0x28/0x30
Oct 15 09:56:36 localhost kernel: [24675.488274] Mem-Info:
Oct 15 09:56:36 localhost kernel: [24675.488282] Node 0 DMA per-cpu:
Oct 15 09:56:36 localhost kernel: [24675.488289] CPU    0: hi:    0, btch:   1 usd:   0
Oct 15 09:56:36 localhost kernel: [24675.488291] CPU    1: hi:    0, btch:   1 usd:   0
Oct 15 09:56:36 localhost kernel: [24675.488292] Node 0 DMA32 per-cpu:
Oct 15 09:56:36 localhost kernel: [24675.488295] CPU    0: hi:  186, btch:  31 usd:  30
Oct 15 09:56:36 localhost kernel: [24675.488296] CPU    1: hi:  186, btch:  31 usd:  75
Oct 15 09:56:36 localhost kernel: [24675.488300] active_anon:351547 inactive_anon:117815 isolated_anon:0
Oct 15 09:56:36 localhost kernel: [24675.488300]  active_file:13 inactive_file:9 isolated_file:0
Oct 15 09:56:36 localhost kernel: [24675.488300]  unevictable:0 dirty:0 writeback:1 unstable:0
Oct 15 09:56:36 localhost kernel: [24675.488300]  free:13255 slab_reclaimable:2325 slab_unreclaimable:6595
Oct 15 09:56:36 localhost kernel: [24675.488300]  mapped:127 shmem:469 pagetables:15325 bounce:0
Oct 15 09:56:36 localhost kernel: [24675.488300]  free_cma:0
Oct 15 09:56:36 localhost kernel: [24675.488303] Node 0 DMA free:8316kB min:340kB low:424kB high:508kB active_anon:3600kB inactive_anon:3688kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15652kB managed:15908kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:56kB slab_unreclaimable:4kB kernel_stack:0kB pagetables:80kB unstable:0kB bounce:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Oct 15 09:56:36 localhost kernel: [24675.488311] lowmem_reserve[]: 0 2000 2000 2000
Oct 15 09:56:36 localhost kernel: [24675.488321] Node 0 DMA32 free:44704kB min:44712kB low:55888kB high:67068kB active_anon:1402588kB inactive_anon:467572kB active_file:52kB inactive_file:36kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:2048248kB managed:2027300kB mlocked:0kB dirty:0kB writeback:4kB mapped:508kB shmem:1876kB slab_reclaimable:9244kB slab_unreclaimable:26376kB kernel_stack:1496kB pagetables:61220kB unstable:0kB bounce:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:213 all_unreclaimable? yes
Oct 15 09:56:36 localhost kernel: [24675.488328] lowmem_reserve[]: 0 0 0 0
Oct 15 09:56:36 localhost kernel: [24675.488331] Node 0 DMA: 1*4kB (M) 7*8kB (E) 8*16kB (UE) 2*32kB (EM) 6*64kB (UEM) 2*128kB (UM) 1*256kB (U) 2*512kB (EM) 2*1024kB (UE) 2*2048kB (ER) 0*4096kB = 8316kB
Oct 15 09:56:36 localhost kernel: [24675.488367] Node 0 DMA32: 218*4kB (UEM) 259*8kB (UEM) 180*16kB (UEM) 123*32kB (UE) 62*64kB (UEM) 40*128kB (UE) 31*256kB (UE) 13*512kB (UE) 7*1024kB (EM) 0*2048kB 1*4096kB (R) = 44704kB
Oct 15 09:56:36 localhost kernel: [24675.488382] 2188 total pagecache pages
Oct 15 09:56:36 localhost kernel: [24675.488406] 1686 pages in swap cache
Oct 15 09:56:36 localhost kernel: [24675.488412] Swap cache stats: add 210103, delete 208417, find 21137/27309
Oct 15 09:56:36 localhost kernel: [24675.488414] Free swap  = 0kB
Oct 15 09:56:36 localhost kernel: [24675.488415] Total swap = 524284kB
Oct 15 09:56:36 localhost kernel: [24675.496319] 524270 pages RAM
Oct 15 09:56:36 localhost kernel: [24675.496323] 11487 pages reserved
Oct 15 09:56:36 localhost kernel: [24675.496324] 578580 pages shared
Oct 15 09:56:36 localhost kernel: [24675.496325] 498282 pages non-shared
Oct 15 09:56:36 localhost kernel: [24675.496326] [ pid ]   uid  tgid total_vm      rss nr_ptes swapents oom_score_adj name
Oct 15 09:56:36 localhost kernel: [24675.496333] [  333]     0   333     5915        1      16       59             0 cgmanager
Oct 15 09:56:36 localhost kernel: [24675.496364] [  407]     0   407     4901       33      14       76             0 upstart-udev-br
Oct 15 09:56:36 localhost kernel: [24675.496366] [  412]     0   412    12412        1      28      156         -1000 systemd-udevd
Oct 15 09:56:36 localhost kernel: [24675.496369] [  476]   102   476     9778       33      23       62             0 dbus-daemon
Oct 15 09:56:36 localhost kernel: [24675.496372] [  497]     0   497     8754        0      23       78             0 systemd-logind
Oct 15 09:56:36 localhost kernel: [24675.496374] [  508]   101   508    63960       79      28       81             0 rsyslogd
Oct 15 09:56:36 localhost kernel: [24675.496376] [  807]     0   807     3983       32      14      188             0 upstart-file-br
Oct 15 09:56:36 localhost kernel: [24675.496379] [  821]     0   821     3847       29      12       73             0 upstart-socket-
Oct 15 09:56:36 localhost kernel: [24675.496381] [  837]     0   837     3954        1      13       41             0 getty
Oct 15 09:56:36 localhost kernel: [24675.496383] [  839]     0   839     3954        1      14       41             0 getty
Oct 15 09:56:36 localhost kernel: [24675.496400] [  845]     0   845     3954        1      13       39             0 getty
Oct 15 09:56:36 localhost kernel: [24675.496403] [  846]     0   846     3954        1      13       38             0 getty
Oct 15 09:56:36 localhost kernel: [24675.496405] [  850]     0   850     3954        1      12       41             0 getty
Oct 15 09:56:36 localhost kernel: [24675.496407] [  886]     0   886    15341        0      34      170         -1000 sshd
Oct 15 09:56:36 localhost kernel: [24675.496409] [  893]     0   893     1091        0       8       33             0 acpid
Oct 15 09:56:36 localhost kernel: [24675.496411] [  899]     0   899     5913       23      17       41             0 cron
Oct 15 09:56:36 localhost kernel: [24675.496413] [  900]     0   900     4784        2      13       39             0 atd
Oct 15 09:56:36 localhost kernel: [24675.496415] [ 1104]   110  1104     7051        0      17       61             0 dnsmasq
Oct 15 09:56:36 localhost kernel: [24675.496418] [ 1260]   106  1260    13554        6      27      120             0 exim4
Oct 15 09:56:36 localhost kernel: [24675.496420] [ 1341]     0  1341    99848      617     130     1162             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496422] [ 1406]     0  1406    66390      599      32     1174             0 fail2ban-server
Oct 15 09:56:36 localhost kernel: [24675.496424] [ 1469]     0  1469     3954        1      13       39             0 getty
Oct 15 09:56:36 localhost kernel: [24675.496427] [ 3723]    33  3723   112417     6456     172     6965             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496429] [ 3726]    33  3726   106848     7510     158     1317             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496431] [ 3727]    33  3727   107102     7457     159     1667             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496433] [ 3728]    33  3728   106850     7325     169     1453             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496434] [ 3729]    33  3729   106469     7116     159     1322             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496436] [ 3730]    33  3730   105584     6129     156     1393             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496438] [ 3731]    33  3731   105832     6429     167     1416             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496440] [ 3732]    33  3732   107405     7006     161     1367             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496442] [ 3733]    33  3733   110436     7616     149     4840             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496444] [ 3735]    33  3735   109345     6402     176     3937             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496446] [ 3747]    33  3747   105517     5976     138     1371             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496447] [ 3749]    33  3749   105531     6666     139     1205             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496450] [ 3750]    33  3750   105493     6011     138     1340             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496452] [ 3751]    33  3751   104254     4900     135     1335             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496454] [ 3752]    33  3752   104236     4937     135     1288             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496456] [ 3753]    33  3753   106301     6826     139     1305             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496457] [ 3754]    33  3754   103922     4858     135     1340             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496459] [ 3755]    33  3755   100898     1589     129     1307             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496461] [ 3756]    33  3756   105011     1611     135     5322             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496463] [ 3757]    33  3757   101448     2195     130     1169             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496465] [ 3758]    33  3758   102367     1476     132     2879             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496467] [ 3759]    33  3759   105011     1522     135     5450             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496469] [ 3760]    33  3760   105011     1435     135     5565             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496471] [ 3761]    33  3761   105011     1616     135     5340             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496473] [ 3762]    33  3762   105011     1717     135     5262             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496474] [ 3763]    33  3763   109064     5777     144     5188             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496477] [ 3764]    33  3764   109477     5630     144     5701             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496478] [ 3765]    33  3765   109124     5881     143     5060             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496480] [ 3766]    33  3766   109077     5533     144     5375             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496482] [ 3767]    33  3767   108999     5496     143     5357             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496484] [ 3768]    33  3768   109064     5247     144     5710             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496486] [ 3769]    33  3769   104142     4781     133     1204             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496497] [ 3770]    33  3770   102949     3754     133     1146             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496499] [ 3771]    33  3771   104202     4713     133     1275             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496501] [ 3772]    33  3772   102700     3484     129     1160             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496503] [ 3773]    33  3773   102322     3143     129     1064             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496505] [ 3774]    33  3774   104049     4753     136     1260             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496506] [ 3775]    33  3775   103250     4031     130     1171             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496509] [ 3776]    33  3776   103161     3879     130     1165             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496511] [ 3777]    33  3777   108288     4670     142     5423             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496513] [ 3778]    33  3778   109477     5809     144     5525             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496514] [ 3787]    33  3787   106849     5843     139     2808             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496516] [ 3788]    33  3788   106657     6103     139     2588             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496518] [ 3789]    33  3789   106785     6074     139     2506             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496520] [ 3790]    33  3790   103626     4360     134     1093             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496522] [ 3792]    33  3792   106849     6096     139     2578             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496524] [ 3793]    33  3793   106284     5972     138     2326             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496526] [ 3794]    33  3794   101767     2456     127     1193             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496528] [ 3796]    33  3796   101755     2137     127     1479             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496529] [ 3797]    33  3797   106841     6524     139     2088             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496531] [ 3798]    33  3798   101614     2372     127     1206             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496533] [ 3799]    33  3799   100674     1368     126     1161             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496535] [ 3800]    33  3800   106657     6893     139     1792             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496537] [ 3801]    33  3801   106374     6370     138     1824             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496539] [ 3802]    33  3802   102128     2722     128     1254             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496541] [ 3803]    33  3803   101364     2112     127     1138             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496542] [ 3804]    33  3804   101815     2817     128     1081             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496544] [ 3805]    33  3805   102030     2891     128     1140             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496546] [ 3806]    33  3806   106274     6700     137     1487             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496548] [ 3807]    33  3807   106274     6643     137     1507             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496550] [ 3808]    33  3808   105689     6085     136     1537             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496552] [ 3809]    33  3809   105689     6112     136     1515             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496554] [ 3811]    33  3811   105364     5906     136     1325             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496556] [ 3813]    33  3813   105689     6328     136     1309             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496558] [ 3815]    33  3815   105754     6218     136     1392             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496560] [ 3816]    33  3816   105689     6290     136     1329             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496562] [ 3817]    33  3817   105624     6405     136     1245             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496563] [ 3818]    33  3818   105104     5642     135     1420             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496565] [ 3819]    33  3819   105494     6159     136     1279             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496567] [ 3820]    33  3820   105429     6188     136     1253             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496569] [ 3821]    33  3821   105104     5877     135     1181             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496571] [ 3838]    33  3838   105612     6243     136     1151             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496587] [ 3839]    33  3839   105929     6577     137     1172             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496589] [ 3840]    33  3840   106011     6725     137     1171             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496591] [ 3841]    33  3841   105613     6356     136     1143             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496593] [ 3845]    33  3845   105943     6589     137     1222             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496595] [ 3848]    33  3848   105395     6211     135     1111             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496607] [ 3849]    33  3849   103999     4922     132     1029             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496610] [ 3850]    33  3850   105417     5952     135     1286             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496612] [ 3851]    33  3851   105929     6573     137     1204             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496614] [ 3852]    33  3852   104247     5051     136     1107             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496616] [ 3853]    33  3853   105483     6189     135     1190             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496618] [ 3854]    33  3854   105493     6163     135     1207             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496619] [ 3855]    33  3855   104247     5049     136     1105             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496621] [ 3856]    33  3856   104247     5021     136     1106             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496623] [ 3858]    33  3858   105301     5875     135     1240             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496625] [ 3859]    33  3859   105089     5778     134     1122             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496627] [ 3865]    33  3865   103374     4967     135     1140             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496629] [ 3867]    33  3867   103981     4663     135     1218             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496631] [ 3868]    33  3868   103516     4778     136     1254             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496633] [ 3872]    33  3872   103368     4696     135     1208             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496635] [ 3873]    33  3873   103279     4024     133     1170             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496637] [ 3876]    33  3876   103987     4594     135     1159             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496639] [ 3884]    33  3884   103981     4517     135     1392             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496641] [ 3885]    33  3885   104247     5026     136     1138             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496643] [ 3886]    33  3886   103516     4563     136     1285             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496645] [ 3887]    33  3887   103311     4112     133     1136             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496646] [ 3891]    33  3891   102820     3556     133     1203             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496648] [ 3892]    33  3892   103316     4123     130     1182             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496650] [ 3893]    33  3893   103911     4646     135     1141             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496652] [ 3894]    33  3894   103837     4480     134     1241             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496654] [ 3919]    33  3919   100071      906     124      995             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496656] [ 3922]    33  3922   100157     1031     123     1055             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496658] [ 3923]    33  3923   100328     1106     124     1042             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496660] [ 3931]    33  3931   100027      771     122     1066             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496662] [ 3932]    33  3932   100027      806     122     1027             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496664] [ 3934]    33  3934   100027      812     122     1024             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496666] [ 3937]    33  3937   100027      818     122     1024             0 apache2
Oct 15 09:56:36 localhost kernel: [24675.496668] Out of memory: Kill process 3723 (apache2) score 21 or sacrifice child
Oct 15 09:56:36 localhost kernel: [24675.496889] Killed process 3723 (apache2) total-vm:449668kB, anon-rss:25572kB, file-rss:252kB
```

Any ideas are appreciated. :)

Dave

---

