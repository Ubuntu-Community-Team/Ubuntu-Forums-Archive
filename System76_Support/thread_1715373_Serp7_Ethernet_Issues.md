---
title: "Serp7 Ethernet Issues"
date: 2011-03-26
forum: System76 Support
---

### Post by koenigjm on 2011-03-26
I just got my new serval pro yesterday and I have noticed the ethernet port is not functioning.  Occasionally it is able to obtain an IP address but usually it just fails all together.  When eth0 does have a valid IP it cannot sustain any communication, whether on my local network or outside.  I have isolated the failure to my serval, as other computers are able to connect with the same router port and cable that I tested my serval with.  

Has anyone else noticed this issue?  Any known fixes? 

I had a similar issues with my previous system76 (gen 1 Lemur).  The problem then was the BIOS overflowing into the MAC address.  I haven't noticed the MAC address change yet and the ethernet port (so far) has always enumerated as eth0. 

What data can I provide to help further troubleshoot this issue?

---

### Post by koenigjm on 2011-03-27
Below is the only interesting log data I have been able to find so far.  dmesg and /var/log/messages don't report anything overly interesting. 

```
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> Activation (eth0) starting connection 'Auto eth0'
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> dhclient started with pid 2616
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Mar 27 08:41:36 shadow dhclient: Internet Systems Consortium DHCP Client V3.1.3
Mar 27 08:41:36 shadow dhclient: Copyright 2004-2009 Internet Systems Consortium.
Mar 27 08:41:36 shadow dhclient: All rights reserved.
Mar 27 08:41:36 shadow dhclient: For info, please visit https://www.isc.org/software/dhcp/
Mar 27 08:41:36 shadow dhclient: 
Mar 27 08:41:36 shadow NetworkManager[1218]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Mar 27 08:41:36 shadow dhclient: Listening on LPF/eth0/00:90:f5:b6:55:8f
Mar 27 08:41:36 shadow dhclient: Sending on   LPF/eth0/00:90:f5:b6:55:8f
Mar 27 08:41:36 shadow dhclient: Sending on   Socket/fallback
Mar 27 08:41:36 shadow dhclient: DHCPREQUEST of 192.168.1.104 on eth0 to 255.255.255.255 port 67
Mar 27 08:41:53 shadow dhclient: last message repeated 2 times
Mar 27 08:41:53 shadow vmnetBridge: Removing interface eth0 index:2
Mar 27 08:41:53 shadow NetworkManager[1218]: <info> (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 27 08:41:55 shadow dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Mar 27 08:41:56 shadow vmnetBridge: Adding interface eth0 index:2
Mar 27 08:41:56 shadow NetworkManager[1218]: <info> (eth0): carrier now ON (device state 7)
Mar 27 08:41:58 shadow dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Mar 27 08:42:05 shadow dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Mar 27 08:42:11 shadow vmnetBridge: Removing interface eth0 index:2
Mar 27 08:42:11 shadow NetworkManager[1218]: <info> (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Mar 27 08:42:14 shadow vmnetBridge: Adding interface eth0 index:2
Mar 27 08:42:14 shadow NetworkManager[1218]: <info> (eth0): carrier now ON (device state 7)
Mar 27 08:42:17 shadow dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Mar 27 08:42:21 shadow NetworkManager[1218]: <warn> (eth0): DHCPv4 request timed out.
Mar 27 08:42:21 shadow NetworkManager[1218]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2616
Mar 27 08:42:21 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Mar 27 08:42:21 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Mar 27 08:42:21 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar 27 08:42:21 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Mar 27 08:42:21 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Mar 27 08:42:21 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Mar 27 08:42:21 shadow NetworkManager[1218]: <info> (eth0): device state change: 7 -> 9 (reason 5)
Mar 27 08:42:21 shadow NetworkManager[1218]: <info> Marking connection 'Auto eth0' invalid.
Mar 27 08:42:21 shadow NetworkManager[1218]: <warn> Activation (eth0) failed.
Mar 27 08:42:21 shadow NetworkManager[1218]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 27 08:42:21 shadow NetworkManager[1218]: <info> (eth0): device state change: 9 -> 3 (reason 0)
Mar 27 08:42:21 shadow NetworkManager[1218]: <info> (eth0): deactivating device (reason: 0).
```

---

### Post by nevius on 2011-03-27
Burn an ubuntu live CD and see if the problem occurs in a live session.

---

### Post by koenigjm on 2011-03-27
I will try the live session later tonight.

This morning I tried setting a static IP (via network manager) appropriate for my home network and I was unable to even ping the gateway.

---

### Post by koenigjm on 2011-03-28
Wired connection works as expected in the live CD environment (same network as before, my home network).

System76, any thoughts?  I have updated the latest Ubuntu stack and made sure to reinstall the system76 drivers afterwards.  Have I missed something?

---

### Post by koenigjm on 2011-03-28
Seems that are having similar issues with JMicron and its current driver version 1.0.7.1:

[http://forums.fedoraforum.org/showthread.php?t=258574]("http://forums.fedoraforum.org/showthread.php?t=258574")

I have tried the current driver version and still no luck:

[http://bbs.cooldavid.org/git/?p=jme.git]("http://bbs.cooldavid.org/git/?p=jme.git")

---

### Post by koenigjm on 2011-03-28
Well..while I am flooding this thread.  I captured the following dmesg output using the stock System76 jme version (1.06) at the time eth0 became inoperable:

> [  281.163501] ------------[ cut here ]------------
[  281.163524] WARNING: at /build/buildd/linux-2.6.35/net/sched/sch_generic.c:258 dev_watchdog+0x25f/0x270()
[  281.163530] Hardware name: Serval Professional
[  281.163534] NETDEV WATCHDOG: eth0 (jme): transmit queue 0 timed out
[  281.163538] Modules linked in: aesni_intel cryptd aes_x86_64 aes_generic dm_crypt snd_hda_codec_nvhdmi binfmt_misc ppdev parport_pc joydev snd_hda_codec_realtek nvidia(P) snd_hda_intel arc4 snd_hda_codec snd_hwdep snd_pcm iwlagn uvcvideo snd_seq_midi snd_rawmidi snd_seq_midi_event videodev snd_seq v4l1_compat v4l2_compat_ioctl32 snd_timer snd_seq_device iwlcore mac80211 snd lp parport cfg80211 psmouse xhci_hcd soundcore snd_page_alloc serio_raw dm_raid45 xor firewire_ohci sdhci_pci firewire_core sdhci ahci libahci led_class jme crc_itu_t mii video output intel_agp
[  281.163623] Pid: 0, comm: swapper Tainted: P            2.6.35-28-generic #49-Ubuntu
[  281.163628] Call Trace:
[  281.163632]  <IRQ>  [<ffffffff81060b7f>] warn_slowpath_common+0x7f/0xc0
[  281.163652]  [<ffffffff81060c76>] warn_slowpath_fmt+0x46/0x50
[  281.163662]  [<ffffffff814b894f>] dev_watchdog+0x25f/0x270
[  281.163673]  [<ffffffff8107af8e>] ? insert_work+0x7e/0xd0
[  281.163684]  [<ffffffff81011923>] ? native_sched_clock+0x13/0x60
[  281.163693]  [<ffffffff814b86f0>] ? dev_watchdog+0x0/0x270
[  281.163702]  [<ffffffff814b86f0>] ? dev_watchdog+0x0/0x270
[  281.163711]  [<ffffffff8106f862>] call_timer_fn+0x42/0x120
[  281.163718]  [<ffffffff8105d4f0>] ? scheduler_tick+0x140/0x2d0
[  281.163727]  [<ffffffff814b86f0>] ? dev_watchdog+0x0/0x270
[  281.163736]  [<ffffffff81070e24>] run_timer_softirq+0x154/0x270
[  281.163746]  [<ffffffff8102fb67>] ? native_apic_msr_write+0x37/0x40
[  281.163753]  [<ffffffff81067b99>] __do_softirq+0xb9/0x1f0
[  281.163763]  [<ffffffff8108f38a>] ? tick_program_event+0x2a/0x30
[  281.163771]  [<ffffffff8100afdc>] call_softirq+0x1c/0x30
[  281.163778]  [<ffffffff8100cab5>] do_softirq+0x65/0xa0
[  281.163785]  [<ffffffff81067a55>] irq_exit+0x85/0x90
[  281.163793]  [<ffffffff81592d60>] smp_apic_timer_interrupt+0x70/0x9b
[  281.163800]  [<ffffffff8100aa93>] apic_timer_interrupt+0x13/0x20
[  281.163804]  <EOI>  [<ffffffff8130a4c4>] ? intel_idle+0xe4/0x180
[  281.163821]  [<ffffffff8130a4a7>] ? intel_idle+0xc7/0x180
[  281.163832]  [<ffffffff81472d32>] cpuidle_idle_call+0x92/0x140
[  281.163841]  [<ffffffff81008da3>] cpu_idle+0xb3/0x110
[  281.163851]  [<ffffffff815853d5>] start_secondary+0x100/0x102
[  281.163857] ---[ end trace 24f73af835458a4c ]---
[  281.174222] jme: Disable RX engine timeout.
[  281.184258] jme: Disable TX engine timeout.
[  281.184952] jme 0000:03:00.0: eth0: Link is down.
[  283.821828] jme 0000:03:00.0: eth0: Link is up at ANed: 1000 Mbps, Full-Duplex, MDI-X.

From this point forward eth0 can no longer obtain an IP address or communicate over a wired connection in any meaningful way.

---

### Post by thomasaaron on 2011-03-29
OK, this does look like a hardware issue, and we've not seen it on other Servals. We received your tech support form entry.

---

