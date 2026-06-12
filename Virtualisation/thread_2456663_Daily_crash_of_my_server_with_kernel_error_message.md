---
title: "Daily crash of my server with kernel error message"
date: 2021-01-16
forum: Virtualisation
---

### Post by hedy-dargere on 2021-01-16
Hi,

I have a Ubuntu 20.04.1 LTS (GNU/Linux 5.5.4-050504-generic x86_64) server running like a charm during one year.
But since 3 weeks, my server is "crashing" around once a day, at random timing.
A don't have choice to reboot it, and it's starting again for one more day approximately !
But it's not a very sustainable solution !

On the log during the time crash, I have this kind of messages :

```
janv. 16 09:25:02 server.domain.tld CRON[1426508]: pam_unix(cron:session): session closed for user admin
janv. 16 09:25:02 server.domain.tld sudo[1426529]: pam_unix(sudo:session): session closed for user root
janv. 16 09:25:02 server.domain.tld kernel: Fixing recursive fault but reboot is needed!
janv. 16 09:25:02 server.domain.tld kernel: CR2: 00007fe2c17892d1 CR3: 000000000260a000 CR4: 0000000000040660
janv. 16 09:25:02 server.domain.tld kernel: CS:  e030 DS: 0000 ES: 0000 CR0: 0000000080050033
janv. 16 09:25:02 server.domain.tld kernel: FS:  00007fe2c16a0740(0000) GS:ffff88807d240000(0000) knlGS:0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: R13: ffffc90040c9bc60 R14: ffff88807931a398 R15: 0000561336c74000
janv. 16 09:25:02 server.domain.tld kernel: R10: 0000000000000001 R11: 0000000000000001 R12: 0000561336c73000
janv. 16 09:25:02 server.domain.tld kernel: RBP: ffffc90040c9bb30 R08: ffffea0001bd5300 R09: 0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: RDX: 0000000000000000 RSI: 0000561336c73000 RDI: 0000001ad394c125
janv. 16 09:25:02 server.domain.tld kernel: RAX: ffffea0001bd5300 RBX: 0000001ad394c125 RCX: 0000000000000125
janv. 16 09:25:02 server.domain.tld kernel: RSP: e02b:ffffc90040c9ba88 EFLAGS: 00010202
janv. 16 09:25:02 server.domain.tld kernel: Code: 00 10 00 00 e8 15 f6 ff ff 48 83 7d 98 00 49 89 c0 74 09 48 85 c0 0f 85 91 05 00 00 41 f6 45 20 01 0f 84 b5 02 00 00 49>
janv. 16 09:25:02 server.domain.tld kernel: RIP: e030:zap_pte_range.isra.0+0x19c/0x880
janv. 16 09:25:02 server.domain.tld kernel: ---[ end trace 778135425d0d7b88 ]---
janv. 16 09:25:02 server.domain.tld kernel: Modules linked in: ipt_REJECT nf_reject_ipv4 xt_tcpudp xt_multiport iptable_filter bpfilter intel_rapl_msr intel_rapl_common >
janv. 16 09:25:02 server.domain.tld kernel:   call  1: op=26 arg=[ffff88807d217b10] result=-22
janv. 16 09:25:02 server.domain.tld kernel: R13: 000056133797d800 R14: 000056133797d320 R15: 000056133797d000
janv. 16 09:25:02 server.domain.tld kernel: R10: 0000000000000008 R11: 0000000000000246 R12: 00000000ffffffff
janv. 16 09:25:02 server.domain.tld kernel: 1 of 1 multicall(s) failed: cpu 0
janv. 16 09:25:02 server.domain.tld kernel: RBP: 000056133797d040 R08: 000056133797d800 R09: 0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: ---[ end trace 778135425d0d7b87 ]---
janv. 16 09:25:02 server.domain.tld kernel: RDX: 000056133797d320 RSI: 000056133797d800 RDI: 000056133797d040
janv. 16 09:25:02 server.domain.tld kernel: RAX: ffffffffffffffda RBX: 000056133797cfe0 RCX: 00007fe2c17892fb
janv. 16 09:25:02 server.domain.tld kernel:  ret_from_fork+0x35/0x40
janv. 16 09:25:02 server.domain.tld kernel: RSP: 002b:00007ffeb9f837d8 EFLAGS: 00000246 ORIG_RAX: 000000000000003b
janv. 16 09:25:02 server.domain.tld kernel:  ? kthread_park+0x90/0x90
janv. 16 09:25:02 server.domain.tld kernel: Code: Bad RIP value.
janv. 16 09:25:02 server.domain.tld kernel:  ? process_one_work+0x3b0/0x3b0
janv. 16 09:25:02 server.domain.tld kernel: RIP: 0033:0x7fe2c17892fb
janv. 16 09:25:02 server.domain.tld kernel:  kthread+0x104/0x140
janv. 16 09:25:02 server.domain.tld kernel:  rewind_stack_do_exit+0x17/0x20
janv. 16 09:25:02 server.domain.tld kernel:  worker_thread+0x4d/0x400
janv. 16 09:25:02 server.domain.tld kernel:  ? __x64_sys_execve+0x39/0x50
janv. 16 09:25:02 server.domain.tld kernel:  process_one_work+0x1eb/0x3b0
janv. 16 09:25:02 server.domain.tld kernel:  netstamp_clear+0x34/0x40
janv. 16 09:25:02 server.domain.tld kernel:  do_exit+0x2fd/0xac0
janv. 16 09:25:02 server.domain.tld kernel:  static_key_disable+0x1b/0x30
janv. 16 09:25:02 server.domain.tld kernel:  mmput+0x5d/0x130
janv. 16 09:25:02 server.domain.tld kernel:  static_key_disable_cpuslocked+0x66/0x90
janv. 16 09:25:02 server.domain.tld kernel:  ? _cond_resched+0x19/0x30
janv. 16 09:25:02 server.domain.tld kernel:  jump_label_update+0x64/0xc0
janv. 16 09:25:02 server.domain.tld kernel:  exit_mmap+0xb4/0x1b0
janv. 16 09:25:02 server.domain.tld kernel:  __jump_label_update+0x115/0x120
janv. 16 09:25:02 server.domain.tld kernel:  unmap_vmas+0x79/0xf0
janv. 16 09:25:02 server.domain.tld kernel:  arch_jump_label_transform_apply+0x32/0x50
janv. 16 09:25:02 server.domain.tld kernel:  unmap_single_vma+0x7f/0xf0
janv. 16 09:25:02 server.domain.tld kernel:  text_poke_bp_batch+0xf7/0x160
janv. 16 09:25:02 server.domain.tld kernel:  unmap_page_range+0x2d7/0x4e0
janv. 16 09:25:02 server.domain.tld kernel:  __text_poke+0x21a/0x4a0
janv. 16 09:25:02 server.domain.tld kernel:  ? exit_mmap+0xb4/0x1b0
janv. 16 09:25:02 server.domain.tld kernel:  ? netif_receive_skb_list_internal+0x47/0x2b0
janv. 16 09:25:02 server.domain.tld kernel:  zap_pte_range.isra.0+0x126/0x880
janv. 16 09:25:02 server.domain.tld kernel:  switch_mm_irqs_off+0x19b/0x500
janv. 16 09:25:02 server.domain.tld kernel: Call Trace:
janv. 16 09:25:02 server.domain.tld kernel:  load_new_mm_cr3+0x4d/0xf0
janv. 16 09:25:02 server.domain.tld kernel: CR2: 000055558da6d138 CR3: 000000000260a000 CR4: 0000000000040660
janv. 16 09:25:02 server.domain.tld kernel: CS:  e030 DS: 0000 ES: 0000 CR0: 0000000080050033
janv. 16 09:25:02 server.domain.tld kernel:  xen_write_cr3+0xf9/0x160
janv. 16 09:25:02 server.domain.tld kernel: FS:  00007fe2c16a0740(0000) GS:ffff88807d240000(0000) knlGS:0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: R13: ffffc90040c9be20 R14: ffff888072d32ff0 R15: ffff888072d33ff8
janv. 16 09:25:02 server.domain.tld kernel: Call Trace:
janv. 16 09:25:02 server.domain.tld kernel: R10: 0000000000000001 R11: 0000000000000001 R12: 00007fffffffe000
janv. 16 09:25:02 server.domain.tld kernel: RBP: ffffc90040c9bc38 R08: 00007ffffffff000 R09: 0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: CR2: 0000561337976bc8 CR3: 00000000250ee000 CR4: 0000000000040660
janv. 16 09:25:02 server.domain.tld kernel: CS:  10000e030 DS: 0000 ES: 0000 CR0: 0000000080050033
janv. 16 09:25:02 server.domain.tld kernel: RDX: 0000000000000001 RSI: ffff8880043e0898 RDI: ffff88801d8a1980
janv. 16 09:25:02 server.domain.tld kernel: RAX: 0000000000000001 RBX: ffff888007b18ff8 RCX: ffff888000000ff0
janv. 16 09:25:02 server.domain.tld kernel: FS:  00007fe2c16a0740(0000) GS:ffff88807d200000(0000) knlGS:0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: R13: ffff88807d217300 R14: 0000000000000020 R15: ffff8880743ee600
janv. 16 09:25:02 server.domain.tld kernel: RSP: e02b:ffffc90040c9bc38 EFLAGS: 00010202
janv. 16 09:25:02 server.domain.tld kernel: R10: 0000000000007ff0 R11: ffffc90040b87ad3 R12: 0000000000000001
janv. 16 09:25:02 server.domain.tld kernel: RBP: ffffc90040b87c78 R08: 0000000000000000 R09: 0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: Code: e8 b4 b0 02 00 5d c3 66 90 0f 1f 44 00 00 55 48 89 e5 65 8b 05 e8 07 fa 7e 85 c0 75 0d 65 c7 05 d9 07 fa 7e 01 00 00 00>
janv. 16 09:25:02 server.domain.tld kernel: RDX: 0000000000000000 RSI: 0000000000000001 RDI: ffff88807d217b10
janv. 16 09:25:02 server.domain.tld kernel: RAX: ffffffffffffffea RBX: ffff8880250ee000 RCX: 0000000000000001
janv. 16 09:25:02 server.domain.tld kernel: RIP: e030:paravirt_enter_lazy_mmu+0x21/0x30
janv. 16 09:25:02 server.domain.tld kernel: RSP: e02b:ffffc90040b87c48 EFLAGS: 00010002
janv. 16 09:25:02 server.domain.tld kernel: CPU: 1 PID: 1426643 Comm: bash Tainted: G      D W         5.5.4-050504-generic #202002150446
janv. 16 09:25:02 server.domain.tld kernel: Code: 05 00 10 00 81 e8 fa 83 dd 00 48 89 c1 49 89 45 18 48 c1 e9 3f 48 89 ce e9 fa fe ff ff 49 c7 45 18 ea ff ff ff be 01 00>
janv. 16 09:25:02 server.domain.tld kernel: invalid opcode: 0000 [#2] SMP NOPTI
janv. 16 09:25:02 server.domain.tld kernel: RIP: e030:xen_mc_flush+0x1a6/0x1d0
janv. 16 09:25:02 server.domain.tld kernel: kernel BUG at arch/x86/kernel/paravirt.c:216!
janv. 16 09:25:02 server.domain.tld kernel: Workqueue: events netstamp_clear
janv. 16 09:25:02 server.domain.tld kernel: ------------[ cut here ]------------
janv. 16 09:25:02 server.domain.tld kernel: CPU: 0 PID: 1417825 Comm: kworker/0:2 Tainted: G      D W         5.5.4-050504-generic #202002150446
janv. 16 09:25:02 server.domain.tld kernel: CR2: 00007fe2c17892d1 CR3: 0000000001e6e000 CR4: 0000000000040660
janv. 16 09:25:02 server.domain.tld kernel: CS:  e030 DS: 0000 ES: 0000 CR0: 0000000080050033
janv. 16 09:25:02 server.domain.tld kernel: Modules linked in: ipt_REJECT nf_reject_ipv4 xt_tcpudp xt_multiport iptable_filter bpfilter intel_rapl_msr intel_rapl_common >
janv. 16 09:25:02 server.domain.tld kernel: FS:  00007fe2c16a0740(0000) GS:ffff88807d240000(0000) knlGS:0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: WARNING: CPU: 0 PID: 1417825 at arch/x86/xen/multicalls.c:102 xen_mc_flush+0x1a6/0x1d0
janv. 16 09:25:02 server.domain.tld kernel: R13: ffffc90040c9bc60 R14: ffff88807931a398 R15: 0000561336c74000
janv. 16 09:25:02 server.domain.tld kernel: R10: 0000000000000001 R11: 0000000000000001 R12: 0000561336c73000
janv. 16 09:25:02 server.domain.tld kernel: ------------[ cut here ]------------
janv. 16 09:25:02 server.domain.tld kernel: RBP: ffffc90040c9bb30 R08: ffffea0001bd5300 R09: 0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: RDX: 0000000000000000 RSI: 0000561336c73000 RDI: 0000001ad394c125
janv. 16 09:25:02 server.domain.tld kernel:   call  1: op=26 arg=[ffff88807d217b10] result=-22
janv. 16 09:25:02 server.domain.tld kernel: RAX: ffffea0001bd5300 RBX: 0000001ad394c125 RCX: 0000000000000125
janv. 16 09:25:02 server.domain.tld kernel: 1 of 1 multicall(s) failed: cpu 0
janv. 16 09:25:02 server.domain.tld kernel: RSP: e02b:ffffc90040c9ba88 EFLAGS: 00010202
janv. 16 09:25:02 server.domain.tld kernel: ---[ end trace 778135425d0d7b86 ]---
janv. 16 09:25:02 server.domain.tld kernel: Code: 00 10 00 00 e8 15 f6 ff ff 48 83 7d 98 00 49 89 c0 74 09 48 85 c0 0f 85 91 05 00 00 41 f6 45 20 01 0f 84 b5 02 00 00 49>
janv. 16 09:25:02 server.domain.tld kernel:  ret_from_fork+0x35/0x40
janv. 16 09:25:02 server.domain.tld kernel: RIP: e030:zap_pte_range.isra.0+0x19c/0x880
janv. 16 09:25:02 server.domain.tld kernel:  ? kthread_park+0x90/0x90
janv. 16 09:25:02 server.domain.tld kernel: ---[ end trace 778135425d0d7b85 ]---
janv. 16 09:25:02 server.domain.tld kernel:  ? process_one_work+0x3b0/0x3b0
janv. 16 09:25:02 server.domain.tld kernel: CR2: ffff88807931a398
janv. 16 09:25:02 server.domain.tld kernel:  kthread+0x104/0x140
janv. 16 09:25:02 server.domain.tld kernel: Modules linked in: ipt_REJECT nf_reject_ipv4 xt_tcpudp xt_multiport iptable_filter bpfilter intel_rapl_msr intel_rapl_common >
janv. 16 09:25:02 server.domain.tld kernel: R13: 000056133797d800 R14: 000056133797d320 R15: 000056133797d000
janv. 16 09:25:02 server.domain.tld kernel:  worker_thread+0x4d/0x400
janv. 16 09:25:02 server.domain.tld kernel: R10: 0000000000000008 R11: 0000000000000246 R12: 00000000ffffffff
janv. 16 09:25:02 server.domain.tld kernel: RBP: 000056133797d040 R08: 000056133797d800 R09: 0000000000000000
janv. 16 09:25:02 server.domain.tld kernel:  process_one_work+0x1eb/0x3b0
janv. 16 09:25:02 server.domain.tld kernel: RDX: 000056133797d320 RSI: 000056133797d800 RDI: 000056133797d040
janv. 16 09:25:02 server.domain.tld kernel: RAX: ffffffffffffffda RBX: 000056133797cfe0 RCX: 00007fe2c17892fb
janv. 16 09:25:02 server.domain.tld kernel:  netstamp_clear+0x34/0x40
janv. 16 09:25:02 server.domain.tld kernel: RSP: 002b:00007ffeb9f837d8 EFLAGS: 00000246 ORIG_RAX: 000000000000003b
janv. 16 09:25:02 server.domain.tld kernel:  static_key_disable+0x1b/0x30
janv. 16 09:25:02 server.domain.tld kernel: Code: Bad RIP value.
janv. 16 09:25:02 server.domain.tld kernel:  static_key_disable_cpuslocked+0x66/0x90
janv. 16 09:25:02 server.domain.tld kernel: RIP: 0033:0x7fe2c17892fb
janv. 16 09:25:02 server.domain.tld kernel:  jump_label_update+0x64/0xc0
janv. 16 09:25:02 server.domain.tld kernel:  __jump_label_update+0x115/0x120
janv. 16 09:25:02 server.domain.tld kernel:  entry_SYSCALL_64_after_hwframe+0x44/0xa9
janv. 16 09:25:02 server.domain.tld kernel:  arch_jump_label_transform_apply+0x32/0x50
janv. 16 09:25:02 server.domain.tld kernel:  do_syscall_64+0x57/0x1b0
janv. 16 09:25:02 server.domain.tld kernel:  text_poke_bp_batch+0xf7/0x160
janv. 16 09:25:02 server.domain.tld kernel:  __x64_sys_execve+0x39/0x50
janv. 16 09:25:02 server.domain.tld kernel:  __text_poke+0x21a/0x4a0
janv. 16 09:25:02 server.domain.tld kernel:  __do_execve_file.isra.0+0x4fe/0x830
janv. 16 09:25:02 server.domain.tld kernel:  ? netif_receive_skb+0x29/0x160
janv. 16 09:25:02 server.domain.tld kernel:  switch_mm_irqs_off+0x19b/0x500
janv. 16 09:25:02 server.domain.tld kernel:  search_binary_handler+0x8b/0x1c0
janv. 16 09:25:02 server.domain.tld kernel:  load_new_mm_cr3+0x4d/0xf0
janv. 16 09:25:02 server.domain.tld kernel:  ? ima_bprm_check+0x87/0xb0
janv. 16 09:25:02 server.domain.tld kernel:  xen_write_cr3+0xf9/0x160
janv. 16 09:25:02 server.domain.tld kernel:  load_elf_binary+0x2f7/0x10f0
janv. 16 09:25:02 server.domain.tld kernel: Call Trace:
janv. 16 09:25:02 server.domain.tld kernel:  flush_old_exec+0x1b5/0x240
janv. 16 09:25:02 server.domain.tld kernel: CR2: 0000561337976bc8 CR3: 00000000250ee000 CR4: 0000000000040660
janv. 16 09:25:02 server.domain.tld kernel: CS:  10000e030 DS: 0000 ES: 0000 CR0: 0000000080050033
janv. 16 09:25:02 server.domain.tld kernel:  mmput+0x5d/0x130
janv. 16 09:25:02 server.domain.tld kernel: FS:  00007fe2c16a0740(0000) GS:ffff88807d200000(0000) knlGS:0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: R13: ffff88807d217300 R14: 0000000000000020 R15: ffff8880743ee600
janv. 16 09:25:02 server.domain.tld kernel:  ? _cond_resched+0x19/0x30
janv. 16 09:25:02 server.domain.tld kernel: R10: 0000000000007ff0 R11: 00000000000375e4 R12: 0000000000000001
janv. 16 09:25:02 server.domain.tld kernel: RBP: ffffc90040b87c78 R08: 0000000000000000 R09: 0000000000000000
janv. 16 09:25:02 server.domain.tld kernel:  exit_mmap+0xb4/0x1b0
janv. 16 09:25:02 server.domain.tld kernel: RDX: 0000000000000000 RSI: 0000000000000001 RDI: ffff88807d217b10
janv. 16 09:25:02 server.domain.tld kernel: RAX: ffffffffffffffea RBX: ffff8880250ee000 RCX: 0000000000000001
janv. 16 09:25:02 server.domain.tld kernel:  unmap_vmas+0x79/0xf0
janv. 16 09:25:02 server.domain.tld kernel: RSP: e02b:ffffc90040b87c48 EFLAGS: 00010002
janv. 16 09:25:02 server.domain.tld kernel:  unmap_single_vma+0x7f/0xf0
janv. 16 09:25:02 server.domain.tld kernel: Code: 05 00 10 00 81 e8 fa 83 dd 00 48 89 c1 49 89 45 18 48 c1 e9 3f 48 89 ce e9 fa fe ff ff 49 c7 45 18 ea ff ff ff be 01 00>
janv. 16 09:25:02 server.domain.tld kernel:  unmap_page_range+0x2d7/0x4e0
janv. 16 09:25:02 server.domain.tld kernel: RIP: e030:xen_mc_flush+0x1a6/0x1d0
janv. 16 09:25:02 server.domain.tld kernel: Call Trace:
janv. 16 09:25:02 server.domain.tld kernel: Workqueue: events netstamp_clear
janv. 16 09:25:02 server.domain.tld kernel: CR2: ffff88807931a398 CR3: 0000000001e6e000 CR4: 0000000000040660
janv. 16 09:25:02 server.domain.tld kernel: CS:  e030 DS: 0000 ES: 0000 CR0: 0000000080050033
janv. 16 09:25:02 server.domain.tld kernel: CPU: 0 PID: 1417825 Comm: kworker/0:2 Tainted: G        W         5.5.4-050504-generic #202002150446
janv. 16 09:25:02 server.domain.tld kernel: FS:  00007fe2c16a0740(0000) GS:ffff88807d240000(0000) knlGS:0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: R13: ffffc90040c9bc60 R14: ffff88807931a398 R15: 0000561336c74000
janv. 16 09:25:02 server.domain.tld kernel: Modules linked in: ipt_REJECT nf_reject_ipv4 xt_tcpudp xt_multiport iptable_filter bpfilter intel_rapl_msr intel_rapl_common >
janv. 16 09:25:02 server.domain.tld kernel: R10: 0000000000000001 R11: 0000000000000001 R12: 0000561336c73000
janv. 16 09:25:02 server.domain.tld kernel: RBP: ffffc90040c9bb30 R08: ffffea0001bd5300 R09: 0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: WARNING: CPU: 0 PID: 1417825 at arch/x86/xen/multicalls.c:102 xen_mc_flush+0x1a6/0x1d0
janv. 16 09:25:02 server.domain.tld kernel: RDX: 0000000000000000 RSI: 0000561336c73000 RDI: 0000001ad394c125
janv. 16 09:25:02 server.domain.tld kernel: RAX: ffffea0001bd5300 RBX: 0000001ad394c125 RCX: 0000000000000125
janv. 16 09:25:02 server.domain.tld kernel: ------------[ cut here ]------------
janv. 16 09:25:02 server.domain.tld kernel:   call  1: op=26 arg=[ffff88807d217b10] result=-22
janv. 16 09:25:02 server.domain.tld kernel: RSP: e02b:ffffc90040c9ba88 EFLAGS: 00010202
janv. 16 09:25:02 server.domain.tld kernel: 1 of 1 multicall(s) failed: cpu 0
janv. 16 09:25:02 server.domain.tld kernel: Code: 00 10 00 00 e8 15 f6 ff ff 48 83 7d 98 00 49 89 c0 74 09 48 85 c0 0f 85 91 05 00 00 41 f6 45 20 01 0f 84 b5 02 00 00 49>
janv. 16 09:25:02 server.domain.tld kernel: RIP: e030:zap_pte_range.isra.0+0x19c/0x880
janv. 16 09:25:02 server.domain.tld kernel: ---[ end trace 778135425d0d7b84 ]---
janv. 16 09:25:02 server.domain.tld kernel: CPU: 1 PID: 1426643 Comm: bash Tainted: G        W         5.5.4-050504-generic #202002150446
janv. 16 09:25:02 server.domain.tld kernel: Oops: 0003 [#1] SMP NOPTI
janv. 16 09:25:02 server.domain.tld kernel:  ret_from_fork+0x35/0x40
janv. 16 09:25:02 server.domain.tld kernel:  ? kthread_park+0x90/0x90
janv. 16 09:25:02 server.domain.tld kernel: PGD 260c067 P4D 260c067 PUD 3000067 PMD 7ff40067 PTE 801000007931a065
janv. 16 09:25:02 server.domain.tld kernel: #PF: error_code(0x0003) - permissions violation
janv. 16 09:25:02 server.domain.tld kernel:  ? process_one_work+0x3b0/0x3b0
janv. 16 09:25:02 server.domain.tld kernel: #PF: supervisor write access in kernel mode
janv. 16 09:25:02 server.domain.tld kernel: BUG: unable to handle page fault for address: ffff88807931a398
janv. 16 09:25:02 server.domain.tld kernel:  kthread+0x104/0x140
janv. 16 09:25:02 server.domain.tld kernel:  worker_thread+0x4d/0x400
janv. 16 09:25:02 server.domain.tld kernel:  process_one_work+0x1eb/0x3b0
janv. 16 09:25:02 server.domain.tld kernel:  netstamp_clear+0x34/0x40
janv. 16 09:25:02 server.domain.tld kernel:  static_key_disable+0x1b/0x30
janv. 16 09:25:02 server.domain.tld kernel:  static_key_disable_cpuslocked+0x66/0x90
janv. 16 09:25:02 server.domain.tld kernel:  jump_label_update+0x64/0xc0
janv. 16 09:25:02 server.domain.tld kernel:  __jump_label_update+0x115/0x120
janv. 16 09:25:02 server.domain.tld kernel:  arch_jump_label_transform_apply+0x32/0x50
janv. 16 09:25:02 server.domain.tld kernel:   call 19: op=14 arg=[ffff888001efc000] result=-16
janv. 16 09:25:02 server.domain.tld kernel:  text_poke_bp_batch+0xf7/0x160
janv. 16 09:25:02 server.domain.tld kernel:   call 17: op=14 arg=[ffff88801c9de000] result=-16
janv. 16 09:25:02 server.domain.tld kernel:   call 16: op=14 arg=[ffff88807c36d000] result=-16
janv. 16 09:25:02 server.domain.tld kernel:  __text_poke+0x21a/0x4a0
janv. 16 09:25:02 server.domain.tld kernel:   call 14: op=14 arg=[ffff8880735d1000] result=-16
janv. 16 09:25:02 server.domain.tld kernel:   call 12: op=14 arg=[ffff888076aea000] result=-16
janv. 16 09:25:02 server.domain.tld kernel:  ? __netif_receive_skb_core+0x37/0xf70
janv. 16 09:25:02 server.domain.tld kernel:  switch_mm_irqs_off+0x19b/0x500
janv. 16 09:25:02 server.domain.tld kernel:   call 10: op=14 arg=[ffff888074fc7000] result=-16
janv. 16 09:25:02 server.domain.tld kernel:   call  9: op=14 arg=[ffff888076dbe000] result=-16
janv. 16 09:25:02 server.domain.tld kernel:  load_new_mm_cr3+0x4d/0xf0
janv. 16 09:25:02 server.domain.tld kernel:   call  8: op=14 arg=[ffff888010097000] result=-16
janv. 16 09:25:02 server.domain.tld kernel:   call  6: op=14 arg=[ffff88807931a000] result=-16
janv. 16 09:25:02 server.domain.tld kernel:  xen_write_cr3+0xf9/0x160
janv. 16 09:25:02 server.domain.tld kernel:   call  4: op=14 arg=[ffff88800293f000] result=-16
janv. 16 09:25:02 server.domain.tld kernel:   call  3: op=14 arg=[ffff888002ebf000] result=-16
janv. 16 09:25:02 server.domain.tld kernel: Call Trace:
janv. 16 09:25:02 server.domain.tld kernel: CR2: 0000561337976bc8 CR3: 00000000250ee000 CR4: 0000000000040660
janv. 16 09:25:02 server.domain.tld kernel:   call  2: op=14 arg=[ffff88807b30a000] result=-16
janv. 16 09:25:02 server.domain.tld kernel: 12 of 20 multicall(s) failed: cpu 1
janv. 16 09:25:02 server.domain.tld kernel: CS:  10000e030 DS: 0000 ES: 0000 CR0: 0000000080050033
janv. 16 09:25:02 server.domain.tld kernel: ---[ end trace 778135425d0d7b83 ]---
janv. 16 09:25:02 server.domain.tld kernel: FS:  00007fe2c16a0740(0000) GS:ffff88807d200000(0000) knlGS:0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: R13: 000056133797d800 R14: 000056133797d320 R15: 000056133797d000
janv. 16 09:25:02 server.domain.tld kernel: R10: 0000000000000008 R11: 0000000000000246 R12: 00000000ffffffff
janv. 16 09:25:02 server.domain.tld kernel: RBP: 000056133797d040 R08: 000056133797d800 R09: 0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: RDX: 000056133797d320 RSI: 000056133797d800 RDI: 000056133797d040
janv. 16 09:25:02 server.domain.tld kernel: RAX: ffffffffffffffda RBX: 000056133797cfe0 RCX: 00007fe2c17892fb
janv. 16 09:25:02 server.domain.tld kernel: RSP: 002b:00007ffeb9f837d8 EFLAGS: 00000246 ORIG_RAX: 000000000000003b
janv. 16 09:25:02 server.domain.tld kernel: Code: Bad RIP value.
janv. 16 09:25:02 server.domain.tld kernel: R13: ffff88807d217300 R14: 0000000000000020 R15: ffff8880743ee600
janv. 16 09:25:02 server.domain.tld kernel: R10: 0000000000007ff0 R11: ffffffff826654c8 R12: 0000000000000001
janv. 16 09:25:02 server.domain.tld kernel: RBP: ffffc90040b87c78 R08: 0000000000000000 R09: 0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: RDX: 0000000000000000 RSI: 0000000000000001 RDI: ffff88807d217b10
janv. 16 09:25:02 server.domain.tld kernel: RAX: ffffffffffffffea RBX: ffff8880250ee000 RCX: 0000000000000001
janv. 16 09:25:02 server.domain.tld kernel: RSP: e02b:ffffc90040b87c48 EFLAGS: 00010002
janv. 16 09:25:02 server.domain.tld kernel: RIP: 0033:0x7fe2c17892fb
janv. 16 09:25:02 server.domain.tld kernel: Code: 05 00 10 00 81 e8 fa 83 dd 00 48 89 c1 49 89 45 18 48 c1 e9 3f 48 89 ce e9 fa fe ff ff 49 c7 45 18 ea ff ff ff be 01 00>
janv. 16 09:25:02 server.domain.tld kernel:  entry_SYSCALL_64_after_hwframe+0x44/0xa9
janv. 16 09:25:02 server.domain.tld kernel: RIP: e030:xen_mc_flush+0x1a6/0x1d0
janv. 16 09:25:02 server.domain.tld kernel:  do_syscall_64+0x57/0x1b0
janv. 16 09:25:02 server.domain.tld kernel: Workqueue: events netstamp_clear
janv. 16 09:25:02 server.domain.tld kernel:  __x64_sys_execve+0x39/0x50
janv. 16 09:25:02 server.domain.tld kernel: CPU: 0 PID: 1417825 Comm: kworker/0:2 Not tainted 5.5.4-050504-generic #202002150446
janv. 16 09:25:02 server.domain.tld kernel:  __do_execve_file.isra.0+0x4fe/0x830
janv. 16 09:25:02 server.domain.tld kernel:  crc32_pclmul
janv. 16 09:25:02 server.domain.tld kernel:  search_binary_handler+0x8b/0x1c0
janv. 16 09:25:02 server.domain.tld kernel:  drm ip_tables x_tables autofs4
janv. 16 09:25:02 server.domain.tld kernel:  ? ima_bprm_check+0x87/0xb0
janv. 16 09:25:02 server.domain.tld kernel:  intel_rapl_perf quota_v2 quota_tree sch_fq_codel
janv. 16 09:25:02 server.domain.tld kernel:  load_elf_binary+0x2f7/0x10f0
janv. 16 09:25:02 server.domain.tld kernel:  crypto_simd cryptd glue_helper
janv. 16 09:25:02 server.domain.tld kernel:  flush_old_exec+0x1b5/0x240
janv. 16 09:25:02 server.domain.tld kernel:  crct10dif_pclmul ghash_clmulni_intel aesni_intel
janv. 16 09:25:02 server.domain.tld kernel:  mmput+0x5d/0x130
janv. 16 09:25:02 server.domain.tld kernel:  intel_rapl_msr intel_rapl_common sb_edac
janv. 16 09:25:02 server.domain.tld kernel:  ? _cond_resched+0x19/0x30
janv. 16 09:25:02 server.domain.tld kernel:  xt_multiport iptable_filter bpfilter
janv. 16 09:25:02 server.domain.tld kernel:  ? xen_write_cr3+0xa4/0x160
janv. 16 09:25:02 server.domain.tld kernel:  ipt_REJECT nf_reject_ipv4 xt_tcpudp
janv. 16 09:25:02 server.domain.tld kernel:  exit_mmap+0x66/0x1b0
janv. 16 09:25:02 server.domain.tld kernel: Modules linked in:
janv. 16 09:25:02 server.domain.tld kernel: WARNING: CPU: 0 PID: 1417825 at arch/x86/xen/multicalls.c:102 xen_mc_flush+0x1a6/0x1d0
janv. 16 09:25:02 server.domain.tld kernel:  xen_exit_mmap+0x19b/0x1c0
janv. 16 09:25:02 server.domain.tld kernel:  __xen_pgd_unpin+0xfd/0x210
janv. 16 09:25:02 server.domain.tld kernel: ------------[ cut here ]------------
janv. 16 09:25:02 server.domain.tld kernel: Call Trace:
janv. 16 09:25:02 server.domain.tld kernel: CR2: 00007f1dfdd3ff30 CR3: 0000000001e6e000 CR4: 0000000000040660
janv. 16 09:25:02 server.domain.tld kernel: CS:  10000e030 DS: 0000 ES: 0000 CR0: 0000000080050033
janv. 16 09:25:02 server.domain.tld kernel: FS:  00007fe2c16a0740(0000) GS:ffff88807d240000(0000) knlGS:0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: R13: ffff88807d257300 R14: ffff8880fb30a000 R15: 0000000000000000
janv. 16 09:25:02 server.domain.tld kernel: R10: ffff88807c439fb0 R11: 0000000000006f73 R12: 0000000000000014
janv. 16 09:25:02 server.domain.tld kernel: RBP: ffffc90040c9bbd8 R08: ffff88807d2577d0 R09: ffff88801c9df000
janv. 16 09:25:02 server.domain.tld kernel: RDX: 0000000000000000 RSI: 000000000000000c RDI: ffff88807d257310
janv. 16 09:25:02 server.domain.tld kernel: RAX: ffff88807d257818 RBX: 0000777f80000000 RCX: ffff88807d257818
janv. 16 09:25:02 server.domain.tld kernel: RSP: e02b:ffffc90040c9bba8 EFLAGS: 00010006
janv. 16 09:25:02 server.domain.tld kernel: Code: 05 00 10 00 81 e8 fa 83 dd 00 48 89 c1 49 89 45 18 48 c1 e9 3f 48 89 ce e9 fa fe ff ff 49 c7 45 18 ea ff ff ff be 01 00>
janv. 16 09:25:02 server.domain.tld kernel: RIP: e030:xen_mc_flush+0x1a6/0x1d0
janv. 16 09:25:02 server.domain.tld kernel: CPU: 1 PID: 1426643 Comm: bash Not tainted 5.5.4-050504-generic #202002150446
janv. 16 09:25:02 server.domain.tld kernel: Modules linked in: ipt_REJECT nf_reject_ipv4 xt_tcpudp xt_multiport iptable_filter bpfilter intel_rapl_msr intel_rapl_common >
janv. 16 09:25:02 server.domain.tld kernel: WARNING: CPU: 1 PID: 1426643 at arch/x86/xen/multicalls.c:102 xen_mc_flush+0x1a6/0x1d0


```

My host is Gandi.net and the server is virtualized (if it can help)

I also changed the kernel from a 5.4 to 5.5.4 to test if the issue could comes from it, but no : the crashs are still there...

Any idea what could I do now ?

---

### Post by slickymaster on 2021-01-18
*Thread moved to **Virtualisation**.*

---

### Post by hedy-dargere on 2021-02-25
thanks for the move :)

However, I still have random crash of my server.
And I really don't know what can I do to solve it. After the kernel change, the crashes seams occurs less often but they are still there.

In you opinion, is the problem can comes from the Xen supervisor (Gandi.net side), or is it obviously on my system server side ?

---

