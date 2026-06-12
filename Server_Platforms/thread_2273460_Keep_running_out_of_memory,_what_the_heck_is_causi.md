---
title: "Keep running out of memory, what the heck is causing it?!"
date: 2015-04-13
forum: Server Platforms
---

### Post by nicole9 on 2015-04-13
I keep running out of memory out of nowhere, causing oom-killer to kill mysql. I use monit to monitor and restart mysql, but it's still causing crashes and I am trying to figure out the reasons. I have an 8GB system, and when this happens, I am at around 20% free memory when I execute ```
[COLOR=#000000][FONT=Arial]free | awk 'FNR == 3 {print $4/($3+$4)*100}'[/FONT][/COLOR]
```. For reference, right now I'm around 90%.

There's nothing wacky going on in any of my access.log files during these periods (that I can tell). 

Here's the output in syslog, if that gives any insight:

```

Apr 12 11:09:17 myserver kernel: apache2 invoked oom-killer: gfp_mask=0x201da, order=0, oom_score_adj=0
Apr 12 11:09:17 myserver kernel: apache2 cpuset=/ mems_allowed=0
Apr 12 11:09:17 myserver kernel: CPU: 3 PID: 3970 Comm: apache2 Not tainted 3.18.5-x86_64-linode52 #1
Apr 12 11:09:17 myserver kernel: 0000000000000000 0000000000000000 ffffffff817e91fa ffff880002510f80
Apr 12 11:09:17 myserver kernel: ffffffff811266ce ffffffff81c43980 ffff8800020d6c80 00000000000201da
Apr 12 11:09:17 myserver kernel: 00000000000001a9 ffffffff81c18460 ffff880105dafa90 0000000000000000
Apr 12 11:09:17 myserver kernel: Call Trace:
Apr 12 11:09:17 myserver kernel: [<ffffffff817e91fa>] ? dump_stack+0x41/0x57
Apr 12 11:09:17 myserver kernel: [<ffffffff811266ce>] ? dump_header+0x71/0xad
Apr 12 11:09:17 myserver kernel: [<ffffffff8112695f>] ? oom_kill_process+0x65/0x32f
Apr 12 11:09:17 myserver kernel: [<ffffffff810b0455>] ? has_ns_capability_noaudit+0x10/0x18
Apr 12 11:09:17 myserver kernel: [<ffffffff81126ec2>] ? out_of_memory+0x299/0x2cc
Apr 12 11:09:17 myserver kernel: [<ffffffff8112b461>] ? __alloc_pages_nodemask+0x761/0x8ae
Apr 12 11:09:17 myserver kernel: [<ffffffff81158269>] ? alloc_pages_current+0xe7/0x104
Apr 12 11:09:17 myserver kernel: [<ffffffff81125577>] ? filemap_fault+0x279/0x35d
Apr 12 11:09:17 myserver kernel: [<ffffffff8114203b>] ? __do_fault+0x35/0x6d
Apr 12 11:09:17 myserver kernel: [<ffffffff81004361>] ? __raw_callee_save_xen_pmd_val+0x11/0x1e
Apr 12 11:09:17 myserver kernel: [<ffffffff811433ae>] ? do_read_fault+0x1d5/0x2ad
Apr 12 11:09:17 myserver kernel: [<ffffffff81006bf8>] ? pte_mfn_to_pfn+0x58/0xc3
Apr 12 11:09:17 myserver kernel: [<ffffffff811438f1>] ? handle_pte_fault+0x7f/0x1b1
Apr 12 11:09:17 myserver kernel: [<ffffffff81143d86>] ? __handle_mm_fault+0xfd/0x157
Apr 12 11:09:17 myserver kernel: [<ffffffff81143e6e>] ? handle_mm_fault+0x8e/0x92
Apr 12 11:09:17 myserver kernel: [<ffffffff810346bd>] ? __do_page_fault+0x390/0x3b7
Apr 12 11:09:17 myserver kernel: [<ffffffff81124308>] ? __filemap_fdatawrite_range+0x4b/0x50
Apr 12 11:09:17 myserver kernel: [<ffffffff810e3f51>] ? T.1039+0xd5/0xdd
Apr 12 11:09:17 myserver kernel: [<ffffffff81175d03>] ? dput+0x19/0x145
Apr 12 11:09:17 myserver kernel: [<ffffffff810074bd>] ? xen_clocksource_read+0x16/0x18
Apr 12 11:09:17 myserver kernel: [<ffffffff810eb4d6>] ? __getnstimeofday64+0x31/0xa5
Apr 12 11:09:17 myserver kernel: [<ffffffff817ee4f8>] ? page_fault+0x28/0x30
Apr 12 11:09:17 myserver kernel: Mem-Info:
Apr 12 11:09:17 myserver kernel: Node 0 DMA per-cpu:
Apr 12 11:09:17 myserver kernel: CPU    0: hi:    0, btch:   1 usd:   0
Apr 12 11:09:17 myserver kernel: CPU    1: hi:    0, btch:   1 usd:   0
Apr 12 11:09:17 myserver kernel: CPU    2: hi:    0, btch:   1 usd:   0
Apr 12 11:09:17 myserver kernel: CPU    3: hi:    0, btch:   1 usd:   0
Apr 12 11:09:17 myserver kernel: CPU    4: hi:    0, btch:   1 usd:   0
Apr 12 11:09:17 myserver kernel: CPU    5: hi:    0, btch:   1 usd:   0
Apr 12 11:09:17 myserver kernel: Node 0 DMA32 per-cpu:
Apr 12 11:09:17 myserver kernel: CPU    0: hi:  186, btch:  31 usd:  61
Apr 12 11:09:17 myserver kernel: CPU    1: hi:  186, btch:  31 usd:  55
Apr 12 11:09:17 myserver kernel: CPU    2: hi:  186, btch:  31 usd:  83
Apr 12 11:09:17 myserver kernel: CPU    3: hi:  186, btch:  31 usd:  83
Apr 12 11:09:17 myserver kernel: CPU    4: hi:  186, btch:  31 usd: 135
Apr 12 11:09:17 myserver kernel: CPU    5: hi:  186, btch:  31 usd: 175
Apr 12 11:09:17 myserver kernel: Node 0 Normal per-cpu:
Apr 12 11:09:17 myserver kernel: CPU    0: hi:  186, btch:  31 usd:  93
Apr 12 11:09:17 myserver kernel: CPU    1: hi:  186, btch:  31 usd: 116
Apr 12 11:09:17 myserver kernel: CPU    2: hi:  186, btch:  31 usd:  83
Apr 12 11:09:17 myserver kernel: CPU    3: hi:  186, btch:  31 usd: 105
Apr 12 11:09:17 myserver kernel: CPU    4: hi:  186, btch:  31 usd:  96
Apr 12 11:09:17 myserver kernel: CPU    5: hi:  186, btch:  31 usd: 160
Apr 12 11:09:17 myserver kernel: active_anon:1646529 inactive_anon:329572 isolated_anon:0
Apr 12 11:09:17 myserver kernel: active_file:150 inactive_file:199 isolated_file:0
Apr 12 11:09:17 myserver kernel: unevictable:0 dirty:0 writeback:0 unstable:0
Apr 12 11:09:17 myserver kernel: free:10685 slab_reclaimable:29689 slab_unreclaimable:9370
Apr 12 11:09:17 myserver kernel: mapped:201 shmem:21 pagetables:6614 bounce:0
Apr 12 11:09:17 myserver kernel: free_cma:0
Apr 12 11:09:17 myserver kernel: Node 0 DMA free:15912kB min:20kB low:24kB high:28kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15996kB managed:15912kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Apr 12 11:09:17 myserver kernel: lowmem_reserve[]: 0 4065 8000 8000
Apr 12 11:09:17 myserver kernel: Node 0 DMA32 free:21444kB min:5812kB low:7264kB high:8716kB active_anon:3349340kB inactive_anon:670636kB active_file:160kB inactive_file:488kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:4177920kB managed:4165020kB mlocked:0kB dirty:0kB writeback:0kB mapped:508kB shmem:72kB slab_reclaimable:60856kB slab_unreclaimable:17020kB kernel_stack:848kB pagetables:12824kB unstable:0kB bounce:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:4920 all_unreclaimable? yes
Apr 12 11:09:17 myserver kernel: lowmem_reserve[]: 0 0 3934 3934
Apr 12 11:09:17 myserver kernel: Node 0 Normal free:5384kB min:5624kB low:7028kB high:8436kB active_anon:3236776kB inactive_anon:647652kB active_file:440kB inactive_file:308kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:4194304kB managed:4029316kB mlocked:0kB dirty:0kB writeback:0kB mapped:296kB shmem:12kB slab_reclaimable:57900kB slab_unreclaimable:20460kB kernel_stack:1744kB pagetables:13632kB unstable:0kB bounce:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:1432 all_unreclaimable? no
Apr 12 11:09:17 myserver kernel: lowmem_reserve[]: 0 0 0 0
Apr 12 11:09:17 myserver kernel: Node 0 DMA: 0*4kB 1*8kB (U) 0*16kB 1*32kB (U) 2*64kB (U) 1*128kB (U) 1*256kB (U) 0*512kB 1*1024kB (U) 1*2048kB (U) 3*4096kB (MR) = 15912kB
Apr 12 11:09:17 myserver kernel: Node 0 DMA32: 3663*4kB (UE) 0*8kB 35*16kB (R) 41*32kB (R) 34*64kB (R) 9*128kB (R) 2*256kB (R) 2*512kB (R) 0*1024kB 0*2048kB 0*4096kB = 21388kB
Apr 12 11:09:17 myserver kernel: Node 0 Normal: 141*4kB (UEM) 0*8kB 62*16kB (R) 31*32kB (R) 15*64kB (R) 6*128kB (R) 1*256kB (R) 1*512kB (R) 0*1024kB 0*2048kB 0*4096kB = 5044kB
Apr 12 11:09:17 myserver kernel: 2193 total pagecache pages
Apr 12 11:09:17 myserver kernel: 1779 pages in swap cache
Apr 12 11:09:17 myserver kernel: Swap cache stats: add 1493419, delete 1491640, find 63929745/64368060
Apr 12 11:09:17 myserver kernel: Free swap  = 0kB
Apr 12 11:09:17 myserver kernel: Total swap = 262140kB
Apr 12 11:09:17 myserver kernel: 2097055 pages RAM
Apr 12 11:09:17 myserver kernel: 0 pages HighMem/MovableOnly
Apr 12 11:09:17 myserver kernel: 44493 pages reserved
Apr 12 11:09:17 myserver kernel: [ pid ]   uid  tgid total_vm      rss nr_ptes swapents oom_score_adj name
Apr 12 11:09:17 myserver kernel: [ 1544]     0  1544     5310        1      16      101         -1000 udevd
Apr 12 11:09:17 myserver kernel: [ 1616]     0  1616     5309        2      15       95         -1000 udevd
Apr 12 11:09:17 myserver kernel: [ 1618]     0  1618     5309        2      15       96         -1000 udevd
Apr 12 11:09:17 myserver kernel: [ 3068]     0  3068     2493       57       7      519         -1000 dhclient
Apr 12 11:09:17 myserver kernel: [ 3164]     0  3164    30318      430      24      697             0 rsyslogd
Apr 12 11:09:17 myserver kernel: [ 3194]     0  3194    29242     3664      58     2084             0 linode-longview
Apr 12 11:09:17 myserver kernel: [ 3309]     0  3309     4171        1      12       39             0 atd
Apr 12 11:09:17 myserver kernel: [ 3383]     0  3383    12485       16      27      137         -1000 sshd
Apr 12 11:09:17 myserver kernel: [ 3819]     0  3819    17833      582      32      929             0 fail2ban-server
Apr 12 11:09:17 myserver kernel: [ 3857]     0  3857     5578       52      16       31             0 gam_server
Apr 12 11:09:17 myserver kernel: [ 4443]   101  4443    11704       23      24       90             0 exim4
Apr 12 11:09:17 myserver kernel: [ 5096]   104  5096     9770       29      24      125             0 ntpd
Apr 12 11:09:17 myserver kernel: [ 5173]     0  5173     3647        2      12       37             0 agetty
Apr 12 11:09:17 myserver kernel: [ 3327]     0  3327    10185       60      21      101             0 monit
Apr 12 11:09:17 myserver kernel: [25499]     0 25499     1048        2       8       34             0 mysqld_safe
Apr 12 11:09:17 myserver kernel: [25924]   105 25924  1091121   839661    1850    58881             0 mysqld
Apr 12 11:09:17 myserver kernel: [25925]     0 25925     1025        2       8       24             0 logger
Apr 12 11:09:17 myserver kernel: [26834]     0 26834    56517      471     106     1613             0 apache2
Apr 12 11:09:17 myserver kernel: [ 6759]     0  6759     5105       22      15       40             0 cron
Apr 12 11:09:17 myserver kernel: [ 3796]    33  3796   209222   153198     408      812             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3821]    33  3821   210642   154338     409      811             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3832]    33  3832   207522   151578     405      762             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3833]    33  3833    66994    11200     127      858             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3838]    33  3838    71971    16159     138      808             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3926]    33  3926   208706   153217     407      816             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3930]    33  3930    71747    15949     136      844             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3940]    33  3940   206832   151167     402      820             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3941]    33  3941    75729    20424     143      870             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3951]    33  3951    57688     1883     106     1236             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3953]    33  3953    99317    43763     188      817             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3956]    33  3956    68742    12838     130      861             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3959]    33  3959    71235    15933     133      851             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3963]    33  3963    56931      893     101     1587             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3966]    33  3966   114082    58089     220      768             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3970]    33  3970   110821    55334     211      817             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3973]    33  3973   152553    96913     295      820             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3976]    33  3976    80053    24161     153      768             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3982]    33  3982    56553      548     100     1586             0 apache2
Apr 12 11:09:17 myserver kernel: [ 3985]    33  3985    56617      609     101     1588             0 apache2
Apr 12 11:09:17 myserver kernel: Out of memory: Kill process 25924 (mysqld) score 425 or sacrifice child
Apr 12 11:09:17 myserver kernel: Killed process 25924 (mysqld) total-vm:4364484kB, anon-rss:3358644kB, file-rss:0kB
Apr 12 11:09:18 myserver mysqld_safe: Number of processes running now: 0
Apr 12 11:09:18 myserver mysqld_safe: mysqld restarted
Apr 12 11:09:18 myserver mysqld: 150412 11:09:18 [Warning] Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead.
Apr 12 11:09:18 myserver mysqld: 150412 11:09:18 [Warning] The syntax '--log-slow-queries' is deprecated and will be removed in a future release. Please use '--slow-query-log'/'--slow-query-log-file' instead.
Apr 12 11:09:18 myserver mysqld: 150412 11:09:18 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
Apr 12 11:09:18 myserver mysqld: 150412 11:09:18 [Note] Plugin 'FEDERATED' is disabled.
Apr 12 11:09:18 myserver mysqld: 150412 11:09:18 InnoDB: The InnoDB memory heap is disabled
Apr 12 11:09:18 myserver mysqld: 150412 11:09:18 InnoDB: Mutexes and rw_locks use GCC atomic builtins
Apr 12 11:09:18 myserver mysqld: 150412 11:09:18 InnoDB: Compressed tables use zlib 1.2.7
Apr 12 11:09:18 myserver mysqld: 150412 11:09:18 InnoDB: Using Linux native AIO
Apr 12 11:09:18 myserver mysqld: 150412 11:09:18 InnoDB: Initializing buffer pool, size = 3.0G
Apr 12 11:09:18 myserver mysqld: 150412 11:09:18 InnoDB: Completed initialization of buffer pool
Apr 12 11:09:18 myserver mysqld: 150412 11:09:18 InnoDB: highest supported file format is Barracuda.
Apr 12 11:09:18 myserver mysqld: InnoDB: Log scan progressed past the checkpoint lsn 207916286574
Apr 12 11:09:18 myserver mysqld: 150412 11:09:18  InnoDB: Database was not shut down normally!
Apr 12 11:09:18 myserver mysqld: InnoDB: Starting crash recovery.
Apr 12 11:09:18 myserver mysqld: InnoDB: Reading tablespace information from the .ibd files...
Apr 12 11:09:18 myserver mysqld: InnoDB: Restoring possible half-written data pages from the doublewrite
Apr 12 11:09:18 myserver mysqld: InnoDB: buffer...
Apr 12 11:09:18 myserver mysqld: InnoDB: Doing recovery: scanned up to log sequence number 207917075044
Apr 12 11:09:19 myserver mysqld: 150412 11:09:19  InnoDB: Starting an apply batch of log records to the database...
Apr 12 11:09:19 myserver mysqld: InnoDB: Progress in percents: 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96 97 98 99
Apr 12 11:09:19 myserver mysqld: InnoDB: Apply batch completed
Apr 12 11:09:19 myserver mysqld: 150412 11:09:19  InnoDB: Waiting for the background threads to start
Apr 12 11:09:20 myserver mysqld: 150412 11:09:20 InnoDB: 5.5.35 started; log sequence number 207917075044
Apr 12 11:09:20 myserver mysqld: 150412 11:09:20 [Note] Server hostname (bind-address): '127.0.0.1'; port: 3306
Apr 12 11:09:20 myserver mysqld: 150412 11:09:20 [Note]   - '127.0.0.1' resolves to '127.0.0.1';
Apr 12 11:09:20 myserver mysqld: 150412 11:09:20 [Note] Server socket created on IP: '127.0.0.1'.
Apr 12 11:09:20 myserver mysqld: 150412 11:09:20 [Note] Event Scheduler: Loaded 0 events
Apr 12 11:09:20 myserver mysqld: 150412 11:09:20 [Note] /usr/sbin/mysqld: ready for connections.
Apr 12 11:09:20 myserver mysqld: Version: '5.5.35-0+wheezy1-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Debian)

```

---

### Post by Kenneth_Benson on 2015-04-14
Two things I can see here are no available swap out of 256Meg and what the heck is apache doing? 21 different processes? You might want to see what apache is doing with all those processes and if possible (if you have any free disk space) you might want to bump your swap size up. Not always possible, but it might help if you could. Apache though seems to be going wild tho.

---

### Post by nicole9 on 2015-04-15
Thank you so much for your reply. I'm truly lost as to what is causing this issue. Is Apache having multiple processes open not a normal thing? Here is my apache2.conf and my.cnf for reference. My server uses prefork:

```

# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.2/ for detailed information about
# the directives and /usr/share/doc/apache2-common/README.Debian.gz about
# Debian specific hints.
#
#
# Summary of how the Apache 2 configuration works in Debian:
# The Apache 2 web server configuration in Debian is quite different to
# upstream's suggested way to configure the web server. This is because Debian's
# default Apache2 installation attempts to make adding and removing modules,
# virtual hosts, and extra configuration directives as flexible as possible, in
# order to make automating the changes and administering the server as easy as
# possible.


# It is split into several files forming the configuration hierarchy outlined
# below, all located in the /etc/apache2/ directory:
#
#    /etc/apache2/
#    |-- apache2.conf
#    |    `--  ports.conf
#    |-- mods-enabled
#    |    |-- *.load
#    |    `-- *.conf
#    |-- conf.d
#    |    `-- *
#     `-- sites-enabled
#         `-- *
#
#
# * apache2.conf is the main configuration file (this file). It puts the pieces
#   together by including all remaining configuration files when starting up the
#   web server.
#
#   In order to avoid conflicts with backup files, the Include directive is
#   adapted to ignore files that:
#   - do not begin with a letter or number
#   - contain a character that is neither letter nor number nor _-:.
#   - contain .dpkg
#
#   Yet we strongly suggest that all configuration files either end with a
#   .conf or .load suffix in the file name. The next Debian release will
#   ignore files not ending with .conf (or .load for mods-enabled).
#
# * ports.conf is always included from the main configuration file. It is
#   supposed to determine listening ports for incoming connections, and which
#   of these ports are used for name based virtual hosts.
#
# * Configuration files in the mods-enabled/ and sites-enabled/ directories
#   contain particular configuration snippets which manage modules or virtual
#   host configurations, respectively.
#
#   They are activated by symlinking available configuration files from their
#   respective *-available/ counterparts. These should be managed by using our
#   helpers a2enmod/a2dismod, a2ensite/a2dissite. See
#   their respective man pages for detailed information.
#
# * Configuration files in the conf.d directory are either provided by other
#   packages or may be added by the local administrator. Local additions
#   should start with local- or end with .local.conf to avoid name clashes. All
#   files in conf.d are considered (excluding the exceptions noted above) by
#   the Apache 2 web server.
#
# * The binary is called apache2. Due to the use of environment variables, in
#   the default configuration, apache2 needs to be started/stopped with
#   /etc/init.d/apache2 or apache2ctl. Calling /usr/bin/apache2 directly will not
#   work with the default configuration.




# Global configuration
#


ServerName seitan
#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs/2.2/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
ServerRoot "/etc/apache2"


#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
LockFile ${APACHE_LOCK_DIR}/accept.lock


#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}


#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300


#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On


#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100


#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 5


##
## Server-Pool Size Regulation (MPM specific)
## 


# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   1000
</IfModule>


# worker MPM
# StartServers: initial number of server processes to start
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadLimit: ThreadsPerChild can be changed to this maximum value during a
#              graceful restart. ThreadLimit can only be changed by stopping
#              and starting Apache.
# ThreadsPerChild: constant number of worker threads in each server process
# MaxClients: maximum number of simultaneous client connections
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>


# event MPM
# StartServers: initial number of server processes to start
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxClients: maximum number of simultaneous client connections
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_event_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>


# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}


#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#


AccessFileName .htaccess


#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>


#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
# It is also possible to omit any default MIME type and let the
# client's browser guess an appropriate action instead. Typically the
# browser will decide based on the file's extension then. In cases
# where no good assumption can be made, letting the default MIME type
# unset is suggested  instead of forcing the browser to accept
# incorrect  metadata.
#
DefaultType None




#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., www.apache.org (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off


# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog ${APACHE_LOG_DIR}/error.log


#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn


# Include module configuration:
Include mods-enabled/*.load
Include mods-enabled/*.conf


# Include list of ports to listen on and which to use for name based vhosts
Include ports.conf


#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent


# Include of directories ignores editors' and dpkg's backup files,
# see the comments above for details.


# Include generic snippets of statements
Include conf.d/


# Include the virtual host configurations:
Include sites-enabled/


# Deny all Git repos
<Directorymatch "^/.*/\.git/">
Order deny,allow
Deny from all
</Directorymatch>

```

```

#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
# 
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html


# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port        = 3306
socket        = /var/run/mysqld/mysqld.sock


# Here is entries for some specific programs
# The following values assume you have at least 32M ram


# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket        = /var/run/mysqld/mysqld.sock
nice        = 0


[mysqld]
#
# * Basic Settings
#
user        = mysql
pid-file    = /var/run/mysqld/mysqld.pid
socket        = /var/run/mysqld/mysqld.sock
port        = 3306
basedir        = /usr
datadir        = /var/lib/mysql
tmpdir        = /tmp
lc-messages-dir    = /usr/share/mysql
skip-external-locking
# Added to prevent memory issues
innodb_log_buffer_size          = 8M
innodb_buffer_pool_size         = 3G
innodb_log_file_size            = 768M
innodb_fast_shutdown=0
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address        = 127.0.0.1
#
# * Fine Tuning
#
key_buffer        = 16M
key_buffer_size        = 280M
max_allowed_packet    = 16M
thread_stack        = 192K
thread_cache_size       = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover         = BACKUP
#max_connections        = 100
table_cache            = 500
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit    = 1M
query_cache_size        = 70M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file        = /var/log/mysql/mysql.log
#general_log             = 1
#
# Error logging goes to syslog due to /etc/mysql/conf.d/mysqld_safe_syslog.cnf.
#
# Here you can see queries with especially long duration
log_slow_queries    = /var/log/mysql/mysql-slow.log
long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id        = 1
#log_bin            = /var/log/mysql/mysql-bin.log
expire_logs_days    = 10
max_binlog_size         = 100M
#binlog_do_db        = include_database_name
#binlog_ignore_db    = include_database_name
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem






[mysqldump]
quick
quote-names
max_allowed_packet    = 16M


[mysql]
#no-auto-rehash    # faster start of mysql but no tab completition


[isamchk]
key_buffer        = 16M


#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/

```

---

### Post by Kenneth_Benson on 2015-05-04
Sorry for taking so long to get back to you. I'm not sure; you're config looks pretty much like mine. Why it's running so many I can't figure; with you're config, it should only have maybe 5 running. Unless the thread config is wrong and I've not checked that on mine. I'll look at it and get back to you.

---

### Post by tgalati4 on 2015-05-05
I saw a reference to XEN in your stack dump.  Are you running this server in a virtual environment?  Yes, you want a large enough swap so that you can get meaningful logs before the out-of-memory process killer does its bidding.

---

