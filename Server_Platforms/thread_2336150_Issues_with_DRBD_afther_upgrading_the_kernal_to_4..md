---
title: "Issues with DRBD afther upgrading the kernal to 4.4.0-36-generic"
date: 2016-09-05
forum: Server Platforms
---

### Post by gkooistrago on 2016-09-05
Dear reader,

Last day's, we've upgraded a part of our servers, running on ubuntu 14.04, to kernal 4.4.0-36-generic. But now we got issues with DRBD.
The isue: afther some hours/days, one of the nodes is missing his connectio to the other one, get in a time-oud but don't reconect. The other node has good status.

The syslog message:
```
Sep  5 09:16:18 node0 kernel: [169133.126069] block drbd0: Online verify done (total 117976 sec; paused 0 sec;
32580 K/sec)
Sep  5 09:16:18 node0 kernel: [169133.126082] block drbd0: conn( VerifyS -> Connected )
Sep  5 11:39:08 node0 kernel: [177703.190193] BUG: unable to handle kernel NULL pointer dereference at 00000000
00000003
Sep  5 11:39:08 node0 kernel: [177703.190448] IP: [<ffffffff813e20d6>] memcpy_erms+0x6/0x10
Sep  5 11:39:08 node0 kernel: [177703.190624] PGD 0
Sep  5 11:39:08 node0 kernel: [177703.190694] Oops: 0000 [#1] SMP
Sep  5 11:39:08 node0 kernel: [177703.190800] Modules linked in: vhost_net vhost macvtap macvlan ip_vs ebtable_
nat ebtables drbd lru_cache libcrc32c ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_def
rag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_physdev br_netfilter brid
ge stp llc xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables ipmi_ssif x86_pkg_t
emp_thermal nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp intel_powerclamp nf_conntrack coretemp iptable_filter kvm_intel ip_tables x_tables kvm irqbypass crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul sb_edac input_leds glue_helper ipmi_si joydev dm_multipath ablk_helper cryptd mei_me mei serio_raw edac_core ioatdma shpchp wmi lpc_ich 8250_fintek ipmi_msghandler mac_hid bonding lp parport hid_generic usbhid hid igb i2c_algo_bit dca isci libsas ahci ptp psmouse libahci scsi_transport_sas megaraid_sas pps_core fjes
Sep  5 11:39:08 node0 kernel: [177703.193897] CPU: 0 PID: 3205 Comm: drbd_w_r0 Not tainted 4.4.0-36-generic #55~14.04.1-Ubuntu


Sep  5 11:39:08 node0 kernel: [177703.194155] Hardware name: Supermicro X9DRW/X9DRW, BIOS 3.0c 03/24/2014
Sep  5 11:39:08 node0 kernel: [177703.199527] task: ffff883fefb81b80 ti: ffff883fe663c000 task.ti: ffff883fe663c000
Sep  5 11:39:08 node0 kernel: [177703.210410] RIP: 0010:[<ffffffff813e20d6>]  [<ffffffff813e20d6>] memcpy_erms+0x6/0x10
Sep  5 11:39:08 node0 kernel: [177703.221473] RSP: 0018:ffff883fe663fae0  EFLAGS: 00010282
Sep  5 11:39:08 node0 kernel: [177703.227018] RAX: ffff88126bbb9370 RBX: 00000000000000c0 RCX: 00000000000000c0
Sep  5 11:39:08 node0 kernel: [177703.238447] RDX: 00000000000000c0 RSI: 0000000000000003 RDI: ffff88126bbb9370
Sep  5 11:39:08 node0 kernel: [177703.250125] RBP: ffff883fe663fb20 R08: ffff883fe663fc30 R09: ffff883fefb82458
Sep  5 11:39:08 node0 kernel: [177703.261875] R10: 0000000000000000 R11: ffff881fd629cc30 R12: 0000000000000a70
Sep  5 11:39:08 node0 kernel: [177703.273975] R13: ffff883fe663fc50 R14: ffff883fe663fc50 R15: 0000000000000000
Sep  5 11:39:08 node0 kernel: [177703.286295] FS:  0000000000000000(0000) GS:ffff881fff800000(0000) knlGS:0000000000000000
Sep  5 11:39:08 node0 kernel: [177703.298620] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Sep  5 11:39:08 node0 kernel: [177703.304776] CR2: 0000000000000003 CR3: 0000000001c0c000 CR4: 00000000001426f0
Sep  5 11:39:08 node0 kernel: [177703.316830] Stack:
Sep  5 11:39:08 node0 kernel: [177703.322654]  ffffffff813e6917 ffff883fe663fc30 ffff88126bbb9430 ffff881fd629cb00
Sep  5 11:39:08 node0 kernel: [177703.334390]  ffff88126be52200 000000000000fe88 ffff883fe663fc40 0000000000000a70
Sep  5 11:39:08 node0 kernel: [177703.346116]  ffff883fe663fbb0 ffffffff8173ff47 ffffffff8137c548 ffff883fefb82458
Sep  5 11:39:08 node0 kernel: [177703.357839] Call Trace:
Sep  5 11:39:08 node0 kernel: [177703.363542]  [<ffffffff813e6917>] ? copy_from_iter+0x2b7/0x2d0
Sep  5 11:39:08 node0 kernel: [177703.369299]  [<ffffffff8173ff47>] tcp_sendmsg+0x997/0xad0
Sep  5 11:39:08 node0 kernel: [177703.374963]  [<ffffffff8137c548>] ? aa_sk_perm+0x78/0x230
Sep  5 11:39:08 node0 kernel: [177703.380508]  [<ffffffff81769dd7>] inet_sendmsg+0x67/0xa0
Sep  5 11:39:08 node0 kernel: [177703.385916]  [<ffffffff816d6dd8>] sock_sendmsg+0x38/0x50
Sep  5 11:39:08 node0 kernel: [177703.391165]  [<ffffffff816d6eeb>] kernel_sendmsg+0x2b/0x30
Sep  5 11:39:08 node0 kernel: [177703.396371]  [<ffffffffc0514c40>] drbd_send+0xc0/0x1b0 [drbd]
Sep  5 11:39:08 node0 kernel: [177703.401510]  [<ffffffffc0516641>] _drbd_no_send_page.isra.38+0x71/0xb0 [drbd]
Sep  5 11:39:08 node0 kernel: [177703.411524]  [<ffffffffc0516b6c>] drbd_send_dblock+0x33c/0x630 [drbd]
Sep  5 11:39:08 node0 kernel: [177703.416611]  [<ffffffffc04fcbf4>] w_send_dblock+0x94/0x150 [drbd]
Sep  5 11:39:08 node0 kernel: [177703.421598]  [<ffffffffc04fdeca>] drbd_worker+0xea/0x350 [drbd]
Sep  5 11:39:08 node0 kernel: [177703.426491]  [<ffffffffc0513210>] ? drbd_destroy_connection+0x160/0x160 [drbd]
Sep  5 11:39:08 node0 kernel: [177703.435996]  [<ffffffffc051325b>] drbd_thread_setup+0x4b/0x130 [drbd]
Sep  5 11:39:08 node0 kernel: [177703.440821]  [<ffffffffc0513210>] ? drbd_destroy_connection+0x160/0x160 [drbd]
Sep  5 11:39:08 node0 kernel: [177703.450159]  [<ffffffff8109b859>] kthread+0xc9/0xe0
Sep  5 11:39:08 node0 kernel: [177703.454798]  [<ffffffff8109b790>] ? kthread_park+0x60/0x60
Sep  5 11:39:08 node0 kernel: [177703.459393]  [<ffffffff817f788f>] ret_from_fork+0x3f/0x70
Sep  5 11:39:08 node0 kernel: [177703.463915]  [<ffffffff8109b790>] ? kthread_park+0x60/0x60
Sep  5 11:39:08 node0 kernel: [177703.468333] Code: ff eb eb 90 90 eb 1e 0f 1f 00 48 89 f8 48 89 d1 48 c1 e9 03 83 e2 07 f3 48 a5 89 d1 f3 a4 c3 66 0f 1f 44 00 00 48 89 f8 48 89 d1 <f3> a4 c3 0f 1f 80 00 00 00 00 48 89 f8 48 83 fa 20 72 7e 40 38
Sep  5 11:39:08 node0 kernel: [177703.482245] RIP  [<ffffffff813e20d6>] memcpy_erms+0x6/0x10
Sep  5 11:39:08 node0 kernel: [177703.486709]  RSP <ffff883fe663fae0>
Sep  5 11:39:08 node0 kernel: [177703.491024] CR2: 0000000000000003
Sep  5 11:39:08 node0 kernel: [177703.501733] ---[ end trace 8d5cbca266e6c158 ]---
Sep  5 11:39:09 node0 kernel: [177705.010207] block drbd0: Remote failed to finish a request within ko-count * timeout
Sep  5 11:39:09 node0 kernel: [177705.018702] drbd r0: peer( Secondary -> Unknown ) conn( Connected -> Timeout ) pdsk( UpToDate -> DUnknown )
```

DRBD Status node 0

```
 0: cs:Timeout ro:Primary/Unknown ds:UpToDate/DUnknown C r---n-
    ns:21436908 nr:7396 dw:21577856 dr:1719865368 al:1814 bm:0 lo:1 pe:18626 ua:0 ap:18627 ep:1 wo:f oos:53248
 1: cs:Connected ro:Secondary/Primary ds:UpToDate/UpToDate C r-----
    ns:19952 nr:28970644 dw:28990772 dr:1686312224 al:54 bm:0 lo:0 pe:0 ua:0 ap:0 ep:1 wo:f oos:0
```

DRBD Status node 1

```
version: 8.4.3 (api:1/proto:86-101)
srcversion: 6551AD2C98F533733BE558C
 0: cs:Connected ro:Secondary/Primary ds:UpToDate/UpToDate C r-----
    ns:0 nr:21424744 dw:21424744 dr:1696396700 al:0 bm:85 lo:1 pe:0 ua:0 ap:0 ep:1 wo:f oos:0
 1: cs:Connected ro:Primary/Secondary ds:UpToDate/UpToDate C r-----
    ns:28956280 nr:16548 dw:28972828 dr:1714354980 al:2103 bm:86 lo:0 pe:0 ua:0 ap:0 ep:1 wo:f oos:0
```

---

### Post by howefield on 2016-09-05
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by gkooistrago on 2016-09-05
If we look at our server monitoring (zabbix), we see a very high system load.

---

### Post by gkooistrago on 2016-09-30
We are not the only one: ..... [http://e2.howsolveproblem.com/i/1175162/](http://e2.howsolveproblem.com/i/1175162/)

---

