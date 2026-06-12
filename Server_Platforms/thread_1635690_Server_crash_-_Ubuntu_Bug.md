---
title: "Server crash - Ubuntu Bug?"
date: 2010-12-02
forum: Server Platforms
---

### Post by BarryDocks on 2010-12-02
My server fell over last night, I am not sure why, here is the relevant bit from the syslog:
```
Dec  2 01:49:17 server10 kernel: [16490.667698] BUG: unable to handle kernel paging request at 23232323
Dec  2 01:49:17 server10 kernel: [16490.668259] IP: [<c0207967>] kmem_cache_alloc+0x57/0x120
Dec  2 01:49:17 server10 kernel: [16490.668642] *pdpt = 000000002c879001 *pde = 0000000000000000 
Dec  2 01:49:17 server10 kernel: [16490.669017] Oops: 0000 [#1] SMP 
Dec  2 01:49:17 server10 kernel: [16490.669017] last sysfs file: /sys/devices/pci0000:09/0000:09:08.0/irq
Dec  2 01:49:17 server10 kernel: [16490.669017] Modules linked in: bonding sha256_generic bttv v4l2_common videodev v4l1_compat scb2_flash ir_common i2c_algo_bit videobuf_dma_sg mtd videobuf_core chipreg btcx_risc dm_crypt tveeprom map_funcs aes_i586 aes_generic ppdev dell_wmi i2c_piix4 parport_pc lp shpchp parport dcdbas psmouse serio_raw raid10 raid456 async_raid6_recov async_pq raid6_pq async_xor xor async_memcpy async_tx raid1 multipath linear raid0 fbcon tileblit font bitblit usbhid megaraid_mbox usb_storage hid softcursor megaraid_mm floppy sata_sil24 tg3 aic7xxx vga16fb vgastate e100 mii pata_serverworks sworks_agp agpgart
Dec  2 01:49:17 server10 kernel: [16490.669017] 
Dec  2 01:49:17 server10 kernel: [16490.669017] Pid: 8756, comm: miniserv.pl Not tainted (2.6.32-24-generic-pae #43-Ubuntu) PowerEdge 4600             
Dec  2 01:49:17 server10 kernel: [16490.669017] EIP: 0060:[<c0207967>] EFLAGS: 00210002 CPU: 2
Dec  2 01:49:17 server10 kernel: [16490.669017] EIP is at kmem_cache_alloc+0x57/0x120
Dec  2 01:49:17 server10 kernel: [16490.669017] EAX: c330630c EBX: c07a073c ECX: c0213b6f EDX: 00000000
Dec  2 01:49:17 server10 kernel: [16490.669017] ESI: 23232323 EDI: 000080d0 EBP: f6d0fe80 ESP: f6d0fe58
Dec  2 01:49:17 server10 kernel: [16490.669017]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Dec  2 01:49:17 server10 kernel: [16490.669017] Process miniserv.pl (pid: 8756, ti=f6d0e000 task=f6c5e600 task.ti=f6d0e000)
Dec  2 01:49:17 server10 kernel: [16490.669017] Stack:
Dec  2 01:49:17 server10 kernel: [16490.669017]  c020dcbb f56850b0 c0213b6f 00000010 00000080 000080d0 00200246 00008001
Dec  2 01:49:17 server10 kernel: [16490.669017] <0> 00000024 00000001 f6d0feb0 c0213b6f f6d0feac f6d0feac ece5bb80 13000002
Dec  2 01:49:17 server10 kernel: [16490.669017] <0> ec181d5c c2f5f060 f5685528 00008001 00000024 00000001 f6d0ff64 c021ec7d
Dec  2 01:49:17 server10 kernel: [16490.669017] Call Trace:
Dec  2 01:49:17 server10 kernel: [16490.669017]  [<c020dcbb>] ? __mem_cgroup_try_charge+0x3b/0x1c0
Dec  2 01:49:17 server10 kernel: [16490.669017]  [<c0213b6f>] ? get_empty_filp+0xcf/0x1c0
Dec  2 01:49:17 server10 kernel: [16490.669017]  [<c0213b6f>] ? get_empty_filp+0xcf/0x1c0
Dec  2 01:49:17 server10 kernel: [16490.669017]  [<c021ec7d>] ? do_filp_open+0x7d/0x990
Dec  2 01:49:17 server10 kernel: [16490.669017]  [<c01ef0a3>] ? do_wp_page+0x103/0x920
Dec  2 01:49:17 server10 kernel: [16490.669017]  [<c01382a4>] ? kmap_atomic+0x24/0x30
Dec  2 01:49:17 server10 kernel: [16490.669017]  [<c022942d>] ? alloc_fd+0xbd/0xf0
Dec  2 01:49:17 server10 kernel: [16490.669017]  [<c0210575>] ? do_sys_open+0x55/0x160
Dec  2 01:49:17 server10 kernel: [16490.669017]  [<c02106ee>] ? sys_open+0x2e/0x40
Dec  2 01:49:17 server10 kernel: [16490.669017]  [<c010984c>] ? syscall_call+0x7/0xb
Dec  2 01:49:17 server10 kernel: [16490.669017] Code: 9c 58 8d 74 26 00 89 45 f0 fa 90 8d 74 26 00 64 a1 20 67 88 c0 8b 84 83 84 00 00 00 8b 50 10 89 55 e8 8b 30 85 f6 74 51 8b 50 0c <8b> 14 96 89 10 8b 45 f0 50 9d 8d 74 26 00 85 f6 0f 85 89 00 00 
Dec  2 01:49:17 server10 kernel: [16490.669017] EIP: [<c0207967>] kmem_cache_alloc+0x57/0x120 SS:ESP 0068:f6d0fe58
Dec  2 01:49:17 server10 kernel: [16490.669017] CR2: 0000000023232323
Dec  2 01:49:17 server10 kernel: [16490.669017] ---[ end trace 61abcc813951beec ]---

```

Suggestions welcome.

---

### Post by green91 on 2011-01-03
I experienced the same crash today.

---

### Post by Miter_J on 2011-01-03
Wow, that's really an old thread... Haha.
It seems that Chinese server has crashed lately.

---

