---
title: "Ubuntu 14 vs 20x File Copy Performance Slow"
date: 2024-02-07
forum: Virtualisation
---

### Post by sthoreson on 2024-02-07
[COLOR=#0C0D0E][FONT=-apple-system]ISSUE: File Copy on Ubuntu 23 virtual server is slow
VCENTER, ESXI Host, and Virtual Server Details:
[/FONT][/COLOR][TABLE="class: grid, width: 500"]
[TR]
[TD]Name:[/TD]
[TD]Version:[/TD]
[TD]FileSystem:[/TD]
[/TR]
[TR]
[TD]VCenter[/TD]
[TD][COLOR=#565656][FONT=Metropolis]6.7.0 Build [/FONT][/COLOR]18485185[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]ESXi Host/Hypervisor[/TD]
[TD][COLOR=#565656][FONT=Metropolis]6.7.0, 17499825 - [/FONT][/COLOR]PowerEdge R630[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Datastore[/TD]
[TD]TINTRI 5.4.0.2-11870.57000.25421[/TD]
[TD][COLOR=#565656][FONT=Metropolis]NFS 3[/FONT][/COLOR][/TD]
[/TR]
[TR]
[TD]Virtual Server1[/TD]
[TD]Ubuntu 14.04.1[/TD]
[TD]Ext4[/TD]
[/TR]
[TR]
[TD]Virtual Server2[/TD]
[TD]Ubuntu 23.10[/TD]
[TD]Ext4[/TD]
[/TR]
[/TABLE]
[COLOR=#0C0D0E][FONT=-apple-system]
Server 1 and Server 2 created in VCenter with exact same resources including: CPU, MEM, and HD settings.
Server 1 and Server 2 Ubuntu Installation:  Used default options.  Chose SSH Remote.  No other extra Applications.
Basically, I created these two servers as basic as possible.
Post Install on Both Servers:  Ran: [/FONT][/COLOR]apt-get update, apt-get install open-vm-tools

[COLOR=#0C0D0E][FONT=-apple-system]File Copy Test Case Output from: [/FONT][/COLOR]time for ((i = 0 ; i < 10 ; i++ )) ; do cp ubuntu-20.04.6-live-server-amd64.iso test.iso ; rm test.iso ; done[COLOR=#0C0D0E][FONT=-apple-system]
[/FONT][/COLOR]Server1 Ubuntu 14:
```

real    0m25.784s
user    0m0.072s
sys     0m16.468s

```

Server2 Ubuntu 23:
```

real    0m45.702s
user    0m0.002s
sys     0m21.520s

```

IOStat Generation During File Copy:
Server1 Ubuntu 14:
```

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sdb               0.00     0.50    0.00   49.00     0.00 33792.00  1379.27     3.27   37.96    0.00   37.96   1.02   5.00
Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sdb               0.00     0.00    0.00  514.43     0.00 526774.13  2048.00    41.65   83.71    0.00   83.71   1.66  85.37
Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sdb               0.00     0.00    0.54  465.41     2.16 458862.70  1969.61   106.03  206.17  268.00  206.10   1.94  90.59
Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sdb               0.00    20.73    0.00  485.49     0.00 475486.01  1958.78   106.08  221.61    0.00  221.61   1.76  85.60
Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sdb               0.00     0.53    0.53  500.00     2.12 495204.23  1978.73    98.51  197.59  256.00  197.53   1.65  82.75
Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sdb               0.00    21.03    0.00  536.41     0.00 530477.95  1977.88    87.97  167.59    0.00  167.59   1.59  85.54
Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sdb               0.00     1.04    0.52  510.88     2.07 506694.30  1981.61   102.89  187.20  240.00  187.15   1.75  89.33
Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sdb               0.00     0.54    0.00  490.32     0.00 481169.89  1962.67   114.77  242.60    0.00  242.60   1.82  89.46
Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sdb               0.00    26.88    0.54  505.91     2.15 514324.73  2031.10   108.56  232.52   44.00  232.72   1.89  95.48
Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sdb               0.00     0.52    0.00  562.69     0.00 560281.87  1991.43   104.56  185.82    0.00  185.82   1.50  84.35
Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sdb               0.00    18.48    0.54  541.85     2.17 534339.13  1970.32   112.70  207.80  268.00  207.74   1.91 103.70
Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sdb               0.00     8.19    0.00  536.26     0.00 528205.85  1969.97   143.83  256.77    0.00  256.77   1.94 104.09
Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sdb               0.00     0.00    0.00   39.20     0.00 40136.68  2048.00     2.86  207.64    0.00  207.64   1.69   6.63

```

Server2 Ubuntu 23:
```

Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.50      2.00     0.00   0.00    2.00     4.00  100.50 109696.00     2.00   1.95    9.53  1091.50    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    0.96  38.20
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.00      0.00     0.00   0.00    0.00     0.00  231.84 240509.45     7.96   3.32   10.60  1037.39    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    2.46  92.54
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.00      0.00     0.00   0.00    0.00     0.00  203.00 222116.00     4.50   2.17   12.00  1094.17    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    2.44  74.00
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.00      0.00     0.00   0.00    0.00     0.00  283.00 315136.00     8.00   2.75   11.26  1113.55    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    3.19  98.40
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.50      1.99     0.00   0.00    2.00     4.00  211.94 232601.00     5.97   2.74   12.50  1097.48    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    2.65  73.43
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.00      0.00     0.00   0.00    0.00     0.00  262.00 290816.00     7.50   2.78   11.84  1109.98    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    3.10  91.60
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.00      0.00     0.00   0.00    0.00     0.00  245.00 249154.00     9.50   3.73   10.53  1016.96    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    2.58  79.80
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.00      0.00     0.00   0.00    0.00     0.00  222.50 240326.00    10.50   4.51   11.88  1080.12    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    2.64  75.60
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              1.00      4.00     0.00   0.00    3.50     4.00  288.50 310692.00    10.50   3.51   10.51  1076.92    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    3.04  94.20
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.00      0.00     0.00   0.00    0.00     0.00  240.80 243130.35     6.47   2.62    9.74  1009.69    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    2.34  72.64
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.00      0.00     0.00   0.00    0.00     0.00  291.00 316326.00     9.50   3.16   11.03  1087.03    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    3.21  97.00
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.00      0.00     0.00   0.00    0.00     0.00  206.00 223794.00     7.50   3.51   12.11  1086.38    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    2.49  73.80
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.50      2.00     0.00   0.00    2.00     4.00  297.00 300024.00     7.50   2.46   10.32  1010.18    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    3.07  90.40
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.00      0.00     0.00   0.00    0.00     0.00  256.22 268149.25     5.97   2.28   10.23  1046.56    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    2.62  80.00
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.00      0.00     0.00   0.00    0.00     0.00  243.00 262212.00     8.50   3.38    9.97  1079.06    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    2.42  75.20
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.50      2.00     0.00   0.00    1.00     4.00  298.50 331776.00     7.50   2.45   10.19  1111.48    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    3.04  96.40
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.00      0.00     0.00   0.00    0.00     0.00  232.00 247362.00     5.50   2.32    9.19  1066.22    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    2.13  71.80
Device            r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dkB/s   drqm/s  %drqm d_awa
it dareq-sz     f/s f_await  aqu-sz  %util
sdb              0.00      0.00     0.00   0.00    0.00     0.00  236.50 249270.00    10.00   4.06   11.98  1054.00    0.00      0.00     0.00   0.00    0.
00     0.00    0.00    0.00    2.83  87.20

```

hdparm -Tt  /dev/sdb Output:
Server 1 Ubuntu 14:
```

 Timing cached reads:   17156 MB in  2.00 seconds = 8583.76 MB/sec
 Timing buffered disk reads: 588 MB in  3.00 seconds = 195.90 MB/sec

```

Server 2 Ubuntu 23:
```

 Timing cached reads:   16750 MB in  2.00 seconds = 8383.89 MB/sec
 Timing buffered disk reads: 1172 MB in  3.00 seconds = 390.25 MB/sec

```

Verify VCenter Virtio Enabled on Servers:
Server1 Ubuntu14: /boot# grep CONFIG_VIRTIO config-$(uname -r)
```

CONFIG_VIRTIO_BLK=y
CONFIG_VIRTIO_NET=y
CONFIG_VIRTIO_CONSOLE=y
CONFIG_VIRTIO=y
CONFIG_VIRTIO_PCI=y
CONFIG_VIRTIO_PCI_LEGACY=y
CONFIG_VIRTIO_BALLOON=y
CONFIG_VIRTIO_INPUT=m
CONFIG_VIRTIO_MMIO=y
CONFIG_VIRTIO_MMIO_CMDLINE_DEVICES=y

```


Server2 Ubuntu23: /boot# grep CONFIG_VIRTIO config-$(uname -r)
```

CONFIG_VIRTIO_VSOCKETS=m
CONFIG_VIRTIO_VSOCKETS_COMMON=m
CONFIG_VIRTIO_BLK=y
CONFIG_VIRTIO_NET=y
CONFIG_VIRTIO_CONSOLE=y
CONFIG_VIRTIO_ANCHOR=y
CONFIG_VIRTIO=y
CONFIG_VIRTIO_PCI_LIB=y
CONFIG_VIRTIO_PCI_LIB_LEGACY=y
CONFIG_VIRTIO_MENU=y
CONFIG_VIRTIO_PCI=y
CONFIG_VIRTIO_PCI_LEGACY=y
CONFIG_VIRTIO_VDPA=m
CONFIG_VIRTIO_PMEM=m
CONFIG_VIRTIO_BALLOON=y
CONFIG_VIRTIO_MEM=m
CONFIG_VIRTIO_INPUT=m
CONFIG_VIRTIO_MMIO=y
CONFIG_VIRTIO_MMIO_CMDLINE_DEVICES=y
CONFIG_VIRTIO_DMA_SHARED_BUFFER=m
CONFIG_VIRTIO_IOMMU=y
CONFIG_VIRTIO_FS=m

```


#Ran apt-get update on Both Servers
sudo apt-get update 


# Ran open-vm-tools on both Servers - sudo apt-get install open-vm-tools
Server1 Ubuntu 14:/boot# vmware-toolbox-cmd -v
9.4.0.25793 (build-1280544)


Server2 Ubuntu 23:/tmp# vmware-toolbox-cmd -v
12.3.0.44994 (build-22234872)


#Verified NTP is NOT Installed to avoid VCenter potential conflict with Synchronize guest time with host:
Server1 Ubuntu 14:/boot# sudo service ntp status
ntp: unrecognized service


Server2 Ubuntu 23:/boot# sudo systemctl status ntp
Failed to stop ntp.service: Unit ntp.service not loaded.


#GRUB Boot Modifications on Server2 Ubuntu 23:
#Set disk I/O scheduler to Noop (No Optimization)
Server2 Ubuntu 23: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash elevator=noop"
update-grub
reboot
cat /sys/block/sdb/queue/scheduler
[noop] [mq-deadline] cfq
time for ((i = 0 ; i < 10 ; i++ )) ; do cp ubuntu-20.04.6-live-server-amd64.iso test.iso ; rm test.iso ; done
No file copy performance improvement on Ubuntu 23 Server.


#Set mitigations=off
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash mitigations=off"
update-grub
reboot
cat /sys/block/sdb/queue/scheduler
none [mq-deadline]
time for ((i = 0 ; i < 10 ; i++ )) ; do cp ubuntu-20.04.6-live-server-amd64.iso test.iso ; rm test.iso ; done
No file copy performance improvement on Ubuntu 23 Server.




#Mount Point Options
mount | grep '^/'
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
/dev/sdb1 on /d01 type ext4 (rw)




#Cross-Compare fs vm settings:
Server1 Ubuntu 14: sysctl -a | grep 'vm\|fs'
```

fs.aio-max-nr = 65536
fs.aio-nr = 0
fs.dentry-state = 33815 22349   45      0       0       0
fs.dir-notify-enable = 1
fs.epoll.max_user_watches = 824217
fs.file-max = 401361
fs.file-nr = 576        0       401361
fs.inode-nr = 28005     329
fs.inode-state = 28005  329     0       0       0       0       0
fs.inotify.max_queued_events = 16384
fs.inotify.max_user_instances = 128
fs.inotify.max_user_watches = 8192
fs.lease-break-time = 45
fs.leases-enable = 1
fs.mqueue.msg_default = 10
fs.mqueue.msg_max = 10
fs.mqueue.msgsize_default = 8192
fs.mqueue.msgsize_max = 8192
fs.mqueue.queues_max = 256
fs.nr_open = 1048576
fs.overflowgid = 65534
fs.overflowuid = 65534
fs.pipe-max-size = 1048576
fs.pipe-user-pages-hard = 0
fs.pipe-user-pages-soft = 16384
fs.protected_hardlinks = 1
fs.protected_symlinks = 1
fs.quota.allocated_dquots = 0
fs.quota.cache_hits = 0
fs.quota.drops = 0
fs.quota.free_dquots = 0
fs.quota.lookups = 0
fs.quota.reads = 0
fs.quota.syncs = 88
fs.quota.writes = 0
fs.suid_dumpable = 2
kernel.sched_cfs_bandwidth_slice_us = 5000
sysctl: reading key "net.ipv6.conf.all.stable_secret"
sysctl: reading key "net.ipv6.conf.default.stable_secret"
sysctl: reading key "net.ipv6.conf.eth0.stable_secret"
sysctl: reading key "net.ipv6.conf.lo.stable_secret"
vm.admin_reserve_kbytes = 8192
vm.block_dump = 0
vm.compact_unevictable_allowed = 1
vm.dirty_background_bytes = 0
vm.dirty_background_ratio = 10
vm.dirty_bytes = 0
vm.dirty_expire_centisecs = 3000
vm.dirty_ratio = 20
vm.dirty_writeback_centisecs = 500
vm.dirtytime_expire_seconds = 43200
vm.drop_caches = 0
vm.extfrag_threshold = 500
vm.hugepages_treat_as_movable = 0
vm.hugetlb_shm_group = 0
vm.laptop_mode = 0
vm.legacy_va_layout = 0
vm.lowmem_reserve_ratio = 256   256     32      1
vm.max_map_count = 65530
vm.memory_failure_early_kill = 0
vm.memory_failure_recovery = 1
vm.min_free_kbytes = 67584
vm.min_slab_ratio = 5
vm.min_unmapped_ratio = 1
vm.mmap_min_addr = 65536
vm.nr_hugepages = 0
vm.nr_hugepages_mempolicy = 0
vm.nr_overcommit_hugepages = 0
vm.nr_pdflush_threads = 0
vm.numa_zonelist_order = default
vm.oom_dump_tasks = 1
vm.oom_kill_allocating_task = 0
vm.overcommit_kbytes = 0
vm.overcommit_memory = 0
vm.overcommit_ratio = 50
vm.page-cluster = 3
vm.panic_on_oom = 0
vm.percpu_pagelist_fraction = 0
vm.stat_interval = 1
vm.swappiness = 60
vm.user_reserve_kbytes = 125478
vm.vfs_cache_pressure = 100
vm.zone_reclaim_mode = 0

```


Server2 Ubuntu 23: sysctl -a | grep 'vm\|fs'
```

fs.aio-max-nr = 65536
fs.aio-nr = 0
fs.binfmt_misc.python3/11 = enabled
fs.binfmt_misc.python3/11 = interpreter /usr/bin/python3.11
fs.binfmt_misc.python3/11 = flags:
fs.binfmt_misc.python3/11 = offset 0
fs.binfmt_misc.python3/11 = magic a70d0d0a
fs.binfmt_misc.status = enabled
fs.dentry-state = 121588        99325   45      0       45257   0
fs.dir-notify-enable = 1
fs.epoll.max_user_watches = 867105
fs.fanotify.max_queued_events = 16384
fs.fanotify.max_user_groups = 128
fs.fanotify.max_user_marks = 31556
fs.file-max = 9223372036854775807
fs.file-nr = 1216       0       9223372036854775807
fs.inode-nr = 76293     658
fs.inode-state = 76293  658     0       0       0       0       0
fs.inotify.max_queued_events = 16384
fs.inotify.max_user_instances = 128
fs.inotify.max_user_watches = 29677
fs.lease-break-time = 45
fs.leases-enable = 1
fs.mount-max = 100000
fs.mqueue.msg_default = 10
fs.mqueue.msg_max = 10
fs.mqueue.msgsize_default = 8192
fs.mqueue.msgsize_max = 8192
fs.mqueue.queues_max = 256
fs.nr_open = 1048576
fs.overflowgid = 65534
fs.overflowuid = 65534
fs.pipe-max-size = 1048576
fs.pipe-user-pages-hard = 0
fs.pipe-user-pages-soft = 16384
fs.protected_fifos = 1
fs.protected_hardlinks = 1
fs.protected_regular = 2
fs.protected_symlinks = 1
fs.quota.allocated_dquots = 0
fs.quota.cache_hits = 0
fs.quota.drops = 0
fs.quota.free_dquots = 0
fs.quota.lookups = 0
fs.quota.reads = 0
fs.quota.syncs = 142
fs.quota.writes = 0
fs.suid_dumpable = 2
fs.verity.require_signatures = 0
kernel.firmware_config.force_sysfs_fallback = 0
kernel.firmware_config.ignore_sysfs_fallback = 0
kernel.sched_cfs_bandwidth_slice_us = 5000
vm.admin_reserve_kbytes = 8192
vm.compact_unevictable_allowed = 1
vm.compaction_proactiveness = 20
vm.dirty_background_bytes = 0
vm.dirty_background_ratio = 10
vm.dirty_bytes = 0
vm.dirty_expire_centisecs = 3000
vm.dirty_ratio = 20
vm.dirty_writeback_centisecs = 500
vm.dirtytime_expire_seconds = 43200
vm.extfrag_threshold = 500
vm.hugetlb_optimize_vmemmap = 0
vm.hugetlb_shm_group = 0
vm.laptop_mode = 0
vm.legacy_va_layout = 0
vm.lowmem_reserve_ratio = 256   256     32      0       0
vm.max_map_count = 65530
vm.memfd_noexec = 0
vm.memory_failure_early_kill = 0
vm.memory_failure_recovery = 1
vm.min_free_kbytes = 67584
vm.min_slab_ratio = 5
vm.min_unmapped_ratio = 1
vm.mmap_min_addr = 65536
vm.mmap_rnd_bits = 28
vm.mmap_rnd_compat_bits = 8
vm.nr_hugepages = 0
vm.nr_hugepages_mempolicy = 0
vm.nr_overcommit_hugepages = 0
vm.numa_stat = 1
vm.numa_zonelist_order = Node
vm.oom_dump_tasks = 1
vm.oom_kill_allocating_task = 0
vm.overcommit_kbytes = 0
vm.overcommit_memory = 0
vm.overcommit_ratio = 50
vm.page-cluster = 3
vm.page_lock_unfairness = 5
vm.panic_on_oom = 0
vm.percpu_pagelist_high_fraction = 0
vm.stat_interval = 1
vm.swappiness = 60
vm.unprivileged_userfaultfd = 0
vm.user_reserve_kbytes = 121460
vm.vfs_cache_pressure = 100
vm.watermark_boost_factor = 15000
vm.watermark_scale_factor = 10
vm.zone_reclaim_mode = 0

```


#Compare Reserved block count
Server1 Ubuntu 23: tune2fs -l /dev/sdb1 | grep 'Reserved block count'
Reserved block count:     1310694


Server2 Ubuntu 23: tune2fs -l /dev/sdb1 | grep 'Reserved block count'
Reserved block count:     1310694


#Disabled and Purge ALL snapd and snapd.sockets on Server2:
systemctl stop snapd
systemctl disable snapd
systemctl stop snapd.socket
systemctl disable snapd.socket
systemctl mask snapd
systemctl mask snapd.socket
apt purge snapd
apt autoremove
Reboot
No file copy performance improvement on Ubuntu 23 Server.


#Reverted to Snapshot Prior to SNAP removal from Server2.
#Removed VCenter Snapshot of Server2.


#Compare hugepage settings
Server1 Ubuntu 14: cat /sys/kernel/mm/transparent_hugepage/enabled
[always] madvise never


Server2 Ubuntu 23:/d01/user# cat /sys/kernel/mm/transparent_hugepage/enabled
always [madvise] never


#Modify Dirty Parameters on Server2 Ubuntu23:
echo 10 > /proc/sys/vm/dirty_background_ratio
echo 20 > /proc/sys/vm/dirty_ratio
echo 3000 > /proc/sys/vm/dirty_expire_centisecs
echo 500 > /proc/sys/vm/dirty_writeback_centisecs
echo $((64*1024*1024)) > /proc/sys/vm/dirty_background_bytes
echo $((512*1024*1024)) > /proc/sys/vm/dirty_bytes
sync; echo 3 > /proc/sys/vm/drop_caches
reboot
No file copy performance improvement on Ubuntu 23 Server.


#Verify metadata_csum is enabled
tune2fs -l /dev/sdb1 | grep grep "metadata_csum"
metadata_csum


#Defrag Disk sdb1 on Server2 Ubuntu 23 Server
e2fsck /dev/sdb1
e2fsck 1.46.5 (30-Dec-2021)
DataVol: clean, 442605/201326592 files, 588558952/805305856 blocks
reboot
No file copy performance improvement on Ubuntu 23 Server.


#Verify No snaps for Server2 Ubuntu 23:
losetup -a
0 rows


#Verify loop on Server2 Ubuntu 23
journalctl | grep loop
```

Feb 07 20:21:26 Server2 kernel: Calibrating delay loop (skipped) preset value.. 4599.99 BogoMIPS (lpj=9199992)
Feb 07 20:21:27 Server2 kernel: loop: module loaded
Feb 07 20:21:27 Server2 systemd[1]: Starting modprobe@loop.service - Load Kernel Module loop...
Feb 07 20:21:27 Server2 systemd[1]: modprobe@loop.service: Deactivated successfully.
Feb 07 20:21:27 Server2 systemd[1]: Finished modprobe@loop.service - Load Kernel Module loop.
Feb 07 20:37:44 Server2 kernel: Calibrating delay loop (skipped) preset value.. 4399.99 BogoMIPS (lpj=8799992)
Feb 07 20:37:44 Server2 kernel: loop: module loaded
Feb 07 20:37:44 Server2 systemd[1]: Starting modprobe@loop.service - Load Kernel Module loop...
Feb 07 20:37:44 Server2 systemd[1]: modprobe@loop.service: Deactivated successfully.
Feb 07 20:37:44 Server2 systemd[1]: Finished modprobe@loop.service - Load Kernel Module loop.

```


#Show Current cgroup2 Settings on Server2 Ubuntu 23:
mount | grep cgroup2
cgroup2 on /sys/fs/cgroup type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate,memory_recursiveprot)


#Show Current Mounts on Server2 Ubuntu 23:
cat /proc/mounts
```

sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,nosuid,relatime,size=1947604k,nr_inodes=486901,mode=755,inode64 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,nodev,noexec,relatime,size=400088k,mode=755,inode64 0 0
/dev/sda2 / ext4 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev,inode64 0 0
tmpfs /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k,inode64 0 0
cgroup2 /sys/fs/cgroup cgroup2 rw,nosuid,nodev,noexec,relatime,nsdelegate,memory_recursiveprot 0 0
pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0
bpf /sys/fs/bpf bpf rw,nosuid,nodev,noexec,relatime,mode=700 0 0
systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=29,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=19240 0 0
debugfs /sys/kernel/debug debugfs rw,nosuid,nodev,noexec,relatime 0 0
mqueue /dev/mqueue mqueue rw,nosuid,nodev,noexec,relatime 0 0
hugetlbfs /dev/hugepages hugetlbfs rw,relatime,pagesize=2M 0 0
tracefs /sys/kernel/tracing tracefs rw,nosuid,nodev,noexec,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,nosuid,nodev,noexec,relatime 0 0
configfs /sys/kernel/config configfs rw,nosuid,nodev,noexec,relatime 0 0
ramfs /run/credentials/systemd-sysusers.service ramfs ro,nosuid,nodev,noexec,relatime,mode=700 0 0
ramfs /run/credentials/systemd-sysctl.service ramfs ro,nosuid,nodev,noexec,relatime,mode=700 0 0
ramfs /run/credentials/systemd-tmpfiles-setup-dev.service ramfs ro,nosuid,nodev,noexec,relatime,mode=700 0 0
vmware-vmblock /run/vmblock-fuse fuse.vmware-vmblock rw,relatime,user_id=0,group_id=0,default_permissions,allow_other 0 0
/dev/sdb1 /d01 ext4 rw,relatime 0 0
ramfs /run/credentials/systemd-tmpfiles-setup.service ramfs ro,nosuid,nodev,noexec,relatime,mode=700 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
ramfs /run/credentials/systemd-resolved.service ramfs ro,nosuid,nodev,noexec,relatime,mode=700 0 0
/dev/sdc1 /d02 ext4 rw,relatime 0 0
tmpfs /run/user/1000 tmpfs rw,nosuid,nodev,relatime,size=400084k,nr_inodes=100021,mode=700,uid=1000,gid=1000,inode64 0 0

```

---

### Post by TheFu on 2024-02-07
The post formatting is too hard to read.  Please learn to use forum code-tags to maintain columns.

Multiple kernel security fixes which impacted performance have been included in newer kernels.

NFSv3 has been deprecated a long time - even in 2014.  Please use NFSv4.

---

### Post by sthoreson on 2024-02-08
Thank you for your response.  I reformatted the initial post to be much more readable as per recommendation.
Can you confirm if the reason for the slow file copies is distinctly related to NFSv3 on the ESXi Host and the later version of Ubuntu 23?
If so, is there any specific Ubuntu related documentation that can be referenced for the specifications concerning this situation?
Again, thank you and appreciate your time.

---

### Post by TheFu on 2024-02-08
> **sthoreson said:**
> Can you confirm if the reason for the slow file copies is distinctly related to NFSv3 on the ESXi Host and the later version of Ubuntu 23?
Nope. I confirm nothing.  

You skipped right over all the kernel security improvements. 

We've been using NFSv4 nearly 15 yrs.  It was released in 2002.  What are you waiting for?

If you don't provide details for everything attempted, nobody will try to reproduce it, assuming they could.  We dumped ESXi around 2011 due to license costs, so there's no way  to try anything even close to your setup.

With all testing, simplify each component and test. How fast is the networking without any storage involved?  How fast is the storage without any networking involve? Which is the bottleneck?  Then add on complexity and try different, but similar tests.  Test NFS3, NFS4, scp, rsync, nc, sftp between the systems.  Is it only these 2 systems in the same box?  What about systems in different boxes?  Test without the hypervisor involved at all. How fast is that?  Could it be the hypervisor's file system?

For testing storage, most people would use fio these days.  [https://arstechnica.com/gadgets/2020/02/how-fast-are-your-disks-find-out-the-open-source-way-with-fio/](https://arstechnica.com/gadgets/2020/02/how-fast-are-your-disks-find-out-the-open-source-way-with-fio/)


But my gut is telling me that kernel security fixes since 2014 are the real issue.  You have to use those security improvements. You can disable some with kernel boot options, but I don't. I decided that security is more important than performance.

---

### Post by sthoreson on 2024-02-09
Thank you again for your response.  I skipped over all of the details for everything attempted and chose to summarize as I didn't want to over saturate the thread with pages and pages of output.
However, I will detail these out for review.  As per your emphasis to upgrade from NFS3 to NFS4, this has already been presented for priority consideration to the company IT Directors.
Thank you for your patience as I work through detailing out the attempted modifications.

---

### Post by MAFoElffen on 2024-02-12
As per what you said in post #1... You are comparing apples to oranges. You said you are running the same system requirement allocations for both. They do not use the same.

In 2014, Ubuntu Server Edition min requirements was:
```

300 MHz x86 processor
192 MiB of system memory (RAM)
1 GB of disk space
Graphics card and monitor capable of 640x480
CD drive

```
For 22.04 Server Edition it says:
```

CPU: 1 gigahertz or better
RAM: 1 gigabyte or more
Disk: a minimum of 2.5 gigabytes

```
But I can tell you that it will peg 2GB in the install.

There is a lot more going on, than it was with 14.04. You need to adjust the allocations to what it needs.

One of the things I do, is that I beta test vSphere/vCenter updates and versions for VMware. from my notes:

Use the LSI Logic virtual SCSI adapter instead of the BusLogic virtual SCSI adapter. You'll encounter less problems with Linux OS'es doing that.

The vdisk performance is a lot better setting your VMDK files to static instead of dynamic.

There are some quarks with vSphere and many Linux distro's, where booth fight each other for who is in charge of what. This often slows things down. Here it a few examples--

You can get clock drift if both NTP and VMware Tools are fighting over who is in charge. Disable the time synchronization in VMware Tools by opening the virtual machine configuration file and set these options to FALSE:
tools.syncTime
tools.synchronize.restore
time.synchronize.resume.disk
time.synchronize.continue
time.synchronize.shrink

Let vSphere handle the disk I/O scheduling. You can turn off Linux from scheduling disk I/O, (so they don't fight for that) by editing /etc/default/grub and add "elevator-noop" as a boot parameter in line GRUB_CMDLINE_DEFAULT_LINUX.

For Ubuntu server VM's, I usually allocate 2-4 vcpu's and 4GB RAM at the start and adjust from there.

I hope those help.

---

### Post by sthoreson on 2024-02-13
Thank you.  I will review your recommendations.

---

### Post by sthoreson on 2024-02-13
#Recommened Changes from Ubuntu Forum Post:
Modified CPU to 4.
Modified RAM to 8G.
Modified SCSI From VMWare Paravirtual to LSI Logic Parallel
Added New HD, Thick Provision Lazy Zeroed, ext 4 filesystem


Added these to Adv. Config on VM Server:
tools.syncTime FALSE
tools.synchronize.restore FALSE
time.synchronize.resume.disk FALSE
time.synchronize.continue FALSE
time.synchronize.shrink FALSE


Turned Off Ubuntu Disk I/O scheduling:
Edited  GRUB_CMDLINE_DEFAULT_LINUX "elevator-noop" to /etc/default/grub
update-grub
reboot


Ran same copy test on both Server1 Ubuntu 14 (Unmodified) and Server2 Ubuntu 23 (Modified with recommended changes).
Server1 Ubuntu 14:
time for ((i = 0 ; i < 10 ; i++ )) ; do cp ubuntu-20.04.6-live-server-amd64.iso test.iso ; rm test.iso ; done
```

real    0m23.759s
user    0m0.100s
sys     0m15.676s

```


On Server2 Ubuntu 23:
time for ((i = 0 ; i < 10 ; i++ )) ; do cp ubuntu-20.04.6-live-server-amd64.iso test.iso ; rm test.iso ; done
```

real    0m44.284s
user    0m0.015s
sys     0m43.078s

```


Sadly, the file copy slow performance on Ubuntu 23 remains.

---

### Post by sthoreson on 2024-02-13
Server1 has 4G RAM.
I Increased Server2 to 8G RAM.
There appears to be a big difference in swapd, si, so, and bi columns between the 2 Servers.

Server1 Ubuntu 14:
```

(vmstat 1 60 &) ; dd if=/dev/zero of=/d01/testfile.txt bs=1G count=1 oflag=dsync
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 1  0     60 1273868 135280 2501932    0    0     5   115   60   13  0  0 100  0  0
 1  0     60 1500572 135280 1824896    0    0     0     0  269  177  0 100  0  0  0
 1  0     60 973368 135280 1824896    0    0     0     0  280   74  0 100  0  0  0
 1  0     60 515656 135288 2218964    0    0     0 196608  439   92  1 99  0  0  0
 1  0     60 131324 135304 2591300    0    0     0 393216  734  148  0 100  0  0  0
 0  1     60 139864 135316 2576032    0    0     0 358400  493  140  0 96  0  4  0
1+0 records in
1+0 records out
1073741824 bytes (1.1 GB) copied, 5.21418 s, 206 MB/s

```


Server2 Ubuntu 23:
```

(vmstat 1 60 &) ; dd if=/dev/zero of=/d01/testfile.txt bs=1G count=1 oflag=dsync
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 2  0  50852 207700  12904 122840  521  525  5583  7248  295    0  0  1 98  1  0
 3  0 184224 102920    348  43824   92 133580   296 133580 22865  875  0 39 59  2  0
 3  1 424012 103876    636  38432  596 238916  4136 238916 37241 1952  0 53 39  7  0
 3  0 639708 104340    420  37032  436 220180  3288 220180 36887 1910  0 54 40  6  0
 4  0 878972 107732    420  36604  132 237280  3124 237280 37089 1339  0 49 47  3  0
 2  0 962164 119016    640  73812 33940 85992 38516 118160 3980 3008  0 22 60 18  0
 2  0 1034856 185320    652  43216 38824 73076 39128 108864 5089 2865  0 24 61 15  0
 1  1 1049760 148332    652  48900 45084 14968 45084 60840 2567 3116  0 15 70 14  0
 1  1 1096960 151120    480  55172 39656 47524 39656 89388 3666 2862  0 20 65 15  0
 1  1 1104664 121464    420  46140 46448 7728 49396 52640 2970 3502  0 18 68 14  0
 1  1 1106984 147008    788  58696 41956 2636 43972 42080 3773 3156  0 17 68 15  0
 2  1 1106984 162136    804  66068 43176   28 43184 43676 3564 3101  0 17 69 14  0
 1  1 1106728 179980    788  45284 42304  104 49092 39252 3312 3507  0 20 64 16  0
 1  1 1106728 152632    372  51740 44204    0 44204 44324 3599 3189  0 16 70 14  0
 2  0 1106984 135924    380  36940 43476  436 43740 47088 3577 3208  0 16 70 15  0
 2  1 1106984 146004    644  36512 44012   92 45808 43672 3818 3376  0 17 69 15  0
 1  1 1106984 119132    444  81960 44360    0 44576 41364 3591 3118  0 15 70 15  0
 2  1 1106984 177848    416  36396 46768   20 46768 48704 3890 3419  0 18 68 14  0
 2  0 1106984 154676    556  42048 44968   92 45472 44576 3528 3334  0 18 70 13  0
 1  1 1106984 134320    452  41876 46276  124 46276 46648 2271 3356  0 16 71 13  0
 2  0 1106984 198456    532  45508 46260    0 47744 44892 2493 3410  0 19 68 14  0
 2  1 1106984 142304    532  54776 46552   32 46552 47620 2122 3346  0 14 72 14  0
 2  1 1106984 127020    404  57692 45336    0 45696 43252 2401 3287  0 16 71 13  0
 1  1 1106984 141004    392  43176 46388   20 46644 46748 2347 3444  0 16 71 14  0
 1  1 1106984 139524    384  53620 45912   52 46128 46548 2312 3271  0 18 69 13  0
 2  0 1106984 122832    480  72520 47028    0 48352 45284 2940 3372  0 17 69 14  0
 6  0 1106728 148052    412  50348 47556    0 48132 48716 3647 3255  0 18 69 14  0
 2  0 1106728 161824    400  42168 45056   32 45232 43156 3627 3133  0 16 69 15  0
1+0 records in
1+0 records out
1073741824 bytes (1.1 GB, 1.0 GiB) copied, 28.0894 s, 38.2 MB/s

```

---

### Post by MAFoElffen on 2024-02-13
I do not use dd for my i/o benchmarks.

Though saying that, with your command on my 22.04.3 server, using:
```

(vmstat 1 60 &) ; dd if=/dev/zero of=./testfile.txt bs=1G count=1 oflag=dsync

```
kpool
```

procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 1  0      0 59025772  16972 1483196    0    0   243    17    0    0  0  0 100  0  0
1+0 records in
1+0 records out
1073741824 bytes (1.1 GB, 1.0 GiB) copied, 0.467651 s, 2.3 GB/s
 0  0      0 58958896  16972 1483196    0    0     0  7160 1784 5053  0  6 94  0  0
 0  0      0 58959680  16972 1483196    0    0     0     0  576 1626  0  0 100  0  0
 0  0      0 58959680  16972 1483196    0    0     0   136  638 1727  0  0 100  0  0
 0  0      0 58959680  16972 1483196    0    0     0     0  640 1655  0  0 100  0  0
 0  0      0 58959680  16972 1483196    0    0     0   136  599 1681  0  0 100  0  0
 0  0      0 58977908  16972 1483196    0    0     0  4400  993 3026  0  0 100  0  0
 0  0      0 58977908  16972 1483196    0    0     0     0  610 1661  0  0 100  0  0
 0  0      0 58977908  16972 1483196    0    0     0   392  631 1800  0  0 100  0  0
 0  0      0 58977908  16972 1483196    0    0     0   136  610 1692  0  0 100  0  0
 0  0      0 58977908  16972 1483196    0    0     0     0  659 1669  0  0 100  0  0
 0  0      0 58977908  16972 1483196    0    0     0   136  582 1677  0  0 100  0  0
 0  0      0 58977908  16972 1483196    0    0     0     0  556 1662  0  0 100  0  0
 0  0      0 58977908  16972 1483196    0    0     0     0  647 1695  0  0 100  0  0
 0  0      0 58977780  16972 1483196    0    0   128   600  634 2147  0  0 100  0  0
 0  0      0 58977584  16972 1483196    0    0     0  9632 1101 3759  0  0 100  0  0
 0  0      0 58976204  16972 1483196    0    0     0     0  647 1744  0  0 100  0  0
 0  0      0 58972108  16972 1483196    0    0     0     0  626 1696  0  0 100  0  0
 0  0      0 58972108  16972 1483196    0    0     0   520  538 1602  0  0 100  0  0
 1  0      0 58972108  16972 1483196    0    0     0     0  656 1800  0  0 100  0  0
 0  0      0 58972108  16972 1483196    0    0     0     0  578 1701  0  0 100  0  0

```
datapool
```

procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 1  0      0 59032140  16972 1483052    0    0   243    17    0    0  0  0 100  0  0
1+0 records in
1+0 records out
1073741824 bytes (1.1 GB, 1.0 GiB) copied, 0.700268 s, 1.5 GB/s
 0  0      0 58973864  16972 1483052    0    0     0 217152 3840 17258  0  6 94  0  0
 0  0      0 58973676  16972 1483052    0    0     0   264  616 1754  0  0 100  0  0
 0  0      0 58973676  16972 1483052    0    0     0     0  567 1661  0  0 100  0  0
 0  0      0 58973676  16972 1483052    0    0     0     0  638 1713  0  0 100  0  0
 0  0      0 58979760  16972 1483052    0    0   128  1088  675 2348  0  0 100  0  0
 0  0      0 59004080  16972 1483052    0    0     0 10952 1094 3899  0  1 99  0  0
 0  0      0 59003068  16972 1483052    0    0     0     0  659 1781  0  0 100  0  0
 0  0      0 59003068  16972 1483052    0    0     0   136  611 1774  0  0 100  0  0
 0  0      0 59003068  16972 1483052    0    0     0     0  591 1808  0  0 100  0  0
 0  0      0 59002816  16972 1483052    0    0     0     0  608 1745  0  0 100  0  0
 0  0      0 59002816  16972 1483052    0    0     0     0  552 1731  0  0 100  0  0
 0  0      0 59002816  16972 1483052    0    0     0     0  581 1711  0  0 100  0  0
 0  0      0 59002816  16972 1483052    0    0     0     0  581 1760  0  0 100  0  0
 0  0      0 59002816  16972 1483052    0    0     0     0  571 1727  0  0 100  0  0
 0  0      0 59002816  16972 1483052    0    0     0   136  551 1699  0  0 100  0  0
 0  0      0 59002816  16972 1483052    0    0     0   136  632 1824  0  0 100  0  0
 0  0      0 59002816  16972 1483052    0    0     0   264  593 1716  0  0 100  0  0
 0  0      0 59002816  16972 1483052    0    0     0     0  536 1647  0  0 100  0  0
 0  0      0 59002816  16972 1483052    0    0     0     0  532 1629  0  0 100  0  0
 1  0      0 59002816  16972 1483052    0    0     0     0  554 1738  0  0 100  0  0

```
Now using what I do use to benchmark my i/o:
```

fio --name TEST_WRITE --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting && fio --name TEST_READ --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting

```
on kpool
```

TEST_WRITE: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST_WRITE: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=0): [f(1)][100.0%][w=1229MiB/s][w=1229 IOPS][eta 00m:00s]
TEST_WRITE: (groupid=0, jobs=1): err= 0: pid=861108: Tue Feb 13 07:53:00 2024
  write: IOPS=2098, BW=2098MiB/s (2200MB/s)(10.0GiB/4880msec); 0 zone resets
    slat (usec): min=96, max=3276, avg=426.75, stdev=290.89
    clat (nsec): min=1298, max=492662k, avg=14646886.37, stdev=27230294.44
     lat (usec): min=133, max=493306, avg=15074.17, stdev=27330.79
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    5], 10.00th=[    5], 20.00th=[    5],
     | 30.00th=[    5], 40.00th=[    6], 50.00th=[   13], 60.00th=[   17],
     | 70.00th=[   23], 80.00th=[   23], 90.00th=[   24], 95.00th=[   25],
     | 99.00th=[   31], 99.50th=[   33], 99.90th=[  489], 99.95th=[  489],
     | 99.99th=[  493]
   bw (  MiB/s): min= 1620, max= 2848, per=100.00%, avg=2211.50, stdev=380.69, samples=9
   iops        : min= 1620, max= 2848, avg=2211.22, stdev=380.52, samples=9
  lat (usec)   : 2=0.01%, 10=0.03%, 100=0.01%, 250=0.01%, 500=0.04%
  lat (usec)   : 750=0.04%, 1000=0.04%
  lat (msec)   : 2=0.14%, 4=0.31%, 10=46.72%, 20=14.88%, 50=37.47%
  lat (msec)   : 500=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=545, max=545, avg=545.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  548],  5.00th=[  548], 10.00th=[  548], 20.00th=[  548],
     | 30.00th=[  548], 40.00th=[  548], 50.00th=[  548], 60.00th=[  548],
     | 70.00th=[  548], 80.00th=[  548], 90.00th=[  548], 95.00th=[  548],
     | 99.00th=[  548], 99.50th=[  548], 99.90th=[  548], 99.95th=[  548],
     | 99.99th=[  548]
  cpu          : usr=15.52%, sys=76.08%, ctx=1397, majf=14, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=2098MiB/s (2200MB/s), 2098MiB/s-2098MiB/s (2200MB/s-2200MB/s), io=10.0GiB (10.7GB), run=4880-4880msec
TEST_READ: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1)
TEST_READ: (groupid=0, jobs=1): err= 0: pid=861150: Tue Feb 13 07:53:02 2024
  read: IOPS=8455, BW=8456MiB/s (8867MB/s)(10.0GiB/1211msec)
    slat (usec): min=77, max=365, avg=117.13, stdev=25.77
    clat (nsec): min=1592, max=9939.1k, avg=3626639.49, stdev=691749.17
     lat (usec): min=105, max=10270, avg=3743.93, stdev=711.48
    clat percentiles (usec):
     |  1.00th=[ 2212],  5.00th=[ 3392], 10.00th=[ 3425], 20.00th=[ 3458],
     | 30.00th=[ 3490], 40.00th=[ 3523], 50.00th=[ 3523], 60.00th=[ 3556],
     | 70.00th=[ 3589], 80.00th=[ 3621], 90.00th=[ 3687], 95.00th=[ 3785],
     | 99.00th=[ 7308], 99.50th=[ 7373], 99.90th=[ 7832], 99.95th=[ 8979],
     | 99.99th=[ 9765]
   bw (  MiB/s): min= 7952, max= 8784, per=98.96%, avg=8368.00, stdev=588.31, samples=2
   iops        : min= 7952, max= 8784, avg=8368.00, stdev=588.31, samples=2
  lat (usec)   : 2=0.05%, 250=0.10%, 500=0.10%, 750=0.11%, 1000=0.14%
  lat (msec)   : 2=0.42%, 4=95.18%, 10=3.92%
  cpu          : usr=0.58%, sys=99.26%, ctx=14, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=8456MiB/s (8867MB/s), 8456MiB/s-8456MiB/s (8867MB/s-8867MB/s), io=10.0GiB (10.7GB), run=1211-1211msec

```
On datapool
```

TEST_WRITE: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]                          
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s] 
TEST_WRITE: (groupid=0, jobs=1): err= 0: pid=861190: Tue Feb 13 07:54:18 2024
  write: IOPS=872, BW=873MiB/s (915MB/s)(10.0GiB/11736msec); 0 zone resets
    slat (usec): min=121, max=1734, avg=407.70, stdev=273.42
    clat (nsec): min=1198, max=7534.3M, avg=35377576.92, stdev=412853630.65
     lat (usec): min=135, max=7535.0k, avg=35785.57, stdev=412876.22
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    5], 10.00th=[    6], 20.00th=[    6],
     | 30.00th=[    6], 40.00th=[    8], 50.00th=[   11], 60.00th=[   15],
     | 70.00th=[   16], 80.00th=[   18], 90.00th=[   21], 95.00th=[   31],
     | 99.00th=[   46], 99.50th=[   49], 99.90th=[ 7550], 99.95th=[ 7550],
     | 99.99th=[ 7550]
   bw (  MiB/s): min=  548, max= 4800, per=100.00%, avg=2215.33, stdev=1465.65, samples=9
   iops        : min=  548, max= 4800, avg=2215.33, stdev=1465.65, samples=9
  lat (usec)   : 2=0.02%, 4=0.03%, 250=0.03%, 500=0.04%, 750=0.07%
  lat (usec)   : 1000=0.03%
  lat (msec)   : 2=0.21%, 4=0.41%, 10=45.43%, 20=40.48%, 50=12.95%
  lat (msec)   : >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=446, max=446, avg=446.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  446],  5.00th=[  446], 10.00th=[  446], 20.00th=[  446],
     | 30.00th=[  446], 40.00th=[  446], 50.00th=[  446], 60.00th=[  446],
     | 70.00th=[  446], 80.00th=[  446], 90.00th=[  446], 95.00th=[  446],
     | 99.00th=[  446], 99.50th=[  446], 99.90th=[  446], 99.95th=[  446],
     | 99.99th=[  446]
  cpu          : usr=3.69%, sys=29.50%, ctx=13527, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=873MiB/s (915MB/s), 873MiB/s-873MiB/s (915MB/s-915MB/s), io=10.0GiB (10.7GB), run=11736-11736msec
TEST_READ: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1)
TEST_READ: (groupid=0, jobs=1): err= 0: pid=861236: Tue Feb 13 07:54:20 2024
  read: IOPS=8006, BW=8006MiB/s (8395MB/s)(10.0GiB/1279msec)
    slat (usec): min=77, max=511, avg=123.68, stdev=39.18
    clat (nsec): min=1240, max=9849.2k, avg=3827351.26, stdev=1161532.91
     lat (usec): min=111, max=10188, avg=3951.21, stdev=1197.20
    clat percentiles (usec):
     |  1.00th=[ 2212],  5.00th=[ 3326], 10.00th=[ 3359], 20.00th=[ 3425],
     | 30.00th=[ 3425], 40.00th=[ 3458], 50.00th=[ 3490], 60.00th=[ 3490],
     | 70.00th=[ 3523], 80.00th=[ 3589], 90.00th=[ 4686], 95.00th=[ 7308],
     | 99.00th=[ 7635], 99.50th=[ 7832], 99.90th=[ 8225], 99.95th=[ 8848],
     | 99.99th=[ 9634]
   bw (  MiB/s): min= 6522, max= 8928, per=96.49%, avg=7725.00, stdev=1701.30, samples=2
   iops        : min= 6522, max= 8928, avg=7725.00, stdev=1701.30, samples=2
  lat (usec)   : 2=0.04%, 4=0.01%, 250=0.10%, 500=0.10%, 750=0.10%
  lat (usec)   : 1000=0.14%
  lat (msec)   : 2=0.43%, 4=87.92%, 10=11.17%
  cpu          : usr=0.23%, sys=99.37%, ctx=1, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=8006MiB/s (8395MB/s), 8006MiB/s-8006MiB/s (8395MB/s-8395MB/s), io=10.0GiB (10.7GB), run=1279-1279msec

```
For benchmarking I/O, I use what I think shows a much clearer picture of what is going on. Just saying...

---

### Post by TheFu on 2024-02-13
Is the physical storage used by both the same?  Same connections, same controller, same physical disk?  I'm not talking about the virtual stuff.

---

### Post by sthoreson on 2024-02-13
I may have found the solution.  Currently working through tests for confirmation.
Basically, I boosted these and will post the final results.

#Modify Dirty Parameters on Server2 Ubuntu23:
echo 10 > /proc/sys/vm/dirty_background_ratio
echo 20 > /proc/sys/vm/dirty_ratio
echo 3000 > /proc/sys/vm/dirty_expire_centisecs
echo 500 > /proc/sys/vm/dirty_writeback_centisecs
echo $((64*1024*1024)) | sudo tee /proc/sys/vm/dirty_background_bytes
echo $((512*1024*1024)) | sudo tee /proc/sys/vm/dirty_bytes
sync; echo 3 > /proc/sys/vm/drop_caches

---

### Post by sthoreson on 2024-02-13
The issue is not resolved.
I am now working through using your latest suggestion for a clearer benchmark.
Thank you.

---

### Post by sthoreson on 2024-02-13
Yes, the 2 servers are on the same ESXi Host and both servers vmdk's are located on the same physical disks.
I have been monitoring the ESXI host using vscsiStats -l and esxtop to which I can post here if there is something I might have overlooked.
There are no special rules, configurations, priority groups, or reserved resources assigned to either box at the virtual level.

---

### Post by MAFoElffen on 2024-02-13
On a 14.04 VM:
```

TEST_WRITE: (g=0): rw=write, bs=1M-1M/1M-1M/1M-1M, ioengine=libaio, iodepth=32
fio-2.1.3
Starting 1 process
TEST_WRITE: (groupid=0, jobs=1): err= 0: pid=2884: Tue Feb 13 08:34:27 2024
  write: io=1024.0MB, bw=6918.1MB/s, iops=6918, runt=   148msec
    slat (usec): min=25, max=1372, avg=128.72, stdev=83.95
    clat (usec): min=474, max=14618, avg=4415.14, stdev=2057.45
     lat (usec): min=588, max=15097, avg=4544.06, stdev=2072.32
    clat percentiles (usec):
     |  1.00th=[ 1416],  5.00th=[ 3344], 10.00th=[ 3440], 20.00th=[ 3536],
     | 30.00th=[ 3600], 40.00th=[ 3664], 50.00th=[ 3792], 60.00th=[ 3984],
     | 70.00th=[ 4128], 80.00th=[ 4384], 90.00th=[ 6240], 95.00th=[ 8032],
     | 99.00th=[13888], 99.50th=[14144], 99.90th=[14400], 99.95th=[14656],
     | 99.99th=[14656]
    lat (usec) : 500=0.10%, 750=0.49%
    lat (msec) : 2=0.88%, 4=58.69%, 10=36.23%, 20=3.61%
  cpu          : usr=62.59%, sys=27.21%, ctx=21, majf=0, minf=8
  IO depths    : 1=0.1%, 2=0.2%, 4=0.4%, 8=0.8%, 16=1.6%, 32=97.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=99.9%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued    : total=r=0/w=1024/d=0, short=r=0/w=0/d=0
Run status group 0 (all jobs):
  WRITE: io=1024.0MB, aggrb=6918.1MB/s, minb=6918.1MB/s, maxb=6918.1MB/s, mint=148msec, maxt=148msec
Disk stats (read/write):
  vda: ios=0/987, merge=0/0, ticks=0/1280, in_queue=1308, util=56.00%
TEST_READ: (g=0): rw=read, bs=1M-1M/1M-1M/1M-1M, ioengine=libaio, iodepth=32
fio-2.1.3
Starting 1 process
TEST_READ: (groupid=0, jobs=1): err= 0: pid=2888: Tue Feb 13 08:34:27 2024
  read : io=1024.0MB, bw=6606.5MB/s, iops=6606, runt=   155msec
    slat (usec): min=24, max=929, avg=112.97, stdev=86.92
    clat (usec): min=435, max=23661, avg=4637.92, stdev=3753.76
     lat (usec): min=509, max=23763, avg=4751.25, stdev=3752.69
    clat percentiles (usec):
     |  1.00th=[ 1160],  5.00th=[ 1720], 10.00th=[ 2096], 20.00th=[ 2608],
     | 30.00th=[ 2928], 40.00th=[ 3152], 50.00th=[ 3408], 60.00th=[ 3600],
     | 70.00th=[ 4128], 80.00th=[ 5536], 90.00th=[ 8768], 95.00th=[13888],
     | 99.00th=[20352], 99.50th=[23680], 99.90th=[23680], 99.95th=[23680],
     | 99.99th=[23680]
    lat (usec) : 500=0.10%, 750=0.29%, 1000=0.20%
    lat (msec) : 2=8.11%, 4=59.57%, 10=23.14%, 20=7.32%, 50=1.27%
  cpu          : usr=0.00%, sys=80.52%, ctx=80, majf=0, minf=8200
  IO depths    : 1=0.1%, 2=0.2%, 4=0.4%, 8=0.8%, 16=1.6%, 32=97.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=99.9%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued    : total=r=1024/w=0/d=0, short=r=0/w=0/d=0
Run status group 0 (all jobs):
   READ: io=1024.0MB, aggrb=6606.5MB/s, minb=6606.5MB/s, maxb=6606.5MB/s, mint=155msec, maxt=155msec
Disk stats (read/write):
  vda: ios=967/0, merge=0/0, ticks=3176/0, in_queue=3220, util=59.44%

```
Note that option '--io_size=' was not in the 14.04 version of fio, so was removed for that test...

On a Mantic VM:
```

mafoelffen@minatuar-02:~/Documents$ fio --name TEST_WRITE --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting && fio --name TEST_READ --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST_WRITE: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.35
Starting 1 process
TEST_WRITE: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [W(1)][25.0%][w=85.9MiB/s][w=85 IOPS][eta 00m:24s]
Jobs: 1 (f=1): [W(1)][41.9%][w=292MiB/s][w=292 IOPS][eta 00m:18s] 
Jobs: 1 (f=1): [W(1)][61.3%][w=338MiB/s][w=338 IOPS][eta 00m:12s] 
Jobs: 1 (f=1): [W(1)][78.1%][w=310MiB/s][w=310 IOPS][eta 00m:07s] 
Jobs: 1 (f=1): [W(1)][93.9%][w=381MiB/s][w=381 IOPS][eta 00m:02s] 
Jobs: 1 (f=1): [W(1)][100.0%][w=64.1MiB/s][w=64 IOPS][eta 00m:00s]
TEST_WRITE: (groupid=0, jobs=1): err= 0: pid=3492: Tue Feb 13 08:51:10 2024
  write: IOPS=318, BW=318MiB/s (334MB/s)(10.0GiB/32160msec); 0 zone resets
    slat (usec): min=100, max=1088.7k, avg=3063.82, stdev=43769.40
    clat (usec): min=2, max=1137.9k, avg=96870.10, stdev=235523.45
     lat (usec): min=156, max=1139.5k, avg=99933.91, stdev=238866.44
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    6], 10.00th=[    6], 20.00th=[    7],
     | 30.00th=[    8], 40.00th=[   11], 50.00th=[   15], 60.00th=[   21],
     | 70.00th=[   27], 80.00th=[   36], 90.00th=[  211], 95.00th=[  827],
     | 99.00th=[  995], 99.50th=[ 1020], 99.90th=[ 1116], 99.95th=[ 1133],
     | 99.99th=[ 1133]
   bw (  KiB/s): min=16384, max=1058816, per=100.00%, avg=486089.93, stdev=290007.48, samples=42
   iops        : min=   16, max= 1034, avg=474.69, stdev=283.22, samples=42
  lat (usec)   : 4=0.05%, 250=0.01%, 500=0.04%, 750=0.07%, 1000=0.03%
  lat (msec)   : 2=0.20%, 4=0.43%, 10=37.58%, 20=21.40%, 50=22.85%
  lat (msec)   : 100=2.44%, 250=6.74%, 500=0.30%, 750=0.52%, 1000=6.44%
  lat (msec)   : 2000=0.92%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=626603k, max=626603k, avg=626603257.00, stdev= 0.00
    sync percentiles (msec):
     |  1.00th=[  625],  5.00th=[  625], 10.00th=[  625], 20.00th=[  625],
     | 30.00th=[  625], 40.00th=[  625], 50.00th=[  625], 60.00th=[  625],
     | 70.00th=[  625], 80.00th=[  625], 90.00th=[  625], 95.00th=[  625],
     | 99.00th=[  625], 99.50th=[  625], 99.90th=[  625], 99.95th=[  625],
     | 99.99th=[  625]
  cpu          : usr=1.31%, sys=4.82%, ctx=17751, majf=13, minf=10
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=318MiB/s (334MB/s), 318MiB/s-318MiB/s (334MB/s-334MB/s), io=10.0GiB (10.7GB), run=32160-32160msec
TEST_READ: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.35
Starting 1 process
Jobs: 1 (f=1): [R(1)][83.3%][r=2216MiB/s][r=2216 IOPS][eta 00m:01s]
TEST_READ: (groupid=0, jobs=1): err= 0: pid=3559: Tue Feb 13 08:51:15 2024
  read: IOPS=2128, BW=2128MiB/s (2232MB/s)(10.0GiB/4811msec)
    slat (usec): min=173, max=4160, avg=453.57, stdev=146.60
    clat (nsec): min=1494, max=49629k, avg=13964383.67, stdev=3321470.00
     lat (usec): min=175, max=51683, avg=14417.95, stdev=3412.82
    clat percentiles (usec):
     |  1.00th=[ 6718],  5.00th=[10683], 10.00th=[12649], 20.00th=[13042],
     | 30.00th=[13173], 40.00th=[13304], 50.00th=[13566], 60.00th=[13698],
     | 70.00th=[14091], 80.00th=[14877], 90.00th=[16188], 95.00th=[17171],
     | 99.00th=[26346], 99.50th=[32900], 99.90th=[47449], 99.95th=[49021],
     | 99.99th=[49021]
   bw (  MiB/s): min= 1412, max= 2310, per=99.24%, avg=2112.38, stdev=274.00, samples=9
   iops        : min= 1412, max= 2310, avg=2112.22, stdev=274.00, samples=9
  lat (usec)   : 2=0.03%, 4=0.02%, 250=0.05%, 500=0.05%, 750=0.05%
  lat (usec)   : 1000=0.05%
  lat (msec)   : 2=0.14%, 4=0.26%, 10=3.99%, 20=92.83%, 50=2.53%
  cpu          : usr=0.94%, sys=91.62%, ctx=10394, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2128MiB/s (2232MB/s), 2128MiB/s-2128MiB/s (2232MB/s-2232MB/s), io=10.0GiB (10.7GB), run=4811-4811msec

```
Hmmm. I do see a difference, at minimum specs allocated. Both of those VM's vdisks are on the same Host, on the same storage pool (same disks)...

I confirm that I see a difference, but I can't explain why.

---

### Post by sthoreson on 2024-02-13
Using fio to get a more detailed Benchmark:
fio --name TEST_WRITE --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting && fio --name TEST_READ --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
```

TEST_WRITE: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.35
Starting 1 process
Jobs: 1 (f=1): [W(1)][21.9%][w=283MiB/s][w=283 IOPS][eta 00m:25s]
Jobs: 1 (f=1): [W(1)][39.4%][w=280MiB/s][w=280 IOPS][eta 00m:20s]
Jobs: 1 (f=1): [W(1)][55.9%][w=274MiB/s][w=274 IOPS][eta 00m:15s]
Jobs: 1 (f=1): [W(1)][73.5%][w=302MiB/s][w=302 IOPS][eta 00m:09s]
Jobs: 1 (f=1): [W(1)][91.2%][w=220MiB/s][w=220 IOPS][eta 00m:03s]
Jobs: 1 (f=1): [W(1)][100.0%][w=287MiB/s][w=287 IOPS][eta 00m:00s]
TEST_WRITE: (groupid=0, jobs=1): err= 0: pid=1780: Tue Feb 13 17:10:47 2024
  write: IOPS=295, BW=296MiB/s (310MB/s)(10.0GiB/34622msec); 0 zone resets
    slat (usec): min=85, max=130670, avg=217.52, stdev=2591.22
    clat (msec): min=8, max=333, avg=107.82, stdev=32.53
     lat (msec): min=8, max=333, avg=108.03, stdev=32.43
    clat percentiles (msec):
     |  1.00th=[   23],  5.00th=[   56], 10.00th=[   78], 20.00th=[   89],
     | 30.00th=[   94], 40.00th=[   99], 50.00th=[  103], 60.00th=[  109],
     | 70.00th=[  118], 80.00th=[  131], 90.00th=[  148], 95.00th=[  167],
     | 99.00th=[  199], 99.50th=[  215], 99.90th=[  288], 99.95th=[  317],
     | 99.99th=[  330]
   bw (  KiB/s): min=219136, max=584558, per=100.00%, avg=302971.26, stdev=51309.14, samples=69
   iops        : min=  214, max=  570, avg=295.84, stdev=50.04, samples=69
  lat (msec)   : 10=0.19%, 20=0.72%, 50=2.46%, 100=42.12%, 250=54.36%
  lat (msec)   : 500=0.16%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=233773k, max=233773k, avg=233773249.00, stdev= 0.00
    sync percentiles (msec):
     |  1.00th=[  234],  5.00th=[  234], 10.00th=[  234], 20.00th=[  234],
     | 30.00th=[  234], 40.00th=[  234], 50.00th=[  234], 60.00th=[  234],
     | 70.00th=[  234], 80.00th=[  234], 90.00th=[  234], 95.00th=[  234],
     | 99.00th=[  234], 99.50th=[  234], 99.90th=[  234], 99.95th=[  234],
     | 99.99th=[  234]
  cpu          : usr=2.32%, sys=2.75%, ctx=9498, majf=0, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32


Run status group 0 (all jobs):
  WRITE: bw=296MiB/s (310MB/s), 296MiB/s-296MiB/s (310MB/s-310MB/s), io=10.0GiB (10.7GB), run=34622-34622msec


Disk stats (read/write):
  sdc: ios=0/17646, merge=0/592, ticks=0/1852003, in_queue=1852002, util=99.71%
TEST_READ: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.35
Starting 1 process
Jobs: 1 (f=1): [R(1)][70.0%][r=889MiB/s][r=889 IOPS][eta 00m:03s]
Jobs: 1 (f=1): [R(1)][100.0%][r=922MiB/s][r=921 IOPS][eta 00m:00s]
TEST_READ: (groupid=0, jobs=1): err= 0: pid=1787: Tue Feb 13 17:10:58 2024
  read: IOPS=959, BW=960MiB/s (1006MB/s)(10.0GiB/10669msec)
    slat (usec): min=78, max=5005, avg=143.03, stdev=213.65
    clat (usec): min=10039, max=78712, avg=33013.74, stdev=5933.09
     lat (usec): min=10569, max=78793, avg=33156.77, stdev=5898.63
    clat percentiles (usec):
     |  1.00th=[16581],  5.00th=[27395], 10.00th=[28443], 20.00th=[28705],
     | 30.00th=[29230], 40.00th=[30016], 50.00th=[31327], 60.00th=[33162],
     | 70.00th=[35914], 80.00th=[38011], 90.00th=[40109], 95.00th=[41157],
     | 99.00th=[52167], 99.50th=[61080], 99.90th=[67634], 99.95th=[71828],
     | 99.99th=[76022]
   bw (  KiB/s): min=821248, max=1134592, per=99.99%, avg=982734.14, stdev=101143.49, samples=21
   iops        : min=  802, max= 1108, avg=959.62, stdev=98.68, samples=21
  lat (msec)   : 20=1.68%, 50=96.81%, 100=1.51%
  cpu          : usr=0.39%, sys=13.31%, ctx=7255, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32


Run status group 0 (all jobs):
   READ: bw=960MiB/s (1006MB/s), 960MiB/s-960MiB/s (1006MB/s-1006MB/s), io=10.0GiB (10.7GB), run=10669-10669msec


Disk stats (read/write):
  sdc: ios=12573/3, merge=3058/1, ticks=399820/169, in_queue=399989, util=99.23%

```

---

### Post by sthoreson on 2024-02-13
Yes, this is a head scratcher.  Process of elimination has been quite extensive but still have not found the root cause.  I have reviewed the Ubuntu online documentation to search for any notes, updates, vm specific required changes, or if NFS3 is simply the root of the problem in the way Ubuntu updated versions interacts/writes/caches/etc... with an nfs filesystem.  I currently trying to get access to an esxi host and datastore that isn't being used within my company to create a test case where nfs is updated to the latest version.  But this is proving to be a challenge due to cost and all current resources being utilized.
Thus, am hopeful for a temporary solution to this issue until I can get the backend upgraded which could take a long time.

Any other suggestions are much appreciated and thank you for your time thus far in attempting to help me.

---

### Post by MAFoElffen on 2024-02-13
Okay... I found where my difference was. I spun u[p a new Mantic server VM. I ran it on an existing, and when I looked at it, it was on an encrypted filesystem. Not a fair comparison. Dang.

I also removed --io_size from my Mantic VM run, so that the commands were the same for both:
```

TEST_WRITE: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.35
Starting 1 process
TEST_WRITE: (groupid=0, jobs=1): err= 0: pid=5687: Tue Feb 13 18:31:26 2024
  write: IOPS=3531, BW=3531MiB/s (3703MB/s)(1024MiB/290msec); 0 zone resets
    slat (usec): min=68, max=1872, avg=279.60, stdev=147.21
    clat (usec): min=131, max=16588, avg=8583.53, stdev=2666.41
     lat (usec): min=393, max=16843, avg=8863.14, stdev=2732.06
    clat percentiles (usec):
     |  1.00th=[ 5080],  5.00th=[ 6783], 10.00th=[ 6849], 20.00th=[ 6980],
     | 30.00th=[ 7046], 40.00th=[ 7177], 50.00th=[ 7308], 60.00th=[ 7635],
     | 70.00th=[ 8160], 80.00th=[11994], 90.00th=[13173], 95.00th=[14222],
     | 99.00th=[15533], 99.50th=[15795], 99.90th=[15926], 99.95th=[16581],
     | 99.99th=[16581]
  lat (usec)   : 250=0.10%, 500=0.10%, 1000=0.10%
  lat (msec)   : 2=0.20%, 4=0.29%, 10=77.83%, 20=21.39%
  cpu          : usr=18.69%, sys=77.85%, ctx=964, majf=0, minf=13
  IO depths    : 1=0.1%, 2=0.2%, 4=0.4%, 8=0.8%, 16=1.6%, 32=97.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=99.9%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,1024,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32
Run status group 0 (all jobs):
  WRITE: bw=3531MiB/s (3703MB/s), 3531MiB/s-3531MiB/s (3703MB/s-3703MB/s), io=1024MiB (1074MB), run=290-290msec
Disk stats (read/write):
    dm-0: ios=0/574, merge=0/0, ticks=0/144, in_queue=144, util=58.06%, aggrios=0/8192, aggrmerge=0/0, aggrticks=0/1791, aggrin_queue=1790, aggrutil=66.52%
  sda: ios=0/8192, merge=0/0, ticks=0/1791, in_queue=1790, util=66.52%

TEST_READ: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.35
Starting 1 process
TEST_READ: (groupid=0, jobs=1): err= 0: pid=5691: Tue Feb 13 18:31:26 2024
  read: IOPS=3835, BW=3835MiB/s (4022MB/s)(1024MiB/267msec)
    slat (usec): min=149, max=406, avg=258.00, stdev=35.20
    clat (usec): min=84, max=10964, avg=7905.76, stdev=938.24
     lat (usec): min=350, max=11366, avg=8163.76, stdev=948.02
    clat percentiles (usec):
     |  1.00th=[ 2704],  5.00th=[ 7439], 10.00th=[ 7504], 20.00th=[ 7570],
     | 30.00th=[ 7701], 40.00th=[ 7832], 50.00th=[ 7898], 60.00th=[ 8029],
     | 70.00th=[ 8225], 80.00th=[ 8356], 90.00th=[ 8717], 95.00th=[ 8717],
     | 99.00th=[ 9765], 99.50th=[10421], 99.90th=[10814], 99.95th=[10945],
     | 99.99th=[10945]
  lat (usec)   : 100=0.10%, 500=0.10%, 750=0.10%, 1000=0.10%
  lat (msec)   : 2=0.39%, 4=0.78%, 10=97.56%, 20=0.88%
  cpu          : usr=1.13%, sys=98.50%, ctx=10, majf=0, minf=8206
  IO depths    : 1=0.1%, 2=0.2%, 4=0.4%, 8=0.8%, 16=1.6%, 32=97.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=99.9%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=1024,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32
Run status group 0 (all jobs):
   READ: bw=3835MiB/s (4022MB/s), 3835MiB/s-3835MiB/s (4022MB/s-4022MB/s), io=1024MiB (1074MB), run=267-267msec
Disk stats (read/write):
    dm-0: ios=555/0, merge=0/0, ticks=184/0, in_queue=184, util=61.29%, aggrios=8192/0, aggrmerge=0/0, aggrticks=1223/0, aggrin_queue=1223, aggrutil=65.23%
  sda: ios=8192/0, merge=0/0, ticks=1223/0, in_queue=1223, util=65.23%

```

So the results for 14.04:
```

  WRITE: io=1024.0MB, aggrb=6918.1MB/s, minb=6918.1MB/s, maxb=6918.1MB/s, mint=148msec, maxt=148msec
  READ: io=1024.0MB, aggrb=6606.5MB/s, minb=6606.5MB/s, maxb=6606.5MB/s, mint=155msec, maxt=155msec

```
And for 23.10:
```

  WRITE: bw=3531MiB/s (3703MB/s), 3531MiB/s-3531MiB/s (3703MB/s-3703MB/s), io=1024MiB (1074MB), run=290-290msec
  READ: bw=3835MiB/s (4022MB/s), 3835MiB/s-3835MiB/s (4022MB/s-4022MB/s), io=1024MiB (1074MB), run=267-267msec

```
Yes, it shows as faster with 23.10, by those results... That is on the same host & storage pool for both, with 23.10 using 'levator-noop' as a boot parameter.

---

### Post by TheFu on 2024-02-13
If you just mount with _-t nfs_ option, you get nfsv4 in Debian-based OSes.  The only way I'd expect NFSv3 to be used is if the client specifically requests it or if the NFS server is on hardware from 2005.

---

### Post by sthoreson on 2024-02-13
Please confirm for my understanding from your results that 23.10 is faster?  For the 14.4 server, mint/maxt = 148/155ms and the 23.10 server, run=290/267ms.
For my continued education, in the output, what is showing 23 is faster than 14?

---

### Post by MAFoElffen on 2024-02-13
Dang. The different version of fio between the two are in a different output format from each other!!! Hmmm.

Just going off the times:
WRITE: maxt=148msec
WRITE: run=290-290msec
=================
14.04 was 19% faster on writes...

READ:  maxt=155msec
READ:  run=267-267msec
================
14.04 was 14% faster on Reads.

Dang.

---

### Post by TheFu on 2024-02-14
Mike, there's much more security in the kernel now as well as a number of those CPU security flaws that have been discovered and mitigated since 14.04.  Some of the mitigations had 20-30% DBMS performance impacts.

---

### Post by MAFoElffen on 2024-02-14
+1 --- Thank you. Yes. Sorry/Got distracted looking at the numbers. LOL. That would make up for that. I did mention that it has a lot more going on with it.

I was going to say, even though it is somewhat slower. It really doesn't really matter. It would be insane to think that running 14.04 would be safe or a good idea. It has been EOL for about 5 years now. 

I just helped a municipality to upgrade their closed, open-gaped embedded system from 14.04 to 18.04, where it dead-ended them, because the application they had on them only ran on 32bit. But that bought them some time, to get a 64bit application written.

There is nothing in 14.04.x that couldn't be migrated to something more current. And if you still can't get it all the way to 'current support', it shouldn't be on something that has connections to anything. Big Period.

There is not much you can do with VMware vSphere to optimize disk I/O under the covers. It takes over the very limited hardware it supports in it's own way (their way). And even though I used to beta test for VMware, and I have licenses for vSphere/vCenter from my past endeavors with them... BroadCom buying  VMware and doing away with perpetual licensing, free versions of ESXi,  and other things... Their market is in flux right now with a lot of unknowns. The initial direction they are heading is... I leave that unsaid right now. I may not be testing for them anymore, and saying  my goodbyes. Their loss. But that is okay. 

My first choice personally  has always been with using KVM. You can do more with KVM. It is a lot more  flexible, adaptable, and tunable. And it is opensource. It is the base  for more of the Virtual Host market than anything else in the World. For very good reason. If you want more from what you are doing... And not end up in a dead-end with your hands-tied, I challenge you to try and learn KVM.

You are only looking at disk I/O. Deal with what is currently supported on current, modern hardware, on and for currently supported OS'es. If disk I/O is your only requirement (besides the system being secure and system running faster overall), then optimize your disk performance. As TheFu touched on, I use SSD's and PCIe M.2 NVME's in ZFS RAIDZ2 & RAIDZ3 with hardware SLOG and L2ARC caches optimized to the arrays. Even being a COW filesystem, I don't think you will find anything faster than that for Disk I/O performance. I can lose 2 disks, keep live, and not notice the performance hit unless I keep looking at my logs and alerts. It's honestly that fast.

You mentioned performance in VM's. ZFS RAIDZ is what I put my VM Storage pools onto. I optimize the block and record sizes to run VMs. They run faster in virtual, than most machines on metal. The performance is wild. Of course there is more 'to that', in the tuning and optimization. It is not just throw a switch and go. There are things that have to work together for that to happen.

---

### Post by sthoreson on 2024-02-14
Well... I increased all the dirty values and confirm the issue is resolved.  
Part of the issue was that the use of the time in a loop was not correctly showing direct copy results after any change was made to the kernel parameters.
Here is the actual results now and a simple file copy is lightning fast again using a simple time cp command (without the loop):

Server2 Ubunt23: time cp ubuntu-20.04.6-live-server-amd64.iso test.iso
```

real    0m2.542s
user    0m0.024s
sys     0m2.512s

```

I apologize to you guys for wasting so much of your time and is my fault for not remembering the basics of what a loop does that attributed to the skewed time results from earlier in this thread.
Again, I thank you for assisting me with resolving this issue.

---

### Post by MAFoElffen on 2024-02-14
No problem at all. It keeps things entertaining! LOL I need a distraction from time-to-time.

Before you go and duck out:
So it still begs for me to ask: Why 14.04? What is your use case? Are your plans to moving something from 14.04 to 23.10?

Then why to an interim version of Server (23.10), and not to an LTS version (22.04 -> 24.04)?

Please feed my curiosity...

I'm on the Server team, so I have to ask these questions for my own "keep-in-touch" reasons to help push directions.

---

### Post by sthoreson on 2024-02-14
Here is the final resolution notes:
vi /etc/sysctl.conf
Add or Modify:
vm.dirty_background_ratio = 10
vm.dirty_ratio = 20
vm.dirty_expire_centisecs = 3000
vm.dirty_writeback_centisecs = 500
vm.dirty_background_bytes = 67108864
vm.dirty_bytes = 536870912


sysctl -p

---

### Post by TheFu on 2024-02-14
Please ----

"Thread Tools" button ---> "SOLVED"

---

### Post by sthoreson on 2024-02-14
The long story short:
Initially a server was required years ago:  Installed Ubuntu 14.04
The application to which it was create for required Ubuntu 20x
We installed a new server with Ubuntu 20x and the file copies were slow.
For this test, I installed the latest Ubuntu 23 on a clean server in hopes to find the issue.

Basically, the new Ubuntu 20x server was supposed to be replace the existing one.

Thanks again for your help and patience.

---

### Post by MAFoElffen on 2024-02-14
Glad you found your answer. Thank you for sharing the use case. 20.04 goes EOL in one year. I would really look at migrating to 22.04 and get ahead of that. Especially for a production server. Most of my pushes for security are still currently for 22.04.3.

As TheFu mentioned, please select the "Thread Tools" link on the upper right of the first page of this thread, then select "Solved". That will help other Users to find what worked for you to help with their similar issues.

---

