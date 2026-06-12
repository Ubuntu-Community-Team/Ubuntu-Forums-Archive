---
title: "problem with boot from network"
date: 2008-03-10
forum: Sun Sparc Users
---

### Post by atf1084 on 2008-03-10
Hi,

I have a sunfire T1000 which comes with no cdrom so i have to boot an install image from network, i followed all directions at [https://help.ubuntu.com/community/Installation/Sparc](https://help.ubuntu.com/community/Installation/Sparc) and have a problem after booting the image.. error pasted below. i have googled and searched these forums and found nothing that can help, does anyone have any ideas?

[   12.185390] TCP established hash table entries: 1048576 (order: 10, 8388608 b                                                                              ytes)
[   12.464631] TCP bind hash table entries: 65536 (order: 6, 524288 bytes)
[   12.675709] TCP: Hash tables configured (established 1048576 bind 65536)
[   12.879716] TCP reno registered
[   12.982880] TCP bic registered
[   13.081112] NET: Registered protocol family 1
[   13.222871] NET: Registered protocol family 17
[   15.031663] tg3.c:v3.49 (Feb 2, 2006)
[   15.398968] NON-RESUMABLE ERROR: Reporting on cpu 0
[   15.796795] NON-RESUMABLE ERROR: err_handle[10000000000078] err_stick[1b95d2f                                                                              980] err_type[00000002:precise nonresumable]
[   16.151346] NON-RESUMABLE ERROR: err_attrs[02000004:  pio    privileged ]
[   16.372806] NON-RESUMABLE ERROR: err_raddr[0000000000000000] err_size[64] err                                                                              _cpu[0]
[   16.625984] TSTATE: 0000000011001607 TPC: 0000000010008d68 TNPC: 000000001000                                                                              8d6c Y: 00000000    Not tainted
[   16.946287] TPC: <tg3_read32+0x8/0x20 [tg3]>
[   17.084162] g0: 0000000000000000 g1: 0000000010008d60 g2: 000000000041e3c0 g3                                                                              : 0000000000000000
[    0.187003] g4: fffff8000119b400 g5: 0000000000000020 g6: fffff80005e8c000 g7                                                                              : 0000000001000000
[    0.472236] o0: 000000f200206808 o1: 0000000000006808 o2: 0000000001000008 o3                                                                              : 000000009001009a
[    0.752969] o4: 000000000000020a o5: 0000000008060000 sp: fffff80005e8ecb1 re                                                                              t_pc: 0000000010006114
[    1.032974] RPC: <_tw32_flush+0x74/0xa0 [tg3]>
[    1.172282] l0: fffff80005e8f80c l1: fffff80005e8f810 l2: 0000000000000048 l3                                                                              : 000000000000004c
[    1.455993] l4: fffff800011d5000 l5: 00000000f7ed0000 l6: fffff801fffc9070 l7                                                                              : fffff801fffc9000
[    1.739512] i0: 0000000000000064 i1: 0000000000006808 i2: 0000000001000008 i3                                                                              : 0000000000000064
[    2.020128] i4: 0000000000000000 i5: 0000000000000000 i6: fffff80005e8ed71 i7                                                                              : 000000001000d7b4
[    2.306288] I7: <tg3_set_power_state+0x754/0x880 [tg3]>
[    2.470028] Kernel panic - not syncing: Non-resumable error.
[    2.638036]  <0>Press Stop-A (L1-A) to return to the boot prom

---

### Post by atf1084 on 2008-03-11
sorted it out.. needed to upgrade to an even newer version of firmware

---

