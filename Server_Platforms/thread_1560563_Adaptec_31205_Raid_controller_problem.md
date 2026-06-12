---
title: "Adaptec 31205 Raid controller problem"
date: 2010-08-25
forum: Server Platforms
---

### Post by vandervyvere on 2010-08-25
Hi 
I hope someone can help me.

I have installed an Adaptec 31205 controller on a Dell PowerEdge 2900 server running Ubuntu 8.04 64 server . The problem I am getting is that every couple of hours or so it seems that Ubuntu looses its link to the controller. The raid array "/dev/sdb" is still visible on Ubuntu but I am ot able to do anything with it.
When I try and reboot the machine with "reboot" or "shutdown -r now" Ubuntu hangs on the following message "synching SCSI cache" or something like that. 
Then I have to cold reboot the machine :(.

See below the error message I found in the /var/log/messages file.

Aug 23 15:51:41 data4 kernel: [16532.911047] PGD 0
Aug 23 15:51:41 data4 kernel: [16532.911914] CPU 2
Aug 23 15:51:41 data4 kernel: [16532.912246] Modules linked in: ipv6 bonding iptable_filter ip_tables x_tables parport_pc lp parport loop joydev pcspkr dcdbas serio_raw psmouse button i5000_edac iTCO_wdt iTCO_vendor_support shpchp pci_hotplug edac_core evdev ext3 jbd mbcache sr_mod cdrom usbhid hid ata_piix sg sd_mod pata_acpi ata_generic ehci_hcd libata uhci_hcd aacraid usbcore megaraid_sas bnx2 scsi_mod thermal processor fan fuse vesafb fbcon tileblit font bitblit softcursor
Aug 23 15:51:41 data4 kernel: [16532.919527] Pid: 2271, comm: aacraid Not tainted 2.6.24-26-server #1
Aug 23 15:51:41 data4 kernel: [16532.920567] RIP: 0010:[aacraid:aac_command_thread+0xe9/0x7d0]  [aacraid:aac_command_thread+0xe9/0x7d0] :aacraid:aac_command_thread+0xe9/0x7d0
Aug 23 15:51:41 data4 kernel: [16532.922130] RSP: 0018:ffff81042a47de30  EFLAGS: 00010246
Aug 23 15:51:41 data4 kernel: [16532.922997] RAX: 0000000000000000 RBX: 00000000ffffffff RCX: 0000000000000002
Aug 23 15:51:41 data4 kernel: [16532.924168] RDX: ffff81042b427c60 RSI: 0000000000000286 RDI: ffff81042db64000
Aug 23 15:51:41 data4 kernel: [16532.925338] RBP: ffff81042b427c60 R08: ffff81042a47c000 R09: 00000000ffffffff
Aug 23 15:51:41 data4 kernel: [16532.926508] R10: ffff8100809cd000 R11: ffffffff80220720 R12: ffffffff880f1db0
Aug 23 15:51:41 data4 kernel: [16532.927678] R13: 0000000000000000 R14: 0000000000000000 R15: 0000000000000000
Aug 23 15:51:41 data4 kernel: [16532.928849] FS:  0000000000000000(0000) GS:ffff810430c01b80(0000) knlGS:0000000000000000
Aug 23 15:51:41 data4 kernel: [16532.930178] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Aug 23 15:51:41 data4 kernel: [16532.931117] CR2: 0000000000000060 CR3: 0000000000201000 CR4: 00000000000006e0
Aug 23 15:51:41 data4 kernel: [16532.932287] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 23 15:51:41 data4 kernel: [16532.933457] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 23 15:51:41 data4 kernel: [16532.934628] Process aacraid (pid: 2271, threadinfo ffff81042a47c000, task ffff81042a9957d0)
Aug 23 15:51:41 data4 kernel: [16532.936000] Stack:  0000000000000000 0000000000000000 ffff81042b427cc0 ffff81042b427cb0
Aug 23 15:51:41 data4 kernel: [16532.937384]  0000000000000000 ffff81042b427c60 0000000000000000 ffffffff80682c80
Aug 23 15:51:41 data4 kernel: [16532.938653]  0000000100185409 00000001009c29fd ffffffff8067f0a0 ffffffff80682c80
Aug 23 15:51:41 data4 kernel: [16532.939908] Call Trace:
Aug 23 15:51:41 data4 kernel: [16532.940320]  [<ffffffff80236540>] default_wake_function+0x0/0x10
Aug 23 15:51:41 data4 kernel: [16532.941307]  [aacraid:aac_command_thread+0x0/0x7d0] :aacraid:aac_command_thread+0x0/0x7d0
Aug 23 15:51:41 data4 kernel: [16532.942394]  [kthread+0x4b/0x80] kthread+0x4b/0x80
Aug 23 15:51:41 data4 kernel: [16532.943190]  [child_rip+0xa/0x12] child_rip+0xa/0x12
Aug 23 15:51:41 data4 kernel: [16532.944002]  [lapic_next_event+0x0/0x10] lapic_next_event+0x0/0x10
Aug 23 15:51:41 data4 kernel: [16532.944914]  [kthread+0x0/0x80] kthread+0x0/0x80
Aug 23 15:51:41 data4 kernel: [16532.945694]  [child_rip+0x0/0x12] child_rip+0x0/0x12
Aug 23 15:51:41 data4 kernel: [16532.946504]
Aug 23 15:51:41 data4 kernel: [16532.946735]
Aug 23 15:51:41 data4 kernel: [16532.946735] Code: 48 8b 78 60 e8 3e 05 38 f8 48 8b 4c 24 28 48 89 c6 48 8b 51
Aug 23 15:51:41 data4 kernel: [16532.949623]  RSP <ffff81042a47de30>
Aug 23 15:51:41 data4 kernel: [16533.039489] ---[ end trace 5d183e6f53604ab6 ]---

---

