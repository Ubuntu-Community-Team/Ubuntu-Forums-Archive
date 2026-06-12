---
title: "How to file a bug report from &quot;general protection fault&quot; traces (CPU: 18 PID: 16236)?"
date: 2015-03-06
forum: Server Platforms
---

### Post by soonthorn.ios on 2015-03-06
Helllo,

What/where is the proper way to file a bug report from "general protection failt" traces?  
Also what other information will we need to figure out if the issues are fixed in later kernel?
Basically, the system completely logged up when this happened, we can see the trace on the console. Then we reset the box. The logs below are from /var/log/kern.log
It's not reproducible at the moment. The issue happened when we tried to stop a VM (qemu-system-x86) hosted on the box via OpenNebula VM management web interface.
```

root@node-101:~# cat /proc/version_signature 
Ubuntu 3.13.0-32.57-generic 3.13.11.4
root@node-101:~# cat /etc/issue
Ubuntu 14.04.1 LTS \n \l

```

```

Mar  5 15:29:22 node-101 kernel: [18293149.767254] general protection fault: 0000 [#1] SMP 
Mar  5 15:29:22 node-101 kernel: [18293149.810640] Modules linked in: ipmi_devintf ipmi_si nfnetlink bluetooth ebtable_filter vhost_net vhost macvtap macvlan nbd ipt_MASQUERADE iptable_nat nf_nat_
ipv4 nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack ipt_REJECT xt_CHECKSUM iptable_mangle xt_tcpudp ip6table_filter ip6_tables iptable_filter ip_tables ebtable_nat ebtables x_ta
bles bridge stp llc nfsd auth_rpcgss nfs_acl nfs lockd sunrpc fscache x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel gpi
o_ich aes_x86_64 sb_edac lrw gf128mul edac_core glue_helper mei_me ablk_helper ioatdma mei joydev wmi cryptd lpc_ich mac_hid xfs libcrc32c lp parport raid10 raid456 async_raid6_recov async_memcpy 
async_pq async_xor async_tx xor raid6_pq raid0 multipath linear raid1 igb i2c_algo_bit isci dca hid_generic libsas usbhid ptp hid ahci libahci scsi_transport_sas pps_core [last unloaded: ipmi_si]
Mar  5 15:29:22 node-101 kernel: [18293150.361734] CPU: 18 PID: 16236 Comm: qemu-system-x86 Not tainted 3.13.0-32-generic #57-Ubuntu
Mar  5 15:29:22 node-101 kernel: [18293150.448654] Hardware name: Supermicro SYS-F627R3-RTB+/X9DRFR, BIOS 3.0a 01/29/2014
Mar  5 15:29:22 node-101 kernel: [18293150.539953] task: ffff881026eadfc0 ti: ffff8813c7a84000 task.ti: ffff8813c7a84000
Mar  5 15:29:22 node-101 kernel: [18293150.629011] RIP: 0010:[<ffffffff811a4383>]  [<ffffffff811a4383>] __kmalloc_node_track_caller+0x173/0x290
Mar  5 15:29:22 node-101 kernel: [18293150.740566] RSP: 0018:ffff8813c7a85bb8  EFLAGS: 00010246
Mar  5 15:29:22 node-101 kernel: [18293150.795788] RAX: 0000000000000000 RBX: ffff881dc796cd00 RCX: 00000000012267b0
Mar  5 15:29:22 node-101 kernel: [18293150.904469] RDX: 00000000012267af RSI: 0000000000000000 RDI: 00000000000172a0
Mar  5 15:29:22 node-101 kernel: [18293151.013444] RBP: ffff8813c7a85c00 R08: ffff88207fcd72a0 R09: ffff88103f803500
Mar  5 15:29:22 node-101 kernel: [18293151.121781] R10: ffff88103f803500 R11: 0000000000000293 R12: 00000000000106d0
Mar  5 15:29:22 node-101 kernel: [18293151.230534] R13: 00000000000002c0 R14: 2d70757465732220 R15: 00000000ffffffff
Mar  5 15:29:22 node-101 kernel: [18293151.337326] FS:  00007f772b0ab980(0000) GS:ffff88207fcc0000(0000) knlGS:0000000000000000
Mar  5 15:29:22 node-101 kernel: [18293151.441748] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar  5 15:29:22 node-101 kernel: [18293151.484866] CR2: 00007f7473600000 CR3: 0000002015c11000 CR4: 00000000001427e0
Mar  5 15:29:22 node-101 kernel: [18293151.569286] Stack:
Mar  5 15:29:22 node-101 kernel: [18293151.613617]  ffff8820217c9808 ffff880b00000000 ffff88103f803500 ffffffff81610e7e
Mar  5 15:29:22 node-101 kernel: [18293151.717684]  ffff881dc796cd00 ffff8813c7a85c5f 00000000000004d0 00000000000002c0
Mar  5 15:29:22 node-101 kernel: [18293151.818459]  00000000ffffffff ffff8813c7a85c40 ffffffff816104f1 ffffffff81610e4e
Mar  5 15:29:22 node-101 kernel: [18293151.923644] Call Trace:
Mar  5 15:29:22 node-101 kernel: [18293151.974362]  [<ffffffff81610e7e>] ? __alloc_skb+0x7e/0x2b0
Mar  5 15:29:22 node-101 kernel: [18293152.025346]  [<ffffffff816104f1>] __kmalloc_reserve.isra.25+0x31/0x90
Mar  5 15:29:22 node-101 kernel: [18293152.073995]  [<ffffffff81610e4e>] ? __alloc_skb+0x4e/0x2b0
Mar  5 15:29:22 node-101 kernel: [18293152.123817]  [<ffffffff81610e7e>] __alloc_skb+0x7e/0x2b0
Mar  5 15:29:22 node-101 kernel: [18293152.171263]  [<ffffffff8160beda>] sock_alloc_send_pskb+0x1aa/0x3e0
Mar  5 15:29:22 node-101 kernel: [18293152.216564]  [<ffffffff816b6bcf>] unix_stream_sendmsg+0x26f/0x400
Mar  5 15:29:22 node-101 kernel: [18293152.262179]  [<ffffffff81606b9e>] sock_aio_write+0xfe/0x130
Mar  5 15:29:22 node-101 kernel: [18293152.308666]  [<ffffffff811bc3da>] do_sync_write+0x5a/0x90
Mar  5 15:29:22 node-101 kernel: [18293152.354563]  [<ffffffff811bcc5d>] vfs_write+0x1ad/0x1f0
Mar  5 15:29:22 node-101 kernel: [18293152.398450]  [<ffffffff811bd599>] SyS_write+0x49/0xa0
Mar  5 15:29:22 node-101 kernel: [18293152.440496]  [<ffffffff8172c87f>] tracesys+0xe1/0xe6
Mar  5 15:29:22 node-101 kernel: [18293152.480144] Code: 4c 89 cf 44 89 e6 4c 89 4d c8 e8 69 a3 00 00 4c 8b 4d c8 49 89 c2 e9 01 ff ff ff 0f 1f 44 00 00 49 63 42 20 48 8d 4a 01 49 8b 3a <49> 8b 1c
 06 4c 89 f0 65 48 0f c7 0f 0f 94 c0 84 c0 0f 84 da fe 
Mar  5 15:29:22 node-101 kernel: [18293152.603059] RIP  [<ffffffff811a4383>] __kmalloc_node_track_caller+0x173/0x290
Mar  5 15:29:22 node-101 kernel: [18293152.683558]  RSP <ffff8813c7a85bb8>
Mar  5 15:29:22 node-101 kernel: [18293152.780836] ---[ end trace 240f6ac494da517a ]---

```

```

Mar  5 15:29:42 node-101 kernel: [18293169.810789] general protection fault: 0000 [#2] SMP 
Mar  5 15:29:42 node-101 kernel: [18293169.846313] Modules linked in: ipmi_devintf ipmi_si nfnetlink bluetooth ebtable_filter vhost_net vhost macvtap macvlan nbd ipt_MASQUERADE iptable_nat nf_nat_
ipv4 nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack ipt_REJECT xt_CHECKSUM iptable_mangle xt_tcpudp ip6table_filter ip6_tables iptable_filter ip_tables ebtable_nat ebtables x_ta
bles bridge stp llc nfsd auth_rpcgss nfs_acl nfs lockd sunrpc fscache x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel gpi
o_ich aes_x86_64 sb_edac lrw gf128mul edac_core glue_helper mei_me ablk_helper ioatdma mei joydev wmi cryptd lpc_ich mac_hid xfs libcrc32c lp parport raid10 raid456 async_raid6_recov async_memcpy 
async_pq async_xor async_tx xor raid6_pq raid0 multipath linear raid1 igb i2c_algo_bit isci dca hid_generic libsas usbhid ptp hid ahci libahci scsi_transport_sas pps_core [last unloaded: ipmi_si]
Mar  5 15:29:42 node-101 kernel: [18293170.322073] CPU: 18 PID: 17330 Comm: ruby Tainted: G      D      3.13.0-32-generic #57-Ubuntu
Mar  5 15:29:42 node-101 kernel: [18293170.406604] Hardware name: Supermicro SYS-F627R3-RTB+/X9DRFR, BIOS 3.0a 01/29/2014
Mar  5 15:29:42 node-101 kernel: [18293170.493031] task: ffff88059fad17f0 ti: ffff881dc75cc000 task.ti: ffff881dc75cc000
Mar  5 15:29:42 node-101 kernel: [18293170.582261] RIP: 0010:[<ffffffff811a1e10>]  [<ffffffff811a1e10>] kmem_cache_alloc_trace+0x80/0x1f0
Mar  5 15:29:42 node-101 kernel: [18293170.674900] RSP: 0018:ffff881dc75cde80  EFLAGS: 00010286
Mar  5 15:29:42 node-101 kernel: [18293170.723987] RAX: 0000000000000000 RBX: ffff881c80541500 RCX: 00000000012267b0
Mar  5 15:29:42 node-101 kernel: [18293170.820369] RDX: 00000000012267af RSI: 00000000000080d0 RDI: ffff88103f803500
Mar  5 15:29:42 node-101 kernel: [18293170.918226] RBP: ffff881dc75cdeb8 R08: 00000000000172a0 R09: ffff88103f803500
Mar  5 15:29:42 node-101 kernel: [18293171.016755] R10: ffffffff811c5b6e R11: 0000000000000206 R12: 2d70757465732220
Mar  5 15:29:42 node-101 kernel: [18293171.118553] R13: 00000000000080d0 R14: 0000000000000280 R15: ffff88103f803500
Mar  5 15:29:42 node-101 kernel: [18293171.222610] FS:  00007f9913902700(0000) GS:ffff88207fcc0000(0000) knlGS:0000000000000000
Mar  5 15:29:42 node-101 kernel: [18293171.324449] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar  5 15:29:42 node-101 kernel: [18293171.375434] CR2: 0000000001520260 CR3: 00000011c7500000 CR4: 00000000001427e0
Mar  5 15:29:42 node-101 kernel: [18293171.476269] Stack:
Mar  5 15:29:42 node-101 kernel: [18293171.526136]  ffff88103f803500 ffffffff811c5b6e ffff881c80541500 ffff881dc75cdf60
Mar  5 15:29:42 node-101 kernel: [18293171.624546]  0000000000000000 ffff881dc75cdf58 00000000015eb1c0 ffff881dc75cded0
Mar  5 15:29:42 node-101 kernel: [18293171.723060]  ffffffff811c5b6e ffff88103f71afe8 ffff881dc75cdf10 ffffffff811c6086
Mar  5 15:29:42 node-101 kernel: [18293171.821162] Call Trace:
Mar  5 15:29:42 node-101 kernel: [18293171.869051]  [<ffffffff811c5b6e>] ? alloc_pipe_info+0x3e/0xb0
Mar  5 15:29:42 node-101 kernel: [18293171.917771]  [<ffffffff811c5b6e>] alloc_pipe_info+0x3e/0xb0
Mar  5 15:29:42 node-101 kernel: [18293171.965901]  [<ffffffff811c6086>] create_pipe_files+0x46/0x200
Mar  5 15:29:42 node-101 kernel: [18293172.015348]  [<ffffffff8109ddf4>] ? vtime_account_user+0x54/0x60
Mar  5 15:29:42 node-101 kernel: [18293172.062270]  [<ffffffff811c6274>] __do_pipe_flags+0x34/0xf0
Mar  5 15:29:42 node-101 kernel: [18293172.108545]  [<ffffffff811c6440>] SyS_pipe+0x20/0xa0
Mar  5 15:29:42 node-101 kernel: [18293172.154926]  [<ffffffff8172c87f>] tracesys+0xe1/0xe6
Mar  5 15:29:42 node-101 kernel: [18293172.199456] Code: dc 00 00 49 8b 50 08 4d 8b 20 49 8b 40 10 4d 85 e4 0f 84 14 01 00 00 48 85 c0 0f 84 0b 01 00 00 49 63 47 20 48 8d 4a 01 4d 8b 07 <49> 8b 1c
 04 4c 89 e0 65 49 0f c7 08 0f 94 c0 84 c0 74 b9 49 63 
Mar  5 15:29:42 node-101 kernel: [18293172.336809] RIP  [<ffffffff811a1e10>] kmem_cache_alloc_trace+0x80/0x1f0
Mar  5 15:29:42 node-101 kernel: [18293172.382694]  RSP <ffff881dc75cde80>
Mar  5 15:29:42 node-101 kernel: [18293172.425976] ---[ end trace 240f6ac494da517b ]---


```

---

### Post by MAFoElffen on 2015-03-06
"general prtotection fault" gets reported as bugs to launchpad under "linux"
```

apport-cli -f -p linux

```
It's a linux core subject, but if this is happening under a Server Edition, make sure you note that, so a tickler gets sent to the Server Team.

---

