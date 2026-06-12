---
title: "Webserver crashes on a Saturday due to high disk IO"
date: 2018-09-05
forum: Server Platforms
---

### Post by webmuppet57 on 2018-09-05
I've an odd problem on a Serverpilot VPS running Ubuntu 16.04. It's  fine through the week - responsive and not under stress hosting about 60  low traffic Wordpress sites. Then on Saturday between 830-6pm  occasionally the server runs out of resources and crashes. Once the  server is rebooted through the VPS control panel then the sites all come  back again and are fine for at least 1 hour. It maybe happens 1-5 times  through the day. I've not been able to consistently watch top / iotop  during a Saturday so I can't see what is happening second to second but  the VPS provider says the disk is seeing high read/write on and off on  the day of the crashes and the one time I did manage to watch the top  command I could see the requests for pages from the webserver in the  list but not seemingly being served as they didn't drop off but no process seemed to be sitting solidly at the top. 

I think  each request sits on the list consuming a small amount of processor and  memory but over time it gradually builds up until the server runs out of  memory and the CPU is maxed and all I can do is reboot through the VPS  control panel. Nothing seemed to be at the top taking large amounts of  processor - I think it was some process that was thrashing the disk but  not the CPU. It's happened 3 weekends in a row after being stable for  around 6 months. It also happened one single Sunday morning at 830am.

 I have checked cron and can't see anything specifically running on a  Saturday and I'm fairly confident it isn't a traffic issue. It could  definitely be some rogue Wordpress plugin doing something but with 60  sites I'm at a loss how to easily track that down.

I need some tool that will watch the disk usage and record what is  happening so I can view a logfile after the crash and see what process /  webserver site pool was hammering the disk. I installed SAR from  SYSSTAT but I can't seem to get stats on which webserver site pool is  thrashing the disk, just that the disk is under pressure. It's important that I can see the website pool or what matches the process id or else I can't tell which site is causing the problem.

Any help would be much appreciated, it's ruining my weekends!

This is the error I see in messages:
```
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264544] NMI watchdog: BUG: soft lockup - CPU#4 stuck for 24s! [php-fpm:3695]
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264624] Modules linked in: ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs i2c_piix4 input_leds joydev serio_raw mac_hid ip6t_REJECT nf_reject_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables ib_iser nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp rdma_cm iw_cm ib_cm ib_sa nf_nat ib_mad nf_conntrack_ftp nf_conntrack ib_core iptable_filter ip_tables ib_addr x_tables iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi autofs4 btrfs raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear hid_generic usbhid hid cirrus ttm drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops psmouse drm pata_acpi floppy
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264682] CPU: 4 PID: 3695 Comm: php-fpm Not tainted 4.4.0-134-generic #160-Ubuntu
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264684] Hardware name: Red Hat KVM, BIOS 0.5.1 01/01/2007
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264686] task: ffff88018c6a1980 ti: ffff88011da84000 task.ti: ffff88011da84000
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264688] RIP: 0010:[<ffffffff81410729>]  [<ffffffff81410729>] copy_page_regs+0x49/0xe0
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264695] RSP: 0000:ffff88011da87d50  EFLAGS: 00010206
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264697] RAX: 0000000000000000 RBX: 0000000000000000 RCX: 000000000000003a
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264699] RDX: 0000000000000000 RSI: ffff8800c6e73000 RDI: ffff880104335000
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264701] RBP: ffff88011da87e00 R08: 0000000000000000 R09: 0000000000000000
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264703] R10: 0000000000000000 R11: 0000000000000000 R12: 0000000000000000
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264705] R13: ffff880007153398 R14: 00000000031b9cc0 R15: ffff88018c6a1980
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264708] FS:  00007f41b9d97740(0000) GS:ffff880196d00000(0000) knlGS:0000000000000000
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264710] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264712] CR2: 00007f41b9da7000 CR3: 000000011dbfa000 CR4: 0000000000000670
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264723] Stack:
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264725]  ffff88018c6a1980 00000000031c0000 ffffffff812027f8 80000000c6e008e5
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264728]  ffff88011da53c80 ffff88019db64000 ffff88011db64000 ffff880007153000
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264731]  ffff880007153000 ffffea00031b8000 0000160000000000 ffff88011db64d40
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264734] Call Trace:
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264740]  [<ffffffff812027f8>] ? do_huge_pmd_wp_page+0x318/0xb90
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264745]  [<ffffffff811c7805>] handle_mm_fault+0x965/0x19b0
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264750]  [<ffffffff8106da51>] __do_page_fault+0x1a1/0x410
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264753]  [<ffffffff8106dce2>] do_page_fault+0x22/0x30
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264758]  [<ffffffff81857c98>] page_fault+0x28/0x30
Sep  1 12:10:25 2536-15913-2558 kernel: [532719.264760] Code: 00 00 48 ff c9 48 8b 06 48 8b 5e 08 48 8b 56 10 4c 8b 46 18 4c 8b 4e 20 4c 8b 56 28 4c 8b 5e 30 4c 8b 66 38 0f 18 8e 40 01 00 00 <48> 89 07 48 89 5f 08 48 89 57 10 4c 89 47 18 4c 89 4f 20 4c 89
```

---

### Post by SeijiSensei on 2018-09-05
You can do some [tuning in Apache]("https://httpd.apache.org/docs/2.4/misc/perf-tuning.html"), but I don't know if it will help.

> The single biggest hardware issue affecting webserver performance is RAM. A webserver should never ever have to swap, as swapping increases the latency of each request beyond a point that users consider "fast enough". This causes users to hit stop and reload, further increasing the load. You can, and should, control the MaxRequestWorkers setting so that your server does not spawn so many children that it starts swapping. The procedure for doing this is simple: determine the size of your average Apache process, by looking at your process list via a tool such as top, and divide this into your total available memory, leaving some room for other processes.

Beyond that the rest is mundane: get a fast enough CPU, a fast enough network card, and fast enough disks, where "fast enough" is something that needs to be determined by experimentation.

---

