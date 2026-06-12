---
title: "------------------------------------=-----------"
date: 2005-03-28
forum: Repositories &amp; Backports
---

### Post by john6000 on 2005-03-28
ok
downloaded kubantu (install version not live cd)
tested it in vmware and

on boot up of install prog

io scheduler noop registered 
io scheduler anticipatory registered 
io scheduler deadline registered 
io scheduler cfq registered 
RAMDISK driver initialized: 16 RAM disks of 12288K size 1024 blocksize 
invalid operand: 0000 [#1] 
PREEMPT 
Modules linked in: 
CPU: 0 
EIP: 0060:[<c01010dc>] Not tainted VLI 
EFLAGS: 00000286 (2.6.10-5-386) 
EIP is at mwait_idle+0x23/0x40 
eax: c0324008 ebx: c0324000 ecx: 00000000 edx: 00000000 
esi: 00039100 edi: c0360120 ebp: 003ad007 esp: c0325fe0 
ds: 007b es: 007b ss: 0068 
Process swapper (pid: 0, threadinfo=c0324000 task=c02a5b00) 
Stack: c0324000 c0101095 00010800 c03266a4 00000ff0 00000ff0 c03611e0 c010019f 
Call Trace: 
[<c0101095>] cpu_idle+0x21/0x45 
[<c03266a4>] start_kernel+0x16f/0x173 
Code: c5 e8 b3 4b 16 00 eb eb 53 fb ba 00 e0 ff ff 21 e2 8b 42 08 a8 08 75 2e 0
ba 6a 08 10 31 c9 bb 00 e0 ff ff 21 e3 89 ca 8d 43 08 <0f> 01 c8 8b 43 08 a8 0
75 0c 89 c8 0f 01 c9 8b 43 08 a8 08 74 
<0>Kernel panic - not syncing: Attempted to kill the idle task!

---

### Post by john6000 on 2005-03-28
[QUOTE=john6000]ok
downloaded kubantu (install version not live cd)
tested it in vmware and

on boot up of install prog

io scheduler noop registered 
io scheduler anticipatory registered 
io scheduler deadline registered 
io scheduler cfq registered 
RAMDISK driver initialized: 16 RAM disks of 12288K size 1024 blocksize 
invalid operand: 0000 [#1] 
PREEMPT 
Modules linked in: 
CPU: 0 
EIP: 0060:[<c01010dc>] Not tainted VLI 
EFLAGS: 00000286 (2.6.10-5-386) 
EIP is at mwait_idle+0x23/0x40 
eax: c0324008 ebx: c0324000 ecx: 00000000 edx: 00000000 
esi: 00039100 edi: c0360120 ebp: 003ad007 esp: c0325fe0 
ds: 007b es: 007b ss: 0068 
Process swapper (pid: 0, threadinfo=c0324000 task=c02a5b00) 
Stack: c0324000 c0101095 00010800 c03266a4 00000ff0 00000ff0 c03611e0 c010019f 
Call Trace: 
[<c0101095>] cpu_idle+0x21/0x45 
[<c03266a4>] start_kernel+0x16f/0x173 
Code: c5 e8 b3 4b 16 00 eb eb 53 fb ba 00 e0 ff ff 21 e2 8b 42 08 a8 08 75 2e 0
ba 6a 08 10 31 c9 bb 00 e0 ff ff 21 e3 89 ca 8d 43 08 <0f> 01 c8 8b 43 08 a8 0
75 0c 89 c8 0f 01 c9 8b 43 08 a8 08 74 
<0>Kernel panic - not syncing: Attempted to kill the idle task![/QUOTE]




i just notced i posted in wrong bit and i cant delete i

---

### Post by ember on 2005-03-28
You can delete your message by editing it and selecting "delete message".

---

