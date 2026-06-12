---
title: "Random 9.04 x86_64 server crashes"
date: 2010-11-09
forum: Server Platforms
---

### Post by sergiup on 2010-11-09
Hello all,
Newbie here, and without an in-depth Linux knowledge - recipe for disaster and/or silly questions! Anyway, enough self-pity, I do need some help with something that's got me stumped. I have to first mention that I've just applied some updates (including Kernel), so hopefully this might've fixed it in the first place. As such, don't reply yet, I'm more using this as a log of what's happening and for the benefit of others if it does fix it. I will come back and update in a few days.
 
Currently running "2.6.28-18-server #60-Ubuntu SMP Fri Mar 12 05:11:07 UTC 2010 x86_64 GNU/Linux"
 
Every few days, the server crashes. In messages, I can find the following error sequence repeating itself many many times (with slightly different addresses etc each time, but otherwise the same) every 4-6 seconds. It eventually brings the whole box down, and only a hard reset will bring it back to life. There were no system changes to my knowledge to make this start happening. The process (in this case "console-kit-dae") does change between crashes though.
 
```

Nov 6 06:48:08 rcapp01 kernel: [206246.481251] Modules linked in: nfs lockd nfs_acl sunrpc i915 drm tun input_polldev video output bridge stp coretemp lp parport iTCO_wdt pcspkr iTCO_vendor_support intel_agp usbhid r8169 mii raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear fbcon tileblit font bitblit softcursor
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] CPU 1:
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] Modules linked in: nfs lockd nfs_acl sunrpc i915 drm tun input_polldev video output bridge stp coretemp lp parport iTCO_wdt pcspkr iTCO_vendor_support intel_agp usbhid r8169 mii raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear fbcon tileblit font bitblit softcursor
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] Pid: 484, comm: console-kit-dae Tainted: G D 2.6.28-18-server #60-Ubuntu
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] RIP: 0010:[<ffffffff802fb5b4>] [<ffffffff802fb5b4>] __d_lookup+0x94/0x150
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] RSP: 0018:ffff8800c7973d48 EFLAGS: 00000212
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] RAX: ffff88001a3d61b8 RBX: ffff8800c7973d98 RCX: 0000000000000013
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] RDX: 00c390efff98abbf RSI: ffff8800c7973df8 RDI: ffff8800347541a0
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] RBP: ffff8800c7973d98 R08: 0000000000000002 R09: ffffffff8033b4b0
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] R10: 0000000000000002 R11: ffff8800c7973e88 R12: 00000000000000d0
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] R13: ffffffff803364cb R14: ffff88012f822000 R15: 0000000000000282
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] FS: 00007f20d3e5d6f0(0000) GS:ffff88012f802b80(0000) knlGS:0000000000000000
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] CS: 0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] CR2: 00007f20d27d9440 CR3: 00000000cd8a1000 CR4: 00000000000406a0
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] Call Trace:
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] [<ffffffff802fb6b3>] d_lookup+0x43/0x60
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] [<ffffffff8033b4b0>] ? proc_fd_instantiate+0x0/0x160
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] [<ffffffff80337677>] proc_fill_cache+0x87/0x170
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] [<ffffffff802f6f40>] ? filldir+0x0/0xe0
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] [<ffffffff802f6f40>] ? filldir+0x0/0xe0
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] [<ffffffff80338d45>] proc_readfd_common+0xf5/0x1c0
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] [<ffffffff8033b4b0>] ? proc_fd_instantiate+0x0/0x160
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] [<ffffffff802f6f40>] ? filldir+0x0/0xe0
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] [<ffffffff80338e40>] proc_readfd+0x10/0x20
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] [<ffffffff802f71b3>] vfs_readdir+0xb3/0xd0
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] [<ffffffff802f7333>] sys_getdents+0x83/0xe0
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] [<ffffffff8069b18a>] ? error_exit+0x0/0x70
Nov 6 06:48:08 rcapp01 kernel: [206246.481251] [<ffffffff8021252a>] system_call_fastpath+0x16/0x1b

```
 
Thanks for your time!
Sergiu

---

### Post by sergiup on 2010-11-09
OK.. have successfully installed the 2.6.28-19 kernel, and after a reboot and trying to install further updates I get the below. Not good... I have a spare couple of RAM modules to test, I guess that'll be my next stop for now.
 
```

Nov 9 20:17:21 rcapp01 kernel: [ 315.952857] apt-get[3951]: segfault at 7f810dbd100c ip 00007f802f6148d8 sp 00007fff9a89b9e0 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[7f802f5b3000+bc000]
Nov 9 20:17:22 rcapp01 kernel: [ 317.040172] apt-get[3955]: segfault at 7fb9c5bc900c ip 00007fb8e760c8d8 sp 00007fff0589ef30 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[7fb8e75ab000+bc000]
Nov 9 20:17:22 rcapp01 kernel: [ 317.586247] apt-get[3959]: segfault at 7f0fb584d00c ip 00007f0ed72908d8 sp 00007fff4ce29cb0 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[7f0ed722f000+bc000]
Nov 9 20:20:03 rcapp01 kernel: [ 478.757454] apt-check[4169]: segfault at 7f8f5619c01c ip 00007f8e77f238d8 sp 00007ffffa5a2e50 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[7f8e77ec2000+bc000]
Nov 9 20:23:22 rcapp01 kernel: [ 676.954556] apt-get[4276]: segfault at 7fa9c56d500c ip 00007fa8e71188d8 sp 00007fff1b5ec140 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[7fa8e70b7000+bc000]
Nov 9 20:23:22 rcapp01 kernel: [ 677.400887] apt-get[4280]: segfault at 7f13627cc00c ip 00007f128420f8d8 sp 00007fffb0e93630 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[7f12841ae000+bc000]

```

---

### Post by FuturePilot on 2010-11-09
Possible file system corruption? If nothing else works, I would try a reinstall with 10.10 (or 10.04 if you want LTS). 9.04 isn't supported anymore.

---

