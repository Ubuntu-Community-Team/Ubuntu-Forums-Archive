---
title: "quota &amp; reiserfs"
date: 2007-03-12
forum: Server Platforms
---

### Post by gostek_1 on 2007-03-12
I'm no very experienced with adminstrative tasks and i have a probem. I'm trying to set up user filesystems quotas, and i get system crash. I don't know if it is a bug or just my misconfiguration.
I've had successfully set up quotas at /home partition, but when i changed fstab and add userquota option to /var partition i got this during system startup:

[42949409.310000] ReiserFS: hda8: found reiserfs format "3.6" with standard journal
[42949410.440000] ReiserFS: hda8: using ordered data mode
[42949410.460000] ReiserFS: hda8: journal params: device hda8, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[42949410.460000] ReiserFS: hda8: checking transaction log (hda8)
[42949410.480000] ReiserFS: hda8: Using r5 hash to sort names
[42949534.290000] Unable to handle kernel paging request at virtual address ffd06000
[42949534.290000]  printing eip:
[42949534.290000] f8921703
[42949534.290000] *pde = 7b242066
[42949534.290000] Oops: 000b [#1]
[42949534.290000] SMP
[42949534.290000] Modules linked in: quota_v1 ext3 jbd ext2 dm_mod md_mod lp tsdev e1000 e100 mii parport_pc shpchp pci_hotplug parport hw_random floppy pcspkr serio_raw psmouse evdev reiserfs ide_generic uhci_hcd usbcore ide_cd cdrom ide_disk piix generic thermal processor fan fbcon tileblit font bitblit softcursor capability commoncap
[42949534.290000] CPU:    0
[42949534.290000] EIP:    0060:[<f8921703>]    Not tainted VLI
[42949534.290000] EFLAGS: 00010206   (2.6.15-28-server)
[42949534.290000] EIP is at _get_block_create_0+0x263/0x6f0 [reiserfs]
[42949534.290000] eax: 00000000   ebx: f178fc0c   ecx: 00000400   edx: 00001000
[42949534.290000] esi: ffd06000   edi: ffd06000   ebp: e07d50d8   esp: f178fb78
[42949534.290000] ds: 007b   es: 007b   ss: 0068
[42949534.290000] Process quotaon (pid: 3451, threadinfo=f178e000 task=c1be5030)
[42949534.290000] Stack: f178fdd8 e07d50d8 f178fbac 00000000 0000000f 00000003 00000001 00000000
[42949534.290000]        dfdbe000 f7d42b1c e07cab64 ffd06000 ffd06000 00000004 00000000 00000000
[42949534.290000]        00000000 00000000 00000000 c1adc2a8 00000000 c1adc5b4 00000005 e07cab64
[42949534.290000] Call Trace:
[42949534.290000]  [<f8922afb>] reiserfs_get_block+0xc7b/0x14e0 [reiserfs]
[42949534.290000]  [<c01f0010>] deadline_merged_requests+0x70/0x1c0
[42949534.290000]  [<c0270400>] wait_for_ready+0xd0/0xf0
[42949534.290000]  [<c01f0296>] deadline_dispatch_requests+0x86/0x180
[42949534.290000]  [<c01530e2>] bad_range+0x42/0x60
[42949534.290000]  [<f89437a1>] journal_mark_dirty+0x131/0x2d0 [reiserfs]
[42949534.290000]  [<c013c130>] autoremove_wake_function+0x0/0x60
[42949534.290000]  [<f8945088>] do_journal_end+0x9b8/0xb30 [reiserfs]
[42949534.290000]  [<f8932147>] reiserfs_quota_read+0x137/0x200 [reiserfs]
[42949534.290000]  [<f89439fc>] journal_end+0xbc/0x110 [reiserfs]
[42949534.290000]  [<f8ce22e6>] v1_check_quota_file+0x86/0xd0 [quota_v1]
[42949534.290000]  [<c01a812f>] vfs_quota_on_inode+0x21f/0x2f0
[42949534.290000]  [<c01a8275>] vfs_quota_on+0x75/0x80
[42949534.290000]  [<c018c65e>] dput+0xfe/0x210
[42949534.290000]  [<c0191d89>] mntput_no_expire+0x29/0xb0
[42949534.290000]  [<f8931fda>] reiserfs_quota_on+0xba/0xf0 [reiserfs]
[42949534.290000]  [<c01813ff>] getname+0xdf/0x110
[42949534.290000]  [<c01a96d6>] do_quotactl+0x406/0x4c0
[42949534.290000]  [<c018c64e>] dput+0xee/0x210
[42949534.290000]  [<c0191d89>] mntput_no_expire+0x29/0xb0
[42949534.290000]  [<c017c07c>] lookup_bdev+0x6c/0xa0
[42949534.290000]  [<c01c9f30>] capable+0x20/0x40
[42949534.290000]  [<c01a8d7e>] generic_quotactl_valid+0xbe/0x1e0
[42949534.290000]  [<c01a8ff5>] check_quotactl_valid+0x45/0xb0
[42949534.290000]  [<c01a9861>] sys_quotactl+0xd1/0x103
[42949534.290000]  [<c0103313>] sysenter_past_esp+0x54/0x75
[42949534.290000] Code: b4 fe ff ff 8d 74 26 00 8b 84 24 c0 00 00 00 8b 90 a0 00 00 00 8b 7c 24 2c 31 c0 01 fe 89 74 24 30 89 f7 8b 52 0c 89 d1 c1 e9 02 <f3> ab f6 c2 02 74 02 66 ab f6 c2 01 74 01 aa 0f b7 55 16 66 85

/dev/hda8 is my /var.
The hardware seems to be fine. Is it possible that there is an error on /var filesystem? fsck passes and fixes all errors. Should I report a bug? (never done it)
My OS is ubuntu-server-6.06 LTS and kernel 2.6.15-28-server #1 SMP

---

