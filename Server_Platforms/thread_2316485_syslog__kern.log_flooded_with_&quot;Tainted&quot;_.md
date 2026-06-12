---
title: "syslog / kern.log flooded with &quot;Tainted&quot; messages"
date: 2016-03-08
forum: Server Platforms
---

### Post by nwilson5 on 2016-03-08
I apologize if this should be directed elsewhere. I've seen it directed towards Postgres mailing lists, but it doesn't appear to be an issue specific to user software.

We have 4 servers of the same build. Every few weeks (at differing times) they get flooded with the below logs in syslog and kern.log to the point that the disk fills up to 100%. If I update/upgrade/reboot and clear out space, they are "OK" again (are not spamming the below errors in the logs). Until, a few weeks later when it happens again.

Any direction in figuring out what's going on would be appreciated. I could not find any BIOS upgrades available for this server. The fact that it happens to all 4 servers of the same build makes me think it unlikely to be the exact same hardware problem on each of them..

flooded in syslog with:
```
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123818] ------------[ cut here ]------------[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123820] WARNING: CPU: 9 PID: 14163 at /build/buildd/linux-3.13.0/net/core/dst.c:285 dst_release+0x45/0[/FONT]
[FONT=arial]x60()[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123821] Modules linked in: gpio_ich intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_[/FONT]
[FONT=arial]clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd serio_raw lpc_ich ipmi_si mac_hid i7core_edac edac_core shpc[/FONT]
[FONT=arial]hp lp parport raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq igb raid1 i2c_algo_bit raid0 dca multipa[/FONT]
[FONT=arial]th ptp ahci linear libahci pps_core[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123838] CPU: 9 PID: 14163 Comm: postgres Tainted: G        W I   3.13.0-46-generic #79-Ubuntu[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123839] Hardware name: HP ProLiant DL160 G6  , BIOS O33 07/01/2013[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123840]  0000000000000009 ffff88001697bb18 ffffffff817212c6 0000000000000000[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123843]  ffff88001697bb50 ffffffff810677dd ffff88090859b780 00000000fffffffe[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123846]  ffff88097a5e0000 0000000000000000 0000000000000000 ffff88001697bb60[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123848] Call Trace:[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123850]  [<ffffffff817212c6>] dump_stack+0x45/0x56[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123853]  [<ffffffff810677dd>] warn_slowpath_common+0x7d/0xa0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123855]  [<ffffffff810678ba>] warn_slowpath_null+0x1a/0x20[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123857]  [<ffffffff8162dc65>] dst_release+0x45/0x60[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123859]  [<ffffffff8160ec99>] sk_dst_check+0xb9/0xe0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123861]  [<ffffffff816c169f>] ip6_sk_dst_lookup_flow+0x2f/0x1b0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123864]  [<ffffffff816dc58e>] udpv6_sendmsg+0x61e/0xb10[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123866]  [<ffffffff810aaa18>] ? __wake_up_common+0x58/0x90[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123868]  [<ffffffff810aafd0>] ? __wake_up_sync_key+0x50/0x60[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123871]  [<ffffffff8160f40a>] ? sock_def_readable+0x3a/0x70[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123873]  [<ffffffff81693b44>] inet_sendmsg+0x64/0xb0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123876]  [<ffffffff81313bf7>] ? apparmor_socket_sendmsg+0x17/0x20[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123878]  [<ffffffff8160c7eb>] sock_sendmsg+0x8b/0xc0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123881]  [<ffffffff8172d354>] ? __do_page_fault+0x204/0x560[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123883]  [<ffffffff8160cd31>] SYSC_sendto+0x121/0x1c0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123885]  [<ffffffff8117e751>] ? remove_vma+0x71/0x90[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123887]  [<ffffffff81180667>] ? do_munmap+0x297/0x3b0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123890]  [<ffffffff8172d6ca>] ? do_page_fault+0x1a/0x70[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123892]  [<ffffffff8160d71e>] SyS_sendto+0xe/0x10[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123894]  [<ffffffff81731d7d>] system_call_fastpath+0x1a/0x1f[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123895] ---[ end trace f2eff45315ac0c3f ]---[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123932] ------------[ cut here ]------------[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123935] WARNING: CPU: 9 PID: 14163 at /build/buildd/linux-3.13.0/net/core/dst.c:285 dst_release+0x45/0x60()[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123936] Modules linked in: gpio_ich intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd serio_raw lpc_ich ipmi_si mac_hid i7core_edac edac_core shpchp lp parport raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq igb raid1 i2c_algo_bit raid0 dca multipath ptp ahci linear libahci pps_core[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123953] CPU: 9 PID: 14163 Comm: postgres Tainted: G        W I   3.13.0-46-generic #79-Ubuntu[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123954] Hardware name: HP ProLiant DL160 G6  , BIOS O33 07/01/2013[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123955]  0000000000000009 ffff88001697baa0 ffffffff817212c6 0000000000000000[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123958]  ffff88001697bad8 ffffffff810677dd ffff88090859b780 00000000ffffffff[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123960]  ffff88097a5e0378 ffff88090859b780 ffffffff81cdaa00 ffff88001697bae8[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123963] Call Trace:[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123965]  [<ffffffff817212c6>] dump_stack+0x45/0x56[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123967]  [<ffffffff810677dd>] warn_slowpath_common+0x7d/0xa0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123970]  [<ffffffff810678ba>] warn_slowpath_null+0x1a/0x20[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123972]  [<ffffffff8162dc65>] dst_release+0x45/0x60[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123974]  [<ffffffff816c0c7c>] ip6_cork_release.isra.30+0x6c/0x120[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123976]  [<ffffffff816c1c81>] ip6_push_pending_frames+0x341/0x480[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123979]  [<ffffffff816dba49>] udp_v6_push_pending_frames+0x129/0x3d0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123981]  [<ffffffff816dc68e>] udpv6_sendmsg+0x71e/0xb10[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123983]  [<ffffffff8160f40a>] ? sock_def_readable+0x3a/0x70[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123986]  [<ffffffff81693b44>] inet_sendmsg+0x64/0xb0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123989]  [<ffffffff81313bf7>] ? apparmor_socket_sendmsg+0x17/0x20[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123991]  [<ffffffff8160c7eb>] sock_sendmsg+0x8b/0xc0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123994]  [<ffffffff8172d354>] ? __do_page_fault+0x204/0x560[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123996]  [<ffffffff8160cd31>] SYSC_sendto+0x121/0x1c0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123998]  [<ffffffff8117e751>] ? remove_vma+0x71/0x90[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.124001]  [<ffffffff81180667>] ? do_munmap+0x297/0x3b0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.124003]  [<ffffffff8172d6ca>] ? do_page_fault+0x1a/0x70[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.124005]  [<ffffffff8160d71e>] SyS_sendto+0xe/0x10[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.124007]  [<ffffffff81731d7d>] system_call_fastpath+0x1a/0x1f[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.124009] ---[ end trace f2eff45315ac0c40 ]---[/FONT]

```

flooded in kern.log with (similarly):
```

[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123661] ------------[ cut here ]------------[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123674] WARNING: CPU: 9 PID: 14163 at /build/buildd/linux-3.13.0/net/core/dst.c:285 dst_release+0x45/0x60()[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123675] Modules linked in: gpio_ich intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd serio_raw lpc_ich ipmi_si mac_hid i7core_edac edac_core shpchp lp parport raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq igb raid1 i2c_algo_bit raid0 dca multipath ptp ahci linear libahci pps_core[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123703] CPU: 9 PID: 14163 Comm: postgres Tainted: G        W I   3.13.0-46-generic #79-Ubuntu[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123705] Hardware name: HP ProLiant DL160 G6  , BIOS O33 07/01/2013[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123706]  0000000000000009 ffff88001697bb18 ffffffff817212c6 0000000000000000[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123710]  ffff88001697bb50 ffffffff810677dd ffff88090859b780 00000000ffffffff[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123712]  ffff88097a5e0000 0000000000000000 0000000000000000 ffff88001697bb60[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123715] Call Trace:[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123722]  [<ffffffff817212c6>] dump_stack+0x45/0x56[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123727]  [<ffffffff810677dd>] warn_slowpath_common+0x7d/0xa0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123729]  [<ffffffff810678ba>] warn_slowpath_null+0x1a/0x20[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123731]  [<ffffffff8162dc65>] dst_release+0x45/0x60[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123735]  [<ffffffff8160ec91>] sk_dst_check+0xb1/0xe0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123751]  [<ffffffff816c169f>] ip6_sk_dst_lookup_flow+0x2f/0x1b0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123760]  [<ffffffff816dc58e>] udpv6_sendmsg+0x61e/0xb10[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123772]  [<ffffffff810aaa18>] ? __wake_up_common+0x58/0x90[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123776]  [<ffffffff810aafd0>] ? __wake_up_sync_key+0x50/0x60[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123778]  [<ffffffff8160f40a>] ? sock_def_readable+0x3a/0x70[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123783]  [<ffffffff81693b44>] inet_sendmsg+0x64/0xb0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123789]  [<ffffffff81313bf7>] ? apparmor_socket_sendmsg+0x17/0x20[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123792]  [<ffffffff8160c7eb>] sock_sendmsg+0x8b/0xc0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123797]  [<ffffffff8172d354>] ? __do_page_fault+0x204/0x560[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123799]  [<ffffffff8160cd31>] SYSC_sendto+0x121/0x1c0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123804]  [<ffffffff8117e751>] ? remove_vma+0x71/0x90[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123807]  [<ffffffff81180667>] ? do_munmap+0x297/0x3b0[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123809]  [<ffffffff8172d6ca>] ? do_page_fault+0x1a/0x70[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123812]  [<ffffffff8160d71e>] SyS_sendto+0xe/0x10[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123815]  [<ffffffff81731d7d>] system_call_fastpath+0x1a/0x1f[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123817] ---[ end trace f2eff45315ac0c3e ]---[/FONT]
[FONT=arial]Mar  7 06:45:22 data8 kernel: [1528896.123818] ------------[ cut here ]------------
Mar  7 06:45:22 data8 kernel: [1528896.123820] WARNING: CPU: 9 PID: 14163 at /build/buildd/linux-3.13.0/net/core/dst.c:285 dst_release+0x45/0x60()
Mar  7 06:45:22 data8 kernel: [1528896.123821] Modules linked in: gpio_ich intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd serio_raw lpc_ich ipmi_si mac_hid i7core_edac edac_core shpchp lp parport raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq igb raid1 i2c_algo_bit raid0 dca multipath ptp ahci linear libahci pps_core
Mar  7 06:45:22 data8 kernel: [1528896.123838] CPU: 9 PID: 14163 Comm: postgres Tainted: G        W I   3.13.0-46-generic #79-Ubuntu
Mar  7 06:45:22 data8 kernel: [1528896.123839] Hardware name: HP ProLiant DL160 G6  , BIOS O33 07/01/2013
Mar  7 06:45:22 data8 kernel: [1528896.123840]  0000000000000009 ffff88001697bb18 ffffffff817212c6 0000000000000000
Mar  7 06:45:22 data8 kernel: [1528896.123843]  ffff88001697bb50 ffffffff810677dd ffff88090859b780 00000000fffffffe
Mar  7 06:45:22 data8 kernel: [1528896.123846]  ffff88097a5e0000 0000000000000000 0000000000000000 ffff88001697bb60
Mar  7 06:45:22 data8 kernel: [1528896.123848] Call Trace:
Mar  7 06:45:22 data8 kernel: [1528896.123850]  [<ffffffff817212c6>] dump_stack+0x45/0x56
Mar  7 06:45:22 data8 kernel: [1528896.123853]  [<ffffffff810677dd>] warn_slowpath_common+0x7d/0xa0
Mar  7 06:45:22 data8 kernel: [1528896.123855]  [<ffffffff810678ba>] warn_slowpath_null+0x1a/0x20
Mar  7 06:45:22 data8 kernel: [1528896.123857]  [<ffffffff8162dc65>] dst_release+0x45/0x60
Mar  7 06:45:22 data8 kernel: [1528896.123859]  [<ffffffff8160ec99>] sk_dst_check+0xb9/0xe0
Mar  7 06:45:22 data8 kernel: [1528896.123861]  [<ffffffff816c169f>] ip6_sk_dst_lookup_flow+0x2f/0x1b0
Mar  7 06:45:22 data8 kernel: [1528896.123864]  [<ffffffff816dc58e>] udpv6_sendmsg+0x61e/0xb10
Mar  7 06:45:22 data8 kernel: [1528896.123866]  [<ffffffff810aaa18>] ? __wake_up_common+0x58/0x90
Mar  7 06:45:22 data8 kernel: [1528896.123868]  [<ffffffff810aafd0>] ? __wake_up_sync_key+0x50/0x60
Mar  7 06:45:22 data8 kernel: [1528896.123871]  [<ffffffff8160f40a>] ? sock_def_readable+0x3a/0x70
Mar  7 06:45:22 data8 kernel: [1528896.123873]  [<ffffffff81693b44>] inet_sendmsg+0x64/0xb0
Mar  7 06:45:22 data8 kernel: [1528896.123876]  [<ffffffff81313bf7>] ? apparmor_socket_sendmsg+0x17/0x20
Mar  7 06:45:22 data8 kernel: [1528896.123878]  [<ffffffff8160c7eb>] sock_sendmsg+0x8b/0xc0
Mar  7 06:45:22 data8 kernel: [1528896.123881]  [<ffffffff8172d354>] ? __do_page_fault+0x204/0x560
Mar  7 06:45:22 data8 kernel: [1528896.123883]  [<ffffffff8160cd31>] SYSC_sendto+0x121/0x1c0
Mar  7 06:45:22 data8 kernel: [1528896.123885]  [<ffffffff8117e751>] ? remove_vma+0x71/0x90
Mar  7 06:45:22 data8 kernel: [1528896.123887]  [<ffffffff81180667>] ? do_munmap+0x297/0x3b0
Mar  7 06:45:22 data8 kernel: [1528896.123890]  [<ffffffff8172d6ca>] ? do_page_fault+0x1a/0x70
Mar  7 06:45:22 data8 kernel: [1528896.123892]  [<ffffffff8160d71e>] SyS_sendto+0xe/0x10
Mar  7 06:45:22 data8 kernel: [1528896.123894]  [<ffffffff81731d7d>] system_call_fastpath+0x1a/0x1f
Mar  7 06:45:22 data8 kernel: [1528896.123895] ---[ end trace f2eff45315ac0c3f ]---
[/FONT]

```

---

### Post by Thirtysixway on 2016-04-23
nwilson5,

I've been doing a little bit of research and it looks like this is indeed some type of kernel bug.  I would suggest looking into upgrading your kernel to either the latest available for your Trusty install, or possibly install the kernel from a newer Ubuntu release.

Example, some comments here have mentioned a similar problem was solved by upgrading their kernel
[https://github.com/openstreetmap/operations/issues/29#issuecomment-126150628](https://github.com/openstreetmap/operations/issues/29#issuecomment-126150628)

According to your traces, you're running 3.13.0-46-generic . It looks like 3.13.0-85 should be available for Trusty?  Try doing an apt-get install linux-generic or look on this page

[http://askubuntu.com/questions/175385/why-is-apt-no-longer-updating-the-kernel](http://askubuntu.com/questions/175385/why-is-apt-no-longer-updating-the-kernel)


Also you may want to do this on 1 server, test it out for a while, and if it solves your problem then deploy this on the rest of them.

---

