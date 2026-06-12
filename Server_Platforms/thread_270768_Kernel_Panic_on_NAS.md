---
title: "Kernel Panic on NAS"
date: 2006-10-03
forum: Server Platforms
---

### Post by scorch_jb on 2006-10-03
I'm trying to get Ubuntu to work for us on a large NAS that we've purchased.  It uses 3ware drive controllers, so I'm using the driver in the 2.6.15-26-server kernel.  

The thing works for about 1 week or so and then the kernel panics and I can't reboot the system.  Below are the errors that I'm seeing.  The two things that jump out are the smbd process and the resierfs file system.  I don't know enough about kernel panics to identify the offending driver/application, can someone give me some ideas?

Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] Unable to handle kernel NULL pointer dereference at virtual address 00000000
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  printing eip:
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] f8988048
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] *pde = 23397001
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] Oops: 0000 [#1]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] SMP 
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] Modules linked in: vmnet parport_pc vmmon af_packet ipv6 dm_mod md_mod lp parport pcspkr e1000 psmouse serio_raw hw_random shpchp pci_hotplug sg tsdev sr_mod cdrom evdev usbhid reiserfs usb_storage ide_generic ehci_hcd uhci_hcd usbcore 3w_xxxx sd_mod 3w_9xxx scsi_mod thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] CPU:    0
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] EIP:    0060:[pg0+944951368/1069167616]    Tainted: P      VLI
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] EFLAGS: 00010282   (2.6.15-26-server) 
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] EIP is at scan_bitmap_block+0x48/0x320 [reiserfs]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] eax: 00008a97   ebx: 00003196   ecx: 00007fff   edx: 00000000
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] esi: 00003196   edi: f8d29cb0   ebp: d5565c70   esp: d5565c10
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] ds: 007b   es: 007b   ss: 0068
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] Process smbd (pid: 22113, threadinfo=d5564000 task=dfec4a90)
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] Stack: 00000000 17a67001 00000000 179e0001 10000000 f76ab000 00000000 d5565dd4 
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]        00003196 00003196 00003196 00003196 f8988588 d5565f38 00003196 d5565c70 
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]        00007400 00000001 00000011 00000001 00001000 00003195 000073ff 00008000 
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] Call Trace:
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  [pg0+944952712/1069167616] scan_bitmap+0x148/0x260 [reiserfs]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  [pg0+944958087/1069167616] reiserfs_allocate_blocknrs+0x187/0x640 [reiserfs]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  [pg0+945128879/1069167616] journal_begin+0x7f/0x140 [reiserfs]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  [pg0+945014426/1069167616] reiserfs_allocate_blocks_for_region+0x27a/0x15a0 [reiserfs]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  [alloc_buffer_head+62/80] alloc_buffer_head+0x3e/0x50
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  [pg0+944988703/1069167616] make_cpu_key+0x4f/0x60 [reiserfs]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  [pg0+945087872/1069167616] pathrelse+0x30/0x50 [reiserfs]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  [pg0+945025842/1069167616] reiserfs_file_write+0x732/0x770 [reiserfs]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  [fasync_helper+51/272] fasync_helper+0x33/0x110
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  [locks_delete_lock+219/272] locks_delete_lock+0xdb/0x110
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  [__posix_lock_file+399/1520] __posix_lock_file+0x18f/0x5f0
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  [posix_test_lock+85/96] posix_test_lock+0x55/0x60
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  [fcntl_getlk64+406/448] fcntl_getlk64+0x196/0x1c0
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  [vfs_write+214/432] vfs_write+0xd6/0x1b0
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  [sys_pwrite64+128/144] sys_pwrite64+0x80/0x90
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  [sysenter_past_esp+84/117] sysenter_past_esp+0x54/0x75
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000] Code: 80 70 01 00 00 8b 50 08 8b 45 00 01 d7 8b 54 24 34 89 44 24 18 8b 42 10 85 c0 0f 84 cb 02 00 00 85 ff 0f 84 88 02 00 00 8b 57 04 <8b> 02 a8 04 0f 85 6e 02 00 00 8d b4 26 00 00 00 00 8d bc 27 00 
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.430000]  Badness in do_exit at kernel/exit.c:796
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.750000]  [do_exit+980/992] do_exit+0x3d4/0x3e0
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.760000]  [die+388/400] die+0x184/0x190
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.770000]  [do_page_fault+1004/1790] do_page_fault+0x3ec/0x6fe
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.780000]  [do_page_fault+0/1790] do_page_fault+0x0/0x6fe
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.790000]  [error_code+79/84] error_code+0x4f/0x54
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.800000]  [pg0+944951368/1069167616] scan_bitmap_block+0x48/0x320 [reiserfs]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.810000]  [pg0+944952712/1069167616] scan_bitmap+0x148/0x260 [reiserfs]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.810000]  [pg0+944958087/1069167616] reiserfs_allocate_blocknrs+0x187/0x640 [reiserfs]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.830000]  [pg0+945128879/1069167616] journal_begin+0x7f/0x140 [reiserfs]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.840000]  [pg0+945014426/1069167616] reiserfs_allocate_blocks_for_region+0x27a/0x15a0 [reiserfs]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.860000]  [alloc_buffer_head+62/80] alloc_buffer_head+0x3e/0x50
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.870000]  [pg0+944988703/1069167616] make_cpu_key+0x4f/0x60 [reiserfs]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.880000]  [pg0+945087872/1069167616] pathrelse+0x30/0x50 [reiserfs]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.890000]  [pg0+945025842/1069167616] reiserfs_file_write+0x732/0x770 [reiserfs]
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.900000]  [fasync_helper+51/272] fasync_helper+0x33/0x110
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.910000]  [locks_delete_lock+219/272] locks_delete_lock+0xdb/0x110
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.920000]  [__posix_lock_file+399/1520] __posix_lock_file+0x18f/0x5f0
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.930000]  [posix_test_lock+85/96] posix_test_lock+0x55/0x60
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.940000]  [fcntl_getlk64+406/448] fcntl_getlk64+0x196/0x1c0
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.950000]  [vfs_write+214/432] vfs_write+0xd6/0x1b0
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.960000]  [sys_pwrite64+128/144] sys_pwrite64+0x80/0x90
Sep 28 01:46:53 rlssecnas01 kernel: [43155751.970000]  [sysenter_past_esp+84/117] sysenter_past_esp+0x54/0x75

---

