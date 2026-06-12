---
title: "BUG: unable to handle kernel NULL pointer dereference at 00000030"
date: 2011-04-07
forum: Server Platforms
---

### Post by toshko3 on 2011-04-07
Hi, guys :)
I'm using Pacemaker/corosync over drbd and kvm over all of them. Last night the master node became unresponsive for everything except icmp. I went there and the messages below popped up at the monitor one after another in 2-3 minutes. Is this a bug or something?


```
Apr  6 00:08:53 node1 kernel: [7705392.715179] BUG: unable to handle kernel NULL pointer dereference at 00000030
Apr  6 00:08:53 node1 kernel: [7705392.718738] IP: [<f8ad15f1>] mmu_page_remove_parent_pte+0x11/0x100 [kvm]
Apr  6 00:08:53 node1 kernel: [7705392.718738] *pdpt = 0000000036f44001 *pde = 0000000000000000
Apr  6 00:08:53 node1 kernel: [7705392.718738] Oops: 0000 [#1] SMP
Apr  6 00:08:53 node1 kernel: [7705392.718738] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.0/0000:1a:00.0/irq
Apr  6 00:08:53 node1 kernel: [7705392.718738] Modules linked in: btrfs zlib_deflate libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs exportfs reiserfs xt_multiport crc32c ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT drbd xt_tcpudp iptable_filter ip_tables x_tables kvm_intel kvm fbcon tileblit font bitblit softcursor vga16fb vgastate radeon bridge stp ttm drm_kms_helper drm i5000_edac agpgart i2c_algo_bit edac_core shpchp i5k_amb ppdev lp parport_pc parport serio_raw ses enclosure usbhid hid tg3 8139too 8139cp mii aacraid
Apr  6 00:08:53 node1 kernel: [7705392.796818]
Apr  6 00:08:53 node1 kernel: [7705392.796818] Pid: 2448, comm: kvm Not tainted (2.6.32-27-generic-pae #49-Ubuntu) IBM eServer x3400-[7976K9G]-
Apr  6 00:08:53 node1 kernel: [7705392.796818] EIP: 0060:[<f8ad15f1>] EFLAGS: 00010292 CPU: 0
Apr  6 00:08:53 node1 kernel: [7705392.796818] EIP is at mmu_page_remove_parent_pte+0x11/0x100 [kvm]
Apr  6 00:08:53 node1 kernel: [7705392.796818] EAX: 00000000 EBX: f1dc86e8 ECX: 00000002 EDX: f1553ff8
Apr  6 00:08:53 node1 kernel: [7705392.796818] ESI: f1553ff8 EDI: ffffffff EBP: ea66de2c ESP: ea66de1c
Apr  6 00:08:53 node1 kernel: [7705392.796818]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Apr  6 00:08:53 node1 kernel: [7705392.796818] Process kvm (pid: 2448, ti=ea66c000 task=ea91b300 task.ti=ea66c000)
Apr  6 00:08:53 node1 kernel: [7705392.796818] Stack:
Apr  6 00:08:53 node1 kernel: [7705392.796818]  00000000 f1dc86e8 f1553ff8 ffffffff ea66de5c f8ad228f 00000000 fffff000
Apr  6 00:08:53 node1 kernel: [7705392.796818] <0> 000fffff f1dc86e8 ea9ec000 000001ff ffffffff e9d0a390 00000008 31553001
Apr  6 00:08:53 node1 kernel: [7705392.796818] <0> ea66de78 f8ad2805 31553000 00000000 e9d0a390 00000000 ea70b000 ea66de80
Apr  6 00:08:53 node1 kernel: [7705392.796818] Call Trace:
Apr  6 00:08:53 node1 kernel: [7705392.796818]  [<f8ad228f>] ? kvm_mmu_zap_page+0x10f/0x340 [kvm]
Apr  6 00:08:53 node1 kernel: [7705392.796818]  [<f8ad2805>] ? mmu_free_roots+0xd5/0x140 [kvm]
Apr  6 00:08:53 node1 kernel: [7705392.796818]  [<f8ad28ad>] ? kvm_mmu_unload+0xd/0x10 [kvm]
Apr  6 00:08:53 node1 kernel: [7705392.796818]  [<f8ac7e5f>] ? vcpu_enter_guest+0x2df/0x460 [kvm]
Apr  6 00:08:53 node1 kernel: [7705392.796818]  [<f8ac8042>] ? __vcpu_run+0x62/0x2f0 [kvm]
Apr  6 00:08:53 node1 kernel: [7705392.796818]  [<f8acdb68>] ? kvm_arch_vcpu_ioctl_run+0x68/0x180 [kvm]
Apr  6 00:08:53 node1 kernel: [7705392.796818]  [<f8abea2d>] ? kvm_vcpu_ioctl+0x3cd/0x500 [kvm]
Apr  6 00:08:53 node1 kernel: [7705392.796818]  [<c05b3e1d>] ? _spin_lock+0xd/0x10
Apr  6 00:08:53 node1 kernel: [7705392.796818]  [<c0181044>] ? futex_wake+0xe4/0x100
Apr  6 00:08:53 node1 kernel: [7705392.796818]  [<f8abe660>] ? kvm_vcpu_ioctl+0x0/0x500 [kvm]
Apr  6 00:08:53 node1 kernel: [7705392.796818]  [<c0221101>] ? vfs_ioctl+0x21/0x90
Apr  6 00:08:53 node1 kernel: [7705392.796818]  [<c02213e9>] ? do_vfs_ioctl+0x79/0x310
Apr  6 00:08:53 node1 kernel: [7705392.796818]  [<c02216e7>] ? sys_ioctl+0x67/0x80
Apr  6 00:08:53 node1 kernel: [7705392.796818]  [<c01096c3>] ? sysenter_do_call+0x12/0x28
Apr  6 00:08:53 node1 kernel: [7705392.796818] Code: 4d f0 0f b3 31 e9 d1 fe ff ff 0f 8e 0f ff ff ff 01 45 e0 e9 c3 fe ff ff 66 90 55 89 e5 57 56 53 83 ec 04 0f 1f 44 00 00 89 45 f0 <8b> 48 30 85 c9 75 1b 39 50 40 0f 85 cc 00 00 00 8b 45 f0 c7 40
Apr  6 00:08:53 node1 kernel: [7705392.796818] EIP: [<f8ad15f1>] mmu_page_remove_parent_pte+0x11/0x100 [kvm] SS:ESP 0068:ea66de1c
Apr  6 00:08:53 node1 kernel: [7705392.796818] CR2: 0000000000000030
Apr  6 00:08:53 node1 kernel: [7705392.807720] ---[ end trace fc27836c7e71d167 ]---
Apr  6 00:09:13 node1 snmpd[1012]: error on subcontainer 'ia_addr' insert (-1)
Apr  6 00:09:31 node1 kernel: [7705431.110245] block drbd0: peer( Secondary -> Unknown ) conn( Connected -> TearDown ) pdsk( UpToDate -> DUnknown )
Apr  6 00:09:31 node1 kernel: [7705431.129902] block drbd0: Creating new current UUID
Apr  6 00:09:31 node1 kernel: [7705431.140095] block drbd0: asender terminated
Apr  6 00:09:31 node1 kernel: [7705431.149545] block drbd0: Terminating asender thread
Apr  6 00:09:31 node1 kernel: [7705431.159135] block drbd0: Connection closed
Apr  6 00:09:31 node1 kernel: [7705431.168043] block drbd0: conn( TearDown -> Unconnected )
Apr  6 00:09:31 node1 kernel: [7705431.176728] block drbd0: receiver terminated
Apr  6 00:09:31 node1 kernel: [7705431.185391] block drbd0: Restarting receiver thread
Apr  6 00:09:31 node1 kernel: [7705431.194094] block drbd0: receiver (re)started
Apr  6 00:09:31 node1 kernel: [7705431.203401] block drbd0: conn( Unconnected -> WFConnection )
Apr  6 00:09:32 node1 kernel: [7705431.656524] block drbd0: Handshake successful: Agreed network protocol version 91
Apr  6 00:09:32 node1 kernel: [7705431.674821] block drbd0: conn( WFConnection -> WFReportParams )
Apr  6 00:09:32 node1 kernel: [7705431.684456] block drbd0: Starting asender thread (from drbd0_receiver [1194])
Apr  6 00:09:32 node1 kernel: [7705431.703729] block drbd0: data-integrity-alg: crc32c
Apr  6 00:09:32 node1 kernel: [7705431.713709] block drbd0: drbd_sync_handshake:
Apr  6 00:09:32 node1 kernel: [7705431.723427] block drbd0: self 5D608A94BCA16BDF:D8B8FC5BB59C4597:022D4CFD4D2AD290:E52EC664F886A985 bits:0 flags:0
Apr  6 00:09:32 node1 kernel: [7705431.742884] block drbd0: peer 36C0D452EF348643:D8B8FC5BB59C4596:022D4CFD4D2AD290:E52EC664F886A985 bits:0 flags:0
Apr  6 00:09:32 node1 kernel: [7705431.762767] block drbd0: uuid_compare()=100 by rule 90
Apr  6 00:09:32 node1 kernel: [7705431.772769] block drbd0: Split-Brain detected, dropping connection!
Apr  6 00:09:32 node1 kernel: [7705431.782793] block drbd0: helper command: /sbin/drbdadm split-brain minor-0
Apr  6 00:09:32 node1 kernel: [7705431.792974] block drbd0: meta connection shut down by peer.
Apr  6 00:09:32 node1 kernel: [7705431.802243] block drbd0: conn( WFReportParams -> NetworkFailure )
Apr  6 00:09:32 node1 kernel: [7705431.811519] block drbd0: asender terminated
Apr  6 00:09:32 node1 kernel: [7705431.820874] block drbd0: Terminating asender thread
Apr  6 00:09:32 node1 kernel: [7705431.988702] block drbd0: helper command: /sbin/drbdadm split-brain minor-0 exit code 0 (0x0)
Apr  6 00:09:32 node1 kernel: [7705432.006939] block drbd0: conn( NetworkFailure -> Disconnecting )
Apr  6 00:09:32 node1 kernel: [7705432.016288] block drbd0: error receiving ReportState, l: 4!
Apr  6 00:09:32 node1 kernel: [7705432.026519] block drbd0: Connection closed
Apr  6 00:09:32 node1 kernel: [7705432.036274] block drbd0: conn( Disconnecting -> StandAlone )
Apr  6 00:09:32 node1 kernel: [7705432.046081] block drbd0: receiver terminated
Apr  6 00:09:32 node1 kernel: [7705432.055698] block drbd0: Terminating receiver thread
Apr  6 00:09:43 node1 snmpd[1012]: error on subcontainer 'ia_addr' insert (-1)
Apr  6 00:09:58 node1 kernel: [7705458.021000] BUG: soft lockup - CPU#2 stuck for 61s! [ksmd:53]
Apr  6 00:09:58 node1 kernel: [7705458.021001] Modules linked in: btrfs zlib_deflate libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs exportfs reiserfs xt_multiport crc32c ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT drbd xt_tcpudp iptable_filter ip_tables x_tables kvm_intel kvm fbcon tileblit font bitblit softcursor vga16fb vgastate radeon bridge stp ttm drm_kms_helper drm i5000_edac agpgart i2c_algo_bit edac_core shpchp i5k_amb ppdev lp parport_pc parport serio_raw ses enclosure usbhid hid tg3 8139too 8139cp mii aacraid
Apr  6 00:09:58 node1 kernel: [7705458.021001]
Apr  6 00:09:58 node1 kernel: [7705458.021001] Pid: 53, comm: ksmd Tainted: G      D    (2.6.32-27-generic-pae #49-Ubuntu) IBM eServer x3400-[7976K9G]-
Apr  6 00:09:58 node1 kernel: [7705458.021001] EIP: 0060:[<c0130d95>] EFLAGS: 00000293 CPU: 2
Apr  6 00:09:58 node1 kernel: [7705458.021001] EIP is at __ticket_spin_lock+0x15/0x20
Apr  6 00:09:58 node1 kernel: [7705458.021001] EAX: ea9ec000 EBX: ea9ec000 ECX: 64905000 EDX: 00009391
Apr  6 00:09:58 node1 kernel: [7705458.021001] ESI: 64905000 EDI: eafa3a40 EBP: f76dbe8c ESP: f76dbe8c
Apr  6 00:09:58 node1 kernel: [7705458.021001]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Apr  6 00:09:58 node1 kernel: [7705458.021001] CR0: 8005003b CR2: b738a4b0 CR3: 00793000 CR4: 000026f0
Apr  6 00:09:58 node1 kernel: [7705458.021001] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Apr  6 00:09:58 node1 kernel: [7705458.021001] DR6: ffff0ff0 DR7: 00000400
Apr  6 00:09:58 node1 kernel: [7705458.021001] Call Trace:
Apr  6 00:09:58 node1 kernel: [7705458.021001]  [<c05b3e1d>] _spin_lock+0xd/0x10
Apr  6 00:09:58 node1 kernel: [7705458.021001]  [<f8abc870>] kvm_mmu_notifier_change_pte+0x20/0x50 [kvm]
Apr  6 00:09:58 node1 kernel: [7705458.021001]  [<f8abc850>] ? kvm_mmu_notifier_change_pte+0x0/0x50 [kvm]
Apr  6 00:09:58 node1 kernel: [7705458.021001]  [<c0202a3e>] __mmu_notifier_change_pte+0x3e/0x80
Apr  6 00:09:58 node1 kernel: [7705458.021001]  [<c0204098>] write_protect_page+0x1b8/0x1c0
Apr  6 00:09:58 node1 kernel: [7705458.021001]  [<c0204728>] try_to_merge_one_page+0x88/0x100
Apr  6 00:09:58 node1 kernel: [7705458.021001]  [<c0204805>] try_to_merge_with_ksm_page+0x65/0x70
Apr  6 00:09:58 node1 kernel: [7705458.021001]  [<c0204997>] cmp_and_merge_page+0x47/0x190
Apr  6 00:09:58 node1 kernel: [7705458.021001]  [<c0204b07>] ksm_do_scan+0x27/0x90
Apr  6 00:09:58 node1 kernel: [7705458.021001]  [<c0204bd6>] ksm_scan_thread+0x66/0x140
Apr  6 00:09:58 node1 kernel: [7705458.021001]  [<c016ff10>] ? autoremove_wake_function+0x0/0x50
Apr  6 00:09:58 node1 kernel: [7705458.021001]  [<c0204b70>] ? ksm_scan_thread+0x0/0x140
Apr  6 00:09:58 node1 kernel: [7705458.021001]  [<c016fc84>] kthread+0x74/0x80
Apr  6 00:09:58 node1 kernel: [7705458.021001]  [<c016fc10>] ? kthread+0x0/0x80
Apr  6 00:09:58 node1 kernel: [7705458.021001]  [<c010a447>] kernel_thread_helper+0x7/0x10
Apr  6 00:09:58 node1 kernel: [7705458.024505] BUG: soft lockup - CPU#3 stuck for 61s! [kvm:2447]
Apr  6 00:09:59 node1 kernel: [7705458.024505] Modules linked in: btrfs zlib_deflate libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs exportfs reiserfs xt_multiport crc32c ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT drbd xt_tcpudp iptable_filter ip_tables x_tables kvm_intel kvm fbcon tileblit font bitblit softcursor vga16fb vgastate radeon bridge stp ttm drm_kms_helper drm i5000_edac agpgart i2c_algo_bit edac_core shpchp i5k_amb ppdev lp parport_pc parport serio_raw ses enclosure usbhid hid tg3 8139too 8139cp mii aacraid
Apr  6 00:09:59 node1 kernel: [7705458.024505]
Apr  6 00:09:59 node1 kernel: [7705458.024505] Pid: 2447, comm: kvm Tainted: G      D    (2.6.32-27-generic-pae #49-Ubuntu) IBM eServer x3400-[7976K9G]-
Apr  6 00:09:59 node1 kernel: [7705458.024505] EIP: 0060:[<c0130d8d>] EFLAGS: 00000297 CPU: 3
Apr  6 00:09:59 node1 kernel: [7705458.024505] EIP is at __ticket_spin_lock+0xd/0x20
Apr  6 00:09:59 node1 kernel: [7705458.024505] EAX: ea9ec000 EBX: e9d08000 ECX: 0005dc00 EDX: 00009291
Apr  6 00:09:59 node1 kernel: [7705458.024505] ESI: 00051518 EDI: 00000000 EBP: e9c6be38 ESP: e9c6be38
Apr  6 00:09:59 node1 kernel: [7705458.024505]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Apr  6 00:09:59 node1 kernel: [7705458.024505] CR0: 80050033 CR2: 7ffaeea0 CR3: 2afb7000 CR4: 000026f0
Apr  6 00:09:59 node1 kernel: [7705458.024505] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Apr  6 00:09:59 node1 kernel: [7705458.024505] DR6: ffff0ff0 DR7: 00000400
Apr  6 00:09:59 node1 kernel: [7705458.024505] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Apr  6 00:09:59 node1 kernel: [7705458.024505] DR6: ffff0ff0 DR7: 00000400
Apr  6 00:09:59 node1 kernel: [7705458.024505] Call Trace:
Apr  6 00:09:59 node1 kernel: [7705458.024505]  [<c05b3e1d>] _spin_lock+0xd/0x10
Apr  6 00:09:59 node1 kernel: [7705458.024505]  [<f8ad4989>] mmu_alloc_roots+0x79/0x210 [kvm]
Apr  6 00:09:59 node1 kernel: [7705458.024505]  [<c0130d93>] ? __ticket_spin_lock+0x13/0x20
Apr  6 00:09:59 node1 kernel: [7705458.024505]  [<f8ad73ef>] kvm_mmu_load+0x4f/0x90 [kvm]
Apr  6 00:09:59 node1 kernel: [7705458.024505]  [<f8ac7e92>] vcpu_enter_guest+0x312/0x460 [kvm]
Apr  6 00:09:59 node1 kernel: [7705458.024505]  [<f8ac8042>] __vcpu_run+0x62/0x2f0 [kvm]
Apr  6 00:09:59 node1 kernel: [7705458.024505]  [<f8acdb68>] kvm_arch_vcpu_ioctl_run+0x68/0x180 [kvm]
Apr  6 00:09:59 node1 kernel: [7705458.024505]  [<f8abea2d>] kvm_vcpu_ioctl+0x3cd/0x500 [kvm]
Apr  6 00:09:59 node1 kernel: [7705458.024505]  [<c05b3e1d>] ? _spin_lock+0xd/0x10
Apr  6 00:09:59 node1 kernel: [7705458.024505]  [<c0181044>] ? futex_wake+0xe4/0x100
Apr  6 00:09:59 node1 kernel: [7705458.024505]  [<f8abe660>] ? kvm_vcpu_ioctl+0x0/0x500 [kvm]
Apr  6 00:09:59 node1 kernel: [7705458.024505]  [<c0221101>] vfs_ioctl+0x21/0x90
Apr  6 00:09:59 node1 kernel: [7705458.024505]  [<c02213e9>] do_vfs_ioctl+0x79/0x310
Apr  6 00:09:59 node1 kernel: [7705458.024505]  [<c02216e7>] sys_ioctl+0x67/0x80
Apr  6 00:09:59 node1 kernel: [7705458.024505]  [<c01096c3>] sysenter_do_call+0x12/0x28
Apr  6 00:10:04 node1 snmpd[1012]: Connection from UDP: [192.168.16.11]:35270->[192.168.16.2]
Apr  6 00:10:04 node1 snmpd[1012]: Connection from UDP: [192.168.16.11]:43708->[192.168.16.2]
Apr  6 00:10:04 node1 snmpd[1012]: Connection from UDP: [192.168.16.11]:56390->[192.168.16.2]
Apr  6 00:10:04 node1 snmpd[1012]: Connection from UDP: [192.168.16.11]:60953->[192.168.16.2]
Apr  6 00:10:04 node1 snmpd[1012]: Connection from UDP: [192.168.16.11]:53974->[192.168.16.2]
Apr  6 00:10:04 node1 snmpd[1012]: Connection from UDP: [192.168.16.11]:43505->[192.168.16.2]
Apr  6 00:10:04 node1 snmpd[1012]: Connection from UDP: [192.168.16.11]:58529->[192.168.16.2]
Apr  6 00:10:04 node1 snmpd[1012]: Connection from UDP: [192.168.16.11]:40500->[192.168.16.2]
Apr  6 00:10:04 node1 snmpd[1012]: Connection from UDP: [192.168.16.11]:52905->[192.168.16.2]
Apr  6 00:10:04 node1 snmpd[1012]: Connection from UDP: [192.168.16.11]:50177->[192.168.16.2]
Apr  6 00:10:04 node1 snmpd[1012]: Connection from UDP: [192.168.16.11]:58523->[192.168.16.2]
Apr  6 00:10:04 node1 snmpd[1012]: Connection from UDP: [192.168.16.11]:45475->[192.168.16.2]
Apr  6 00:10:04 node1 snmpd[1012]: Connection from UDP: [192.168.16.11]:59845->[192.168.16.2]
Apr  6 00:10:04 node1 snmpd[1012]: Connection from UDP: [192.168.16.11]:34135->[192.168.16.2]
Apr  6 00:10:04 node1 snmpd[1012]: Connection from UDP: [192.168.16.11]:45238->[192.168.16.2]
Apr  6 00:10:07 node1 kernel: [7705466.612000] BUG: soft lockup - CPU#0 stuck for 61s! [kvm:11656]
.......
```

And so on all the night!
:confused:

---

### Post by toshko3 on 2011-04-08
Anyone?

---

