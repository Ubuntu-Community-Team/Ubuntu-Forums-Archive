---
title: "kernel crash?"
date: 2009-07-06
forum: Server Platforms
---

### Post by cdenley on 2009-07-06
Our mail server seems to have been unresponsive all weekend until it was rebooted this morning. There are a bunch of call traces in /var/log/messages. Does this provide a clue about what happened?

[ATTACH]120128[/ATTACH]

Here is the first of many call traces included in the above file
```

Jul  4 09:36:08 zimbra kernel: [5143174.888362] CPU 1:
Jul  4 09:36:08 zimbra kernel: [5143174.888363] Modules linked in: xt_multiport parport_pc lp parport loop ipv6 iTCO_wdt iTCO_vendor_support psmouse evdev pcspkr shpchp container button pci_hotplug ipt_REJECT xt_tcpudp nf_conntrack_ipv4 xt_state nf_conntrack iptable_filter ip_tables x_tables ext3 jbd mbcache ata_piix ata_generic sg sr_mod cdrom sd_mod pata_acpi ahci libata floppy ehci_hcd scsi_mod uhci_hcd usbcore e1000 raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear md_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
Jul  4 09:36:08 zimbra kernel: [5143174.888389] Pid: 28657, comm: smtpd Not tainted 2.6.24-22-server #1
Jul  4 09:36:08 zimbra kernel: [5143174.888391] RIP: 0010:[get_index+0x0/0x50]  [get_index+0x0/0x50] get_index+0x0/0x50
Jul  4 09:36:08 zimbra kernel: [5143174.888397] RSP: 0018:ffff8101072afdf8  EFLAGS: 00000283
Jul  4 09:36:08 zimbra kernel: [5143174.888398] RAX: 00000000000001ff RBX: ffff8101224dd4f8 RCX: ffff8101072afe10
Jul  4 09:36:08 zimbra kernel: [5143174.888399] RDX: ffff8101072afe18 RSI: ffff810042ee8b48 RDI: ffff8101224dd4f8
Jul  4 09:36:08 zimbra kernel: [5143174.888400] RBP: ffff81000102b7b8 R08: ffff8101072afe18 R09: 00000000fffffffe
Jul  4 09:36:08 zimbra kernel: [5143174.888401] R10: 0000000000000000 R11: 00000000000001e8 R12: 0000000000000008
Jul  4 09:36:08 zimbra kernel: [5143174.888402] R13: 0000000000000008 R14: 0000000000000008 R15: ffff81000102b7f8
Jul  4 09:36:08 zimbra kernel: [5143174.888403] FS:  0000000000000000(0000) GS:ffff81012b801800(0000) knlGS:0000000000000000
Jul  4 09:36:08 zimbra kernel: [5143174.888404] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Jul  4 09:36:08 zimbra kernel: [5143174.888405] CR2: 00007f2203ee8798 CR3: 0000000000201000 CR4: 00000000000006e0
Jul  4 09:36:08 zimbra kernel: [5143174.888406] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jul  4 09:36:08 zimbra kernel: [5143174.888408] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jul  4 09:36:08 zimbra kernel: [5143174.888408] 
Jul  4 09:36:08 zimbra kernel: [5143174.888409] Call Trace:
Jul  4 09:36:08 zimbra kernel: [5143174.888414]  [prio_tree_remove+0x66/0xf0] prio_tree_remove+0x66/0xf0
Jul  4 09:36:08 zimbra kernel: [5143174.888419]  [unlink_file_vma+0x3f/0x60] unlink_file_vma+0x3f/0x60
Jul  4 09:36:08 zimbra kernel: [5143174.888421]  [free_pgtables+0x69/0xe0] free_pgtables+0x69/0xe0
Jul  4 09:36:08 zimbra kernel: [5143174.888423]  [exit_mmap+0x92/0x100] exit_mmap+0x92/0x100
Jul  4 09:36:08 zimbra kernel: [5143174.888426]  [mmput+0x1e/0xb0] mmput+0x1e/0xb0
Jul  4 09:36:08 zimbra kernel: [5143174.888428]  [do_exit+0x1c0/0x950] do_exit+0x1c0/0x950
Jul  4 09:36:08 zimbra kernel: [5143174.888431]  [<ffffffff802364b0>] default_wake_function+0x0/0x10
Jul  4 09:36:08 zimbra kernel: [5143174.888434]  [do_group_exit+0x2c/0x80] do_group_exit+0x2c/0x80
Jul  4 09:36:08 zimbra kernel: [5143174.888436]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Jul  4 09:36:08 zimbra kernel: [5143174.888439] 

```

The same call traces are logged in /var/log/kern.log:

[ATTACH]120136[/ATTACH]

```

Jul  4 09:36:08 zimbra kernel: [5143174.888342] BUG: soft lockup - CPU#1 stuck for 11s! [smtpd:28657]
Jul  4 09:36:08 zimbra kernel: [5143174.888362] CPU 1:
Jul  4 09:36:08 zimbra kernel: [5143174.888363] Modules linked in: xt_multiport parport_pc lp parport loop ipv6 iTCO_wdt iTCO_vendor_support psmouse evdev pcspkr shpchp container button pci_hotplug ipt_REJECT xt_tcpudp nf_conntrack_ipv4 xt_state nf_conntrack iptable_filter ip_tables x_tables ext3 jbd mbcache ata_piix ata_generic sg sr_mod cdrom sd_mod pata_acpi ahci libata floppy ehci_hcd scsi_mod uhci_hcd usbcore e1000 raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear md_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
Jul  4 09:36:08 zimbra kernel: [5143174.888389] Pid: 28657, comm: smtpd Not tainted 2.6.24-22-server #1
Jul  4 09:36:08 zimbra kernel: [5143174.888391] RIP: 0010:[get_index+0x0/0x50]  [get_index+0x0/0x50] get_index+0x0/0x50
Jul  4 09:36:08 zimbra kernel: [5143174.888397] RSP: 0018:ffff8101072afdf8  EFLAGS: 00000283
Jul  4 09:36:08 zimbra kernel: [5143174.888398] RAX: 00000000000001ff RBX: ffff8101224dd4f8 RCX: ffff8101072afe10
Jul  4 09:36:08 zimbra kernel: [5143174.888399] RDX: ffff8101072afe18 RSI: ffff810042ee8b48 RDI: ffff8101224dd4f8
Jul  4 09:36:08 zimbra kernel: [5143174.888400] RBP: ffff81000102b7b8 R08: ffff8101072afe18 R09: 00000000fffffffe
Jul  4 09:36:08 zimbra kernel: [5143174.888401] R10: 0000000000000000 R11: 00000000000001e8 R12: 0000000000000008
Jul  4 09:36:08 zimbra kernel: [5143174.888402] R13: 0000000000000008 R14: 0000000000000008 R15: ffff81000102b7f8
Jul  4 09:36:08 zimbra kernel: [5143174.888403] FS:  0000000000000000(0000) GS:ffff81012b801800(0000) knlGS:0000000000000000
Jul  4 09:36:08 zimbra kernel: [5143174.888404] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Jul  4 09:36:08 zimbra kernel: [5143174.888405] CR2: 00007f2203ee8798 CR3: 0000000000201000 CR4: 00000000000006e0
Jul  4 09:36:08 zimbra kernel: [5143174.888406] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jul  4 09:36:08 zimbra kernel: [5143174.888408] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jul  4 09:36:08 zimbra kernel: [5143174.888408] 
Jul  4 09:36:08 zimbra kernel: [5143174.888409] Call Trace:
Jul  4 09:36:08 zimbra kernel: [5143174.888414]  [prio_tree_remove+0x66/0xf0] prio_tree_remove+0x66/0xf0
Jul  4 09:36:08 zimbra kernel: [5143174.888419]  [unlink_file_vma+0x3f/0x60] unlink_file_vma+0x3f/0x60
Jul  4 09:36:08 zimbra kernel: [5143174.888421]  [free_pgtables+0x69/0xe0] free_pgtables+0x69/0xe0
Jul  4 09:36:08 zimbra kernel: [5143174.888423]  [exit_mmap+0x92/0x100] exit_mmap+0x92/0x100
Jul  4 09:36:08 zimbra kernel: [5143174.888426]  [mmput+0x1e/0xb0] mmput+0x1e/0xb0
Jul  4 09:36:08 zimbra kernel: [5143174.888428]  [do_exit+0x1c0/0x950] do_exit+0x1c0/0x950
Jul  4 09:36:08 zimbra kernel: [5143174.888431]  [<ffffffff802364b0>] default_wake_function+0x0/0x10
Jul  4 09:36:08 zimbra kernel: [5143174.888434]  [do_group_exit+0x2c/0x80] do_group_exit+0x2c/0x80
Jul  4 09:36:08 zimbra kernel: [5143174.888436]  [system_call+0x7e/0x83] system_call+0x7e/0x83

```

---

### Post by cdenley on 2009-07-06
Also, the local console was unusable and printing call traces until it was rebooted, even though it was no longer logging them. Is there any way to determine what caused this?

---

