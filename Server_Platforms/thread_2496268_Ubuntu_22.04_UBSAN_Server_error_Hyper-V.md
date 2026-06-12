---
title: "Ubuntu 22.04 UBSAN Server error Hyper-V"
date: 2024-03-21
forum: Server Platforms
---

### Post by duckietm on 2024-03-21
When i do a fresh install on a Ubuntu 22.04 server (latest version) on Hyper-V and installing the latest Azure kernel
I now recive the following error when booting:

```

[    5.539198] UBSAN: array-index-out-of-bounds in /build/linux-azure-6.5-dqcUxs/linux-azure-6.5-6.5.0/drivers/net/hyperv/netvsc.c:1449:41
[    5.539208] index 1 is out of range for type 'vmtransfer_page_range [1]'
[    5.539214] CPU: 0 PID: 1270 Comm: mariadbd Not tainted 6.5.0-1016-azure #16~22.04.1-Ubuntu
[    5.539215] Hardware name: Microsoft Corporation Virtual Machine/Virtual Machine, BIOS Hyper-V UEFI Release v4.1 12/03/2020
[    5.539216] Call Trace:
[    5.539216]  <IRQ>
[    5.539217]  dump_stack_lvl+0x37/0x50
[    5.539219]  dump_stack+0x10/0x20
[    5.539219]  __ubsan_handle_out_of_bounds+0xa2/0xe0
[    5.539221]  ? rndis_filter_receive+0x85/0x190 [hv_netvsc]
[    5.539225]  ? scsi_finish_command+0xc2/0x100
[    5.539227]  netvsc_receive+0x401/0x440 [hv_netvsc]
[    5.539231]  netvsc_poll+0x15c/0x470 [hv_netvsc]
[    5.539234]  __napi_poll+0x30/0x1d0
[    5.539236]  net_rx_action+0x17b/0x2e0
[    5.539237]  __do_softirq+0xd5/0x2de
[    5.539238]  __irq_exit_rcu+0xb0/0xd0
[    5.539240]  irq_exit_rcu+0xe/0x20
[    5.539242]  sysvec_hyperv_callback+0x80/0x90
[    5.539243]  </IRQ>
[    5.539243]  <TASK>
[    5.539243]  asm_sysvec_hyperv_callback+0x1b/0x20
[    5.539245] RIP: 0010:__slab_free+0x0/0x360
[    5.539246] Code: 18 4d 85 e4 0f 85 dc fe ff ff eb 9b e8 e9 f2 bb 00 66 0f 1f 84 00 00 00 00 00 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 <0f> 1f 44 00 00 55 48 89 e5 41 57 49 89 cf 41 56 49 89 fe 41 55 41
[    5.539247] RSP: 0018:ffffb87f037a7b28 EFLAGS: 00000206
[    5.539248] RAX: ffff9c1cffc37620 RBX: ffff9c1c00c95e00 RCX: ffff9c1c00c95e00
[    5.539248] RDX: ffff9c1c00c95e00 RSI: fffff94384032500 RDI: ffff9c1c00045100
[    5.539249] RBP: ffffb87f037a7b70 R08: 0000000000000001 R09: ffffffff998c4fbc
[    5.539250] R10: ffff9c1c08bcca00 R11: 0000000000000000 R12: ffff9c1c00045100
[    5.539250] R13: fffff94384032500 R14: ffffffff998c4fbc R15: ffff9c1c0414be80
[    5.539251]  ? skb_free_head+0x7c/0xb0
[    5.539252]  ? skb_free_head+0x7c/0xb0
[    5.539254]  ? __kmem_cache_free+0x2e7/0x340
[    5.539255]  ? unix_write_space+0x54/0x90
[    5.539257]  kfree+0x71/0xf0
[    5.539258]  skb_free_head+0x7c/0xb0
[    5.539259]  skb_release_data+0x11b/0x210
[    5.539261]  consume_skb+0x46/0xc0
[    5.539262]  unix_stream_read_generic+0x8e8/0xa20
[    5.539264]  unix_stream_recvmsg+0x82/0x90
[    5.539266]  ? __pfx_unix_stream_read_actor+0x10/0x10
[    5.539267]  sock_recvmsg+0xc7/0xd0
[    5.539268]  __sys_recvfrom+0xb7/0x130
[    5.539270]  ? sock_recvmsg+0xc7/0xd0
[    5.539271]  ? rseq_ip_fixup+0x6e/0x190
[    5.539272]  __x64_sys_recvfrom+0x24/0x30
[    5.539274]  do_syscall_64+0x59/0x90
[    5.539275]  ? exit_to_user_mode_prepare+0x49/0x100
[    5.539277]  ? syscall_exit_to_user_mode+0x27/0x40
[    5.539278]  ? do_syscall_64+0x69/0x90
[    5.539279]  ? exit_to_user_mode_prepare+0xe7/0x100
[    5.539281]  ? syscall_exit_to_user_mode+0x27/0x40
[    5.539282]  ? do_syscall_64+0x69/0x90
[    5.539283]  ? exc_page_fault+0x80/0x160
[    5.539284]  entry_SYSCALL_64_after_hwframe+0x6e/0xd8
[    5.539286] RIP: 0033:0x705a1cf276be
[    5.539288] Code: 4c 24 1c e8 54 93 f6 ff 44 8b 54 24 1c 8b 3c 24 45 31 c9 41 89 c4 48 8b 54 24 10 48 8b 74 24 08 45 31 c0 b8 2d 00 00 00 0f 05 <48> 3d 00 f0 ff ff 77 32 44 89 e7 48 89 04 24 e8 8e 93 f6 ff 48 8b
[    5.539289] RSP: 002b:00007059f867c910 EFLAGS: 00000246 ORIG_RAX: 000000000000002d
[    5.539290] RAX: ffffffffffffffda RBX: 00007059a8008548 RCX: 0000705a1cf276be
[    5.539290] RDX: 000000000000003c RSI: 00007059a8008758 RDI: 0000000000000263
[    5.539291] RBP: 00007059f867c9d0 R08: 0000000000000000 R09: 0000000000000000
[    5.539291] R10: 0000000000000040 R11: 0000000000000246 R12: 0000000000000000
[    5.539292] R13: 000000000000003c R14: 00007059a8008758 R15: 00007059f867c950
[    5.539293]  </TASK>
[    5.539293] ================================================================================

```

I have tried it on different Hyper-V machines and all have the same error when booting (Dell / HP)

---

### Post by duckietm on 2024-03-21
Just to make sure :

Module 0:
  DDR4, 32768 MB, 64-bit, 2667 MHz
  ChannelA-DIMM0 BANK 0 859B CP32G4DFRA32A.C16FF
Module 1:
  DDR4, 32768 MB, 64-bit, 2667 MHz
  ChannelA-DIMM0 BANK 1 859B CP32G4DFRA32A.C16FF
Module 2:
  DDR4, 32768 MB, 64-bit, 2667 MHz
  ChannelB-DIMM0 BANK 2 Micron CP32G4DFRA32A.C16FF
Module 3:
  DDR4, 32768 MB, 64-bit, 2667 MHz
  ChannelB-DIMM0 BANK 3 Micron CP32G4DFRA32A.C16FF


0.000: Detecting usable memory (130845 MB theoretical max)...
35.687: 116394 MB Test starting on 32 CPUs...
35.687: Allocating memory...
60.281: Starting loop 1
60.296: Stuck Address Test...
66.031: Random Data Test...
71.750: Move Data Test...
73.765: Bitpattern Test...
250.421: Starting loop 2
250.421: Stuck Address Test...
256.078: Random Data Test...
262.312: Move Data Test...
264.343: Bitpattern Test...
440.843: Starting loop 3
440.843: Stuck Address Test...
455.515: Test finished with no errors detected

---

### Post by MAFoElffen on 2024-03-22
??? 

I am very curious --> Why are you using the Azure Series Kernel on Hyper-V? That series is optimized to "Azure Cloud"... Not Hyper-V. Azure cloud is a very confined, very predictable sandbox to play in, defined by it's own managed service settings.

I do see where nextcloud users claim that using the azure otpimized kernel added some performance gains for nextcloud running on Hyper-V... but when they do it, they ensure they have the HWE stack installed first, before they install the azure series kernel. Did you install that "in that order"?

Did you try it with -generic and -lowlatency series kernels first? I have not had a problem running Ubuntu Desktop and Server with those kernels on Hyper-V.

For VM's, there is a kvm series, but nothing really optimized for Hyper-V. If you look at the Ubuntu Hyper-V Wiki page, there is no mention of changing the kernel series from the default:
[https://wiki.ubuntu.com/Hyper-V](https://wiki.ubuntu.com/Hyper-V)

So the only mention I see of people saying anything about that is from some NextCloud users.

---

