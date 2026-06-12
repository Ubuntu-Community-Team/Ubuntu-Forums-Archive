---
title: "Keep getting errors, root FS gets remounted read only"
date: 2009-11-13
forum: Server Platforms
---

### Post by FuturePilot on 2009-11-13
I'm running Ubuntu 9.10 server edition on an old box I'm using as a server and this is the second time this has happened. Something causes the file system to get remounted as read only.  Here's the relevant part of dmesg

```
[542376.000032] ata1: lost interrupt (Status 0x0)
[542376.000063] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[542376.000091] ata1.00: cmd ca/00:08:6f:00:58/00:00:00:00:00/e4 tag 0 dma 4096 out
[542376.000093]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[542376.000127] ata1.00: status: { DRDY }
[542376.000166] ata1: soft resetting link
[542376.156176] ata1.00: NODEV after polling detection
[542376.156181] ata1.00: revalidation failed (errno=-2)
[542381.156043] ata1: soft resetting link
[542381.312171] ata1.00: NODEV after polling detection
[542381.312176] ata1.00: revalidation failed (errno=-2)
[542386.312047] ata1: soft resetting link
[542386.468173] ata1.00: NODEV after polling detection
[542386.468177] ata1.00: revalidation failed (errno=-2)
[542386.468211] ata1.00: disabled
[542386.468221] ata1.00: device reported invalid CHS sector 0
[542386.468254] ata1: soft resetting link
[542386.624074] ata1: EH complete
[542386.624100] sd 0:0:0:0: [sda] Unhandled error code
[542386.624104] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[542386.624109] end_request: I/O error, dev sda, sector 72876143
[542386.624145] Buffer I/O error on device sda1, logical block 9109510
[542386.624177] lost page write due to I/O error on sda1
[542386.624208] sd 0:0:0:0: [sda] Unhandled error code
[542386.624212] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[542386.624216] end_request: I/O error, dev sda, sector 72876095
[542386.624248] Buffer I/O error on device sda1, logical block 9109504
[542386.624280] lost page write due to I/O error on sda1
[542386.624284] Buffer I/O error on device sda1, logical block 9109505
[542386.624316] lost page write due to I/O error on sda1
[542386.624328] sd 0:0:0:0: [sda] Unhandled error code
[542386.624331] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[542386.624335] end_request: I/O error, dev sda, sector 72876167
[542386.624367] Buffer I/O error on device sda1, logical block 9109513
[542386.624399] lost page write due to I/O error on sda1
[542386.624404] Buffer I/O error on device sda1, logical block 9109514
[542386.624436] lost page write due to I/O error on sda1
[542386.624447] sd 0:0:0:0: [sda] Unhandled error code
[542386.624450] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[542386.624454] end_request: I/O error, dev sda, sector 72876823
[542386.624486] Buffer I/O error on device sda1, logical block 9109595
[542386.624518] lost page write due to I/O error on sda1
[542386.624528] sd 0:0:0:0: [sda] Unhandled error code
[542386.624531] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[542386.624535] end_request: I/O error, dev sda, sector 72991191
[542386.624567] Buffer I/O error on device sda1, logical block 9123891
[542386.624598] lost page write due to I/O error on sda1
[542386.624613] sd 0:0:0:0: [sda] Unhandled error code
[542386.624617] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[542386.624621] end_request: I/O error, dev sda, sector 63
[542386.624651] Buffer I/O error on device sda1, logical block 0
[542386.624682] lost page write due to I/O error on sda1
[542386.624691] sd 0:0:0:0: [sda] Unhandled error code
[542386.624694] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[542386.624698] end_request: I/O error, dev sda, sector 87
[542386.624729] Buffer I/O error on device sda1, logical block 3
[542386.624759] lost page write due to I/O error on sda1
[542386.624911] sd 0:0:0:0: [sda] Unhandled error code
[542386.624915] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[542386.624920] end_request: I/O error, dev sda, sector 76538631
[542386.624967] Aborting journal on device sda1.
[542386.625011] sd 0:0:0:0: [sda] Unhandled error code
[542386.625015] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[542386.625019] end_request: I/O error, dev sda, sector 76288079
[542386.625051] Buffer I/O error on device sda1, logical block 9536002
[542386.625082] lost page write due to I/O error on sda1
[542386.625102] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2278813 offset 0
[542386.625157] Remounting filesystem read-only
[542386.625230] ------------[ cut here ]------------
[542386.625244] WARNING: at /build/buildd/linux-2.6.31/fs/buffer.c:1152 mark_buffer_dirty+0x70/0x90()
[542386.625248] Hardware name: OptiPlex GX260               
[542386.625250] Modules linked in: ipt_REJECT ipt_LOG xt_limit xt_tcpudp xt_state ipt_addrtype ip6table_filter ip6_tables nf_nat_irc nf_conntrack_irc snd_intel8x0 nf_nat_ftp nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 snd_ac97_codec ac97_bus nf_conntrack_ftp lp ppdev snd_pcm snd_timer psmouse parport_pc snd soundcore snd_page_alloc pcspkr serio_raw intel_agp nf_conntrack iptable_filter parport ip_tables agpgart x_tables shpchp dell_wmi dcdbas e1000 floppy
[542386.625298] Pid: 1616, comm: uptimed Not tainted 2.6.31-14-generic-pae #48-Ubuntu
[542386.625301] Call Trace:
[542386.625310]  [<c0146a1d>] warn_slowpath_common+0x6d/0xa0
[542386.625315]  [<c020cb70>] ? mark_buffer_dirty+0x70/0x90
[542386.625319]  [<c020cb70>] ? mark_buffer_dirty+0x70/0x90
[542386.625324]  [<c0146a65>] warn_slowpath_null+0x15/0x20
[542386.625328]  [<c020cb70>] mark_buffer_dirty+0x70/0x90
[542386.625335]  [<c024e215>] T.973+0x45/0x70
[542386.625340]  [<c024e2a6>] ext3_handle_error+0x66/0xb0
[542386.625346]  [<c057419e>] ? printk+0x18/0x1a
[542386.625350]  [<c024e631>] ext3_error+0x51/0x60
[542386.625356]  [<c024b5cc>] ext3_find_entry+0x39c/0x3c0
[542386.625361]  [<c0576638>] ? _spin_lock+0x8/0x10
[542386.625367]  [<c01f2ee9>] ? inode_permission+0x89/0xb0
[542386.625374]  [<c048c900>] ? apparmor_file_alloc_security+0x20/0x90
[542386.625380]  [<c024b62d>] ext3_lookup+0x3d/0x100
[542386.625384]  [<c0576638>] ? _spin_lock+0x8/0x10
[542386.625390]  [<c01fce46>] ? d_alloc+0x136/0x190
[542386.625394]  [<c01f4935>] __lookup_hash+0xc5/0x110
[542386.625399]  [<c01f49a7>] lookup_hash+0x27/0x30
[542386.625403]  [<c01f6a09>] do_filp_open+0x279/0x890
[542386.625409]  [<c0161b83>] ? hrtimer_try_to_cancel+0x33/0x80
[542386.625422]  [<f8475800>] ? snd_timer_open+0x50/0x3b0 [snd_timer]
[542386.625427]  [<c0576638>] ? _spin_lock+0x8/0x10
[542386.625433]  [<c01e8cd0>] do_sys_open+0x50/0x150
[542386.625438]  [<c01e8e39>] sys_open+0x29/0x40
[542386.625443]  [<c010336c>] syscall_call+0x7/0xb
[542386.625447] ---[ end trace 57a674735a552dbc ]---
[542386.625466] sd 0:0:0:0: [sda] Unhandled error code
[542386.625470] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[542386.625474] end_request: I/O error, dev sda, sector 63
[542410.080128] sd 0:0:0:0: [sda] Unhandled error code
[542410.080135] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[542410.080141] end_request: I/O error, dev sda, sector 72810623
[542410.080178] __ratelimit: 1 callbacks suppressed
[542410.080182] Buffer I/O error on device sda1, logical block 9101320
[542410.080214] lost page write due to I/O error on sda1
[542410.080237] sd 0:0:0:0: [sda] Unhandled error code
[542410.080240] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[542410.080244] end_request: I/O error, dev sda, sector 72810751
[542410.080276] Buffer I/O error on device sda1, logical block 9101336
[542410.080308] lost page write due to I/O error on sda1
....
```

And it keeps going on like that. Is this possible signs of hard drive failure or a bug?

---

### Post by FuturePilot on 2009-11-13
This is starting to happen more frequently and sometimes the BIOS doesn't even detect the drive. Definitely a hardware issue, not a bug.

---

