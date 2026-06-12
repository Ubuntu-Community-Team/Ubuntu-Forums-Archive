---
title: "Kernel crashes"
date: 2010-12-21
forum: Server Platforms
---

### Post by wscheun on 2010-12-21
Hi,

For some time now I'm having regular system hangs/crashes on one of my Ubuntu servers. I finally came around to connect teh serers together with a null modem cable so I could get a stack trace through console output.

Servers are running Ubuntu 10.04.1 LTS Server Edition, Kernel 2.6.32-26-generic #48-Ubuntu.
I had this on Ubuntu 9.x as well and hoped the crashes would go away after upgrading.
  
Stack trace I'm getting is:

[19301.260207] BUG: unable to handle kernel NULL pointer dereference at 00000049

[19301.264163] IP: [<c01486f2>] dequeue_task_fair+0x42/0x70
[19301.264163] *pde = 32792067 *pte = 00000000 
[19301.264163] Oops: 0000 [#1] SMP 
[19301.264163] last sysfs file: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
[19301.264163] Modules linked in: softdog drbd snd_hda_codec_via snd_hda_intel snd_hda_codec fbcon snd_hwdep tileblit font snd_pcm bitblit snd_timer softcursor 
snd soundcore vga16fb via_agp ppdev lp parport_pc snd_page_alloc vgastate i2c_viapro psmouse agpgart parport serio_raw shpchp 8139too usb_storage 8139cp mii pata_via
[19301.264163] 
[19301.264163] Pid: 40, comm: kondemand/0 Not tainted (2.6.32-26-generic #48-Ubuntu) To Be Filled By O.E.M.
[19301.264163] EIP: 0060:[<c01486f2>] EFLAGS: 00010002 CPU: 0
[19301.264163] EIP is at dequeue_task_fair+0x42/0x70
[19301.264163] EAX: c9889a5f EBX: 0000029e ECX: f7394cac EDX: 00000021
[19301.264163] ESI: f7394cac EDI: d5a08760 EBP: f6801efc ESP: f6801ef0
[19301.264163]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[19301.264163] Process kondemand/0 (pid: 40, ti=f6800000 task=f7394c80 task.ti=f6800000)
[19301.264163] Stack:
[19301.264163]  c059ac80 f7394c80 c5808760 f6801f24 c0132cdc d5a08760 ecc0a7e9 0000118d
[19301.264163] <0> 00000000 00000000 d5a08760 d5a08760 f7394c80 f6801f30 c0132d95 f7394c80
[19301.264163] <0> f6801f88 c058b80a 00000000 00000000 f6801f4c c0848760 f7394f24 c0848760
[19301.264163] Call Trace:
[19301.264163]  [<c0132cdc>] ? dequeue_task+0xfc/0x150
[19301.264163]  [<c0132d95>] ? deactivate_task+0x25/0x30
[19301.264163]  [<c058b80a>] ? schedule+0x55a/0x840
[19301.264163]  [<c0163a6c>] ? run_workqueue+0xbc/0x150
[19301.264163]  [<c0163bb5>] ? worker_thread+0xb5/0xe0
[19301.264163]  [<c0167b00>] ? autoremove_wake_function+0x0/0x50
[19301.264163]  [<c0163b00>] ? worker_thread+0x0/0xe0
[19301.264163]  [<c0167874>] ? kthread+0x74/0x80
[19301.264163]  [<c0167800>] ? kthread+0x0/0x80
[19301.264163]  [<c0104087>] ? kernel_thread_helper+0x7/0x10
[19301.264163] Code: 90 8b b6 48 01 00 00 b9 01 00 00 00 85 f6 74 15 8b 9e 4c 01
 00 00 89 f2 89 d8 e8 da f8 ff ff 8b 1b 85 db 74 dc 8b 97 34 04 00 00 <81> 7a 28
 80 ac 59 c0 74 05 5b 5e 5f 5d c3 8b 82 78 01 00 00 8b 
[19301.264163] EIP: [<c01486f2>] dequeue_task_fair+0x42/0x70 SS:ESP 0068:f6801ef0
[19301.264163] CR2: 0000000000000049
[19301.264163] ---[ end trace 8ab0df66568ebdc0 ]---

Is this software, kernel, hardware? What can I do?

Regards,

Willem

---

