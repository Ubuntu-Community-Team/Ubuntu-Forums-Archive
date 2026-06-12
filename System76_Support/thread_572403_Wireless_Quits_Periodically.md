---
title: "Wireless Quits Periodically"
date: 2007-10-10
forum: System76 Support
---

### Post by AusIV4 on 2007-10-10
My gazelle value has run into a new problem recently.

When it boots up, the wireless connection works fine. If I'm using the AC adapter for power, it works continuously. However if I'm using running on battery, the wireless connection drops after about 15 minutes.

If I have the console open, I get the following error:

```

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:58 2007 ...
AusIVPortable kernel: [  485.092000] invalid opcode: 0000 [#1]

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:58 2007 ...
AusIVPortable kernel: [  485.092000] SMP 

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:58 2007 ...
AusIVPortable kernel: [  485.092000] CPU:    0

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:58 2007 ...
AusIVPortable kernel: [  485.092000] EIP:    
0060:[run_workqueue+238/320]    Tainted: P      VLI

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:58 2007 ...
AusIVPortable kernel: [  485.092000] EFLAGS: 00010286   
(2.6.20-16-generic #2)

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:58 2007 ...
AusIVPortable kernel: [  485.092000] EIP is at run_workqueue+0xee/0x140

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:58 2007 ...
AusIVPortable kernel: [  485.092000] eax: 00000300   ebx: dfb525cc   
ecx: 00000246   edx: 00000000

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:58 2007 ...
AusIVPortable kernel: [  485.092000] esi: dfb525c0   edi: dfb525c8   
ebp: 00000246   esp: f7899f58

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:58 2007 ...
AusIVPortable kernel: [  485.092000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:58 2007 ...
AusIVPortable kernel: [  485.092000] Process ipw3945/0 (pid: 3698, 
ti=f7898000 task=dfe34a90 task.ti=f7898000)

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:58 2007 ...
AusIVPortable kernel: [  485.092000] Stack: 00000000 dfb525d4 f7899f9c 
dfe34a90 dfb525cb dfb525e0 00000001 dfb525c0 

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:58 2007 ...
AusIVPortable kernel: [  485.092000]        dfb525cc dfb525d4 f7899f9c 
c0137d97 00000001 00000000 c1c01740 00010000 

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:59 2007 ...
AusIVPortable kernel: [  485.092000]        00000000 00000000 dfe34a90 
c0120b40 00100100 00200200 ffffffff ffffffff 

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:59 2007 ...
AusIVPortable kernel: [  485.092000] Call Trace:

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:59 2007 ...
AusIVPortable kernel: [  485.092000]  [worker_thread+327/368] 
worker_thread+0x147/0x170

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:59 2007 ...
AusIVPortable kernel: [  485.092000]  [default_wake_function+0/16] 
default_wake_function+0x0/0x10

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:59 2007 ...
AusIVPortable kernel: [  485.092000]  [worker_thread+0/368] 
worker_thread+0x0/0x170

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:59 2007 ...
AusIVPortable kernel: [  485.092000]  [kthread+186/240] 
kthread+0xba/0xf0

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:59 2007 ...
AusIVPortable kernel: [  485.092000]  [kthread+0/240] kthread+0x0/0xf0

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:59 2007 ...
AusIVPortable kernel: [  485.092000]  [kernel_thread_helper+7/16] 
kernel_thread_helper+0x7/0x10

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:59 2007 ...
AusIVPortable kernel: [  485.092000]  =======================

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:59 2007 ...
AusIVPortable kernel: [  485.092000] Code: 24 00 00 00 00 e8 f3 72 fe ff 
8b 44 24 10 3b 46 0c 0f 85 78 ff ff ff 83 6e 34 01 89 ea 83 c4 1c 89 f0 
5b 5e 5f 5d e9 a2 76 1b 00 <0f> 0b eb fe 65 a1 08 00 00 00 8b 90 a4 00 
00 00 05 94 01 00 00 

Message from syslogd@AusIVPortable at Tue Oct  9 11:07:59 2007 ...
AusIVPortable kernel: [  485.092000] EIP: [run_workqueue+238/320] 
run_workqueue+0xee/0x140 SS:ESP 0068:f7899f58

```

If I run iwlist scan, I get: 
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

```
Normally eth1 is my wireless device, but after this unknown event, it's as though Ubuntu thinks it's a wired device.

Has anyone run across this? The fact that it only happens on battery makes me wonder if it could be a hardware issue.

It's getting really annoying, because I can't use the internet for very long if I don't have the power cable with me.

---

### Post by tgalati4 on 2007-10-10
I sometimes get the same problem on an old Dell Inspiron 7500 with a pcmcia card.  When I pull the card, it's warm.  When I let it cool down it works fine.

I assume your wireless is built in.  It could be that running on battery causes a voltage drop which draws more current.  More current usually means more heat, so your wireless chip could be shutting down due to a heat issue.

From a terminal, post the output of:

>dmesg | tail -50

---

### Post by AusIV4 on 2007-10-10
> **tgalati4 said:**
> I sometimes get the same problem on an old Dell Inspiron 7500 with a pcmcia card.  When I pull the card, it's warm.  When I let it cool down it works fine.

I assume your wireless is built in.  It could be that running on battery causes a voltage drop which draws more current.  More current usually means more heat, so your wireless chip could be shutting down due to a heat issue.

From a terminal, post the output of:

>dmesg | tail -50

Will do next time this happens.

---

### Post by AusIV4 on 2007-10-13
dmesg: 

```
[   46.348000] vmnet8: no IPv6 routers present

[   46.608000] vmnet1: no IPv6 routers present

[   55.160000] NET: Registered protocol family 17

[   55.180000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

[   56.708000] ieee80211_crypt: registered algorithm 'CCMP'

[   57.600000] ieee80211_crypt: registered algorithm 'TKIP'

[   74.028000] eth1: no IPv6 routers present

[ 1554.464000] hdb: status timeout: status=0xd1 { Busy }

[ 1554.464000] ide: failed opcode was: unknown

[ 1554.464000] ipw3945: Microcode SW error detected.  Restarting.

[ 1554.464000] ipw3945: request scan called when driver not ready.

[ 1554.964000] ipw3945: Error sending ADD_STA: time out after 500ms.

[ 1554.964000] ipw3945: Can't stop Rx DMA.

[ 1554.976000] ------------[ cut here ]------------

[ 1554.976000] kernel BUG at kernel/workqueue.c:323!

[ 1554.976000] invalid opcode: 0000 [#1]

[ 1554.976000] SMP 

[ 1554.976000] Modules linked in: michael_mic arc4 ecb blkcipher ieee80211_crypt_tkip aes ieee80211_crypt_ccmp af_packet vmnet(P) vmmon(P) binfmt_misc rfcomm l2cap bluetooth ipv6 ppdev i915 drm cpufreq_ondemand cpufreq_stats cpufreq_userspace cpufreq_powersave freq_table cpufreq_conservative pcc_acpi sony_acpi dev_acpi tc1100_wmi ac sbs i2c_ec i2c_core battery dock asus_acpi backlight container button video sbp2 lp fuse snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm pcmcia snd_seq_dummy sdhci joydev snd_seq_oss mmc_core ipw3945 yenta_socket rsrc_nonstatic pcmcia_core ieee80211 ieee80211_crypt snd_seq_midi snd_rawmidi snd_seq_midi_event pcspkr snd_seq snd_timer snd_seq_device parport_pc parport iTCO_wdt iTCO_vendor_support snd soundcore snd_page_alloc intel_agp psmouse agpgart shpchp pci_hotplug serio_raw tsdev evdev ext3 jbd mbcache ide_cd cdrom ide_disk ata_generic libata scsi_mod r8169 ohci1394 ieee1394 generic ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap piix

[ 1554.976000] CPU:    0

[ 1554.976000] EIP:    0060:[<c013736e>]    Tainted: P      VLI

[ 1554.976000] EFLAGS: 00010292   (2.6.20-16-generic #2)

[ 1554.976000] EIP is at run_workqueue+0xee/0x140

[ 1554.976000] eax: 0000074c   ebx: f7808d4c   ecx: 00000246   edx: 00000000

[ 1554.976000] esi: f7808d40   edi: f7808d48   ebp: 00000246   esp: f7815f58

[ 1554.976000] ds: 007b   es: 007b   ss: 0068

[ 1554.976000] Process ipw3945/0 (pid: 3643, ti=f7814000 task=dfaa4560 task.ti=f7814000)

[ 1554.976000] Stack: 00000000 f780007b f780007b f78100d8 f7808d4b f7808d60 00000001 f7808d40 

[ 1554.976000]        f7808d4c f7808d54 f7815f9c c0137d97 00000001 00000000 c1bf9740 00010000 

[ 1554.976000]        00000000 00000000 dfaa4560 c0120b40 00100100 00200200 ffffffff ffffffff 

[ 1554.976000] Call Trace:

[ 1554.976000]  [<c0137d97>] worker_thread+0x147/0x170

[ 1554.976000]  [<c0120b40>] default_wake_function+0x0/0x10

[ 1554.976000]  [<c0137c50>] worker_thread+0x0/0x170

[ 1554.976000]  [<c013ac4a>] kthread+0xba/0xf0

[ 1554.976000]  [<c013ab90>] kthread+0x0/0xf0

[ 1554.976000]  [<c01044c7>] kernel_thread_helper+0x7/0x10

[ 1554.976000]  =======================

[ 1554.976000] Code: 24 00 00 00 00 e8 f3 72 fe ff 8b 44 24 10 3b 46 0c 0f 85 78 ff ff ff 83 6e 34 01 89 ea 83 c4 1c 89 f0 5b 5e 5f 5d e9 a2 76 1b 00 <0f> 0b eb fe 65 a1 08 00 00 00 8b 90 a4 00 00 00 05 94 01 00 00 

[ 1554.976000] EIP: [<c013736e>] run_workqueue+0xee/0x140 SS:ESP 0068:f7815f58

[ 1554.976000]  <7>bridge-eth1: disabling the bridge

[ 1564.292000] bridge-eth1: down

[ 1564.300000] ADDRCONF(NETDEV_UP): eth1: link is not ready

[ 1564.300000] bridge-eth1: enabling the bridge

[ 1564.300000] bridge-eth1: is a Wireless Adapter

[ 1564.300000] vmnet: You are trying to use wireless bridged networking together with

[ 1564.300000] vmnet: vmware-any-any-update.  This is not supported configuration, and

[ 1564.300000] vmnet: your wireless bridge will probably not work.

[ 1564.300000] bridge-eth1: up

[ 1580.468000] bridge-eth1: disabling the bridge

[ 1580.480000] bridge-eth1: down
```

---

### Post by thomasaaron on 2007-10-15
```
[ 1564.300000] vmnet: You are trying to use wireless bridged networking together with[ 1564.300000] vmnet: You are trying to use wireless bridged networking together with

[ 1564.300000] vmnet: vmware-any-any-update.  This is not supported configuration, and

[ 1564.300000] vmnet: your wireless bridge will probably not work.
```

That kind of looks like you have a virtual machine running at the same time which is configured as a bridged network. And this is conflicting with your non-vm wireless configuration.

While going to battery power shouldn't kill it, maybe it is a bug with vmware.

Try going to battery without a vm running.

---

### Post by AusIV4 on 2007-10-17
> **thomasaaron said:**
> That kind of looks like you have a virtual machine running at the same time which is configured as a bridged network. And this is conflicting with your non-vm wireless configuration.

While going to battery power shouldn't kill it, maybe it is a bug with vmware.

Try going to battery without a vm running.

VMWare server has some utilities that start automatically and map vmware network connections to connections on the machine. I had thought what we were seeing in dmesg was just the vmware devices complaining that the devices they were mapped to had disappeared.

However, I went ahead and disabled the VMWare startup process, and it's run for a solid 3 hours on battery without losing the connection. I'm not completely convinced, but it certainly looks encouraging.

---

### Post by thomasaaron on 2007-10-17
Excellent.

Keep me posted.

---

### Post by AusIV4 on 2007-10-19
Ran on battery for another 3 hours today, with no wireless drops. My schedule next week should have it running on battery for about 15 hours throughout the course of the week, if I have no drops by Friday, I'll be convinced that the bug is gone.

I'll update then (or sooner if I have a drop).

---

