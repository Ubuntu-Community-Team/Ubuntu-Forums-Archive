---
title: "Recurring Kernel Panic"
date: 2010-10-15
forum: System76 Support
---

### Post by skippy_ on 2010-10-15
Hi there,

I recently got a Pangolin Performance and I'm really enjoying the laptop, but I am having some issues.

First, I did a clean install of 10.10 and my WiFi driver was just not having it, any time I opened up a torrent or tried to transfer a large file the driver would stop working unless I rebooted.

No big deal, I just went back to 10.04, everything works great in 10.04 except I am experiencing regular kernel panics throughout the day. I use this laptop for work, so this is a huge headache for me and I was hoping for some guidance in resolving the issue. The culprit seems to be tcp_input.c 

Here's an excerpt from my logs:

Oct 15 10:17:50 skippy kernel: [ 6309.554333] WARNING: at /build/buildd/linux-2.6.32/net/ipv4/tcp_input.c:4216 tcp_data_queue+0xa71/0xaf0()
Oct 15 10:17:50 skippy kernel: [ 6309.554336] Hardware name: Pangolin Performance              
Oct 15 10:17:50 skippy kernel: [ 6309.554338] Modules linked in: arc4 aesni_intel cryptd aes_x86_64 aes_generic binfmt_misc ppdev joydev snd_hda_codec_atihdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device jmb38x_ms fbcon tileblit font bitblit snd softcursor fglrx(P) psmouse serio_raw memstick jme sdhci_pci mii sdhci vga16fb led_class vgastate soundcore snd_page_alloc r8192se_pci video output intel_agp lp parport usbhid hid ahci
Oct 15 10:17:50 skippy kernel: [ 6309.554389] Pid: 0, comm: swapper Tainted: P        W  2.6.32-25-generic #44-Ubuntu
Oct 15 10:17:50 skippy kernel: [ 6309.554392] Call Trace:
Oct 15 10:17:50 skippy kernel: [ 6309.554395]  <IRQ>  [<ffffffff81065efb>] warn_slowpath_common+0x7b/0xc0
Oct 15 10:17:50 skippy kernel: [ 6309.554407]  [<ffffffff81065f54>] warn_slowpath_null+0x14/0x20
Oct 15 10:17:50 skippy kernel: [ 6309.554412]  [<ffffffff814a4fc1>] tcp_data_queue+0xa71/0xaf0
Oct 15 10:17:50 skippy kernel: [ 6309.554416]  [<ffffffff814a7561>] tcp_rcv_established+0x371/0x730
Oct 15 10:17:50 skippy kernel: [ 6309.554421]  [<ffffffff814af0a3>] tcp_v4_do_rcv+0xf3/0x160
Oct 15 10:17:50 skippy kernel: [ 6309.554425]  [<ffffffff814b07f5>] tcp_v4_rcv+0x5b5/0x7e0
Oct 15 10:17:50 skippy kernel: [ 6309.554431]  [<ffffffff811321f2>] ? kmalloc_large_node+0x62/0xb0
Oct 15 10:17:50 skippy kernel: [ 6309.554436]  [<ffffffff8148e7ad>] ip_local_deliver_finish+0xdd/0x2d0
Oct 15 10:17:50 skippy kernel: [ 6309.554440]  [<ffffffff8148ea30>] ip_local_deliver+0x90/0xa0
Oct 15 10:17:50 skippy kernel: [ 6309.554444]  [<ffffffff8148deed>] ip_rcv_finish+0x12d/0x440
Oct 15 10:17:50 skippy kernel: [ 6309.554447]  [<ffffffff8148e475>] ip_rcv+0x275/0x360
Oct 15 10:17:50 skippy kernel: [ 6309.554453]  [<ffffffff8151d01d>] ? packet_rcv_spkt+0x4d/0x190
Oct 15 10:17:50 skippy kernel: [ 6309.554460]  [<ffffffff8145eaca>] netif_receive_skb+0x38a/0x5d0
Oct 15 10:17:50 skippy kernel: [ 6309.554464]  [<ffffffff8145ed93>] process_backlog+0x83/0xe0
Oct 15 10:17:50 skippy kernel: [ 6309.554468]  [<ffffffff8145f5cf>] net_rx_action+0x10f/0x250
Oct 15 10:17:50 skippy kernel: [ 6309.554474]  [<ffffffff8106d587>] __do_softirq+0xb7/0x1e0
Oct 15 10:17:50 skippy kernel: [ 6309.554480]  [<ffffffff8109381a>] ? tick_program_event+0x2a/0x30
Oct 15 10:17:50 skippy kernel: [ 6309.554486]  [<ffffffff810132ec>] call_softirq+0x1c/0x30
Oct 15 10:17:50 skippy kernel: [ 6309.554490]  [<ffffffff81014cb5>] do_softirq+0x65/0xa0
Oct 15 10:17:50 skippy kernel: [ 6309.554493]  [<ffffffff8106d425>] irq_exit+0x85/0x90
Oct 15 10:17:50 skippy kernel: [ 6309.554498]  [<ffffffff81548ac1>] smp_apic_timer_interrupt+0x71/0x9c
Oct 15 10:17:50 skippy kernel: [ 6309.554502]  [<ffffffff81012cb3>] apic_timer_interrupt+0x13/0x20
Oct 15 10:17:50 skippy kernel: [ 6309.554505]  <EOI>  [<ffffffff8130ebad>] ? acpi_idle_enter_bm+0x294/0x2c8
Oct 15 10:17:50 skippy kernel: [ 6309.554515]  [<ffffffff8130eba6>] ? acpi_idle_enter_bm+0x28d/0x2c8
Oct 15 10:17:50 skippy kernel: [ 6309.554522]  [<ffffffff81439897>] ? cpuidle_idle_call+0xa7/0x140
Oct 15 10:17:50 skippy kernel: [ 6309.554528]  [<ffffffff81010e73>] ? cpu_idle+0xb3/0x110
Oct 15 10:17:50 skippy kernel: [ 6309.554532]  [<ffffffff8152e69b>] ? rest_init+0x6b/0x80
Oct 15 10:17:50 skippy kernel: [ 6309.554539]  [<ffffffff8184bdcc>] ? start_kernel+0x368/0x371
Oct 15 10:17:50 skippy kernel: [ 6309.554544]  [<ffffffff8184b33a>] ? x86_64_start_reservations+0x125/0x129
Oct 15 10:17:50 skippy kernel: [ 6309.554547]  [<ffffffff8184b438>] ? x86_64_start_kernel+0xfa/0x109
Oct 15 10:17:50 skippy kernel: [ 6309.554551] ---[ end trace 5050d56cdc0af5c1 ]---

And here's another:

Oct 15 10:17:48 skippy kernel: [ 6307.963248] WARNING: at /build/buildd/linux-2.6.32/net/ipv4/tcp_input.c:4216 tcp_data_queue+0xa71/0xaf0()
Oct 15 10:17:48 skippy kernel: [ 6307.963252] Hardware name: Pangolin Performance              
Oct 15 10:17:48 skippy kernel: [ 6307.963254] Modules linked in: arc4 aesni_intel cryptd aes_x86_64 aes_generic binfmt_misc ppdev joydev snd_hda_codec_atihdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device jmb38x_ms fbcon tileblit font bitblit snd softcursor fglrx(P) psmouse serio_raw memstick jme sdhci_pci mii sdhci vga16fb led_class vgastate soundcore snd_page_alloc r8192se_pci video output intel_agp lp parport usbhid hid ahci
Oct 15 10:17:48 skippy kernel: [ 6307.963305] Pid: 0, comm: swapper Tainted: P           2.6.32-25-generic #44-Ubuntu
Oct 15 10:17:48 skippy kernel: [ 6307.963308] Call Trace:
Oct 15 10:17:48 skippy kernel: [ 6307.963311]  <IRQ>  [<ffffffff81065efb>] warn_slowpath_common+0x7b/0xc0
Oct 15 10:17:48 skippy kernel: [ 6307.963323]  [<ffffffff81065f54>] warn_slowpath_null+0x14/0x20
Oct 15 10:17:48 skippy kernel: [ 6307.963327]  [<ffffffff814a4fc1>] tcp_data_queue+0xa71/0xaf0
Oct 15 10:17:48 skippy kernel: [ 6307.963332]  [<ffffffff814a7561>] tcp_rcv_established+0x371/0x730
Oct 15 10:17:48 skippy kernel: [ 6307.963336]  [<ffffffff814af0a3>] tcp_v4_do_rcv+0xf3/0x160
Oct 15 10:17:48 skippy kernel: [ 6307.963340]  [<ffffffff814b07f5>] tcp_v4_rcv+0x5b5/0x7e0
Oct 15 10:17:48 skippy kernel: [ 6307.963347]  [<ffffffff811321f2>] ? kmalloc_large_node+0x62/0xb0
Oct 15 10:17:48 skippy kernel: [ 6307.963352]  [<ffffffff8148e7ad>] ip_local_deliver_finish+0xdd/0x2d0
Oct 15 10:17:48 skippy kernel: [ 6307.963356]  [<ffffffff8148ea30>] ip_local_deliver+0x90/0xa0
Oct 15 10:17:48 skippy kernel: [ 6307.963359]  [<ffffffff8148deed>] ip_rcv_finish+0x12d/0x440
Oct 15 10:17:48 skippy kernel: [ 6307.963363]  [<ffffffff8148e475>] ip_rcv+0x275/0x360
Oct 15 10:17:48 skippy kernel: [ 6307.963369]  [<ffffffff8151d01d>] ? packet_rcv_spkt+0x4d/0x190
Oct 15 10:17:48 skippy kernel: [ 6307.963375]  [<ffffffff8145eaca>] netif_receive_skb+0x38a/0x5d0
Oct 15 10:17:48 skippy kernel: [ 6307.963380]  [<ffffffff8145ed93>] process_backlog+0x83/0xe0
Oct 15 10:17:48 skippy kernel: [ 6307.963384]  [<ffffffff8145f5cf>] net_rx_action+0x10f/0x250
Oct 15 10:17:48 skippy kernel: [ 6307.963389]  [<ffffffff8106d587>] __do_softirq+0xb7/0x1e0
Oct 15 10:17:48 skippy kernel: [ 6307.963396]  [<ffffffff81030cd2>] ? ack_apic_level+0x82/0x1f0
Oct 15 10:17:48 skippy kernel: [ 6307.963401]  [<ffffffff810132ec>] call_softirq+0x1c/0x30
Oct 15 10:17:48 skippy kernel: [ 6307.963405]  [<ffffffff81014cb5>] do_softirq+0x65/0xa0
Oct 15 10:17:48 skippy kernel: [ 6307.963408]  [<ffffffff8106d425>] irq_exit+0x85/0x90
Oct 15 10:17:48 skippy kernel: [ 6307.963414]  [<ffffffff815489d5>] do_IRQ+0x75/0xf0
Oct 15 10:17:48 skippy kernel: [ 6307.963417]  [<ffffffff81012b13>] ret_from_intr+0x0/0x11
Oct 15 10:17:48 skippy kernel: [ 6307.963419]  <EOI>  [<ffffffff8130ebad>] ? acpi_idle_enter_bm+0x294/0x2c8
Oct 15 10:17:48 skippy kernel: [ 6307.963430]  [<ffffffff8130eba6>] ? acpi_idle_enter_bm+0x28d/0x2c8
Oct 15 10:17:48 skippy kernel: [ 6307.963437]  [<ffffffff81439897>] ? cpuidle_idle_call+0xa7/0x140
Oct 15 10:17:48 skippy kernel: [ 6307.963443]  [<ffffffff81010e73>] ? cpu_idle+0xb3/0x110
Oct 15 10:17:48 skippy kernel: [ 6307.963448]  [<ffffffff8152e69b>] ? rest_init+0x6b/0x80
Oct 15 10:17:48 skippy kernel: [ 6307.963454]  [<ffffffff8184bdcc>] ? start_kernel+0x368/0x371
Oct 15 10:17:48 skippy kernel: [ 6307.963458]  [<ffffffff8184b33a>] ? x86_64_start_reservations+0x125/0x129
Oct 15 10:17:48 skippy kernel: [ 6307.963462]  [<ffffffff8184b438>] ? x86_64_start_kernel+0xfa/0x109
Oct 15 10:17:48 skippy kernel: [ 6307.963465] ---[ end trace 5050d56cdc0af5c0 ]---
Oct 15 10:17:50 skippy kernel: [ 6309.554318] ------------[ cut here ]------------

If you need anymore information from me just let me know. Thanks!

---

### Post by skippy_ on 2010-10-15
here is my logs.tar file

---

### Post by skippy_ on 2010-10-18
Just happened again. This is pretty much happening every single day. 

Attached is a new logs.tar

---

### Post by skippy_ on 2010-10-18
Failed to mention as well, upon reboot after the KP, I get three long post beeps. Google tells me this is a bad ram warning?

---

### Post by isantop on 2010-10-18
It sounds to me like the beeps are the Kernel Panic Warning beeps. Should be normal (for kernel panics, anyway). It could be a RAM issue, in which the case first step is to try running the machine with one RAM module, then the other. Rseating is a good idea.

As for your issues, it sounds like a bad install, most likely due to download corruption. I'd try redownloading and reinstalling. If you use a LiveCD, be sure to burn it as slow as possible, as this helps prevent errors.

I'd say it's probably a similar situation for the Maverick issues. Maverick is running fine on my Pangolin, so I think there was an issue with the installation. I'd try re-downloading and reinstalling to see if that clears up any issues. You should be good for Maverick.

---

### Post by skippy_ on 2010-10-18
> **isantop said:**
> It sounds to me like the beeps are the Kernel Panic Warning beeps. Should be normal (for kernel panics, anyway). It could be a RAM issue, in which the case first step is to try running the machine with one RAM module, then the other. Rseating is a good idea.

As for your issues, it sounds like a bad install, most likely due to download corruption. I'd try redownloading and reinstalling. If you use a LiveCD, be sure to burn it as slow as possible, as this helps prevent errors.

I'd say it's probably a similar situation for the Maverick issues. Maverick is running fine on my Pangolin, so I think there was an issue with the installation. I'd try re-downloading and reinstalling to see if that clears up any issues. You should be good for Maverick.

Hi there,

Thanks for the response. I thought perhaps RAM as well, but I don't see any evidence of that other than the beeps. I'm convinced it has something to do with the wireless driver. I just compiled / installed the latest driver from realteks website and then tested it by transferring 5 gigs via SCP with no issues :3

I had heard about the download corruption while investigating my issue with maverick, I'll probably try reinstalling from update manager this weekend. 

Thanks for your support!

---

### Post by skippy_ on 2010-10-18
Ok, perhaps it's not resolved just yet.

I just attempted another file transfer via SCP, and my wifi connection dropped and was unable to reconnect.

Here's what was happening in /var/log/messages at the time:

loren@skippy:~$ tail -f /var/log/messages
Oct 18 16:10:33 skippy kernel: [ 9423.014177] ===>tx queue is not empty:6, 3
Oct 18 16:10:33 skippy kernel: [ 9423.115845] ===>tx queue is not empty:6, 3
Oct 18 16:10:33 skippy kernel: [ 9423.421409] ===>tx queue is not empty:6, 3
Oct 18 16:10:33 skippy kernel: [ 9423.626776] ===>tx queue is not empty:6, 3
Oct 18 16:10:33 skippy kernel: [ 9423.728989] ===>tx queue is not empty:6, 3
Oct 18 16:10:34 skippy kernel: [ 9423.829998] ===>tx queue is not empty:6, 3
Oct 18 16:10:34 skippy kernel: [ 9424.034319] ===>tx queue is not empty:6, 3
Oct 18 16:10:34 skippy kernel: [ 9424.136464] ===>tx queue is not empty:6, 3
Oct 18 16:10:34 skippy kernel: [ 9424.238865] ===>tx queue is not empty:6, 3
Oct 18 16:10:34 skippy kernel: [ 9424.340714] ===>tx queue is not empty:6, 3
Oct 18 16:10:34 skippy kernel: [ 9424.444196] ===>tx queue is not empty:6, 3
Oct 18 16:10:34 skippy kernel: [ 9424.648004] ===>tx queue is not empty:6, 3
Oct 18 16:10:35 skippy kernel: [ 9424.852410] ===>tx queue is not empty:6, 3
Oct 18 16:10:35 skippy kernel: [ 9424.953547] ===>tx queue is not empty:6, 3
Oct 18 16:10:35 skippy kernel: [ 9425.158906] ===>tx queue is not empty:6, 3
Oct 18 16:10:35 skippy kernel: [ 9425.260311] ===>tx queue is not empty:6, 3
Oct 18 16:10:35 skippy kernel: [ 9425.362070] ===>tx queue is not empty:6, 3
Oct 18 16:10:35 skippy kernel: [ 9425.465362] ===>tx queue is not empty:6, 3
Oct 18 16:10:35 skippy kernel: [ 9425.668587] ===>tx queue is not empty:6, 3
Oct 18 16:10:36 skippy kernel: [ 9425.874015] ===>tx queue is not empty:6, 3
Oct 18 16:10:36 skippy kernel: [ 9426.078325] ===>tx queue is not empty:6, 3
Oct 18 16:10:36 skippy kernel: [ 9426.179218] ===>tx queue is not empty:6, 3
Oct 18 16:10:36 skippy kernel: [ 9426.281392] ===>tx queue is not empty:6, 3
Oct 18 16:10:36 skippy kernel: [ 9426.383853] ===>tx queue is not empty:6, 3
Oct 18 16:10:36 skippy kernel: [ 9426.487222] ===>tx queue is not empty:6, 3
Oct 18 16:10:36 skippy kernel: [ 9426.599303] ===>tx queue is not empty:6, 3
Oct 18 16:10:36 skippy kernel: [ 9426.690895] ===>tx queue is not empty:6, 3
Oct 18 16:10:37 skippy kernel: [ 9426.996720] ===>tx queue is not empty:6, 3
Oct 18 16:10:37 skippy kernel: [ 9427.099508] ===>tx queue is not empty:6, 3
Oct 18 16:10:37 skippy kernel: [ 9427.302771] ===>tx queue is not empty:6, 3
Oct 18 16:10:37 skippy kernel: [ 9427.405140] ===>tx queue is not empty:6, 3
Oct 18 16:10:37 skippy kernel: [ 9427.508162] ===>tx queue is not empty:6, 3
Oct 18 16:10:37 skippy kernel: [ 9427.711440] ===>tx queue is not empty:6, 3
Oct 18 16:10:38 skippy kernel: [ 9427.813564] ===>tx queue is not empty:6, 3
Oct 18 16:10:38 skippy kernel: [ 9427.917663] ===>tx queue is not empty:6, 3
Oct 18 16:10:38 skippy kernel: [ 9428.018661] ===>tx queue is not empty:6, 3
Oct 18 16:10:38 skippy kernel: [ 9428.222360] ===>tx queue is not empty:6, 3
Oct 18 16:10:38 skippy kernel: [ 9428.325418] ===>tx queue is not empty:6, 3
Oct 18 16:10:38 skippy kernel: [ 9428.427803] ===>tx queue is not empty:6, 3
Oct 18 16:10:38 skippy kernel: [ 9428.529418] ===>tx queue is not empty:6, 3
Oct 18 16:10:38 skippy kernel: [ 9428.623896] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
Oct 18 16:10:39 skippy kernel: [ 9429.621466] ieee->state is RTLLIB_LINKED
Oct 18 16:10:39 skippy kernel: [ 9429.759814] Associated successfully
Oct 18 16:10:39 skippy kernel: [ 9429.759818] Using G rates:108
Oct 18 16:10:39 skippy kernel: [ 9429.759819] Successfully associated, ht not enabled(0, 0)
Oct 18 16:10:39 skippy kernel: [ 9429.759821] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:10:39 skippy kernel: [ 9429.760829] silent reset associate
Oct 18 16:10:57 skippy kernel: [ 9447.526908] ===>tx queue is not empty:6, 1
Oct 18 16:10:58 skippy kernel: [ 9447.732464] ===>tx queue is not empty:6, 1
Oct 18 16:10:58 skippy kernel: [ 9447.936660] ===>tx queue is not empty:6, 1
Oct 18 16:10:58 skippy kernel: [ 9448.140043] ===>tx queue is not empty:6, 1
Oct 18 16:10:58 skippy kernel: [ 9448.241919] ===>tx queue is not empty:6, 1
Oct 18 16:10:58 skippy kernel: [ 9448.345460] ===>tx queue is not empty:6, 1
Oct 18 16:10:58 skippy kernel: [ 9448.446219] ===>tx queue is not empty:6, 1
Oct 18 16:10:58 skippy kernel: [ 9448.548298] ===>tx queue is not empty:6, 1
Oct 18 16:10:59 skippy kernel: [ 9448.752577] ===>tx queue is not empty:6, 1
Oct 18 16:10:59 skippy kernel: [ 9448.854800] ===>tx queue is not empty:6, 1
Oct 18 16:10:59 skippy kernel: [ 9448.956879] ===>tx queue is not empty:6, 1
Oct 18 16:10:59 skippy kernel: [ 9449.059036] ===>tx queue is not empty:6, 1
Oct 18 16:10:59 skippy kernel: [ 9449.162082] ===>tx queue is not empty:6, 1
Oct 18 16:10:59 skippy kernel: [ 9449.366444] ===>tx queue is not empty:6, 1
Oct 18 16:10:59 skippy kernel: [ 9449.468888] ===>tx queue is not empty:6, 1
Oct 18 16:10:59 skippy kernel: [ 9449.571359] ===>tx queue is not empty:6, 1
Oct 18 16:11:00 skippy kernel: [ 9449.877301] ===>tx queue is not empty:6, 1
Oct 18 16:11:00 skippy kernel: [ 9449.980849] ===>tx queue is not empty:6, 1
Oct 18 16:11:00 skippy kernel: [ 9450.081786] ===>tx queue is not empty:6, 1
Oct 18 16:11:00 skippy kernel: [ 9450.182689] ===>tx queue is not empty:6, 1
Oct 18 16:11:00 skippy kernel: [ 9450.284970] ===>tx queue is not empty:6, 1
Oct 18 16:11:00 skippy kernel: [ 9450.388266] ===>tx queue is not empty:6, 1
Oct 18 16:11:00 skippy kernel: [ 9450.489043] ===>tx queue is not empty:6, 1
Oct 18 16:11:01 skippy kernel: [ 9450.999750] ===>tx queue is not empty:6, 1
Oct 18 16:11:01 skippy kernel: [ 9451.204054] ===>tx queue is not empty:6, 1
Oct 18 16:11:01 skippy kernel: [ 9451.306194] ===>tx queue is not empty:6, 1
Oct 18 16:11:01 skippy kernel: [ 9451.510490] ===>tx queue is not empty:6, 1
Oct 18 16:11:01 skippy kernel: [ 9451.613823] ===>tx queue is not empty:6, 1
Oct 18 16:11:02 skippy kernel: [ 9451.817056] ===>tx queue is not empty:6, 1
Oct 18 16:11:02 skippy kernel: [ 9452.022088] ===>tx queue is not empty:6, 1
Oct 18 16:11:03 skippy kernel: [ 9452.838309] ===>tx queue is not empty:6, 1
Oct 18 16:11:03 skippy kernel: [ 9452.941245] ===>tx queue is not empty:6, 1
Oct 18 16:11:03 skippy kernel: [ 9453.145755] ===>tx queue is not empty:6, 1
Oct 18 16:11:03 skippy kernel: [ 9453.247249] ===>tx queue is not empty:6, 1
Oct 18 16:11:03 skippy kernel: [ 9453.451143] ===>tx queue is not empty:6, 1
Oct 18 16:11:03 skippy kernel: [ 9453.553303] ===>tx queue is not empty:6, 1
Oct 18 16:11:04 skippy kernel: [ 9453.758580] ===>tx queue is not empty:6, 1
Oct 18 16:11:04 skippy kernel: [ 9453.963130] ===>tx queue is not empty:6, 1
Oct 18 16:11:04 skippy kernel: [ 9454.063996] ===>tx queue is not empty:6, 1
Oct 18 16:11:04 skippy kernel: [ 9454.167694] ===>tx queue is not empty:6, 1
Oct 18 16:11:04 skippy kernel: [ 9454.269796] ===>tx queue is not empty:6, 1
Oct 18 16:11:04 skippy kernel: [ 9454.371849] ===>tx queue is not empty:6, 1
Oct 18 16:11:04 skippy kernel: [ 9454.474174] ===>tx queue is not empty:6, 1
Oct 18 16:11:04 skippy kernel: [ 9454.574982] ===>tx queue is not empty:6, 1
Oct 18 16:11:05 skippy kernel: [ 9454.881175] ===>tx queue is not empty:6, 1
Oct 18 16:11:05 skippy kernel: [ 9454.983939] ===>tx queue is not empty:6, 1
Oct 18 16:11:05 skippy kernel: [ 9455.188577] ===>tx queue is not empty:6, 1
Oct 18 16:11:05 skippy kernel: [ 9455.292561] ===>tx queue is not empty:6, 1
Oct 18 16:11:05 skippy kernel: [ 9455.494014] ===>tx queue is not empty:6, 1
Oct 18 16:11:05 skippy kernel: [ 9455.596922] ===>tx queue is not empty:6, 1
Oct 18 16:11:05 skippy kernel: [ 9455.698281] ===>tx queue is not empty:6, 1
Oct 18 16:11:06 skippy kernel: [ 9455.802067] ===>tx queue is not empty:6, 1
Oct 18 16:11:06 skippy kernel: [ 9455.902578] ===>tx queue is not empty:6, 1
Oct 18 16:11:06 skippy kernel: [ 9456.005585] ===>tx queue is not empty:6, 1
Oct 18 16:11:06 skippy kernel: [ 9456.108357] ===>tx queue is not empty:6, 1
Oct 18 16:11:06 skippy kernel: [ 9456.210207] ===>tx queue is not empty:6, 1
Oct 18 16:11:06 skippy kernel: [ 9456.415214] ===>tx queue is not empty:6, 1
Oct 18 16:11:06 skippy kernel: [ 9456.516675] ===>tx queue is not empty:6, 1
Oct 18 16:11:07 skippy kernel: [ 9456.822750] ===>tx queue is not empty:6, 1
Oct 18 16:11:07 skippy kernel: [ 9456.924799] ===>tx queue is not empty:6, 1
Oct 18 16:11:07 skippy kernel: [ 9457.027124] ===>tx queue is not empty:6, 1
Oct 18 16:11:07 skippy kernel: [ 9457.129201] ===>tx queue is not empty:6, 1
Oct 18 16:11:07 skippy kernel: [ 9457.332535] ===>tx queue is not empty:6, 1
Oct 18 16:11:07 skippy kernel: [ 9457.435715] ===>tx queue is not empty:6, 1
Oct 18 16:11:07 skippy kernel: [ 9457.536852] ===>tx queue is not empty:6, 1
Oct 18 16:11:08 skippy kernel: [ 9457.741119] ===>tx queue is not empty:6, 1
Oct 18 16:11:08 skippy kernel: [ 9457.844909] ===>tx queue is not empty:6, 1
Oct 18 16:11:08 skippy kernel: [ 9458.048516] ===>tx queue is not empty:6, 1
Oct 18 16:11:08 skippy kernel: [ 9458.149676] ===>tx queue is not empty:6, 1
Oct 18 16:11:08 skippy kernel: [ 9458.354621] ===>tx queue is not empty:6, 1
Oct 18 16:11:08 skippy kernel: [ 9458.456141] ===>tx queue is not empty:6, 1
Oct 18 16:11:08 skippy kernel: [ 9458.559524] ===>tx queue is not empty:6, 1
Oct 18 16:11:09 skippy kernel: [ 9458.764136] ===>tx queue is not empty:6, 1
Oct 18 16:11:09 skippy kernel: [ 9458.966828] ===>tx queue is not empty:6, 1
Oct 18 16:11:09 skippy kernel: [ 9459.478431] ===>tx queue is not empty:6, 1
Oct 18 16:11:09 skippy kernel: [ 9459.682589] ===>tx queue is not empty:6, 1
Oct 18 16:11:10 skippy kernel: [ 9459.784779] ===>tx queue is not empty:6, 1
Oct 18 16:11:10 skippy kernel: [ 9459.886960] ===>tx queue is not empty:6, 1
Oct 18 16:11:10 skippy kernel: [ 9459.989411] ===>tx queue is not empty:6, 1
Oct 18 16:11:10 skippy kernel: [ 9460.091532] ===>tx queue is not empty:6, 1
Oct 18 16:11:10 skippy kernel: [ 9460.193929] ===>tx queue is not empty:6, 1
Oct 18 16:11:10 skippy kernel: [ 9460.398105] ===>tx queue is not empty:6, 1
Oct 18 16:11:10 skippy kernel: [ 9460.499919] ===>tx queue is not empty:6, 1
Oct 18 16:11:10 skippy kernel: [ 9460.602169] ===>tx queue is not empty:6, 1
Oct 18 16:11:11 skippy kernel: [ 9460.703250] ===>tx queue is not empty:6, 1
Oct 18 16:11:11 skippy kernel: [ 9460.805491] ===>tx queue is not empty:6, 1
Oct 18 16:11:11 skippy kernel: [ 9460.907505] ===>tx queue is not empty:6, 1
Oct 18 16:11:11 skippy kernel: [ 9461.013347] ===>tx queue is not empty:6, 1
Oct 18 16:11:11 skippy kernel: [ 9461.111792] ===>tx queue is not empty:6, 1
Oct 18 16:11:11 skippy kernel: [ 9461.316857] ===>tx queue is not empty:6, 1
Oct 18 16:11:11 skippy kernel: [ 9461.521210] ===>tx queue is not empty:6, 1
Oct 18 16:11:11 skippy kernel: [ 9461.623488] ===>tx queue is not empty:6, 1
Oct 18 16:11:12 skippy kernel: [ 9461.724672] ===>tx queue is not empty:6, 1
Oct 18 16:11:12 skippy kernel: [ 9461.828032] ===>tx queue is not empty:6, 1
Oct 18 16:11:12 skippy kernel: [ 9461.928957] ===>tx queue is not empty:6, 1
Oct 18 16:11:12 skippy kernel: [ 9462.031306] ===>tx queue is not empty:6, 1
Oct 18 16:11:12 skippy kernel: [ 9462.134019] ===>tx queue is not empty:6, 1
Oct 18 16:11:12 skippy kernel: [ 9462.439599] ===>tx queue is not empty:6, 1
Oct 18 16:11:12 skippy kernel: [ 9462.543110] ===>tx queue is not empty:6, 1
Oct 18 16:11:12 skippy kernel: [ 9462.645630] ===>tx queue is not empty:6, 1
Oct 18 16:11:13 skippy kernel: [ 9462.849736] ===>tx queue is not empty:6, 1
Oct 18 16:11:13 skippy kernel: [ 9462.950370] ===>tx queue is not empty:6, 1
Oct 18 16:11:13 skippy kernel: [ 9463.052493] ===>tx queue is not empty:6, 1
Oct 18 16:11:13 skippy kernel: [ 9463.155204] ===>tx queue is not empty:6, 1
Oct 18 16:11:13 skippy kernel: [ 9463.258144] ===>tx queue is not empty:6, 1
Oct 18 16:11:13 skippy kernel: [ 9463.360854] ===>tx queue is not empty:6, 1
Oct 18 16:11:13 skippy kernel: [ 9463.461083] ===>tx queue is not empty:6, 1
Oct 18 16:11:13 skippy kernel: [ 9463.563213] ===>tx queue is not empty:6, 1
Oct 18 16:11:13 skippy kernel: [ 9463.659121] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
Oct 18 16:11:14 skippy kernel: [ 9464.656841] ieee->state is RTLLIB_LINKED
Oct 18 16:11:15 skippy kernel: [ 9464.795311] Associated successfully
Oct 18 16:11:15 skippy kernel: [ 9464.795315] Using G rates:108
Oct 18 16:11:15 skippy kernel: [ 9464.795316] Successfully associated, ht not enabled(0, 0)
Oct 18 16:11:15 skippy kernel: [ 9464.795318] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:11:15 skippy kernel: [ 9464.796327] silent reset associate
Oct 18 16:11:39 skippy kernel: [ 9488.895301] ===>tx queue is not empty:6, 1
Oct 18 16:11:39 skippy kernel: [ 9488.996585] ===>tx queue is not empty:6, 1
Oct 18 16:11:39 skippy kernel: [ 9489.099419] ===>tx queue is not empty:6, 1
Oct 18 16:11:39 skippy kernel: [ 9489.201513] ===>tx queue is not empty:6, 1
Oct 18 16:11:39 skippy kernel: [ 9489.303864] ===>tx queue is not empty:6, 1
Oct 18 16:11:39 skippy kernel: [ 9489.405919] ===>tx queue is not empty:6, 1
Oct 18 16:11:39 skippy kernel: [ 9489.507300] ===>tx queue is not empty:6, 1
Oct 18 16:11:39 skippy kernel: [ 9489.610317] ===>tx queue is not empty:6, 1
Oct 18 16:11:40 skippy kernel: [ 9489.712526] ===>tx queue is not empty:6, 1
Oct 18 16:11:40 skippy kernel: [ 9489.915827] ===>tx queue is not empty:6, 1
Oct 18 16:11:40 skippy kernel: [ 9490.018751] ===>tx queue is not empty:6, 1
Oct 18 16:11:40 skippy kernel: [ 9490.120732] ===>tx queue is not empty:6, 1
Oct 18 16:11:40 skippy kernel: [ 9490.223909] ===>tx queue is not empty:6, 1
Oct 18 16:11:40 skippy kernel: [ 9490.325106] ===>tx queue is not empty:6, 1
Oct 18 16:11:40 skippy kernel: [ 9490.427197] ===>tx queue is not empty:6, 1
Oct 18 16:11:40 skippy kernel: [ 9490.529296] ===>tx queue is not empty:6, 1
Oct 18 16:11:41 skippy kernel: [ 9490.632700] ===>tx queue is not empty:6, 1
Oct 18 16:11:41 skippy kernel: [ 9491.142629] ===>tx queue is not empty:6, 1
Oct 18 16:11:41 skippy kernel: [ 9491.244867] ===>tx queue is not empty:6, 1
Oct 18 16:11:41 skippy kernel: [ 9491.347058] ===>tx queue is not empty:6, 1
Oct 18 16:11:41 skippy kernel: [ 9491.449200] ===>tx queue is not empty:6, 1
Oct 18 16:11:41 skippy kernel: [ 9491.551238] ===>tx queue is not empty:6, 1
Oct 18 16:11:42 skippy kernel: [ 9491.652988] ===>tx queue is not empty:6, 1
Oct 18 16:11:42 skippy kernel: [ 9491.958720] ===>tx queue is not empty:6, 1
Oct 18 16:11:42 skippy kernel: [ 9492.060815] ===>tx queue is not empty:6, 1
Oct 18 16:11:42 skippy kernel: [ 9492.163743] ===>tx queue is not empty:6, 1
Oct 18 16:11:42 skippy kernel: [ 9492.265913] ===>tx queue is not empty:6, 1
Oct 18 16:11:42 skippy kernel: [ 9492.469400] ===>tx queue is not empty:6, 1
Oct 18 16:11:43 skippy kernel: [ 9492.776966] ===>tx queue is not empty:6, 1
Oct 18 16:11:43 skippy kernel: [ 9493.082871] ===>tx queue is not empty:6, 1
Oct 18 16:11:43 skippy kernel: [ 9493.184376] ===>tx queue is not empty:6, 1
Oct 18 16:11:43 skippy kernel: [ 9493.288310] ===>tx queue is not empty:6, 1
Oct 18 16:11:43 skippy kernel: [ 9493.490809] ===>tx queue is not empty:6, 1
Oct 18 16:11:43 skippy kernel: [ 9493.593418] ===>tx queue is not empty:6, 1
Oct 18 16:11:44 skippy kernel: [ 9493.696231] ===>tx queue is not empty:6, 1
Oct 18 16:11:44 skippy kernel: [ 9493.798503] ===>tx queue is not empty:6, 1
Oct 18 16:11:44 skippy kernel: [ 9493.900818] ===>tx queue is not empty:6, 1
Oct 18 16:11:44 skippy kernel: [ 9494.206028] ===>tx queue is not empty:6, 1
Oct 18 16:11:44 skippy kernel: [ 9494.411101] ===>tx queue is not empty:6, 1
Oct 18 16:11:45 skippy kernel: [ 9494.615333] ===>tx queue is not empty:6, 1
Oct 18 16:11:45 skippy kernel: [ 9494.819792] ===>tx queue is not empty:6, 1
Oct 18 16:11:45 skippy kernel: [ 9495.125152] ===>tx queue is not empty:6, 1
Oct 18 16:11:45 skippy kernel: [ 9495.227823] ===>tx queue is not empty:6, 1
Oct 18 16:11:45 skippy kernel: [ 9495.331014] ===>tx queue is not empty:6, 1
Oct 18 16:11:45 skippy kernel: [ 9495.433320] ===>tx queue is not empty:6, 1
Oct 18 16:11:45 skippy kernel: [ 9495.534560] ===>tx queue is not empty:6, 1
Oct 18 16:11:46 skippy kernel: [ 9495.635993] ===>tx queue is not empty:6, 1
Oct 18 16:11:46 skippy kernel: [ 9495.739376] ===>tx queue is not empty:6, 1
Oct 18 16:11:46 skippy kernel: [ 9495.840060] ===>tx queue is not empty:6, 1
Oct 18 16:11:46 skippy kernel: [ 9495.943234] ===>tx queue is not empty:6, 1
Oct 18 16:11:46 skippy kernel: [ 9496.147199] ===>tx queue is not empty:6, 1
Oct 18 16:11:46 skippy kernel: [ 9496.249723] ===>tx queue is not empty:6, 1
Oct 18 16:11:46 skippy kernel: [ 9496.351541] ===>tx queue is not empty:6, 1
Oct 18 16:11:46 skippy kernel: [ 9496.452931] ===>tx queue is not empty:6, 1
Oct 18 16:11:46 skippy kernel: [ 9496.556302] ===>tx queue is not empty:6, 1
Oct 18 16:11:47 skippy kernel: [ 9496.659209] ===>tx queue is not empty:6, 1
Oct 18 16:11:47 skippy kernel: [ 9496.862183] ===>tx queue is not empty:6, 1
Oct 18 16:11:47 skippy kernel: [ 9497.271295] ===>tx queue is not empty:6, 1
Oct 18 16:11:47 skippy kernel: [ 9497.373273] ===>tx queue is not empty:6, 1
Oct 18 16:11:47 skippy kernel: [ 9497.475924] ===>tx queue is not empty:6, 1
Oct 18 16:11:47 skippy kernel: [ 9497.577380] ===>tx queue is not empty:6, 1
Oct 18 16:11:48 skippy kernel: [ 9497.678792] ===>tx queue is not empty:6, 1
Oct 18 16:11:48 skippy kernel: [ 9497.781761] ===>tx queue is not empty:6, 1
Oct 18 16:11:48 skippy kernel: [ 9497.882989] ===>tx queue is not empty:6, 1
Oct 18 16:11:48 skippy kernel: [ 9497.986243] ===>tx queue is not empty:6, 1
Oct 18 16:11:48 skippy kernel: [ 9498.190610] ===>tx queue is not empty:6, 1
Oct 18 16:11:48 skippy kernel: [ 9498.291846] ===>tx queue is not empty:6, 1
Oct 18 16:11:48 skippy kernel: [ 9498.394331] ===>tx queue is not empty:6, 1
Oct 18 16:11:48 skippy kernel: [ 9498.496881] ===>tx queue is not empty:6, 1
Oct 18 16:11:49 skippy kernel: [ 9498.598488] ===>tx queue is not empty:6, 1
Oct 18 16:11:49 skippy kernel: [ 9498.802203] ===>tx queue is not empty:6, 1
Oct 18 16:11:49 skippy kernel: [ 9498.905567] ===>tx queue is not empty:6, 1
Oct 18 16:11:49 skippy kernel: [ 9499.008083] ===>tx queue is not empty:6, 1
Oct 18 16:11:49 skippy kernel: [ 9499.109806] ===>tx queue is not empty:6, 1
Oct 18 16:11:49 skippy kernel: [ 9499.314204] ===>tx queue is not empty:6, 1
Oct 18 16:11:49 skippy kernel: [ 9499.415893] ===>tx queue is not empty:6, 1
Oct 18 16:11:49 skippy kernel: [ 9499.518010] ===>tx queue is not empty:6, 1
Oct 18 16:11:50 skippy kernel: [ 9499.620403] ===>tx queue is not empty:6, 1
Oct 18 16:11:50 skippy kernel: [ 9499.722312] ===>tx queue is not empty:6, 1
Oct 18 16:11:50 skippy kernel: [ 9499.824224] ===>tx queue is not empty:6, 1
Oct 18 16:11:50 skippy kernel: [ 9499.925758] ===>tx queue is not empty:6, 1
Oct 18 16:11:50 skippy kernel: [ 9500.027890] ===>tx queue is not empty:6, 1
Oct 18 16:11:50 skippy kernel: [ 9500.130607] ===>tx queue is not empty:6, 1
Oct 18 16:11:50 skippy kernel: [ 9500.233083] ===>tx queue is not empty:6, 1
Oct 18 16:11:50 skippy kernel: [ 9500.335152] ===>tx queue is not empty:6, 1
Oct 18 16:11:50 skippy kernel: [ 9500.437294] ===>tx queue is not empty:6, 1
Oct 18 16:11:50 skippy kernel: [ 9500.539259] ===>tx queue is not empty:6, 1
Oct 18 16:11:51 skippy kernel: [ 9500.641787] ===>tx queue is not empty:6, 1
Oct 18 16:11:51 skippy kernel: [ 9500.947162] ===>tx queue is not empty:6, 1
Oct 18 16:11:51 skippy kernel: [ 9501.050255] ===>tx queue is not empty:6, 1
Oct 18 16:11:51 skippy kernel: [ 9501.152522] ===>tx queue is not empty:6, 1
Oct 18 16:11:51 skippy kernel: [ 9501.254751] ===>tx queue is not empty:6, 1
Oct 18 16:11:51 skippy kernel: [ 9501.356417] ===>tx queue is not empty:6, 1
Oct 18 16:11:51 skippy kernel: [ 9501.457876] ===>tx queue is not empty:6, 1
Oct 18 16:11:51 skippy kernel: [ 9501.560856] ===>tx queue is not empty:6, 1
Oct 18 16:11:52 skippy kernel: [ 9501.662184] ===>tx queue is not empty:6, 1
Oct 18 16:11:52 skippy kernel: [ 9501.765847] ===>tx queue is not empty:6, 1
Oct 18 16:11:52 skippy kernel: [ 9501.867157] ===>tx queue is not empty:6, 1
Oct 18 16:11:52 skippy kernel: [ 9501.969717] ===>tx queue is not empty:6, 1
Oct 18 16:11:52 skippy kernel: [ 9502.071967] ===>tx queue is not empty:6, 1
Oct 18 16:11:52 skippy kernel: [ 9502.173954] ===>tx queue is not empty:6, 1
Oct 18 16:11:52 skippy kernel: [ 9502.276478] ===>tx queue is not empty:6, 1
Oct 18 16:11:52 skippy kernel: [ 9502.378908] ===>tx queue is not empty:6, 1
Oct 18 16:11:52 skippy kernel: [ 9502.480170] ===>tx queue is not empty:6, 1
Oct 18 16:11:53 skippy kernel: [ 9502.683587] ===>tx queue is not empty:6, 1
Oct 18 16:11:53 skippy kernel: [ 9502.786626] ===>tx queue is not empty:6, 1
Oct 18 16:11:53 skippy kernel: [ 9502.888895] ===>tx queue is not empty:6, 1
Oct 18 16:11:53 skippy kernel: [ 9503.092149] ===>tx queue is not empty:6, 1
Oct 18 16:11:53 skippy kernel: [ 9503.194280] ===>tx queue is not empty:6, 1
Oct 18 16:11:53 skippy kernel: [ 9503.399603] ===>tx queue is not empty:6, 1
Oct 18 16:11:53 skippy kernel: [ 9503.501809] ===>tx queue is not empty:6, 1
Oct 18 16:11:54 skippy kernel: [ 9503.602874] ===>tx queue is not empty:6, 1
Oct 18 16:11:54 skippy kernel: [ 9503.705818] ===>tx queue is not empty:6, 1
Oct 18 16:11:54 skippy kernel: [ 9503.807912] ===>tx queue is not empty:6, 1
Oct 18 16:11:54 skippy kernel: [ 9503.909990] ===>tx queue is not empty:6, 1
Oct 18 16:11:54 skippy kernel: [ 9504.114710] ===>tx queue is not empty:6, 1
Oct 18 16:11:54 skippy kernel: [ 9504.216741] ===>tx queue is not empty:6, 1
Oct 18 16:11:54 skippy kernel: [ 9504.523516] ===>tx queue is not empty:6, 1
Oct 18 16:11:55 skippy kernel: [ 9504.625592] ===>tx queue is not empty:6, 1
Oct 18 16:11:55 skippy kernel: [ 9504.681674] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
Oct 18 16:11:56 skippy kernel: [ 9505.679444] ieee->state is RTLLIB_LINKED
Oct 18 16:11:56 skippy kernel: [ 9505.817880] Associated successfully
Oct 18 16:11:56 skippy kernel: [ 9505.817884] Using G rates:108
Oct 18 16:11:56 skippy kernel: [ 9505.817885] Successfully associated, ht not enabled(0, 0)
Oct 18 16:11:56 skippy kernel: [ 9505.817887] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:11:56 skippy kernel: [ 9505.818896] silent reset associate
Oct 18 16:12:14 skippy kernel: [ 9524.133344] ===>tx queue is not empty:6, 1
Oct 18 16:12:14 skippy kernel: [ 9524.236602] ===>tx queue is not empty:6, 1
Oct 18 16:12:14 skippy kernel: [ 9524.338658] ===>tx queue is not empty:6, 1
Oct 18 16:12:14 skippy kernel: [ 9524.439897] ===>tx queue is not empty:6, 1
Oct 18 16:12:15 skippy kernel: [ 9524.541959] ===>tx queue is not empty:6, 1
Oct 18 16:12:15 skippy kernel: [ 9524.747148] ===>tx queue is not empty:6, 1
Oct 18 16:12:15 skippy kernel: [ 9524.849056] ===>tx queue is not empty:6, 1
Oct 18 16:12:15 skippy kernel: [ 9525.053287] ===>tx queue is not empty:6, 1
Oct 18 16:12:15 skippy kernel: [ 9525.257568] ===>tx queue is not empty:6, 1
Oct 18 16:12:15 skippy kernel: [ 9525.359049] ===>tx queue is not empty:6, 1
Oct 18 16:12:15 skippy kernel: [ 9525.462404] ===>tx queue is not empty:6, 1
Oct 18 16:12:16 skippy kernel: [ 9525.564375] ===>tx queue is not empty:6, 1
Oct 18 16:12:16 skippy kernel: [ 9525.666583] ===>tx queue is not empty:6, 1
Oct 18 16:12:16 skippy kernel: [ 9525.768416] ===>tx queue is not empty:6, 1
Oct 18 16:12:16 skippy kernel: [ 9525.973132] ===>tx queue is not empty:6, 1
Oct 18 16:12:16 skippy kernel: [ 9526.074788] ===>tx queue is not empty:6, 1
Oct 18 16:12:16 skippy kernel: [ 9526.180259] ===>tx queue is not empty:6, 1
Oct 18 16:12:16 skippy kernel: [ 9526.483822] ===>tx queue is not empty:6, 1
Oct 18 16:12:17 skippy kernel: [ 9526.584804] ===>tx queue is not empty:6, 1
Oct 18 16:12:17 skippy kernel: [ 9526.789912] ===>tx queue is not empty:6, 1
Oct 18 16:12:17 skippy kernel: [ 9527.096161] ===>tx queue is not empty:6, 1
Oct 18 16:12:17 skippy kernel: [ 9527.300582] ===>tx queue is not empty:6, 1
Oct 18 16:12:17 skippy kernel: [ 9527.402757] ===>tx queue is not empty:6, 1
Oct 18 16:12:17 skippy kernel: [ 9527.504182] ===>tx queue is not empty:6, 1
Oct 18 16:12:18 skippy kernel: [ 9527.606208] ===>tx queue is not empty:6, 1
Oct 18 16:12:18 skippy kernel: [ 9527.709115] ===>tx queue is not empty:6, 1
Oct 18 16:12:18 skippy kernel: [ 9527.811510] ===>tx queue is not empty:6, 1
Oct 18 16:12:18 skippy kernel: [ 9528.016024] ===>tx queue is not empty:6, 1
Oct 18 16:12:18 skippy kernel: [ 9528.220291] ===>tx queue is not empty:6, 1
Oct 18 16:12:18 skippy kernel: [ 9528.322143] ===>tx queue is not empty:6, 1
Oct 18 16:12:18 skippy kernel: [ 9528.425653] ===>tx queue is not empty:6, 1
Oct 18 16:12:19 skippy kernel: [ 9528.525715] ===>tx queue is not empty:6, 1
Oct 18 16:12:19 skippy kernel: [ 9528.629086] ===>tx queue is not empty:6, 1
Oct 18 16:12:19 skippy kernel: [ 9528.832665] ===>tx queue is not empty:6, 1
Oct 18 16:12:19 skippy kernel: [ 9528.934045] ===>tx queue is not empty:6, 1
Oct 18 16:12:19 skippy kernel: [ 9529.139158] ===>tx queue is not empty:6, 1
Oct 18 16:12:19 skippy kernel: [ 9529.241619] ===>tx queue is not empty:6, 1
Oct 18 16:12:19 skippy kernel: [ 9529.343629] ===>tx queue is not empty:6, 1
Oct 18 16:12:19 skippy kernel: [ 9529.445422] ===>tx queue is not empty:6, 1
Oct 18 16:12:20 skippy kernel: [ 9529.533169] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:12:20 skippy kernel: [ 9529.533185] ===>tx queue is not empty:6, 3
Oct 18 16:12:20 skippy kernel: [ 9529.600506] ===>tx queue is not empty:6, 5
Oct 18 16:12:20 skippy kernel: [ 9529.720148] ===>tx queue is not empty:6, 7
Oct 18 16:12:20 skippy kernel: [ 9529.839887] ===>tx queue is not empty:6, 9
Oct 18 16:12:20 skippy kernel: [ 9529.959620] ===>tx queue is not empty:6, 11
Oct 18 16:12:20 skippy kernel: [ 9530.079296] ===>tx queue is not empty:6, 13
Oct 18 16:12:20 skippy kernel: [ 9530.199077] ===>tx queue is not empty:6, 15
Oct 18 16:12:20 skippy kernel: [ 9530.318742] ===>tx queue is not empty:6, 17
Oct 18 16:12:20 skippy kernel: [ 9530.438468] ===>tx queue is not empty:6, 19
Oct 18 16:12:21 skippy kernel: [ 9530.558168] ===>tx queue is not empty:6, 21
Oct 18 16:12:21 skippy kernel: [ 9530.677817] ===>tx queue is not empty:6, 23
Oct 18 16:12:21 skippy kernel: [ 9530.797580] ===>tx queue is not empty:6, 25
Oct 18 16:12:21 skippy kernel: [ 9531.156682] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:12:21 skippy kernel: [ 9531.157726] ===>tx queue is not empty:6, 26
Oct 18 16:12:22 skippy kernel: [ 9531.896862] ===>tx queue is not empty:6, 26
Oct 18 16:12:22 skippy kernel: [ 9531.999200] ===>tx queue is not empty:6, 26
Oct 18 16:12:22 skippy kernel: [ 9532.203889] ===>tx queue is not empty:6, 26
Oct 18 16:12:22 skippy kernel: [ 9532.305347] ===>tx queue is not empty:6, 26
Oct 18 16:12:22 skippy kernel: [ 9532.407864] ===>tx queue is not empty:6, 26
Oct 18 16:12:23 skippy kernel: [ 9532.816933] ===>tx queue is not empty:6, 26
Oct 18 16:12:23 skippy kernel: [ 9533.224001] ===>tx queue is not empty:6, 26
Oct 18 16:12:24 skippy kernel: [ 9533.735878] ===>tx queue is not empty:6, 26
Oct 18 16:12:24 skippy kernel: [ 9533.837144] ===>tx queue is not empty:6, 26
Oct 18 16:12:24 skippy kernel: [ 9534.144444] ===>tx queue is not empty:6, 26
Oct 18 16:12:24 skippy kernel: [ 9534.246705] ===>tx queue is not empty:6, 26
Oct 18 16:12:24 skippy kernel: [ 9534.348453] ===>tx queue is not empty:6, 26
Oct 18 16:12:25 skippy kernel: [ 9534.756153] ===>tx queue is not empty:6, 26
Oct 18 16:12:25 skippy kernel: [ 9534.858306] ===>tx queue is not empty:6, 26
Oct 18 16:12:25 skippy kernel: [ 9534.961274] ===>tx queue is not empty:6, 26
Oct 18 16:12:25 skippy kernel: [ 9535.164742] ===>tx queue is not empty:6, 26
Oct 18 16:12:25 skippy kernel: [ 9535.266862] ===>tx queue is not empty:6, 26
Oct 18 16:12:25 skippy kernel: [ 9535.369004] ===>tx queue is not empty:6, 26
Oct 18 16:12:25 skippy kernel: [ 9535.471136] ===>tx queue is not empty:6, 26
Oct 18 16:12:26 skippy kernel: [ 9535.676498] ===>tx queue is not empty:6, 26
Oct 18 16:12:26 skippy kernel: [ 9535.778333] ===>tx queue is not empty:6, 26
Oct 18 16:12:26 skippy kernel: [ 9535.880611] ===>tx queue is not empty:6, 26
Oct 18 16:12:26 skippy kernel: [ 9535.981980] ===>tx queue is not empty:6, 26
Oct 18 16:12:26 skippy kernel: [ 9536.187120] ===>tx queue is not empty:6, 26
Oct 18 16:12:26 skippy kernel: [ 9536.289434] ===>tx queue is not empty:6, 26
Oct 18 16:12:26 skippy kernel: [ 9536.391090] ===>tx queue is not empty:6, 26
Oct 18 16:12:27 skippy kernel: [ 9536.697865] ===>tx queue is not empty:6, 26
Oct 18 16:12:27 skippy kernel: [ 9536.799154] ===>tx queue is not empty:6, 26
Oct 18 16:12:27 skippy kernel: [ 9536.901983] ===>tx queue is not empty:6, 26
Oct 18 16:12:27 skippy kernel: [ 9537.003911] ===>tx queue is not empty:6, 26
Oct 18 16:12:27 skippy kernel: [ 9537.208655] ===>tx queue is not empty:6, 26
Oct 18 16:12:27 skippy kernel: [ 9537.310786] ===>tx queue is not empty:6, 26
Oct 18 16:12:27 skippy kernel: [ 9537.412674] ===>tx queue is not empty:6, 26
Oct 18 16:12:28 skippy kernel: [ 9537.616831] ===>tx queue is not empty:6, 26
Oct 18 16:12:28 skippy kernel: [ 9537.821572] ===>tx queue is not empty:6, 26
Oct 18 16:12:28 skippy kernel: [ 9537.923263] ===>tx queue is not empty:6, 26
Oct 18 16:12:28 skippy kernel: [ 9538.229941] ===>tx queue is not empty:6, 26
Oct 18 16:12:28 skippy kernel: [ 9538.331119] ===>tx queue is not empty:6, 26
Oct 18 16:12:28 skippy kernel: [ 9538.433262] ===>tx queue is not empty:6, 26
Oct 18 16:12:29 skippy kernel: [ 9538.638586] ===>tx queue is not empty:6, 26
Oct 18 16:12:29 skippy kernel: [ 9538.739689] ===>tx queue is not empty:6, 26
Oct 18 16:12:29 skippy kernel: [ 9538.843229] ===>tx queue is not empty:6, 26
Oct 18 16:12:29 skippy kernel: [ 9539.046799] ===>tx queue is not empty:6, 26
Oct 18 16:12:29 skippy kernel: [ 9539.251053] ===>tx queue is not empty:6, 26
Oct 18 16:12:29 skippy kernel: [ 9539.353781] ===>tx queue is not empty:6, 26
Oct 18 16:12:29 skippy kernel: [ 9539.455543] ===>tx queue is not empty:6, 26
Oct 18 16:12:30 skippy kernel: [ 9539.556840] ===>tx queue is not empty:6, 26
Oct 18 16:12:30 skippy kernel: [ 9539.658970] ===>tx queue is not empty:6, 26
Oct 18 16:12:30 skippy kernel: [ 9539.761112] ===>tx queue is not empty:6, 26
Oct 18 16:12:30 skippy kernel: [ 9539.864133] ===>tx queue is not empty:6, 26
Oct 18 16:12:30 skippy kernel: [ 9539.966171] ===>tx queue is not empty:6, 26
Oct 18 16:12:30 skippy kernel: [ 9540.067584] ===>tx queue is not empty:6, 26
Oct 18 16:12:30 skippy kernel: [ 9540.271818] ===>tx queue is not empty:6, 26
Oct 18 16:12:30 skippy kernel: [ 9540.374720] ===>tx queue is not empty:6, 26
Oct 18 16:12:30 skippy kernel: [ 9540.477669] ===>tx queue is not empty:6, 26
Oct 18 16:12:31 skippy kernel: [ 9540.681486] ===>tx queue is not empty:6, 26
Oct 18 16:12:31 skippy kernel: [ 9540.783391] ===>tx queue is not empty:6, 26
Oct 18 16:12:31 skippy kernel: [ 9540.885407] ===>tx queue is not empty:6, 26
Oct 18 16:12:31 skippy kernel: [ 9540.987426] ===>tx queue is not empty:6, 26
Oct 18 16:12:31 skippy kernel: [ 9541.089797] ===>tx queue is not empty:6, 26
Oct 18 16:12:31 skippy kernel: [ 9541.294411] ===>tx queue is not empty:6, 26
Oct 18 16:12:31 skippy kernel: [ 9541.395927] ===>tx queue is not empty:6, 26
Oct 18 16:12:32 skippy kernel: [ 9541.497707] ===>tx queue is not empty:6, 26
Oct 18 16:12:32 skippy kernel: [ 9541.600812] ===>tx queue is not empty:6, 26
Oct 18 16:12:32 skippy kernel: [ 9541.703048] ===>tx queue is not empty:6, 26
Oct 18 16:12:32 skippy kernel: [ 9541.711494] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
Oct 18 16:12:33 skippy kernel: [ 9542.709212] ieee->state is RTLLIB_LINKED
Oct 18 16:12:33 skippy kernel: [ 9542.847636] Associated successfully
Oct 18 16:12:33 skippy kernel: [ 9542.847639] Using G rates:108
Oct 18 16:12:33 skippy kernel: [ 9542.847640] Successfully associated, ht not enabled(0, 0)
Oct 18 16:12:33 skippy kernel: [ 9542.847642] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:12:33 skippy kernel: [ 9542.848650] silent reset associate
Oct 18 16:12:55 skippy kernel: [ 9564.487350] dis associate packet!
Oct 18 16:12:55 skippy kernel: [ 9564.487956] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:12:59 skippy kernel: [ 9568.791031] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
Oct 18 16:13:00 skippy kernel: [ 9570.264893] Linking with wt,channel:4, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Oct 18 16:13:00 skippy kernel: [ 9570.264910] ===>rtllib_associate_procedure_wq(), chan:4
Oct 18 16:13:00 skippy kernel: [ 9570.264914] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Oct 18 16:13:00 skippy kernel: [ 9570.275016] Linking with wt,channel:4, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Oct 18 16:13:00 skippy kernel: [ 9570.275036] ===>rtllib_associate_procedure_wq(), chan:4
Oct 18 16:13:00 skippy kernel: [ 9570.275040] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Oct 18 16:13:00 skippy kernel: [ 9570.286971] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
Oct 18 16:13:00 skippy kernel: [ 9570.289985] Associated successfully
Oct 18 16:13:00 skippy kernel: [ 9570.289987] normal associate
Oct 18 16:13:00 skippy kernel: [ 9570.289994] Using G rates:108
Oct 18 16:13:00 skippy kernel: [ 9570.289995] Successfully associated, ht not enabled(0, 0)
Oct 18 16:13:00 skippy kernel: [ 9570.289997] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:13:00 skippy kernel: [ 9570.299049] RX: IEEE802.1X EPAOL frame!
Oct 18 16:13:01 skippy kernel: [ 9571.283761] RX: IEEE802.1X EPAOL frame!
Oct 18 16:13:10 skippy kernel: [ 9580.276297] dis associate packet!
Oct 18 16:13:10 skippy kernel: [ 9580.276386] ===>tx queue is not empty:6, 2
Oct 18 16:13:10 skippy kernel: [ 9580.286567] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:13:10 skippy kernel: [ 9580.286630] ===>tx queue is not empty:6, 4
Oct 18 16:13:10 skippy kernel: [ 9580.398685] ===>tx queue is not empty:6, 6
Oct 18 16:13:11 skippy kernel: [ 9580.522110] ===>tx queue is not empty:6, 8
Oct 18 16:13:11 skippy kernel: [ 9580.641906] ===>tx queue is not empty:6, 10
Oct 18 16:13:11 skippy kernel: [ 9580.761622] ===>tx queue is not empty:6, 12
Oct 18 16:13:11 skippy kernel: [ 9580.881363] ===>tx queue is not empty:6, 14
Oct 18 16:13:11 skippy kernel: [ 9580.997195] ===>tx queue is not empty:6, 16
Oct 18 16:13:11 skippy kernel: [ 9581.110746] ===>tx queue is not empty:6, 18
Oct 18 16:13:11 skippy kernel: [ 9581.226711] ===>tx queue is not empty:6, 20
Oct 18 16:13:11 skippy kernel: [ 9581.336440] ===>tx queue is not empty:6, 22
Oct 18 16:13:12 skippy kernel: [ 9581.446122] ===>tx queue is not empty:6, 24
Oct 18 16:13:12 skippy kernel: [ 9581.929710] Linking with wt,channel:4, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Oct 18 16:13:12 skippy kernel: [ 9581.929726] ===>rtllib_associate_procedure_wq(), chan:4
Oct 18 16:13:12 skippy kernel: [ 9581.929731] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Oct 18 16:13:12 skippy kernel: [ 9581.939791] ===>tx queue is not empty:6, 25
Oct 18 16:13:12 skippy kernel: [ 9581.939813] Linking with wt,channel:4, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Oct 18 16:13:12 skippy kernel: [ 9581.939831] ===>rtllib_associate_procedure_wq(), chan:4
Oct 18 16:13:12 skippy kernel: [ 9581.939834] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Oct 18 16:13:12 skippy kernel: [ 9581.949873] ===>tx queue is not empty:6, 26
Oct 18 16:13:12 skippy kernel: [ 9581.953980] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
Oct 18 16:13:12 skippy kernel: [ 9581.954002] ===>tx queue is not empty:6, 27
Oct 18 16:13:12 skippy kernel: [ 9581.959487] Associated successfully
Oct 18 16:13:12 skippy kernel: [ 9581.959493] normal associate
Oct 18 16:13:12 skippy kernel: [ 9581.959506] Using G rates:108
Oct 18 16:13:12 skippy kernel: [ 9581.959508] Successfully associated, ht not enabled(0, 0)
Oct 18 16:13:12 skippy kernel: [ 9581.959512] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:13:12 skippy kernel: [ 9581.967601] RX: IEEE802.1X EPAOL frame!
Oct 18 16:13:13 skippy kernel: [ 9582.954153] RX: IEEE802.1X EPAOL frame!
Oct 18 16:13:15 skippy kernel: [ 9584.728790] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
Oct 18 16:13:16 skippy kernel: [ 9585.726226] ieee->state is RTLLIB_LINKED
Oct 18 16:13:16 skippy kernel: [ 9585.864663] Associated successfully
Oct 18 16:13:16 skippy kernel: [ 9585.864667] Using G rates:108
Oct 18 16:13:16 skippy kernel: [ 9585.864668] Successfully associated, ht not enabled(0, 0)
Oct 18 16:13:16 skippy kernel: [ 9585.864670] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:13:16 skippy kernel: [ 9585.865679] silent reset associate
Oct 18 16:13:22 skippy kernel: [ 9591.944032] dis associate packet!
Oct 18 16:13:22 skippy kernel: [ 9591.954801] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:13:24 skippy kernel: [ 9593.441642] Linking with wt,channel:4, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Oct 18 16:13:24 skippy kernel: [ 9593.441662] ===>rtllib_associate_procedure_wq(), chan:4
Oct 18 16:13:24 skippy kernel: [ 9593.441667] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Oct 18 16:13:24 skippy kernel: [ 9593.451780] Linking with wt,channel:4, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Oct 18 16:13:24 skippy kernel: [ 9593.451802] ===>rtllib_associate_procedure_wq(), chan:4
Oct 18 16:13:24 skippy kernel: [ 9593.451806] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Oct 18 16:13:26 skippy kernel: [ 9595.953849] Linking with wt,channel:4, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Oct 18 16:13:26 skippy kernel: [ 9595.953857] ===>rtllib_associate_procedure_wq(), chan:4
Oct 18 16:13:26 skippy kernel: [ 9595.953860] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Oct 18 16:13:26 skippy kernel: [ 9595.966309] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
Oct 18 16:13:26 skippy kernel: [ 9595.968881] Associated successfully
Oct 18 16:13:26 skippy kernel: [ 9595.968884] normal associate
Oct 18 16:13:26 skippy kernel: [ 9595.968897] Using G rates:108
Oct 18 16:13:26 skippy kernel: [ 9595.968900] Successfully associated, ht not enabled(0, 0)
Oct 18 16:13:26 skippy kernel: [ 9595.968903] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:13:26 skippy kernel: [ 9595.994641] RX: IEEE802.1X EPAOL frame!
Oct 18 16:13:27 skippy kernel: [ 9596.958897] RX: IEEE802.1X EPAOL frame!
Oct 18 16:13:32 skippy kernel: [ 9601.864417] ===>tx queue is not empty:6, 3
Oct 18 16:13:32 skippy kernel: [ 9601.965580] ===>tx queue is not empty:6, 3
Oct 18 16:13:32 skippy kernel: [ 9602.170451] ===>tx queue is not empty:6, 3
Oct 18 16:13:32 skippy kernel: [ 9602.273041] ===>tx queue is not empty:6, 3
Oct 18 16:13:33 skippy kernel: [ 9602.374633] ===>tx queue is not empty:6, 3
Oct 18 16:13:33 skippy kernel: [ 9602.476881] ===>tx queue is not empty:6, 3
Oct 18 16:13:33 skippy kernel: [ 9602.579507] ===>tx queue is not empty:6, 3
Oct 18 16:13:33 skippy kernel: [ 9602.681973] ===>tx queue is not empty:6, 3
Oct 18 16:13:33 skippy kernel: [ 9602.783449] ===>tx queue is not empty:6, 3
Oct 18 16:13:33 skippy kernel: [ 9602.885598] ===>tx queue is not empty:6, 3
Oct 18 16:13:33 skippy kernel: [ 9602.989148] ===>tx queue is not empty:6, 3
Oct 18 16:13:33 skippy kernel: [ 9603.090133] ===>tx queue is not empty:6, 3
Oct 18 16:13:33 skippy kernel: [ 9603.192741] ===>tx queue is not empty:6, 3
Oct 18 16:13:34 skippy kernel: [ 9603.395551] ===>tx queue is not empty:6, 3
Oct 18 16:13:34 skippy kernel: [ 9603.497689] ===>tx queue is not empty:6, 3
Oct 18 16:13:34 skippy kernel: [ 9603.804562] ===>tx queue is not empty:6, 3
Oct 18 16:13:34 skippy kernel: [ 9604.111374] ===>tx queue is not empty:6, 3
Oct 18 16:13:34 skippy kernel: [ 9604.212620] ===>tx queue is not empty:6, 3
Oct 18 16:13:34 skippy kernel: [ 9604.315717] ===>tx queue is not empty:6, 3
Oct 18 16:13:35 skippy kernel: [ 9604.418003] ===>tx queue is not empty:6, 3
Oct 18 16:13:35 skippy kernel: [ 9604.622721] ===>tx queue is not empty:6, 3
Oct 18 16:13:35 skippy kernel: [ 9604.724327] ===>tx queue is not empty:6, 3
Oct 18 16:13:35 skippy kernel: [ 9604.826583] ===>tx queue is not empty:6, 3
Oct 18 16:13:35 skippy kernel: [ 9604.928785] ===>tx queue is not empty:6, 3
Oct 18 16:13:35 skippy kernel: [ 9605.029831] ===>tx queue is not empty:6, 3
Oct 18 16:13:35 skippy kernel: [ 9605.131986] ===>tx queue is not empty:6, 3
Oct 18 16:13:35 skippy kernel: [ 9605.235467] ===>tx queue is not empty:6, 3
Oct 18 16:13:35 skippy kernel: [ 9605.337272] ===>tx queue is not empty:6, 3
Oct 18 16:13:36 skippy kernel: [ 9605.438951] ===>tx queue is not empty:6, 3
Oct 18 16:13:36 skippy kernel: [ 9605.541241] ===>tx queue is not empty:6, 3
Oct 18 16:13:36 skippy kernel: [ 9605.642685] ===>tx queue is not empty:6, 3
Oct 18 16:13:36 skippy kernel: [ 9605.746303] ===>tx queue is not empty:6, 3
Oct 18 16:13:36 skippy kernel: [ 9605.848220] ===>tx queue is not empty:6, 3
Oct 18 16:13:36 skippy kernel: [ 9605.949086] ===>tx queue is not empty:6, 3
Oct 18 16:13:36 skippy kernel: [ 9605.971153] dis associate packet!
Oct 18 16:13:36 skippy kernel: [ 9605.981446] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:13:38 skippy kernel: [ 9607.488579] Linking with wt,channel:4, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Oct 18 16:13:38 skippy kernel: [ 9607.488597] ===>rtllib_associate_procedure_wq(), chan:4
Oct 18 16:13:38 skippy kernel: [ 9607.488602] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Oct 18 16:13:38 skippy kernel: [ 9607.498644] Linking with wt,channel:4, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Oct 18 16:13:38 skippy kernel: [ 9607.498662] ===>rtllib_associate_procedure_wq(), chan:4
Oct 18 16:13:38 skippy kernel: [ 9607.498665] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Oct 18 16:13:38 skippy kernel: [ 9607.510628] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
Oct 18 16:13:38 skippy kernel: [ 9607.513258] Associated successfully
Oct 18 16:13:38 skippy kernel: [ 9607.513261] normal associate
Oct 18 16:13:38 skippy kernel: [ 9607.513270] Using G rates:108
Oct 18 16:13:38 skippy kernel: [ 9607.513272] Successfully associated, ht not enabled(0, 0)
Oct 18 16:13:38 skippy kernel: [ 9607.513274] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:13:38 skippy kernel: [ 9607.523308] RX: IEEE802.1X EPAOL frame!
Oct 18 16:13:38 skippy kernel: [ 9607.686516] ===>tx queue is not empty:6, 29
Oct 18 16:13:38 skippy kernel: [ 9607.787665] ===>tx queue is not empty:6, 29
Oct 18 16:13:38 skippy kernel: [ 9607.890359] ===>tx queue is not empty:6, 29
Oct 18 16:13:38 skippy kernel: [ 9607.993115] ===>tx queue is not empty:6, 29
Oct 18 16:13:38 skippy kernel: [ 9608.196226] ===>tx queue is not empty:6, 29
Oct 18 16:13:38 skippy kernel: [ 9608.299912] ===>tx queue is not empty:6, 29
Oct 18 16:13:39 skippy kernel: [ 9608.401323] ===>tx queue is not empty:6, 29
Oct 18 16:13:39 skippy kernel: [ 9608.502623] ===>tx queue is not empty:6, 29
Oct 18 16:13:39 skippy kernel: [ 9608.509473] RX: IEEE802.1X EPAOL frame!
Oct 18 16:13:39 skippy kernel: [ 9608.706940] ===>tx queue is not empty:6, 29
Oct 18 16:13:39 skippy kernel: [ 9608.809990] ===>tx queue is not empty:6, 29
Oct 18 16:13:39 skippy kernel: [ 9609.014499] ===>tx queue is not empty:6, 29
Oct 18 16:13:39 skippy kernel: [ 9609.115496] ===>tx queue is not empty:6, 29
Oct 18 16:13:39 skippy kernel: [ 9609.218468] ===>tx queue is not empty:6, 29
Oct 18 16:13:39 skippy kernel: [ 9609.321559] ===>tx queue is not empty:6, 29
Oct 18 16:13:40 skippy kernel: [ 9609.422576] ===>tx queue is not empty:6, 29
Oct 18 16:13:40 skippy kernel: [ 9609.525230] ===>tx queue is not empty:6, 29
Oct 18 16:13:40 skippy kernel: [ 9609.627404] ===>tx queue is not empty:6, 29
Oct 18 16:13:40 skippy kernel: [ 9609.728408] ===>tx queue is not empty:6, 29
Oct 18 16:13:40 skippy kernel: [ 9609.788481] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
Oct 18 16:13:41 skippy kernel: [ 9610.785648] ieee->state is RTLLIB_LINKED
Oct 18 16:13:41 skippy kernel: [ 9610.924118] Associated successfully
Oct 18 16:13:41 skippy kernel: [ 9610.924123] Using G rates:108
Oct 18 16:13:41 skippy kernel: [ 9610.924124] Successfully associated, ht not enabled(0, 0)
Oct 18 16:13:41 skippy kernel: [ 9610.924126] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:13:41 skippy kernel: [ 9610.925134] silent reset associate
Oct 18 16:13:48 skippy kernel: [ 9617.499668] dis associate packet!
Oct 18 16:13:48 skippy kernel: [ 9617.510407] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:13:49 skippy kernel: [ 9619.106965] Linking with wt,channel:4, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Oct 18 16:13:49 skippy kernel: [ 9619.106983] ===>rtllib_associate_procedure_wq(), chan:4
Oct 18 16:13:49 skippy kernel: [ 9619.106988] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Oct 18 16:13:49 skippy kernel: [ 9619.117058] Linking with wt,channel:4, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Oct 18 16:13:49 skippy kernel: [ 9619.117261] ===>rtllib_associate_procedure_wq(), chan:4
Oct 18 16:13:49 skippy kernel: [ 9619.117263] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Oct 18 16:13:49 skippy kernel: [ 9619.132027] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
Oct 18 16:13:49 skippy kernel: [ 9619.196465] Associated successfully
Oct 18 16:13:49 skippy kernel: [ 9619.196470] normal associate
Oct 18 16:13:49 skippy kernel: [ 9619.196485] Using G rates:108
Oct 18 16:13:49 skippy kernel: [ 9619.196488] Successfully associated, ht not enabled(0, 0)
Oct 18 16:13:49 skippy kernel: [ 9619.196492] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:13:49 skippy kernel: [ 9619.208340] RX: IEEE802.1X EPAOL frame!
Oct 18 16:13:50 skippy kernel: [ 9620.189900] RX: IEEE802.1X EPAOL frame!
Oct 18 16:13:55 skippy kernel: [ 9624.947503] ===>tx queue is not empty:6, 2
Oct 18 16:13:55 skippy kernel: [ 9625.050462] ===>tx queue is not empty:6, 2
Oct 18 16:13:55 skippy kernel: [ 9625.152082] ===>tx queue is not empty:6, 2
Oct 18 16:13:55 skippy kernel: [ 9625.254402] ===>tx queue is not empty:6, 2
Oct 18 16:13:56 skippy kernel: [ 9625.357243] ===>tx queue is not empty:6, 2
Oct 18 16:13:56 skippy kernel: [ 9625.458685] ===>tx queue is not empty:6, 2
Oct 18 16:13:56 skippy kernel: [ 9625.560678] ===>tx queue is not empty:6, 2
Oct 18 16:13:56 skippy kernel: [ 9625.663864] ===>tx queue is not empty:6, 2
Oct 18 16:13:56 skippy kernel: [ 9625.765421] ===>tx queue is not empty:6, 2
Oct 18 16:13:56 skippy kernel: [ 9625.868976] ===>tx queue is not empty:6, 2
Oct 18 16:13:56 skippy kernel: [ 9626.275351] ===>tx queue is not empty:6, 2
Oct 18 16:13:57 skippy kernel: [ 9626.480735] ===>tx queue is not empty:6, 2
Oct 18 16:13:57 skippy kernel: [ 9626.684652] ===>tx queue is not empty:6, 2
Oct 18 16:13:57 skippy kernel: [ 9626.787438] ===>tx queue is not empty:6, 2
Oct 18 16:13:57 skippy kernel: [ 9626.889385] ===>tx queue is not empty:6, 2
Oct 18 16:13:57 skippy kernel: [ 9626.990589] ===>tx queue is not empty:6, 2
Oct 18 16:13:57 skippy kernel: [ 9627.092481] ===>tx queue is not empty:6, 2
Oct 18 16:13:57 skippy kernel: [ 9627.194624] ===>tx queue is not empty:6, 2
Oct 18 16:13:58 skippy kernel: [ 9627.296823] ===>tx queue is not empty:6, 2
Oct 18 16:13:58 skippy kernel: [ 9627.399901] ===>tx queue is not empty:6, 2
Oct 18 16:13:58 skippy kernel: [ 9627.501769] ===>tx queue is not empty:6, 2
Oct 18 16:13:58 skippy kernel: [ 9627.603187] ===>tx queue is not empty:6, 2
Oct 18 16:13:58 skippy kernel: [ 9627.706023] ===>tx queue is not empty:6, 2
Oct 18 16:13:58 skippy kernel: [ 9627.807900] ===>tx queue is not empty:6, 2
Oct 18 16:13:58 skippy kernel: [ 9627.909568] ===>tx queue is not empty:6, 2
Oct 18 16:13:58 skippy kernel: [ 9628.011768] ===>tx queue is not empty:6, 2
Oct 18 16:13:58 skippy kernel: [ 9628.114243] ===>tx queue is not empty:6, 2
Oct 18 16:13:58 skippy kernel: [ 9628.216966] ===>tx queue is not empty:6, 2
Oct 18 16:13:59 skippy kernel: [ 9628.292986] dis associate packet!
Oct 18 16:13:59 skippy kernel: [ 9628.293307] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:14:04 skippy kernel: [ 9634.244890] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
Oct 18 16:14:06 skippy kernel: [ 9635.718016] Linking with wt,channel:4, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Oct 18 16:14:06 skippy kernel: [ 9635.718031] ===>rtllib_associate_procedure_wq(), chan:4
Oct 18 16:14:06 skippy kernel: [ 9635.718035] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Oct 18 16:14:06 skippy kernel: [ 9635.728140] Linking with wt,channel:4, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Oct 18 16:14:06 skippy kernel: [ 9635.728157] ===>rtllib_associate_procedure_wq(), chan:4
Oct 18 16:14:06 skippy kernel: [ 9635.728161] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Oct 18 16:14:06 skippy kernel: [ 9635.740037] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
Oct 18 16:14:06 skippy kernel: [ 9635.743205] Associated successfully
Oct 18 16:14:06 skippy kernel: [ 9635.743209] normal associate
Oct 18 16:14:06 skippy kernel: [ 9635.743220] Using G rates:108
Oct 18 16:14:06 skippy kernel: [ 9635.743223] Successfully associated, ht not enabled(0, 0)
Oct 18 16:14:06 skippy kernel: [ 9635.743226] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:14:06 skippy kernel: [ 9635.751396] RX: IEEE802.1X EPAOL frame!
Oct 18 16:14:07 skippy kernel: [ 9636.739139] RX: IEEE802.1X EPAOL frame!
Oct 18 16:14:16 skippy kernel: [ 9645.727712] dis associate packet!
Oct 18 16:14:16 skippy kernel: [ 9645.727740] ===>tx queue is not empty:6, 2
Oct 18 16:14:16 skippy kernel: [ 9645.738056] ===>tx queue is not empty:6, 4
Oct 18 16:14:16 skippy kernel: [ 9645.738069] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:14:16 skippy kernel: [ 9645.851749] ===>tx queue is not empty:6, 6
Oct 18 16:14:16 skippy kernel: [ 9645.961520] ===>tx queue is not empty:6, 8
Oct 18 16:14:16 skippy kernel: [ 9646.071279] ===>tx queue is not empty:6, 10
Oct 18 16:14:16 skippy kernel: [ 9646.191046] ===>tx queue is not empty:6, 12
Oct 18 16:14:17 skippy kernel: [ 9646.300761] ===>tx queue is not empty:6, 14
Oct 18 16:14:17 skippy kernel: [ 9646.423909] ===>tx queue is not empty:6, 16
Oct 18 16:14:17 skippy kernel: [ 9646.540089] ===>tx queue is not empty:6, 18
Oct 18 16:14:17 skippy kernel: [ 9646.659862] ===>tx queue is not empty:6, 20
Oct 18 16:14:17 skippy kernel: [ 9646.779716] ===>tx queue is not empty:6, 22
Oct 18 16:14:17 skippy kernel: [ 9646.899309] ===>tx queue is not empty:6, 24
Oct 18 16:14:18 skippy kernel: [ 9647.271356] Linking with wt,channel:4, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Oct 18 16:14:18 skippy kernel: [ 9647.271369] ===>rtllib_associate_procedure_wq(), chan:4
Oct 18 16:14:18 skippy kernel: [ 9647.271373] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Oct 18 16:14:18 skippy kernel: [ 9647.281467] ===>tx queue is not empty:6, 25
Oct 18 16:14:18 skippy kernel: [ 9647.281475] Linking with wt,channel:4, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Oct 18 16:14:18 skippy kernel: [ 9647.281494] ===>rtllib_associate_procedure_wq(), chan:4
Oct 18 16:14:18 skippy kernel: [ 9647.281497] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Oct 18 16:14:18 skippy kernel: [ 9647.291536] ===>tx queue is not empty:6, 26
Oct 18 16:14:18 skippy kernel: [ 9647.295289] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
Oct 18 16:14:18 skippy kernel: [ 9647.295314] ===>tx queue is not empty:6, 27
Oct 18 16:14:18 skippy kernel: [ 9647.297914] Associated successfully
Oct 18 16:14:18 skippy kernel: [ 9647.297917] normal associate
Oct 18 16:14:18 skippy kernel: [ 9647.297928] Using G rates:108
Oct 18 16:14:18 skippy kernel: [ 9647.297930] Successfully associated, ht not enabled(0, 0)
Oct 18 16:14:18 skippy kernel: [ 9647.297934] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:14:18 skippy kernel: [ 9647.302158] RX: IEEE802.1X EPAOL frame!
Oct 18 16:14:19 skippy kernel: [ 9648.288731] RX: IEEE802.1X EPAOL frame!
Oct 18 16:14:21 skippy kernel: [ 9650.811428] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
Oct 18 16:14:22 skippy kernel: [ 9651.808159] ieee->state is RTLLIB_LINKED
Oct 18 16:14:22 skippy kernel: [ 9651.946585] Associated successfully
Oct 18 16:14:22 skippy kernel: [ 9651.946589] Using G rates:108
Oct 18 16:14:22 skippy kernel: [ 9651.946591] Successfully associated, ht not enabled(0, 0)
Oct 18 16:14:22 skippy kernel: [ 9651.946592] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 18 16:14:22 skippy kernel: [ 9651.947601] silent reset associate

---

### Post by skippy_ on 2010-10-18
more headaches.

can't be a bad install because I've reinstalled the driver.

loren@skippy:~$ tail -f /var/log/messages
Oct 18 21:51:25 skippy kernel: [   51.957390] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Oct 18 21:51:25 skippy kernel: [   52.000677] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
Oct 18 21:51:25 skippy kernel: [   52.005871] Associated successfully
Oct 18 21:51:25 skippy kernel: [   52.005880] normal associate
Oct 18 21:51:25 skippy kernel: [   52.005892] Using G rates:108
Oct 18 21:51:25 skippy kernel: [   52.005894] Successfully associated, ht not enabled(0, 0)
Oct 18 21:51:25 skippy kernel: [   52.005901] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
Oct 18 21:51:25 skippy kernel: [   52.007217] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 18 21:51:26 skippy kernel: [   52.879815] DHCP pkt src port:68, dest port:67!!
Oct 18 21:51:26 skippy kernel: [   53.642104] dm_check_edca_turbo():iot peer is unknown, bssid:00:1f:c6:29:3c:0f
Oct 18 21:51:38 skippy kernel: [   65.400461] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
Oct 18 21:52:18 skippy kernel: [  105.405424] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
Oct 18 21:57:12 skippy kernel: [  399.618282] __ratelimit: 9 callbacks suppressed
Oct 18 21:57:12 skippy kernel: [  399.618287] keyboard.c: can't emulate rawmode for keycode 244
Oct 18 21:57:12 skippy kernel: [  399.618309] keyboard.c: can't emulate rawmode for keycode 244
Oct 18 22:06:40 skippy kernel: [  967.803054] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
Oct 18 22:06:42 skippy kernel: [  969.798555] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=3
Oct 18 22:06:44 skippy kernel: [  971.798588] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=4
Oct 18 22:06:46 skippy kernel: [  973.796761] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=5
Oct 18 22:06:46 skippy kernel: [  973.796767] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
Oct 18 22:06:47 skippy kernel: [  974.796134] ieee->state is RTLLIB_LINKED
Oct 18 22:06:47 skippy kernel: [  974.796330] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:47 skippy kernel: [  974.796333] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:47 skippy kernel: [  974.863765] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:47 skippy kernel: [  974.863769] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:47 skippy kernel: [  974.935103] InitializeAdapter8192SE(): Set MRC settings on as default!!
Oct 18 22:06:47 skippy kernel: [  974.935108] HW_VAR_MRC: Turn on 1T1R MRC!
Oct 18 22:06:47 skippy kernel: [  974.983797] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:47 skippy kernel: [  974.983807] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  975.101995] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  975.102002] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  975.115343] Received beacon ContryIE, SSID: <2WIRE572>
Oct 18 22:06:48 skippy kernel: [  975.222989] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  975.222999] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  975.339918] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  975.339921] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  975.449937] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  975.449945] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  975.559933] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  975.559941] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  975.669916] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  975.669923] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  975.779933] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  975.779940] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  975.889855] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  975.889862] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  976.009880] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:48 skippy kernel: [  976.009888] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:49 skippy kernel: [  976.353585] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
Oct 18 22:06:49 skippy kernel: [  976.354602] =====>rtl8192_hard_start_xmit() retrun :0:0:1
Oct 18 22:06:49 skippy kernel: [  976.375285] Associated successfully
Oct 18 22:06:49 skippy kernel: [  976.375294] Using G rates:108
Oct 18 22:06:49 skippy kernel: [  976.375296] Successfully associated, ht not enabled(0, 0)
Oct 18 22:06:49 skippy kernel: [  976.375303] rtl8192se_update_ratr_table: ratr_index=0 ratr_table=0x00000ff5
Oct 18 22:06:49 skippy kernel: [  976.376314] silent reset associat

---

### Post by isantop on 2010-10-19
It may be an issue with something other than the driver, and that could be the culprit of the bad install. I'd try it from a LiveCD to see if you're still getting panics there. If not, I'd say it's almost definitely an issue with the installation. If you do still get them, it's probably a hardware problem.

---

### Post by skippy_ on 2010-10-19
Hey,

Thanks for your help, but I managed to get it working by installing the driver on this page:

[http://justinsomnia.org/2010/02/ubuntu-on-a-lenovo-thinkpad-x100e/](http://justinsomnia.org/2010/02/ubuntu-on-a-lenovo-thinkpad-x100e/)

---

