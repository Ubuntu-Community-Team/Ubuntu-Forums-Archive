---
title: "Help with Kernel Panic"
date: 2017-06-20
forum: Server Platforms
---

### Post by prodriguez-accusoft on 2017-06-20
Running KVM and experienced following kernel panic. Trying to track down possible causes.

```
Jun  8 13:25:59 prod-compute01 kernel: [7220130.572134] RDX: 00000000fc0ca000 RSI: 00000000fc0ca000 RDI: ffff8806cd908000
Jun  8 13:25:59 prod-compute01 kernel: [7220130.573486] R10: ffffc9001f511000 R11: 000000000000000f R12: ffff8806cd908000
Jun  8 13:25:59 prod-compute01 kernel: [7220130.574850] FS:  00007f760094c700(0000) GS:ffff883ffee40000(0000) knlGS:0000000000000000
Jun  8 13:25:59 prod-compute01 kernel: [7220130.576250] CR2: 00000000fc0ca000 CR3: 00000001428cc000 CR4: 00000000003426e0
Jun  8 13:25:59 prod-compute01 kernel: [7220130.577689]  0000000000000001 ffff8806cd908000 ffff880110b37c08 ffffffffc06b7e1e
Jun  8 13:25:59 prod-compute01 kernel: [7220130.579195]  00007f758fa00000 00007f7580000000 ffffc9001c799008 ffffc9001c78f008
Jun  8 13:25:59 prod-compute01 kernel: [7220130.580745]  [<ffffffffc06b7e1e>] kvm_unmap_rmapp+0xe/0x20 [kvm]
Jun  8 13:25:59 prod-compute01 kernel: [7220130.582345]  [<ffffffffc06bffc7>] kvm_unmap_hva_range+0x17/0x20 [kvm]
Jun  8 13:25:59 prod-compute01 kernel: [7220130.583977]  [<ffffffff811e5d35>] __mmu_notifier_invalidate_range_start+0x55/0x80
Jun  8 13:25:59 prod-compute01 kernel: [7220130.585640]  [<ffffffff811caee4>] change_protection+0x14/0x20
Jun  8 13:25:59 prod-compute01 kernel: [7220130.587321]  [<ffffffff810b2efb>] task_numa_work+0x1fb/0x2f0
Jun  8 13:25:59 prod-compute01 kernel: [7220130.588996]  [<ffffffff81003242>] exit_to_usermode_loop+0xc2/0xd0
Jun  8 13:25:59 prod-compute01 kernel: [7220130.590689]  [<ffffffff8183c7d0>] int_ret_from_sys_call+0x25/0x8f
Jun  8 13:25:59 prod-compute01 kernel: [7220130.593312] RIP  [<ffffffffc06b7df7>] kvm_zap_rmapp+0x47/0x60 [kvm]
Jun  8 13:25:59 prod-compute01 kernel: [7220130.595059] CR2: 00000000fc0ca000
Jun  8 13:25:59 prod-compute01 kernel: [7220130.844347] kvm: zapping shadow pages for mmio generation wraparound
Jun  8 13:25:59 prod-compute01 kernel: [7220130.864591] kvm: zapping shadow pages for mmio generation wraparound
Jun  8 13:26:14 prod-compute01 kernel: [7220145.646830] net_ratelimit: 26842 callbacks suppressed
Jun  8 13:26:14 prod-compute01 kernel: [7220145.648175] vxlan: non-ECT from 172.16.4.245 with TOS=0x2
Jun  8 13:26:14 prod-compute01 kernel: [7220145.803262] vxlan: non-ECT from 172.16.4.245 with TOS=0x2
Jun  8 13:26:25 prod-compute01 kernel: [7220156.205727] NMI watchdog: BUG: soft lockup - CPU#1 stuck for 22s! [migration/1:13]
Jun  8 13:26:25 prod-compute01 kernel: [7220156.206342] Modules linked in: mpt3sas raid_class scsi_transport_sas rpcsec_gss_krb5 auth_rpcgss nfsv4 nfs lockd grace fscache ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs nf_conntrack_netlink xt_multiport ebt_arp ebt_among nf_conntrack_ipv6 nf_defrag_ipv6 xt_mac xt_physdev xt_set xt_conntrack ip_set_hash_net ip_set nfnetlink ip6table_raw xt_comment iptable_raw xt_CHECKSUM xt_tcpudp veth ebtable_filter binfmt_misc intel_rapl x86_pkg_temp_thermal intel_powerclamp ipmi_ssif coretemp input_leds joydev sb_edac edac_core mei_me lpc_ich mei ioatdma shpchp 8250_fintek ipmi_si ipmi_msghandler acpi_power_meter acpi_pad mac_hid kvm_intel kvm irqbypass sunrpc ib_iser rdma_cm iw_cm ib_cm ib_sa ib_mad ib_core ib_addr vhost_net vhost macvtap macvlan nbd iscsi_tcp libiscsi_tcp
Jun  8 13:26:25 prod-compute01 kernel: [7220156.209726] NMI watchdog: BUG: soft lockup - CPU#2 stuck for 22s! [migration/2:18]
Jun  8 13:26:25 prod-compute01 kernel: [7220156.209727] Modules linked in: mpt3sas raid_class scsi_transport_sas rpcsec_gss_krb5 auth_rpcgss nfsv4 nfs lockd grace fscache ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs nf_conntrack_netlink xt_multiport ebt_arp ebt_among nf_conntrack_ipv6 nf_defrag_ipv6 xt_mac xt_physdev xt_set xt_conntrack ip_set_hash_net ip_set nfnetlink ip6table_raw xt_comment iptable_raw xt_CHECKSUM xt_tcpudp veth ebtable_filter binfmt_misc intel_rapl x86_pkg_temp_thermal intel_powerclamp ipmi_ssif coretemp input_leds joydev sb_edac edac_core mei_me lpc_ich mei ioatdma shpchp 8250_fintek ipmi_si ipmi_msghandler acpi_power_meter acpi_pad mac_hid kvm_intel kvm irqbypass sunrpc ib_iser rdma_cm iw_cm ib_cm ib_sa ib_mad ib_core ib_addr vhost_net vhost macvtap macvlan nbd iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi ip_vs iptable_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_nat_ipv4 iptable_mangle iptable_filter ipt_REJECT nf_reject_ipv4 ipt_MASQUERADE nf_nat_masquerade_ipv4 nf_nat nf_conntrack ip_tables ip6_tables ebtables x_tables dm_bufio br_netfilter 8021q mrp llc btrfs raid456 async_memcpy async_xor xor libcrc32c multipath raid1 crc32_pclmul ghash_clmulni_intel aesni_intel mxm_wmi aes_x86_64 lrw igb vxlan ablk_helper syscopyarea sysfillrect sysimgblt udp_tunnel ahci drm megaraid_sas i2c_algo_bit fjes usbhid
Jun  8 13:26:25 prod-compute01 kernel: [7220156.209806] Hardware name: Supermicro SBI-7128R-C6/B10DRC, BIOS 2.0a 10/11/2016
Jun  8 13:26:25 prod-compute01 kernel: [7220156.209809] RIP: 0010:[<ffffffff811211ca>] <4>[7220156.209816] RSP: 0018:ffff881ff21e7da0  EFLAGS: 00000246
Jun  8 13:26:25 prod-compute01 kernel: [7220156.209817] RDX: 0000000000000001 RSI: 0000000000000286 RDI: ffff8829bbbc39e0
Jun  8 13:26:25 prod-compute01 kernel: [7220156.209819] R10: ffff881fcf203800 R11: 0000000000004c00 R12: ffff8829bbbc39e0
Jun  8 13:26:25 prod-compute01 kernel: [7220156.209821] FS:  0000000000000000(0000) GS:ffff881fff680000(0000) knlGS:0000000000000000
Jun  8 13:26:25 prod-compute01 kernel: [7220156.209823] CR2: 00007ffc2a230120 CR3: 000000126620f000 CR4: 00000000003426e0
Jun  8 13:26:25 prod-compute01 kernel: [7220156.209824] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
Jun  8 13:26:25 prod-compute01 kernel: [7220156.209826]  ffff881fff68f368 ffffffff81121180
Jun  8 13:26:25 prod-compute01 kernel: ffff881ff21e7e90 ffff881fff68f370<4>[7220156.209829]  ffff881f00000000 00000000fdf61c33
Jun  8 13:26:25 prod-compute01 kernel: [7220156.209834]  [<ffffffff81121180>] ? cpu_stop_queue_work+0x80/0x80
Jun  8 13:26:25 prod-compute01 kernel: [7220156.209840]  [<ffffffff81837e96>] ? __schedule+0x3b6/0xa30
Jun  8 13:26:25 prod-compute01 kernel: [7220156.209845]  [<ffffffff810a3e80>] ? sort_range+0x30/0x30
Jun  8 13:26:25 prod-compute01 kernel: [7220156.209849]  [<ffffffff810a0b10>] ? kthread_create_on_node+0x1e0/0x1e0
Jun  8 13:26:25 prod-compute01 kernel: [7220156.209852]  [<ffffffff810a0b10>] ? kthread_create_on_node+0x1e0/0x1e0
Jun  8 13:26:25 prod-compute01 kernel: 1f 00 49 c5 8b 18 85 0f 86 00 89 48 a3 19 85 41 95 4d 74 24 c9 d2 90 8b 24 39 74 83 02 49 fb 75
```

---

### Post by prodriguez-accusoft on 2017-07-13
Is there anymore info I can provide to try to get some help on this?

---

