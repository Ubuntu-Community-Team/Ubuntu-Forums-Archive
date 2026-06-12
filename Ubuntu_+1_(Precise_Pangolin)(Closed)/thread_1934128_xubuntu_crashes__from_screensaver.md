---
title: "xubuntu crashes  from screensaver"
date: 2012-03-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2012-03-01
After letting the xubuntu desktop run for about 2 hours in screensaver mode I get this result:

---

### Post by prana on 2012-03-01
> **ventrical said:**
> After letting the xubuntu desktop run for about 2 hours in screensaver mode I get this result:

Which screensaver was it? I can try and find out if mine fails as spectacularly as yours.

---

### Post by Elfy on 2012-03-02
> **prana said:**
> Which screensaver was it? I can try and find out if mine fails as spectacularly as yours.

Same.

---

### Post by ventrical on 2012-03-02
> **forestpiskie said:**
> Same.

 I had it on random .. where it chooses different screens every so often. The last I looked it was on the Matrix screen , but , a previous crash was with  Fibre lamp.

---

### Post by Elfy on 2012-03-02
I'll set mine to use it when I go to work - will report back this afternoon. That'll be some 5 hours or so.

---

### Post by ventrical on 2012-03-02
> **forestpiskie said:**
> I'll set mine to use it when I go to work - will report back this afternoon. That'll be some 5 hours or so.

Thanks ..!

---

### Post by ventrical on 2012-03-02
I just did a big update.. so I will try again to see if the bug is still there. I think (if the bug is still there) that it could be a Nvidia driver problem.

 Here's system I'm using:

ventrical@ventrical1ME051:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] LPC Controller (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: NVIDIA Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
ventrical@ventrical1ME051:~$

---

### Post by ventrical on 2012-03-02
Here is a snippet from syslog. You will see here it crashed on 'hypertorus'.

```

Mar  2 07:02:21 ventrical1ME051 kernel: [10995.314390] [drm] nouveau 0000:01:00.0: PFIFO_DMA_PUSHER - Ch 2 Get 0x1f800000 Put 0x01644fb0 State 0xc000c000 (err: MEM_FAULT) Push 0x00000000
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.339759] BUG: unable to handle kernel paging request at f9480004
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.339808] IP: [<c12a7120>] iowrite32+0x30/0x40
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.339842] *pde = 29785067 *pte = 00000000 
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.339863] Oops: 0002 [#1] SMP 
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.339882] Modules linked in: rfcomm ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 ip_tables x_tables bridge stp bnep bluetooth nouveau snd_wavefront snd_cs4236 snd_wss_lib ttm snd_opl3_lib snd_hwdep drm_kms_helper snd_intel8x0 snd_ac97_codec ac97_bus drm snd_mpu401 snd_pcm snd_mpu401_uart snd_seq_midi snd_rawmidi i2c_algo_bit binfmt_misc snd_seq_midi_event snd_seq mxm_wmi snd_timer wmi video snd_seq_device snd snd_page_alloc soundcore sis_agp i2c_sis96x ppdev ns558 shpchp gameport mac_hid parport_pc lp parport usbhid hid 8139too 8139cp floppy
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] 
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] Pid: 2509, comm: hypertorus Not tainted 3.2.0-17-generic #27-Ubuntu    /GA-8S650GXM
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] EIP: 0060:[<c12a7120>] EFLAGS: 00210296 CPU: 0
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] EIP is at iowrite32+0x30/0x40
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] EAX: 21635088 EBX: 21635088 ECX: f9480004 EDX: f9480004
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] ESI: e97031c0 EDI: 00000000 EBP: cedcde18 ESP: cedcde18
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] Process hypertorus (pid: 2509, ti=cedcc000 task=cedf3f20 task.ti=cedcc000)
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] Stack:
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  cedcde20 f8323c57 cedcde8c f83272f0 e975b304 00000000 00000003 cedcde5c
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  cedcde7c c1008b28 ee9fb800 ee080000 cee218a0 cedcdedc ef60cb00 e97031c0
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  e975b200 cee03f20 cedc1120 e975b320 e975b320 cedcde6c cedcde6c ef2d5000
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] Call Trace:
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  [<f8323c57>] nouveau_bo_wr32+0x27/0x30 [nouveau]
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  [<f83272f0>] nouveau_gem_ioctl_pushbuf+0x6a0/0x820 [nouveau]
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  [<c1008b28>] ? sched_clock+0x8/0x10
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  [<f81e9e18>] drm_ioctl+0x378/0x480 [drm]
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  [<f8326c50>] ? nouveau_gem_ioctl_new+0x140/0x140 [nouveau]
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  [<c107a002>] ? clockevents_program_event+0xb2/0x170
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  [<c107b2c9>] ? tick_program_event+0x29/0x30
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  [<c106e800>] ? hrtimer_interrupt+0x160/0x260
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  [<f81e9aa0>] ? drm_copy_field+0x80/0x80 [drm]
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  [<c1142129>] do_vfs_ioctl+0x79/0x2d0
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  [<c11423ef>] sys_ioctl+0x6f/0x80
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  [<c157adc9>] ? smp_apic_timer_interrupt+0x59/0x88
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  [<c15737c4>] syscall_call+0x7/0xb
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  [<c157007b>] ? arch_local_irq_save+0xd/0x15
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] [drm] nouveau 0000:01:00.0: GPU lockup - switching to software fbcon
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003]  [<c1570000>] ? iommu_prepare_identity_map+0x17a/0x1e8
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] Code: 03 00 89 e5 89 d1 77 23 81 fa 00 00 01 00 76 0b 81 e2 ff ff 00 00 ef 5d c3 66 90 ba a0 b3 73 c1 89 c8 e8 44 ff ff ff 5d c3 66 90 <89> 02 5d c3 8d b6 00 00 00 00 8d bf 00 00 00 00 55 81 fa ff ff 
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] EIP: [<c12a7120>] iowrite32+0x30/0x40 SS:ESP 0068:cedcde18
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] CR2: 00000000f9480004
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output A
Mar  2 07:02:21 ventrical1ME051 kernel: [10995.340003] ---[ end trace 1cb1c6b1e4390022 ]---
Mar  2 07:17:01 ventrical1ME051 CRON[2524]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar  2 07:30:01 ventrical1ME051 CRON[2531]: (root) CMD (start -q anacron || :)
Mar  2 07:30:01 ventrical1ME051 anacron[2534]: Anacron 2.3 started on 2012-03-02
Mar  2 07:30:01 ventrical1ME051 anacron[2534]: Normal exit (0 jobs run)

```

---

### Post by ventrical on 2012-03-02
I checked the log of a previous crash and it definitely is 'hypertorus'.

Hope that helps

---

### Post by ventrical on 2012-03-02
Oddly enough , something ripped out my nvidia driver so I reinstalled it and the hyper torus is working in Ubuntu and now I will see how it goes with xubuntu.

---

### Post by Elfy on 2012-03-02
no issue here with fiber lamp - I 'think' I remember an issue with hypertorus a few weeks ago - but I tend not to use screensavers.

Just tried it now and it works ok - at least straight away it does.

I don't use nvidia - so I tried with nouveau.

---

### Post by ventrical on 2012-03-02
> **forestpiskie said:**
> no issue here with fiber lamp - I 'think' I remember an issue with hypertorus a few weeks ago - but I tend not to use screensavers.

Just tried it now and it works ok - at least straight away it does.

I don't use nvidia - so I tried with nouveau.


It was with the nouveau driver that it crashed. All other screensavers worked... but .. I think I have the wrong driver as it is an older nvidia card..

---

### Post by Elfy on 2012-03-02
OK - if you get issues again once you've got nvidia installed - I'll install nvidia and see if I can replicate it. My card is not 'new' by any stretch of the imagination - but it's not 'old' ;)

GeForce 8500 GT

---

### Post by Elfy on 2012-03-02
OK - if you get issues again once you've got nvidia installed - I'll install nvidia and see if I can replicate it. My card is not 'new' by any stretch of the imagination - but it's not 'old' ;)

GeForce 8500 GT

---

### Post by ventrical on 2012-03-02
> **forestpiskie said:**
> OK - if you get issues again once you've got nvidia installed - I'll install nvidia and see if I can replicate it. My card is not 'new' by any stretch of the imagination - but it's not 'old' ;)

GeForce 8500 GT

  Thanks .. err .. umm.. I do not mean to be off topic but somthing is really messed up here (and Ithink I did it).

 The adapter card is:
01:00.0 VGA compatible controller: NVIDIA Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
 and I have nVidia -current installed but  (look at the screenshot) that was the driver that was originally installed and jockey will not detect anything unless I sudo -apt-get install nvidia current. So it tells me it's activated but not in use.So perhaps I need to purge  nvidia-current and get the driver in the screenshot below. Do you know offhand what command I should use to get the other driver?

---

### Post by ventrical on 2012-03-02
and here is the proper driver detected by jockey on the same machine with Oneiric:

---

### Post by Elfy on 2012-03-02
Not sure I'm afraid - I thought that was the right driver for that card - that's the one I used to have before I got this current card, previous being more or less the same as you have.

I guess if I was going to try anything I'd have a go with synaptic rather than jockey.

Are they not actually showing the same driver.

---

### Post by Elfy on 2012-03-03
Installed nvidia - tried the screensaver - no errors

Removed nvidia and then fought the system for a while to get nouveau back with a nice resolution :(

---

### Post by ventrical on 2012-03-03
> **forestpiskie said:**
> Installed nvidia - tried the screensaver - no errors

Removed nvidia and then fought the system for a while to get nouveau back with a nice resolution :(

Thanks for trying. I don't mind doing a fresh install. I think it is somthing I did while switiching harddrives.

Kind Regards,

Ventrical

---

### Post by Elfy on 2012-03-03
Welcome :)

---

