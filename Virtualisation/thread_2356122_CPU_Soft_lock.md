---
title: "CPU Soft lock"
date: 2017-03-20
forum: Virtualisation
---

### Post by low2215 on 2017-03-20
Hi 

We are running KVM in Ubuntu 14.04
4.2.0-27-generic #32~14.04.1-Ubuntu SMP Fri Jan 22 15:32:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

For the 2 months we have been experiencing CPU soft lock error in qemu-system for unknown reason , the KVM disk is running in OCFS2 system ,  multipath  to an IBM SAN storage .

The occurrence is unpredictable  but when it happens  command such as virsh migrate freeze .

This is the error we got , From the stack trace it seems to be  SCSI command thats hung up kernel .

```
kernel: [1804822.532259] NMI watchdog: BUG: soft lockup - CPU#5 stuck for 22s! [qemu-system-x86:1803]
kernel: [1804822.533386] Modules linked in: ipt_MASQUERADE nf_nat_masquerade_ipv4 iptable_nat nf_nat_ipv4 nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack ipt_REJECT nf_reject_ipv4 xt_CHECKSUM iptable_mangle xt_tcpudp ip6table_filter ip6_tables iptable_filter ip_tables ebtable_nat ebtables x_tables ocfs2 quota_tree ocfs2_dlmfs ocfs2_stack_o2cb ocfs2_dlm ocfs2_nodemanager ocfs2_stackglue configfs nls_iso8859_1 ast ttm drm_kms_helper drm syscopyarea sysfillrect sysimgblt ipmi_ssif mei_me mei bridge intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd joydev input_leds sb_edac edac_core lpc_ich ipmi_si shpchp wmi ipmi_msghandler 8250_fintek acpi_power_meter acpi_pad 8021q garp mrp mac_hid stp llc bonding lp parport dm_round_robin raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor hid_generic ahci libahci usbhid qla2xxx hid igb i2c_algo_bit dca ptp scsi_transport_fc pps_core raid6_pq raid1 raid0 multipath linear dm_mirror dm_region_hash dm_log dm_multipath scsi_dh
kernel: [1804822.533491] CPU: 5 PID: 1803 Comm: qemu-system-x86 Not tainted 4.2.0-27-generic #32~14.04.1-Ubuntu
kernel: [1804822.533493] Hardware name: Supermicro Super Server/X10DRT-H, BIOS 2.0a 03/08/2016
kernel: [1804822.533496] task: ffff8801438eb700 ti: ffff88039b684000 task.ti: ffff88039b684000
kernel: [1804822.533499] RIP: 0010:[<ffffffff810bed10>]  [<ffffffff810bed10>] native_queued_spin_lock_slowpath+0x160/0x170
kernel: [1804822.533511] RSP: 0018:ffff88085fb43b68  EFLAGS: 00000202
kernel: [1804822.533513] RAX: 0000000000000101 RBX: 0000000000000000 RCX: 0000000000000001
kernel: [1804822.533515] RDX: 0000000000000101 RSI: 0000000000000001 RDI: ffff8803dca122ec
kernel: [1804822.533517] RBP: ffff88085fb43b68 R08: 0000000000000101 R09: ffff88085fb59b00
kernel: [1804822.533519] R10: ffffffff81178ee7 R11: ffffea0004090c80 R12: ffff88085fb43ad8
kernel: [1804822.533521] R13: ffffffff817bd21b R14: ffff88085fb43b68 R15: ffff8803dca122f0
kernel: [1804822.533524] FS:  00007f045b4a2980(0000) GS:ffff88085fb40000(0000) knlGS:0000000000000000
kernel: [1804822.533526] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
kernel: [1804822.533528] CR2: 000055da2447b618 CR3: 00000003504f5000 CR4: 00000000003426e0
kernel: [1804822.533531] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
kernel: [1804822.533533] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
kernel: [1804822.533534] Stack:
kernel: [1804822.533536]  ffff88085fb43b78 ffffffff817ae9da ffff88085fb43b88 ffffffff817bc000
kernel: [1804822.533540]  ffff88085fb43ba8 ffffffff817ba525 ffff880113194400 ffff8803dca123b0
kernel: [1804822.533543]  ffff88085fb43bb8 ffffffff817ba56b ffff88085fb43be8 ffffffffc05c5c47
kernel: [1804822.533547] Call Trace:
kernel: [1804822.533550]  <IRQ>
kernel: [1804822.533559]  [<ffffffff817ae9da>] queued_spin_lock_slowpath+0xb/0xf
kernel: [1804822.533565]  [<ffffffff817bc000>] _raw_spin_lock+0x20/0x30
kernel: [1804822.533568]  [<ffffffff817ba525>] __mutex_unlock_slowpath+0x25/0x50
kernel: [1804822.533571]  [<ffffffff817ba56b>] mutex_unlock+0x1b/0x20
kernel: [1804822.533607]  [<ffffffffc05c5c47>] ocfs2_dio_end_io+0x67/0x70 [ocfs2]
kernel: [1804822.533614]  [<ffffffff81225384>] dio_complete+0xf4/0x170
kernel: [1804822.533617]  [<ffffffff81225473>] dio_bio_end_aio+0x73/0xf0
kernel: [1804822.533623]  [<ffffffff81372ad8>] bio_endio+0x58/0x90
kernel: [1804822.533628]  [<ffffffff81379a8a>] blk_update_request+0x8a/0x320
kernel: [1804822.533633]  [<ffffffff8163b195>] end_clone_bio+0x45/0x70
kernel: [1804822.533637]  [<ffffffff81372ad8>] bio_endio+0x58/0x90
kernel: [1804822.533641]  [<ffffffff81379a8a>] blk_update_request+0x8a/0x320
kernel: [1804822.533646]  [<ffffffff81552a64>] scsi_end_request+0x34/0x1d0
kernel: [1804822.533650]  [<ffffffff81554f9e>] scsi_io_completion+0xfe/0x600
kernel: [1804822.533653]  [<ffffffff8154c1df>] scsi_finish_command+0xcf/0x120
kernel: [1804822.533657]  [<ffffffff815547c6>] scsi_softirq_done+0x126/0x150
kernel: [1804822.533662]  [<ffffffff8138031c>] blk_done_softirq+0x7c/0x90
kernel: [1804822.533666]  [<ffffffff8107b972>] __do_softirq+0xd2/0x250
kernel: [1804822.533669]  [<ffffffff8107bd25>] irq_exit+0x95/0xa0
kernel: [1804822.533674]  [<ffffffff817befba>] do_IRQ+0x5a/0xe0
kernel: [1804822.533678]  [<ffffffff817bcf2b>] common_interrupt+0x6b/0x6b
kernel: [1804822.533680]  <EOI>
kernel: [1804822.533684]  [<ffffffff817bbff0>] ? _raw_spin_lock+0x10/0x30
kernel: [1804822.533687]  [<ffffffff817ba5fa>] ? __mutex_lock_slowpath+0x4a/0x110
kernel: [1804822.533710]  [<ffffffffc05dae9c>] ? ocfs2_inode_unlock+0xfc/0x110 [ocfs2]
kernel: [1804822.533713]  [<ffffffff817ba6e3>] mutex_lock+0x23/0x37
kernel: [1804822.533735]  [<ffffffffc05e326f>] ocfs2_file_write_iter+0x80f/0xcd0 [ocfs2]
kernel: [1804822.533755]  [<ffffffffc05e2a60>] ? ocfs2_check_range_for_refcount+0x110/0x110 [ocfs2]
kernel: [1804822.533761]  [<ffffffff81235676>] aio_run_iocb+0x226/0x2b0
kernel: [1804822.533769]  [<ffffffff811a5a65>] ? handle_mm_fault+0x7b5/0x1840
kernel: [1804822.533775]  [<ffffffff81207865>] ? __fget_light+0x25/0x60
kernel: [1804822.533778]  [<ffffffff81236a69>] do_io_submit+0x129/0x510
kernel: [1804822.533782]  [<ffffffff81236e60>] SyS_io_submit+0x10/0x20
kernel: [1804822.533785]  [<ffffffff817bc3b2>] entry_SYSCALL_64_fastpath+0x16/0x75
kernel: [1804822.533788] Code: 8b 01 48 85 c0 75 0a f3 90 48 8b 01 48 85 c0 74 f6 c7 40 08 01 00 00 00 e9 61 ff ff ff 83 fa 01 75 07 e9 c2 fe ff ff f3 90 8b 07 <84> c0 75 f8 b8 01 00 00 00 66 89 07 5d c3 66 90 0f 1f 44 00 00
```

---

### Post by jokken on 2018-01-10
hi [COLOR=#000000]low2215,

have you found out the cause of your CPU soft lock issue?

I am seeing very similar issue with Ubuntu 16 and kernel 4.4.0-98. 
we are using ocfs also!
we are using qemu/kvm with openstack.

thanks for any reply!

[/COLOR]

---

