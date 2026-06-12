---
title: "WARNING: at /build/buildd/linux-3.8.0/net/sched/sch_generic.c:254 dev_watchdog+0x242/"
date: 2013-04-14
forum: Ubuntu Development Version
---

### Post by sanderj on 2013-04-14
My fully updated 13.04 Raring daily shows the info below in dmesg, and has problems connecting via wired ethernet. I think the problem is in the cable or the router, not in Ubuntu, but I find the dmesg info a bit strange.

Any explanation?

```
[14472.311431] sky2 0000:06:00.0 eth0: Link is up at 100 Mbps, full duplex, flow control both
[14472.311476] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[14482.785271] ------------[ cut here ]------------
[14482.785294] WARNING: at /build/buildd/linux-3.8.0/net/sched/sch_generic.c:254 dev_watchdog+0x242/0x250()
[14482.785300] Hardware name: R530/R730/R540              
[14482.785306] NETDEV WATCHDOG: eth0 (sky2): transmit queue 0 timed out
[14482.785310] Modules linked in: md4(F) ip6table_filter(F) ip6_tables(F) ebtable_nat(F) ebtables(F) xt_state(F) ipt_REJECT(F) xt_CHECKSUM(F) iptable_mangle(F) xt_tcpudp(F) iptable_filter(F) pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) ipt_MASQUERADE(F) iptable_nat(F) nf_conntrack_ipv4(F) nf_defrag_ipv4(F) nf_nat_ipv4(F) nf_nat(F) nf_conntrack(F) ip_tables(F) x_tables(F) parport_pc(F) ppdev(F) rfcomm bnep bluetooth bridge(F) stp(F) llc(F) nls_utf8 cifs(F) fscache(F) binfmt_misc(F) snd_hda_codec_hdmi snd_hda_codec_realtek uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev coretemp kvm_intel joydev(F) kvm snd_hda_intel snd_hda_codec snd_hwdep(F) snd_pcm(F) arc4(F) ath9k snd_page_alloc(F) snd_seq_midi(F) i915 ath9k_common ath9k_hw snd_seq_midi_event(F) ath snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) mac80211 cfg80211 microcode(F) snd(F) soundcore(F) psmouse(F) drm_kms_helper drm lpc_ich intel_ips samsung_laptop i2c_algo_bit video(F) serio_raw(F) mac_hid lp(F) parport(F) btrfs(F) zlib_deflate(F) libcrc32c(F) hid_generic usbhid hid sky2 ahci(F) libahci(F)
[14482.785449] Pid: 0, comm: swapper/3 Tainted: GF          O 3.8.0-17-generic #27-Ubuntu
[14482.785452] Call Trace:
[14482.785456]  <IRQ>  [<ffffffff810587df>] warn_slowpath_common+0x7f/0xc0
[14482.785471]  [<ffffffff810588dc>] warn_slowpath_fmt+0x4c/0x50
[14482.785485]  [<ffffffff815e7552>] dev_watchdog+0x242/0x250
[14482.785491]  [<ffffffff815e7310>] ? dev_graft_qdisc+0x90/0x90
[14482.785499]  [<ffffffff81068106>] call_timer_fn+0x36/0x120
[14482.785505]  [<ffffffff815e7310>] ? dev_graft_qdisc+0x90/0x90
[14482.785512]  [<ffffffff81069d4e>] run_timer_softirq+0x1fe/0x2a0
[14482.785520]  [<ffffffff81060f1f>] __do_softirq+0xcf/0x210
[14482.785528]  [<ffffffff81572e20>] ? centrino_target+0x370/0x370
[14482.785536]  [<ffffffff816d4d1c>] call_softirq+0x1c/0x30
[14482.785545]  [<ffffffff81016565>] do_softirq+0x75/0xb0
[14482.785551]  [<ffffffff810611c5>] irq_exit+0xa5/0xb0
[14482.785558]  [<ffffffff816d569e>] smp_apic_timer_interrupt+0x6e/0x99
[14482.785563]  [<ffffffff816d45dd>] apic_timer_interrupt+0x6d/0x80
[14482.785566]  <EOI>  [<ffffffff81573868>] ? cpuidle_wrap_enter+0x58/0xa0
[14482.785578]  [<ffffffff815738c0>] cpuidle_enter_tk+0x10/0x20
[14482.785583]  [<ffffffff815734b5>] cpuidle_idle_call+0xa5/0x260
[14482.785591]  [<ffffffff8101d5ef>] cpu_idle+0xaf/0x120
[14482.785601]  [<ffffffff816b4fde>] start_secondary+0x1e0/0x1e5
[14482.785605] ---[ end trace d429973df979f5c7 ]---
[14482.785613] sky2 0000:06:00.0 eth0: tx timeout
[14482.785625] sky2 0000:06:00.0 eth0: transmit ring 10 .. 12 report=10 done=10
[14484.809628] sky2 0000:06:00.0 eth0: Link is up at 100 Mbps, full duplex, flow control both
```

---

