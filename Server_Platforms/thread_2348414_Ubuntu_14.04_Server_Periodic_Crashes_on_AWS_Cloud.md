---
title: "Ubuntu 14.04 Server Periodic Crashes on AWS Cloud"
date: 2017-01-03
forum: Server Platforms
---

### Post by kiri82 on 2017-01-03
We have just upgraded our postgres database servers to Ubuntu 14.04 LTS with default 3.13 kernel and all of sudden after a couple of months with no issues we are seeing constant crashes related to kernel errors on the AWS platform. 

See the console logs below.

```
[76648.480051] Hardware name: Xen HVM domU, BIOS 4.2.amazon 11/11/2016
[76648.480051] task: ffff880ee464c800 ti: ffff880ee4676000 task.ti: ffff880ee4676000
[76648.480051] RIP: 0010:[<ffffffff810dbf92>]  [<ffffffff810dbf92>] generic_exec_single+0x82/0xb0
[76648.480051] RSP: 0018:ffff880ee4677a60  EFLAGS: 00000202
[76648.480051] RAX: 0000000000000100 RBX: ffffffff81432166 RCX: 0000000000000005
[76648.480051] RDX: ffffffff8180ade0 RSI: 0000000000000000 RDI: 0000000000000100
[76648.480051] RBP: ffff880ee4677a90 R08: ffffffff8180adc8 R09: ffff88076d400470
[76648.480051] R10: 000000000000001e R11: 0000000000000005 R12: ffffffff810c26ae
[76648.480051] R13: ffff880ee46779d8 R14: ffffffff810bf187 R15: ffff880ee46779c8
[76648.480051] FS:  0000000000000000(0000) GS:ffff880ef0e60000(0000) knlGS:0000000000000000
[76648.480051] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[76648.480051] CR2: 00007faceda94000 CR3: 0000000eda3d2000 CR4: 00000000001406e0
[76648.480051] Stack:
[76648.480051]  ffff88076dc93f80 0000000000000004 000000000000000b ffffffff81d14380
[76648.480051]  ffffffff8105c7a0 00000002a4242000 ffff880ee4677b08 ffffffff810dc0a5
[76648.480051]  ffffffff813645f0 0000000000000001 ffff88076dc93f80 ffff88076dc93f80
[76648.480051] Call Trace:
[76648.480051]  [<ffffffff8105c7a0>] ? leave_mm+0x80/0x80
[76648.480051]  [<ffffffff810dc0a5>] smp_call_function_single+0xe5/0x190
[76648.480051]  [<ffffffff813645f0>] ? cpumask_next_and+0x30/0x50
[76648.480051]  [<ffffffff8105c7a0>] ? leave_mm+0x80/0x80
[76648.480051]  [<ffffffff810dc4d6>] smp_call_function_many+0x286/0x2d0
[76648.480051]  [<ffffffff8105c7a0>] ? leave_mm+0x80/0x80
[76648.480051]  [<ffffffff8105c8f7>] native_flush_tlb_others+0x37/0x40
[76648.480051]  [<ffffffff8105cbf6>] flush_tlb_page+0x56/0xa0
[76648.480051]  [<ffffffff8105b76d>] ptep_clear_flush_young+0x2d/0x40
[76648.480051]  [<ffffffff81184527>] page_referenced_one+0x57/0x160
[76648.480051]  [<ffffffff81185ae7>] page_referenced+0x127/0x310
[76648.480051]  [<ffffffff81163141>] shrink_active_list+0x1f1/0x430
[76648.480051]  [<ffffffff81164a98>] balance_pgdat+0x198/0x610
[76648.480051]  [<ffffffff8116506b>] kswapd+0x15b/0x3f0
[76648.480051]  [<ffffffff810ab120>] ? prepare_to_wait_event+0x100/0x100
[76648.480051]  [<ffffffff81164f10>] ? balance_pgdat+0x610/0x610
[76648.480051]  [<ffffffff8108b5b2>] kthread+0xd2/0xf0
[76648.480051]  [<ffffffff8108b4e0>] ? kthread_create_on_node+0x1c0/0x1c0
[76648.480051]  [<ffffffff81731f0c>] ret_from_fork+0x7c/0xb0
[76648.480051]  [<ffffffff8108b4e0>] ? kthread_create_on_node+0x1c0/0x1c0
[76648.480051] Code: 08 4c 89 ff 4c 89 23 48 89 4b 08 48 89 19 48 89 55 d0 e8 f2 d3 64 00 4c 3b 65 d0 74 23 45 85 ed 75 09 eb 0d 0f 1f 44 00 00 f3 90 <f6> 43 20 01 75 f8 48 83 c4 08 5b 41 5c 41 5d 41 5e 41 5f 5d c3 
```


Has this been reported already by other customers on the AWS Platform?

What may be causing this issue all of sudden on AWS after these servers have been running on the kernel 3.13 with Ubuntu 14.04 for about 3 to 4 months with no issues such as this?

AWS suggested we upgrade our kernel to 4.4 backported from 16.04 LTS but why is this LTS release installed with a kernel version that is not also LTS release.  Even after sudo apt-get upgrade, the server is still on a 3.13 version of the kernel.

---

### Post by darkod on 2017-01-03
apt-get upgrade (or apt-get dist-upgrade) is not upgrading the kernel to the latest for the "old" LTS releases. There is something called LTS Enablement Stack. [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

If you wish to upgrade 14.04 to latest available kernel (which I usually do after a while), do:
```
sudo apt-get install --install-recommends linux-generic-lts-xenial
```

That will upgrade it to 16.04 kernel while leaving the ubuntu version as 14.04 (probably 14.04.5). As to whether this will fix your issues I don't know, but that is how to do kernel upgrades on LTS releases when the kernel jumps to next major release.

---

### Post by Habitual on 2017-01-04
If running a new kernal install prompts you to "overwrite/keep/compare" and that "noise"...
Accept the default selection and press <enter> to use it.
Common when grub updates.

Forums are at [https://forums.aws.amazon.com/index.jspa?categoryID=1](https://forums.aws.amazon.com/index.jspa?categoryID=1)

---

