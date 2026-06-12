---
title: "Need help debugging kernel crash on Amazon Ubuntu 12.04 VM (3.2.0-31-virtual)"
date: 2012-10-09
forum: Server Platforms
---

### Post by midnightmax on 2012-10-09
Hello Ubuntu Community.  I have an Amazon VM that periodically reboots that I could use some help debugging.  I have been unable to recreate the event.  The times and dates are very sporadic and I see no pattern with them to indicate a cron or backup that might be causing the issue.  Amazon's support has analyzed their logs and show no hardware issues behind the scenes either.

For a little background on the server, it is running an instance of Redis DB.  It has several different servers connecting into it getting and putting information as you would expect for a database server.  Several times a day the database backs itself up to Amazon storage which hasn't had any issues.  I have tried a different VM image and have tried upgrading kernel images with no luck.  Our dev server which is identically built has never crashed.  The only difference with the dev server is it has less load.  We monitor the server with Zabbix and Amazon's Cloud watch and don't see any spikes in any data before the crashes.

The previous stack trace is pasted below.  Any help or suggestions on things to install to help debug, or things to try to eliminate this error would be greatly appreciated.  If you would like more information just let me know.  If you have any suggestions on where else I might post this, that would be appreciated also.  Thank you in advance for your time.


```

[17659.489925] BUG: unable to handle kernel NULL pointer dereference at           (null)
[17659.489944] IP: [<ffffffff8147e826>] xennet_alloc_rx_buffers+0xa6/0x340
[17659.489961] PGD 3a40db067 PUD 3a44d5067 PMD 0 
[17659.489970] Oops: 0002 [#1] SMP 
[17659.489980] CPU 0 
[17659.489983] Modules linked in: isofs acpiphp
[17659.489992] 
[17659.489996] Pid: 0, comm: swapper/0 Not tainted 3.2.0-31-virtual #50-Ubuntu  
[17659.490005] RIP: e030:[<ffffffff8147e826>]  [<ffffffff8147e826>] xennet_alloc_rx_buffers+0xa6/0x340
[17659.490016] RSP: e02b:ffff8803bfc03d40  EFLAGS: 00010282
[17659.490022] RAX: 0000000000000000 RBX: ffff8803a4850000 RCX: 0000000000000000
[17659.490028] RDX: ffff8803a4893c00 RSI: 0000000000000001 RDI: ffffea000e98d7c0
[17659.490035] RBP: ffff8803bfc03d90 R08: 0000000000000000 R09: 00000000000ea7c4
[17659.490041] R10: ffffea000e98d7c0 R11: 0000000000000000 R12: 0000000000000001
[17659.490048] R13: 000000000000001c R14: ffff8803a4851470 R15: ffff8803a6af6d00
[17659.490059] FS:  00007f3f975a3740(0000) GS:ffff8803bfc00000(0000) knlGS:0000000000000000
[17659.490066] CS:  e033 DS: 0000 ES: 0000 CR0: 000000008005003b
[17659.490072] CR2: 0000000000000000 CR3: 00000003a6a3b000 CR4: 0000000000000660
[17659.490079] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[17659.490088] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[17659.490095] Process swapper/0 (pid: 0, threadinfo ffffffff81c00000, task ffffffff81c0d020)
[17659.490103] Stack:
[17659.490106]  ffff8803bfc03d90 ffffffff8147de83 00000001009f4515 00000000009f4539
[17659.490118]  000000000000001b 0000000000000001 ffff8803a4850798 ffff8803bfc03df0
[17659.490129]  ffff8803bfc03dd8 ffff8803a479b400 ffff8803bfc03e60 ffffffff8147eef1
[17659.490140] Call Trace:
[17659.490145]  <IRQ> 
[17659.490151]  [<ffffffff8147de83>] ? handle_incoming_queue+0x133/0x140
[17659.490160]  [<ffffffff8147eef1>] xennet_poll+0x361/0x4d0
[17659.490167]  [<ffffffff8147d7b7>] ? xennet_tx_buf_gc+0x107/0x1c0
[17659.490177]  [<ffffffff8153c524>] net_rx_action+0x134/0x290
[17659.493900]  [<ffffffff8130c27b>] ? radix_tree_lookup+0xb/0x10
[17659.493900]  [<ffffffff8106cf68>] __do_softirq+0xa8/0x210
[17659.493900]  [<ffffffff813a4797>] ? __xen_evtchn_do_upcall+0x207/0x250
[17659.493900]  [<ffffffff8165dc2c>] call_softirq+0x1c/0x30
[17659.493900]  [<ffffffff81015295>] do_softirq+0x65/0xa0
[17659.493900]  [<ffffffff8106d34e>] irq_exit+0x8e/0xb0
[17659.493900]  [<ffffffff813a6815>] xen_evtchn_do_upcall+0x35/0x50
[17659.493900]  [<ffffffff8165dc7e>] xen_do_hypervisor_callback+0x1e/0x30
[17659.493900]  <EOI> 
[17659.493900]  [<ffffffff810013aa>] ? hypercall_page+0x3aa/0x1000
[17659.493900]  [<ffffffff810013aa>] ? hypercall_page+0x3aa/0x1000
[17659.493900]  [<ffffffff8100a2a0>] ? xen_safe_halt+0x10/0x20
[17659.493900]  [<ffffffff8101b8a3>] ? default_idle+0x53/0x1d0
[17659.493900]  [<ffffffff81012236>] ? cpu_idle+0xd6/0x120
[17659.493900]  [<ffffffff8161a17e>] ? rest_init+0x72/0x74
[17659.493900]  [<ffffffff81cf8c03>] ? start_kernel+0x3b0/0x3bd
[17659.493900]  [<ffffffff81cf8388>] ? x86_64_start_reservations+0x132/0x136
[17659.493900]  [<ffffffff81cfbf9b>] ? xen_start_kernel+0x58e/0x595
[17659.493900] Code: 00 00 c7 42 44 00 00 00 00 41 8b 87 d0 00 00 00 49 8b 97 d8 00 00 00 66 c7 04 02 01 00 48 8b 83 78 14 00 00 4d 89 37 49 89 47 08 <4c> 89 38 83 83 80 14 00 00 01 45 39 e5 4c 89 bb 78 14 00 00 0f 
[17659.493900] RIP  [<ffffffff8147e826>] xennet_alloc_rx_buffers+0xa6/0x340
[17659.493900]  RSP <ffff8803bfc03d40>
[17659.493900] CR2: 0000000000000000
Xen Minimal OS!
  start_info: 0x2790000(VA)
    nr_pages: 0x3c0000
  shared_inf: 0xdff52000(MA)
     pt_base: 0x2793000(VA)
nr_pt_frames: 0x19
    mfn_list: 0x990000(VA)
   mod_start: 0x0(VA)
     mod_len: 0
       flags: 0x0
    cmd_line: root=/dev/sda1 ro 4
  stack:      0x94f860-0x96f860
MM: Init
      _text: 0x0(VA)
     _etext: 0x6000d(VA)
   _erodata: 0x78000(VA)
     _edata: 0x80b00(VA)
stack start: 0x94f860(VA)
       _end: 0x98fe68(VA)
  start_pfn: 27af
    max_pfn: 3c0000
Mapping memory range 0x2c00000 - 0x3c0000000
setting 0x0-0x78000 readonly
skipped 0x1000
MM: Initialise page allocator for 45a7000(45a7000)-3c0000000(3c0000000)
MM: done
Demand map pfns at 3c0001000-23c0001000.
Heap resides at 23c0002000-43c0002000.
Initialising timer interface
Initialising console ... done.
gnttab_table mapped at 0x3c0001000.
Initialising scheduler
Thread "Idle": pointer: 0x23c0002010, stack: 0x6440000
Initialising xenbus
Thread "xenstore": pointer: 0x23c00027c0, stack: 0x6450000
Dummy main: start_info=0x96f960
Thread "main": pointer: 0x23c0002f70, stack: 0x6460000
"main" "root=/dev/sda1" "ro" "4" 
vbd 2049 is hd0
******************* BLKFRONT for device/vbd/2049 **********


backend at /local/domain/0/backend/vbd/53/2049
Failed to read /local/domain/0/backend/vbd/53/2049/feature-barrier.
Failed to read /local/domain/0/backend/vbd/53/2049/feature-flush-cache.
209715200 sectors of 512 bytes
**************************
vbd 2064 is hd1
******************* BLKFRONT for device/vbd/2064 **********


backend at /local/domain/0/backend/vbd/53/2064
Failed to read /local/domain/0/backend/vbd/53/2064/feature-barrier.
Failed to read /local/domain/0/backend/vbd/53/2064/feature-flush-cache.
880732160 sectors of 512 bytes
**************************

    [H
    [J  Booting 'Ubuntu 12.04.1 LTS, kernel 3.2.0-31-virtual'


```

---

### Post by mafmaf on 2012-10-10
I see the same problem as you do. Stack-trace looks identical and this is 12.04 on EC2.

Unfortunately I do not know of any solution :(

---

