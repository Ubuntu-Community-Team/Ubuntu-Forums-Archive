---
title: "raspberry pi server 22.04 mt76x02 crash"
date: 2022-04-28
forum: Server Platforms
---

### Post by bjlockie on 2022-04-28
I upgraded my raspberry pi server to 22.04 and I get this:

```
[   25.597319] ================================================================================
[   25.597344] UBSAN: invalid-load in /build/linux-raspi-9r6HWT/linux-raspi-5.15.0/net/mac80211/status.c:1164:21                                                                              
[   25.597367] load of value 255 is not a valid value for type '_Bool'
[   25.597382] CPU: 0 PID: 105 Comm: kworker/u8:2 Tainted: G         C        5.15.0-1005-raspi #5-Ubuntu
[   25.597397] Hardware name: Raspberry Pi 4 Model B Rev 1.1 (DT)
[   25.597406] Workqueue: phy0 mt76x02_mac_work [mt76x02_lib]
[   25.597472] Call trace:
[   25.597477]  dump_backtrace+0x0/0x1f0
[   25.597496]  show_stack+0x24/0x30
[   25.597507]  dump_stack_lvl+0x8c/0xb8
[   25.597520]  dump_stack+0x18/0x34
[   25.597530]  ubsan_epilogue+0x10/0x54
[   25.597539]  __ubsan_handle_load_invalid_value+0x80/0x90
[   25.597553]  ieee80211_tx_status_ext+0x54c/0x550 [mac80211]
[   25.597800]  mt76_tx_status_unlock+0x100/0x160 [mt76]
[   25.597854]  mt76_tx_status_check+0x74/0xa4 [mt76]
[   25.597900]  mt76x02_mac_work+0x174/0x2ac [mt76x02_lib]
[   25.597943]  process_one_work+0x204/0x4c0
[   25.597958]  worker_thread+0x144/0x470
[   25.597970]  kthread+0x12c/0x140
[   25.597981]  ret_from_fork+0x10/0x20
[   25.597996] ================================================================================
```

Everything seems to work so far.

---

### Post by TheFu on 2022-04-29
r-pi v4 issues are usually very specific to r-pi hardware. You're likely to get more useful help if that was included in the thread title.
I cannot help.  Don't know what a mt76x02 is or if it even matters.

Kernel crashes are a security issue a minimum and away to completely pwn a system if a bad-guy can take advantage of it.

---

