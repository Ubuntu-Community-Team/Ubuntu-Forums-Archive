---
title: "&quot;Scheduling while atomic&quot; spamming syslog due to my driver module"
date: 2011-03-31
forum: Ubuntu Dev Link Forum
---

### Post by j.daniel on 2011-03-31
**Hello,**

  First of all; I'm running Ubuntu 10.10; kernel 2.6.35-28-generic
  
  I have a question I thought I'd bounce with you guys to see if you have any clue to whats going on; I am trying to make my first linux driver - its for a small USB gadget - and have graduated from locking up the system completely to recieving a lot of dumps in syslog due to "**BUG: scheduling while atomic: Xorg/1112/0x10010000**". The driver behaves as expected though, but I would like to get rid of the cause of the BUG dumps.

  Google tells me that: '*"Scheduling while atomic" means that a thread has called schedule() during an operation which is supposed to be atomic (ie uninterrupted).*' - and I get that. I am using [FONT="Courier New"]wake_up_interruptible()[/FONT] in an USB bulk transfer URB completion callback function, but I assumed that it wouldn't cause the process to yield ?!? If I remove the corresponding [FONT="Courier New"]wait_event_interruptible()[/FONT] in the read fileops function, the problem disappears.
  
  I guess I could try to schedule a tasklet to do the wake up call if it is the location (inside an URB callback) that is the problem, but I want to avoid to add tasklets into the soup as well if I don't have to - also it would be nice to know why something breaks instead of just getting it to work by chance.
  
  Any thoughts? As I said, if I remove the wait function - not the wake up one in the USB URB callback - it works (with my userspace app sutiably changed to use polling then of course).

  I can give some more details and code excerpts if needed, but I thought this might be a conceptual issue rather than a nuts&bolts issue.
  
  Each time a message is recieved/read from the USB gadget, syslog gets a pounding. A typical syslog block is (where the [FONT="Courier New"]ant+driver[/FONT] is my module, and the first row with the [FONT="Courier New"]usbant+[/FONT] message is when the gadget returns data to the driver);
  
```
Mar 31 17:40:08 acer kernel: [ 2075.853190] usbant+ 5-2:1.0: ANT+ Message recieved.
Mar 31 17:40:08 acer kernel: [ 2075.853199] BUG: scheduling while atomic: Xorg/1112/0x10010000
Mar 31 17:40:08 acer kernel: [ 2075.853203] Modules linked in: ant+driver binfmt_misc snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq nvidia(P) snd_timer ppdev snd_seq_device joydev snd serio_raw ati_agp parport_pc i2c_piix4 soundcore snd_page_alloc agpgart lp parport xfs exportfs hid_logitech ff_memless firewire_ohci usbhid hid ahci usb_storage firewire_core crc_itu_t libahci sky2 pata_atiixp floppy
Mar 31 17:40:08 acer kernel: [ 2075.853240] Modules linked in: ant+driver binfmt_misc snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq nvidia(P) snd_timer ppdev snd_seq_device joydev snd serio_raw ati_agp parport_pc i2c_piix4 soundcore snd_page_alloc agpgart lp parport xfs exportfs hid_logitech ff_memless firewire_ohci usbhid hid ahci usb_storage firewire_core crc_itu_t libahci sky2 pata_atiixp floppy
Mar 31 17:40:08 acer kernel: [ 2075.853269] 
Mar 31 17:40:08 acer kernel: [ 2075.853275] Pid: 1112, comm: Xorg Tainted: P            2.6.35-28-generic #49-Ubuntu MRS600M/Aspire T671
Mar 31 17:40:08 acer kernel: [ 2075.853278] EIP: 0060:[<c0150516>] EFLAGS: 00203246 CPU: 0
Mar 31 17:40:08 acer kernel: [ 2075.853287] EIP is at sys_gettimeofday+0x36/0x70
Mar 31 17:40:08 acer kernel: [ 2075.853290] EAX: 00000000 EBX: bfd6b974 ECX: 00000000 EDX: bfd6b974
Mar 31 17:40:08 acer kernel: [ 2075.853292] ESI: f2365f98 EDI: 00000000 EBP: f2365fac ESP: f2365f98
Mar 31 17:40:08 acer kernel: [ 2075.853295]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Mar 31 17:40:08 acer kernel: [ 2075.853298] Process Xorg (pid: 1112, ti=f2364000 task=f2369960 task.ti=f2364000)
Mar 31 17:40:08 acer kernel: [ 2075.853301] Stack:
Mar 31 17:40:08 acer kernel: [ 2075.853302]  4d94a058 0001ed4d bfd6b974 b77e07d0 000007d0 f2364000 c05cade4 bfd6b974
Mar 31 17:40:08 acer kernel: [ 2075.853309] <0> 00000000 07168340 b77e07d0 000007d0 00000000 0000004e 0000007b ffff007b
Mar 31 17:40:08 acer kernel: [ 2075.853315] <0> c05c0000 00000033 0000004e 003ee416 00000073 00203246 bfd6b928 0000007b
Mar 31 17:40:08 acer kernel: [ 2075.853322] Call Trace:
Mar 31 17:40:08 acer kernel: [ 2075.853330]  [<c05cade4>] ? syscall_call+0x7/0xb
Mar 31 17:40:08 acer kernel: [ 2075.853335]  [<c05c0000>] ? calibrate_delay_direct+0x4a/0xfb
Mar 31 17:40:08 acer kernel: [ 2075.853338] Code: f8 89 7d fc 0f 1f 44 00 00 8b 5d 08 8b 7d 0c 85 db 74 1c 8d 75 ec 89 f0 e8 c8 fb 01 00 b9 08 00 00 00 89 f2 89 d8 e8 1a a8 20 00 <85> c0 75 2e 85 ff 75 0f 31 c0 8b 5d f4 8b 75 f8 8b 7d fc 89 ec 
Mar 31 17:40:08 acer kernel: [ 2075.853371] Call Trace:
Mar 31 17:40:08 acer kernel: [ 2075.853374]  [<c05cade4>] syscall_call+0x7/0xb
Mar 31 17:40:08 acer kernel: [ 2075.853378]  [<c05c0000>] ? calibrate_delay_direct+0x4a/0xfb
```

  Interesting enough, the process generating these differs. Another block is for instance;

```
Mar 31 17:29:49 acer kernel: [ 1457.659976] usbant+ 5-2:1.0: ANT+ Message recieved.
Mar 31 17:29:49 acer kernel: [ 1457.659986] BUG: scheduling while atomic: swapper/0/0x10010000
Mar 31 17:29:49 acer kernel: [ 1457.659990] Modules linked in: ant+driver binfmt_misc snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq nvidia(P) snd_timer ppdev snd_seq_device joydev snd serio_raw ati_agp parport_pc i2c_piix4 soundcore snd_page_alloc agpgart lp parport xfs exportfs hid_logitech ff_memless firewire_ohci usbhid hid ahci usb_storage firewire_core crc_itu_t libahci sky2 pata_atiixp floppy
Mar 31 17:29:49 acer kernel: [ 1457.660026] Modules linked in: ant+driver binfmt_misc snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq nvidia(P) snd_timer ppdev snd_seq_device joydev snd serio_raw ati_agp parport_pc i2c_piix4 soundcore snd_page_alloc agpgart lp parport xfs exportfs hid_logitech ff_memless firewire_ohci usbhid hid ahci usb_storage firewire_core crc_itu_t libahci sky2 pata_atiixp floppy
Mar 31 17:29:49 acer kernel: [ 1457.660055] 
Mar 31 17:29:49 acer kernel: [ 1457.660061] Pid: 0, comm: swapper Tainted: P            2.6.35-28-generic #49-Ubuntu MRS600M/Aspire T671
Mar 31 17:29:49 acer kernel: [ 1457.660065] EIP: 0060:[<c010a826>] EFLAGS: 00000246 CPU: 0
Mar 31 17:29:49 acer kernel: [ 1457.660074] EIP is at mwait_idle+0x56/0xb0
Mar 31 17:29:49 acer kernel: [ 1457.660077] EAX: 00000000 EBX: c0817980 ECX: 00000000 EDX: 00000000
Mar 31 17:29:49 acer kernel: [ 1457.660079] ESI: 00000000 EDI: 2ff68000 EBP: c07c3f84 ESP: c07c3f7c
Mar 31 17:29:49 acer kernel: [ 1457.660082]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Mar 31 17:29:49 acer kernel: [ 1457.660085] Process swapper (pid: 0, ti=c07c2000 task=c07c96e0 task.ti=c07c2000)
Mar 31 17:29:49 acer kernel: [ 1457.660088] Stack:
Mar 31 17:29:49 acer kernel: [ 1457.660090]  c0817980 00000000 c07c3fa4 c0101fcc dd1547d0 0000001a f4d5eef5 84a6e669
Mar 31 17:29:49 acer kernel: [ 1457.660096] <0> c0858b40 00000000 c07c3fac c05b4171 c07c3fd8 c081b815 000000c6 c081b9d8
Mar 31 17:29:49 acer kernel: [ 1457.660102] <0> 2f527000 924e2e5a 0000001a 3b31087c e0f858fb c0858b40 2f527000 c07c3ff8
Mar 31 17:29:49 acer kernel: [ 1457.660109] Call Trace:
Mar 31 17:29:49 acer kernel: [ 1457.660115]  [<c0101fcc>] ? cpu_idle+0x8c/0xd0
Mar 31 17:29:49 acer kernel: [ 1457.660121]  [<c05b4171>] ? rest_init+0x71/0x80
Mar 31 17:29:49 acer kernel: [ 1457.660127]  [<c081b815>] ? start_kernel+0x36e/0x374
Mar 31 17:29:49 acer kernel: [ 1457.660131]  [<c081b9d8>] ? pass_all_bootoptions+0x0/0xa
Mar 31 17:29:49 acer kernel: [ 1457.660135]  [<c081b0d7>] ? i386_start_kernel+0xd7/0xdf
Mar 31 17:29:49 acer kernel: [ 1457.660137] Code: 8c c0 f6 44 11 27 02 75 2c 31 d2 83 c0 08 89 d1 0f 01 c8 0f ae f0 89 f6 89 e0 25 00 e0 ff ff f6 40 08 08 75 1d 31 c0 fb 0f 01 c9 <5b> 5e 5d c3 8d b6 00 00 00 00 0f ae 78 08 89 e0 25 00 e0 ff ff 
Mar 31 17:29:49 acer kernel: [ 1457.660170] Call Trace:
Mar 31 17:29:49 acer kernel: [ 1457.660174]  [<c0101fcc>] cpu_idle+0x8c/0xd0
Mar 31 17:29:49 acer kernel: [ 1457.660177]  [<c05b4171>] rest_init+0x71/0x80
Mar 31 17:29:49 acer kernel: [ 1457.660181]  [<c081b815>] start_kernel+0x36e/0x374
Mar 31 17:29:49 acer kernel: [ 1457.660184]  [<c081b9d8>] ? pass_all_bootoptions+0x0/0xa
Mar 31 17:29:49 acer kernel: [ 1457.660188]  [<c081b0d7>] i386_start_kernel+0xd7/0xdf

```

  To complete the picture, the userspace app is just a simple command line thing printing diagnostics to stdout.

  Any ideas?

Cheers
/ Daniel

---

### Post by j.daniel on 2011-04-01
**Hi there,**

  A thought has occurred to me; does anyone know if the USB URB completion callback is called in an interrupt context?

  That might be it; I use semaphores as mutex objects and I guess that the wait & wake-up functions do that too, so the problem might actually be that the USB URB competion code runs into problems due to this.

Cheers!
/ Daniel

---

### Post by j.daniel on 2011-04-01
Hi again,

  I think I have found the reason, from usb/URB.txt and also mentioned in [Linux Journal article/4786]("http://www.linuxjournal.com/article/4786");

> 190	NOTE:  ***** WARNING *****
191	NEVER SLEEP IN A COMPLETION HANDLER.  These are normally called
192	during hardware interrupt processing.  If you can, defer substantial
193	work to a tasklet (bottom half) to keep system latencies low.  You'll
194	probably need to use spinlocks to protect data structures you manipulate
195	in completion handlers.


Ah well, I guess a tasklet (edit: *workqueue*) it is then.

Cheers!
/ Daniel

---

### Post by j.daniel on 2011-04-01
**Final answer,**

  Problem was caused by usb_submit_urb(). In the completion handler I called it with the same parameters as when I submitted them in the first place, i.e. with the flag GFP_KERNEL. With liberal amounts of printk statements sprinkled around the code, I found that it was the cause.

  From the man-page;

> GFP_ATOMIC is used when (a) you are inside a completion handler, an interrupt, bottom half, tasklet or timer, or (b) you are holding a spinlock or rwlock (does not apply to semaphores), or (c) current->state != TASK_RUNNING, this is the case only after you've changed it. 

  Chnged to GPF_ATOMIC and syslog is quiet!!! 

  Phew!! One day worth of bug hunting for that one...

Cheers!
/ Daniel

---

