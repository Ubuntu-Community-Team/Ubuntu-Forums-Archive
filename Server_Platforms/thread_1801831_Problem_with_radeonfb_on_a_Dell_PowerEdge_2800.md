---
title: "Problem with radeonfb on a Dell PowerEdge 2800"
date: 2011-07-11
forum: Server Platforms
---

### Post by arnuschky on 2011-07-11
Hi,

Ubuntu Server 11.04 64bit seems to work fine on my Dell - most of the time at least. Sometimes upon boot, the screen stays black after grub. If it does boot correctly, I can find the following in dmesg:

```
[    2.201739] [drm] radeon defaulting to kernel modesetting.
[    2.201744] [drm] radeon kernel modesetting enabled.
[    2.201838] radeon 0000:10:0d.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.205039] [drm] initializing kernel modesetting (RV100 0x1002:0x5159).
[    2.205091] [drm] register mmio base: 0xDF1E0000
[    2.205094] [drm] register mmio size: 65536
[    2.205261] radeon 0000:10:0d.0: VRAM: 128M 0x00000000C8000000 - 0x00000000CFFFFFFF (16M used)
[    2.205266] radeon 0000:10:0d.0: GTT: 512M 0x00000000A8000000 - 0x00000000C7FFFFFF
[    2.205277] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.205279] [drm] Driver supports precise vblank timestamp query.
[    2.205315] [drm] radeon: irq initialized.
[    2.205839] [drm] Detected VRAM RAM=128M, BAR=128M
[    2.205847] [drm] RAM width 32bits DDR
[    2.205976] [TTM] Zone  kernel: Available graphics memory: 1028044 kiB.
[    2.205982] [TTM] Initializing pool allocator.
[    2.206017] [drm] radeon: 16M of VRAM memory ready
[    2.206022] [drm] radeon: 512M of GTT memory ready.
[    2.206064] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    2.230236] radeon 0000:10:0d.0: WB enabled
[    2.230408] [drm] Loading R100 Microcode
[    2.240773] [drm] radeon: ring at 0x00000000A8001000
[    2.240819] [drm] ring test succeeded in 1 usecs
[    2.242014] [drm] radeon: ib pool ready.
[    2.242560] [drm] ib test succeeded in 0 usecs
[    2.244072] [drm] Radeon Display Connectors
[    2.244081] [drm] Connector 0:
[    2.244088] [drm]   VGA
[    2.244096] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[    2.244103] [drm]   Encoders:
[    2.244109] [drm]     CRT1: INTERNAL_DAC1
[    2.244115] [drm] Connector 1:
[    2.244122] [drm]   VGA
[    2.244129] [drm]   DDC: 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c
[    2.244135] [drm]   Encoders:
[    2.244142] [drm]     CRT2: INTERNAL_DAC2
[    2.244148] [drm] Connector 2:
[    2.244155] [drm]   DVI-I
[    2.244161] [drm]   HPD1
[    2.244168] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[    2.244175] [drm]   Encoders:
[    2.244181] [drm]     CRT2: INTERNAL_DAC2
[    2.244187] [drm]     DFP1: INTERNAL_TMDS1
[    2.570623] [drm] fb mappable at 0xC8040000
[    2.570636] [drm] vram apper at 0xC8000000
[    2.570644] [drm] size 786432
[    2.570652] [drm] fb depth is 8
[    2.570661] [drm]    pitch is 1024
[    2.669272] irq 18: nobody cared (try booting with the "irqpoll" option)
[    2.669278] Pid: 191, comm: modprobe Not tainted 2.6.38-8-server #42-Ubuntu
[    2.669281] Call Trace:
[    2.669283]  <IRQ>  [<ffffffff810d478b>] ? __report_bad_irq.clone.2+0x2b/0xa0
[    2.669299]  [<ffffffff810d4b8a>] ? note_interrupt+0x19a/0x1e0
[    2.669304]  [<ffffffff8106d3e9>] ? __do_softirq+0xf9/0x1c0
[    2.669308]  [<ffffffff810d5a7d>] ? handle_fasteoi_irq+0xdd/0x110
[    2.669313]  [<ffffffff8100e982>] ? handle_irq+0x22/0x40
[    2.669318]  [<ffffffff815df97d>] ? do_IRQ+0x5d/0xe0
[    2.669323]  [<ffffffff815d7cd3>] ? ret_from_intr+0x0/0x15
[    2.669325]  <EOI>  [<ffffffff812e4add>] ? delay_tsc+0x3d/0x80
[    2.669334]  [<ffffffff812e4aea>] ? delay_tsc+0x4a/0x80
[    2.669338]  [<ffffffff812e4a3e>] ? __const_udelay+0x2e/0x30
[    2.669379]  [<ffffffffa015ccee>] ? radeon_set_pll.clone.4+0x52e/0xb20 [radeon]
[    2.669410]  [<ffffffffa015da3c>] ? radeon_crtc_mode_set+0x3c/0x160 [radeon]
[    2.669419]  [<ffffffffa00b05c3>] ? drm_crtc_helper_set_mode+0x343/0x4e0 [drm_kms_helper]
[    2.669423]  [<ffffffff815d7cce>] ? common_interrupt+0xe/0x13
[    2.669430]  [<ffffffffa00b147d>] ? drm_crtc_helper_set_config+0x84d/0xa10 [drm_kms_helper]
[    2.669435]  [<ffffffff815d5f01>] ? mutex_lock+0x1/0x50
[    2.669440]  [<ffffffffa00af22c>] ? drm_fb_helper_set_par+0x7c/0xf0 [drm_kms_helper]
[    2.669444]  [<ffffffff8132ebd0>] ? fbcon_init+0x650/0x6c0
[    2.669449]  [<ffffffff8139810f>] ? visual_init+0xcf/0x180
[    2.669453]  [<ffffffff813987bc>] ? bind_con_driver+0x1cc/0x410
[    2.669456]  [<ffffffff81398b81>] ? take_over_console+0x61/0x70
[    2.669460]  [<ffffffff81329a73>] ? fbcon_takeover+0x63/0xc0
[    2.669463]  [<ffffffff8132f3bd>] ? fbcon_event_notify+0x4dd/0x550
[    2.669468]  [<ffffffff815db8ed>] ? notifier_call_chain+0x4d/0x70
[    2.669473]  [<ffffffff8108d588>] ? __blocking_notifier_call_chain+0x58/0x80
[    2.669478]  [<ffffffff813246f9>] ? fb_add_videomode+0x89/0xf0
[    2.669482]  [<ffffffff8108d5c6>] ? blocking_notifier_call_chain+0x16/0x20
[    2.669486]  [<ffffffff8131e00b>] ? fb_notifier_call_chain+0x1b/0x20
[    2.669490]  [<ffffffff8131f5d8>] ? register_framebuffer+0x1d8/0x2b0
[    2.669495]  [<ffffffffa00af4f2>] ? drm_fb_helper_single_fb_probe+0x252/0x2f0 [drm_kms_helper]
[    2.669501]  [<ffffffffa00af684>] ? drm_fb_helper_initial_config+0xf4/0x120 [drm_kms_helper]
[    2.669533]  [<ffffffffa0170e8a>] ? radeon_fbdev_init+0xca/0x120 [radeon]
[    2.669564]  [<ffffffffa016a746>] ? radeon_modeset_init+0x226/0x250 [radeon]
[    2.669591]  [<ffffffffa0143048>] ? radeon_driver_load_kms+0x118/0x1a0 [radeon]
[    2.669610]  [<ffffffffa004ea3e>] ? drm_get_pci_dev+0x18e/0x300 [drm]
[    2.669615]  [<ffffffff81154e8f>] ? kmem_cache_alloc_trace+0xef/0x110
[    2.669645]  [<ffffffffa01d36be>] ? radeon_pci_probe+0xb2/0xba [radeon]
[    2.669649]  [<ffffffff812ff26f>] ? local_pci_probe+0x5f/0xd0
[    2.669653]  [<ffffffff81300b69>] ? pci_device_probe+0x129/0x130
[    2.669659]  [<ffffffff813bab9a>] ? driver_sysfs_add+0x7a/0xb0
[    2.669662]  [<ffffffff813bacc8>] ? really_probe+0x68/0x190
[    2.669666]  [<ffffffff813bafd5>] ? driver_probe_device+0x45/0x70
[    2.669670]  [<ffffffff813bb0ab>] ? __driver_attach+0xab/0xb0
[    2.669673]  [<ffffffff813bb000>] ? __driver_attach+0x0/0xb0
[    2.669677]  [<ffffffff813b9e4e>] ? bus_for_each_dev+0x5e/0x90
[    2.669681]  [<ffffffff813bab1e>] ? driver_attach+0x1e/0x20
[    2.669684]  [<ffffffff813ba685>] ? bus_add_driver+0xc5/0x280
[    2.669707]  [<ffffffffa0219000>] ? radeon_init+0x0/0x1000 [radeon]
[    2.669711]  [<ffffffff813bb346>] ? driver_register+0x76/0x140
[    2.669733]  [<ffffffffa0219000>] ? radeon_init+0x0/0x1000 [radeon]
[    2.669736]  [<ffffffff812ff916>] ? __pci_register_driver+0x56/0xd0
[    2.669748]  [<ffffffffa004ef54>] ? drm_pci_init+0xe4/0xf0 [drm]
[    2.669770]  [<ffffffffa0219000>] ? radeon_init+0x0/0x1000 [radeon]
[    2.669780]  [<ffffffffa00465f8>] ? drm_init+0x58/0x70 [drm]
[    2.669802]  [<ffffffffa02190c4>] ? radeon_init+0xc4/0x1000 [radeon]
[    2.669807]  [<ffffffff81002175>] ? do_one_initcall+0x45/0x190
[    2.669812]  [<ffffffff810a472b>] ? sys_init_module+0xfb/0x250
[    2.669816]  [<ffffffff8100bfc2>] ? system_call_fastpath+0x16/0x1b
[    2.669818] handlers:
[    2.669820] [<ffffffff81449f30>] (usb_hcd_irq+0x0/0x80)
[    2.669826] [<ffffffffa0172ae0>] (radeon_driver_irq_handler_kms+0x0/0x20 [radeon])
[    2.669858] Disabling IRQ #18
[    2.894545] Console: switching to colour frame buffer device 128x48
[    2.902883] fb0: radeondrmfb frame buffer device
[    2.902889] drm: registered panic notifier
[    2.902908] [drm] Initialized radeon 2.8.0 20080528 for 0000:10:0d.0 on minor 0
```

# lspci -nn | grep VGA
```
10:0d.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] [1002:5159]
```

# cat /proc/interrupts  | grep 18
```
  18:          0     200002   IO-APIC-fasteoi   uhci_hcd:usb4, radeon
```

Has anyone encountered something like this before? Should I remove the framebuffer? Other ideas to fix this?

Arnuschky

---

### Post by arnuschky on 2011-07-14
I found two posts that seem to be related, in is a debian bug, the other one a LKML post:

[LIST][*][http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=586312](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=586312)
[*] [https://lkml.org/lkml/2011/5/2/271](https://lkml.org/lkml/2011/5/2/271)[/LIST]
 
Thus, I guess it seems to be a general kernel problem. What's the policy on this, should I add an Ubuntu bug for this?

---

