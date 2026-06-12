---
title: "Random e1000 Reset adapter with Call Traces left after &quot;transmit queue 0 timed out&quot;"
date: 2022-04-01
forum: Server Platforms
---

### Post by adrianmarcato on 2022-04-01
After a long due system upgrade (from scratch) on several virtualized servers that run Asterisk, from Ubuntu 14.04 to Ubuntu 20.04, I started noticing some network glitches, interruptions, that turned out to be caused by some Resets on eth0 (legacy names are enabled for backwards compatiblity with a lot of scripts) that start with:

```
[1215853.995409] NETDEV WATCHDOG: eth0 (e1000): transmit queue 0 timed out
```

and ends with one or several resets:
```
[1215854.004601] e1000 0000:02:00.0 eth0: Reset adapter
[1215854.087085] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
```

```
Linux 5.4.0-91-generic #102-Ubuntu SMP Fri Nov 5 16:31:28 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```

```
# ethtool -i eth0driver: e1000
version: 7.3.21-k8-NAPI
firmware-version:
expansion-rom-version:
bus-info: 0000:02:00.0
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
supports-priv-flags: no
```

Full call trace:
```
[1215853.995406] ------------[ cut here ]------------[1215853.995409] NETDEV WATCHDOG: eth0 (e1000): transmit queue 0 timed out
[1215853.995431] WARNING: CPU: 3 PID: 30 at net/sched/sch_generic.c:472 dev_watchdog+0x258/0x260
[1215853.995432] Modules linked in: rpcsec_gss_krb5 auth_rpcgss nfsv4 nfs lockd grace fscache iptable_filter bpfilter vmw_vsock_vmci_transport vsock dm_multipath scsi_dh_rdac scsi_dh_emc scsi_dh_alua intel_rapl_msr intel_rapl_common rapl vmw_balloon joydev input_leds serio_raw vmw_vmci mac_hid sch_fq_codel msr sunrpc ip_tables x_tables autofs4 btrfs zstd_compress raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel vmwgfx ttm crypto_simd drm_kms_helper cryptd syscopyarea glue_helper sysfillrect sysimgblt fb_sys_fops mptspi psmouse mptscsih mptbase drm scsi_transport_spi e1000 i2c_piix4 pata_acpi
[1215853.995500] CPU: 3 PID: 30 Comm: ksoftirqd/3 Not tainted 5.4.0-91-generic #102-Ubuntu
[1215853.995501] Hardware name: VMware, Inc. VMware Virtual Platform/440BX Desktop Reference Platform, BIOS 6.00 12/12/2018
[1215853.995504] RIP: 0010:dev_watchdog+0x258/0x260
[1215853.995505] Code: 85 c0 75 e5 eb 9f 4c 89 ff c6 05 f1 b2 ec 00 01 e8 9d c1 fa ff 44 89 e9 4c 89 fe 48 c7 c7 00 c7 83 a5 48 89 c2 e8 25 e1 13 00 <0f> 0b eb 80 0f 1f 40 00 66 66 66 66 90 55 48 89 e5 41 57 49 89 d7
[1215853.995507] RSP: 0018:ffffb86e0012bd38 EFLAGS: 00010282
[1215853.995508] RAX: 0000000000000000 RBX: ffff9e56efd39a00 RCX: 0000000000000006
[1215853.995509] RDX: 0000000000000007 RSI: 0000000000000086 RDI: ffff9e56f3b978c0
[1215853.995510] RBP: ffffb86e0012bd68 R08: 0000000000000516 R09: 0000000000000004
[1215853.995510] R10: 0000000000000000 R11: 0000000000000001 R12: 0000000000000001
[1215853.995511] R13: 0000000000000000 R14: ffff9e56ef76a480 R15: ffff9e56ef76a000
[1215853.995512] FS:  0000000000000000(0000) GS:ffff9e56f3b80000(0000) knlGS:0000000000000000
[1215853.995513] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[1215853.995514] CR2: 00007ff198ac5760 CR3: 0000000328cee006 CR4: 00000000000606e0
[1215853.995567] Call Trace:
[1215853.995573]  ? pfifo_fast_enqueue+0x150/0x150
[1215853.995578]  call_timer_fn+0x32/0x130
[1215853.995580]  __run_timers.part.0+0x180/0x280
[1215853.995586]  ? __switch_to_asm+0x40/0x70
[1215853.995587]  ? __switch_to_asm+0x40/0x70
[1215853.995588]  ? __switch_to_asm+0x34/0x70
[1215853.995589]  ? __switch_to_asm+0x40/0x70
[1215853.995590]  ? __switch_to_asm+0x34/0x70
[1215853.995591]  ? __switch_to_asm+0x40/0x70
[1215853.995594]  ? __switch_to+0x7f/0x480
[1215853.995595]  ? __switch_to_asm+0x40/0x70
[1215853.995596]  ? __switch_to_asm+0x34/0x70
[1215853.995598]  run_timer_softirq+0x2a/0x50
[1215853.995600]  __do_softirq+0xe1/0x2d6
[1215853.995604]  run_ksoftirqd+0x2b/0x40
[1215853.995606]  smpboot_thread_fn+0xd0/0x170
[1215853.995609]  kthread+0x104/0x140
[1215853.995610]  ? sort_range+0x30/0x30
[1215853.995612]  ? kthread_park+0x90/0x90
[1215853.995613]  ret_from_fork+0x35/0x40
[1215853.995615] ---[ end trace 390ce430d4f02ef3 ]---
[1215854.004601] e1000 0000:02:00.0 eth0: Reset adapter
[1215854.087085] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
```

Any ideas? Traffic patterns are exactly the same as with 14.04, as well as the VMWare infrastructure... No changes were done there.

Thanks in advance.

---

