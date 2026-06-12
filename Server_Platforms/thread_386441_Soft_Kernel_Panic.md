---
title: "Soft Kernel Panic"
date: 2007-03-17
forum: Server Platforms
---

### Post by maiios on 2007-03-17
I have been setting up a box with Ubuntu Server 6.10 with all of the updates. The experience has been a bit kinky so far with hard kernel panics every once in a while (which I traced back to a VMWare server migration issue). However, I have been getting a soft kernel panic lately which I have not been able to trace. This is the output to the ssh window:

================

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000] SMP

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000] CPU:    0

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000] EIP is at cache_reap+0x48/0x1a0

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000] eax: 00000000   ebx: dfffc620   ecx: 00000001   edx: effd0000

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000] Oops: 0000 [#1]

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000] esi: dffff0c0   edi: 00000001   ebp: fffff1a4   esp: effd1f3c

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000] Process events/0 (pid: 5, threadinfo=effd0000 task=dffdf580)

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000] Stack: 00000000 00000000 dfffc970 c1607820 c1607824 c16dd640 00000000 c0131602

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000]        00000000 00000000 c1606b98 c16dd64c c16dd660 00000296 c01678d0 effd0000

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000]        c16dd64c c16dd654 c16dd640 c01321a7 00000001 00000000 00000000 00010000

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000] Call Trace:

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000]  <c0131602> run_workqueue+0x72/0xf0  <c01678d0> cache_reap+0x0/0x1a0

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000]  <c01321a7> worker_thread+0x117/0x140  <c011b170> default_wake_function+0x0/0x10

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000]  <c0132090> worker_thread+0x0/0x140  <c0134e2b> kthread+0xab/0xe0

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000]  <c0134d80> kthread+0x0/0xe0  <c0101005> kernel_thread_helper+0x5/0x10

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000] Code: 47 c0 8b 45 00 0f 18 00 90 81 fd 78 cd 47 c0 75 2d e9 20 01 00 00 c7 43 34 00 00 00 00 8d b6 00 00 00 00 e8 fb 06 17 00 8b 6d 00 <8b> 45 00 0f 18 00 90 81 fd 78 cd 47 c0 0f 84 f8 00 00 00 b8 00

Message from syslogd@cartman at Fri Mar 16 02:53:47 2007 ...
cartman kernel: [42985053.810000] EIP: [cache_reap+72/416] cache_reap+0x48/0x1a0 SS:ESP 0068:effd1f3c

================================

Since it is a soft kernel panic, I can continue to run my machine without problems, but I have always been told to reboot the machine after a panic. I honestly can't decipher anything useful out of the above messages. 

TIA

Brian

---

### Post by maiios on 2007-03-17
Hmm... it actually looks like VMware is causing all of the kernel panics. I am not completely sure why, but it is not playing nice at all.

---

### Post by cookfromfrozen on 2007-03-17
Could be a hardware problem, especially since there is an oops.  Try running Memtest86  and MPrime to rule that  out.

---

### Post by maiios on 2007-03-17
I ran mprime over night and got a hard kernel panic (the aiiie! kind). What kind of hardware problem does that indicate?

---

### Post by cookfromfrozen on 2007-03-18
An MPrime failure can be an overheating/bad CPU, but bad RAM can make MPrime fail as well.  If you can afford to take the system offline overnight, you should run Memtest86.  If you get failures on that it is almost certainly the RAM.  If you have really bad RAM it will fail within the first 15 minutes or so.

---

