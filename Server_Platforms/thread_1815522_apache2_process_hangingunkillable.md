---
title: "apache2 process hanging/unkillable"
date: 2011-07-31
forum: Server Platforms
---

### Post by lendarker on 2011-07-31
Hi. I'm running Ubuntu 10.10 on a webserver, and found that apache wasn't responding anymore. I checked, and got this from /var/log/messages:

```
Jul 31 07:42:11 web1 kernel: [1673445.610690] CPU 2
Jul 31 07:42:11 web1 kernel: [1673445.610696] Modules linked in: parport_pc ppdev snd_hda_codec_atihdmi snd_hda_intel radeon snd_hda_codec snd_hwdep ttm drm_kms_helper drm i7core_edac snd_pcm snd_timer i2c_algo_bit snd soundcore edac_core snd_page_alloc lp parport xfs exportfs multipath linear aacraid 3w_9xxx 3w_xxxx raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx raid0 raid1 ahci r8169 libahci mii sata_nv sata_sil sata_via
Jul 31 07:42:11 web1 kernel: [1673445.610931]
Jul 31 07:42:11 web1 kernel: [1673445.610950] Pid: 27609, comm: apache2 Not tainted 2.6.35-30-server #54-Ubuntu MSI X58 Pro-E (MS-7522)/MS-7522
Jul 31 07:42:11 web1 kernel: [1673445.610998] RIP: 0010:[<ffffffff8104dd2a>]  [<ffffffff8104dd2a>] task_rq_lock+0x4a/0xa0
Jul 31 07:42:11 web1 kernel: [1673445.611047] RSP: 0018:ffff8805a43f3dc8  EFLAGS: 00010082
Jul 31 07:42:11 web1 kernel: [1673445.611073] RAX: 909090909005eb05 RBX: 0000000000015b80 RCX: 0000000000000000
Jul 31 07:42:11 web1 kernel: [1673445.611115] RDX: 0000000000000282 RSI: ffff8805a43f3e20 RDI: 00007fcd07e04b40
Jul 31 07:42:11 web1 kernel: [1673445.611157] RBP: ffff8805a43f3de8 R08: 0000000000000000 R09: dead000000200200
Jul 31 07:42:11 web1 kernel: [1673445.611199] R10: dead000000100100 R11: dead000000200200 R12: 00007fcd07e04b40
Jul 31 07:42:11 web1 kernel: [1673445.611241] R13: ffff8805a43f3e20 R14: 0000000000015b80 R15: 0000000000000002
Jul 31 07:42:11 web1 kernel: [1673445.611283] FS:  00007fcd0889d740(0000) GS:ffff880001e40000(0000) knlGS:0000000000000000
Jul 31 07:42:11 web1 kernel: [1673445.611327] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jul 31 07:42:11 web1 kernel: [1673445.611353] CR2: 00007fcd0a936bb0 CR3: 00000005a4055000 CR4: 00000000000006e0
Jul 31 07:42:11 web1 kernel: [1673445.611395] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jul 31 07:42:11 web1 kernel: [1673445.611437] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jul 31 07:42:11 web1 kernel: [1673445.611480] Process apache2 (pid: 27609, threadinfo ffff8805a43f2000, task ffff8803e2308000)
Jul 31 07:42:11 web1 kernel: [1673445.611543]  00007fcd07e04b40 ffff8802fa6ffec8 000000000000000f 0000000000000000
Jul 31 07:42:11 web1 kernel: [1673445.611576] <0> ffff8805a43f3e58 ffffffff8105895c ffff8803e40ff550 ffff880001e50ea0
Jul 31 07:42:11 web1 kernel: [1673445.611626] <0> ffffffff81a44700 0000000000000286 ffffffff81a52850 0000000000000282
Jul 31 07:42:11 web1 kernel: [1673445.611713]  [<ffffffff8105895c>] try_to_wake_up+0x3c/0x400
Jul 31 07:42:11 web1 kernel: [1673445.611739]  [<ffffffff81058d75>] wake_up_process+0x15/0x20
Jul 31 07:42:11 web1 kernel: [1673445.611767]  [<ffffffff812531b0>] freeary+0x1e0/0x220
Jul 31 07:42:11 web1 kernel: [1673445.611793]  [<ffffffff81254220>] T.579+0xb0/0x100
Jul 31 07:42:11 web1 kernel: [1673445.611819]  [<ffffffff815a6a69>] ? do_page_fault+0x159/0x350
Jul 31 07:42:11 web1 kernel: [1673445.611846]  [<ffffffff812542d9>] sys_semctl+0x69/0xa0
Jul 31 07:42:11 web1 kernel: [1673445.611873]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
Jul 31 07:42:11 web1 kernel: [1673445.612094]  RSP <ffff8805a43f3dc8>
Jul 31 07:42:11 web1 kernel: [1673445.612322] ---[ end trace 11e0bd4d553eab55 ]---
```

Anybody know what this might indicate? Faulty memory/CPU? This is a first for me.

The process was listed with state "Ds", and didn't respond to either an apache stop command, kill -9 or kill -11. "reboot" and "reboot -f" also didn't go through. The latter only kicked me out of ssh, but didn't reboot the server. I had to do a physical reset via the hoster's admin console to get the server back to being responsive.

---

