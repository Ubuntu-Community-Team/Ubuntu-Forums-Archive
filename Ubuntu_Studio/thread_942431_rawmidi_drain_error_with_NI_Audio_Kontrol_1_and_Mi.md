---
title: "rawmidi drain error with NI Audio Kontrol 1 and Mixxx or Jack"
date: 2008-10-09
forum: Ubuntu Studio
---

### Post by LevTermen on 2008-10-09
Hi,

I've just bought a Native Instruments Audio Kontrol 1 soundcard recently. My system is running Ubuntu 8.04 2.6.24-21-rt #1 SMP PREEMPT RT i686.

I've properly set up my .asoundrc file as recommended at the bottom of the 2nd page of [this thread]("http://www.native-instruments.com/forum/showthread.php?t=53898"), but using plughw:1,0,0 instead of hw:1,0,0 (variable ID depending on your wiring), as the related ALSA device called "usb" introduces a huge latency.

Whenever I open the Mixxx sound preferences and choose the NI soundcard, or whenever I try to shutdown the jack server, if previously successfully started on the device; the mouse moves and keystrokes become jittery and slow. It seems to affect all soundcards from NI using the snd-usb-caiaq driver, see [[Mixxx-devel] Native Instruments Audio 8 DJ and mixxx on ubuntu 8.04]("http://sourceforge.net/mailarchive/forum.php?thread_name=48C63084.8010103%40hale.at&forum_name=mixxx-devel"). I guess this is also somehow related to  [bug #134064: [gutsy] midi not working]("https://bugs.launchpad.net/ubuntu/+bug/134064")

Here follows a dmesg snippet right from after a crash. I guess the most interesting part is located at the end close to "rawmidi drain error":```
[ 1792.614751] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000044
[ 1792.614761] printing eip: f8bc06fd *pde = 00000000
[ 1792.614767] Oops: 0000 [#1] PREEMPT SMP
[ 1792.614771] Modules linked in: snd_rtctimer ipv6 i915 drm af_packet rfcomm l2cap ppdev acpi_cpufreq cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_conservative cpufreq_ondemand freq_table container sbs sbshc bay dock iptable_filter ip_tables x_tables nls_iso8859_1 nls_cp437 vfat fat aes_i586 dm_crypt dm_mod ipaq usbserial parport_pc lp parport snd_seq_dummy snd_usb_caiaq snd_seq_oss snd_seq_midi arc4 ecb snd_rawmidi blkcipher snd_seq_midi_event snd_pcm_oss snd_mixer_oss snd_seq snd_pcm joydev snd_seq_device video output ac battery snd_timer usbhid hid iwl3945 hci_usb iwlwifi_mac80211 psmouse bluetooth cfg80211 serio_raw snd tpm_infineon asus_laptop tpm tpm_bios led_class button soundcore evdev snd_page_alloc pcspkr iTCO_wdt iTCO_vendor_support intel_agp shpchp pci_hotplug agpgart ext3 jbd mbcache usb_storage sg sr_mod cdrom sd_mod ata_generic libusual ata_piix r8169 pata_acpi libata uhci_hcd ehci_hcd scsi_mod usbcore thermal processor fan fuse
[ 1792.614845]
[ 1792.614848] Pid: 2133, comm: IRQ-19 Not tainted (2.6.24-21-rt #1)
[ 1792.614850] EIP: 0060:[<f8bc06fd>] EFLAGS: 00010292 CPU: 1
[ 1792.614859] EIP is at snd_rawmidi_transmit_peek+0x1d/0x100 [snd_rawmidi]
[ 1792.614862] EAX: 00000000 EBX: f7df1264 ECX: 0000003d EDX: f7df1407
[ 1792.614864] ESI: ffffffea EDI: 00000000 EBP: f7df1407 ESP: f7139e38
[ 1792.614866]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068 preempt:00000001
[ 1792.614869] Process IRQ-19 (pid: 2133, ti=f7138000 task=f7d580b0 task.ti=f7138000)
[ 1792.614871] Stack: 0000003d 00000000 f7df1264 00000000 00000000 f77c6400 f8b97c79 00000000
[ 1792.614878]        f7df1264 f7df130c 00000000 f77c6400 f77c6400 f7df130c f889e9a8 dfb45300
[ 1792.614884]        f77c6508 00000000 f7df130c f88cb770 df9c92a0 df9c92a0 ffffff8d f730a480
[ 1792.614891] Call Trace:
[ 1792.614896]  [<f8b97c79>] snd_usb_caiaq_midi_send+0x29/0x80 [snd_usb_caiaq]
[ 1792.614908]  [<f889e9a8>] usb_hcd_giveback_urb+0x48/0xc0 [usbcore]
[ 1792.614931]  [<f88cb770>] ehci_urb_done+0x70/0xb0 [ehci_hcd]
[ 1792.614940]  [<f88cc53f>] qh_completions+0x24f/0x430 [ehci_hcd]
[ 1792.614952]  [<f88cd93e>] ehci_work+0x51e/0x810 [ehci_hcd]
[ 1792.614958]  [<c01224d8>] load_balance_fair+0xe8/0x120
[ 1792.614973]  [<f88d0498>] ehci_irq+0x158/0x1c0 [ehci_hcd]
[ 1792.614983]  [<f889ec9b>] usb_hcd_irq+0x2b/0x60 [usbcore]
[ 1792.615001]  [<c016a8dc>] handle_IRQ_event+0x5c/0x100
[ 1792.615010]  [<c016af1a>] thread_simple_irq+0x4a/0x90
[ 1792.615015]  [<c016b869>] do_irqd+0x229/0x290
[ 1792.615023]  [<c016b640>] do_irqd+0x0/0x290
[ 1792.615027]  [<c0141ea2>] kthread+0x42/0x70
[ 1792.615030]  [<c0141e60>] kthread+0x0/0x70
[ 1792.615034]  [<c0105847>] kernel_thread_helper+0x7/0x10
[ 1792.615041]  =======================
[ 1792.615042] Code: 24 10 83 c4 14 c3 bf ea ff ff ff eb e3 90 83 ec 18 89 74 24 0c be ea ff ff ff 89 6c 24 14 89 d5 89 5c 24 08 89 7c 24 10 89 0c 24 <8b> 58 44 8b 7b 04 85 ff 0f 84 8e 00 00 00 8d 43 20 31 f6 89 44
[ 1792.615078] EIP: [<f8bc06fd>] snd_rawmidi_transmit_peek+0x1d/0x100 [snd_rawmidi] SS:ESP 0068:f7139e38
[ 1792.615093] ---[ end trace a8aeb26563050901 ]---
[ 1802.651156] ALSA /usr/src/modules/alsa-driver/acore/rawmidi.c:196: rawmidi drain error (avail = 4095, buffer_size = 4096)
[ 1824.378600] usb 1-7: reset high speed USB device using ehci_hcd and address 7
```

From this clue, I suspected the MIDI part of the driver. Might be dumb, but I tried setting up another MIDI device in the mixxx MIDI controller settings, but it didn't prevent it from crashing. I tried to unload the rawmidi module, but it is required by the caiaq module.

Any idea?

Best,
C.

---

