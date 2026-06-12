---
title: "Virtualbox 1.6 after resume crashes"
date: 2008-05-04
forum: Virtualisation
---

### Post by Kow on 2008-05-04
Everytime I try resuming a virtualbox after resuming (the host) from suspend to ram this happens:

[  607.931204] CPU 1 
[  607.931207] Modules linked in: b44 ssb mii iwl3945 iwlwifi_mac80211 cfg80211 af_packet binfmt_misc rfcomm l2cap bluetooth ipv6 vboxdrv ppdev acpi_cpufreq cpufreq_ondemand cpufreq_powersave cpufreq_stats freq_table cpufreq_userspace cpufreq_conservative sbs sbshc container dock iptable_filter ip_tables x_tables ext2 sbp2 parport_pc lp parport arc4 ecb blkcipher joydev snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm nvidia(P) snd_page_alloc snd_hwdep i2c_core snd_seq_dummy snd_seq_oss snd_seq_midi sdhci snd_rawmidi snd_seq_midi_event mmc_core video output ricoh_mmc iTCO_wdt snd_seq wmi_acer snd_timer snd_seq_device ac serio_raw button battery snd dcdbas evdev iTCO_vendor_support shpchp pci_hotplug intel_agp soundcore psmouse pcspkr ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_acpi ata_piix ata_generic ehci_hcd libata scsi_mod ohci1394 ieee1394 uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  607.931325] Pid: 6519, comm: VirtualBox Tainted: P        2.6.24-16-generic #1
[  607.931330] RIP: 0010:[<ffffffff88c6e2ab>]  [<ffffffff88c6e2ab>] :vboxdrv:g_abExecMemory+0x642b/0x180000
[  607.931345] RSP: 0018:ffff810058975dc0  EFLAGS: 00010046
[  607.931349] RAX: 0000000000000000 RBX: 00000000000056c1 RCX: ffffffff88c60090
[  607.931353] RDX: 0000000000000000 RSI: 000000008005003b RDI: 0000000000006c00
[  607.931357] RBP: ffff810058975e08 R08: ffff810063bea568 R09: 0000000000000002
[  607.931361] R10: 0000000000000000 R11: ffffffff88c733d0 R12: 00000000fffff054
[  607.931364] R13: ffffc20000f02000 R14: 00000000000056c1 R15: 00007fa2e9d9b504
[  607.931369] FS:  0000000040afe950(0063) GS:ffff81007dc01700(0000) knlGS:0000000000000000
[  607.931373] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  607.931377] CR2: 000000000060c5e0 CR3: 000000005f2c9000 CR4: 00000000000006a0
[  607.931381] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  607.931384] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  607.931389] Process VirtualBox (pid: 6519, threadinfo ffff810058974000, task ffff81005f31e000)
[  607.931392] Stack:  ffffffff88c6fa6f 0000000000000000 0000000000000001 00007fa2e4000e18
[  607.931401]  0000000000000000 0000000000000001 00000000000056c1 00000000fffff054
[  607.931408]  ffffc20000f02000 ffff810058975e48 ffffffff88c6d526 0000000000000000
[  607.931414] Call Trace:
[  607.931424]  [<ffffffff88c6fa6f>] :vboxdrv:g_abExecMemory+0x7bef/0x180000
[  607.931445]  [<ffffffff88c6d526>] :vboxdrv:g_abExecMemory+0x56a6/0x180000
[  607.931462]  [<ffffffff88c73449>] :vboxdrv:g_abExecMemory+0xb5c9/0x180000
[  607.931478]  [<ffffffff88c600da>] :vboxdrv:VBoxDrvLinuxIOCtl+0x4a/0x1d0
[  607.931489]  [<ffffffff80460782>] schedule+0x142/0x245
[  607.931498]  [<ffffffff802595d3>] getnstimeofday+0x33/0xa0
[  607.931512]  [<ffffffff802bb06f>] do_ioctl+0x2f/0xa0
[  607.931520]  [<ffffffff802bb300>] vfs_ioctl+0x220/0x2c0
[  607.931532]  [<ffffffff802bb431>] sys_ioctl+0x91/0xb0
[  607.931545]  [<ffffffff8020c37e>] system_call+0x7e/0x83
[  607.931563] 
[  607.931565] 
[  607.931566] Code: 0f 79 fe 73 06 b8 5f f0 ff ff c3 75 05 b8 60 f0 ff ff c3 cc 
[  607.931583] RIP  [<ffffffff88c6e2ab>] :vboxdrv:g_abExecMemory+0x642b/0x180000
[  607.931594]  RSP <ffff810058975dc0>
[  607.931600] ---[ end trace d132a7060dbfc45c ]---

This didn't happen with Virtualbox 1.5.6. I would relay this on to virtualbox.org but since they're owned by Sun they dont let anyone post bug reports... useless. Looks like I'm moving to qemu.

---

### Post by Lesterchakyn on 2008-09-09
After several months, I found the solution on another forum.

At least in my case, if I disable VT-x/AMD-V, it works again after resume without problems.

:)

---

