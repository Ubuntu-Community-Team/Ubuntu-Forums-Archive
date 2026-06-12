---
title: "No wifi on gazp7"
date: 2012-08-16
forum: System76 Support
---

### Post by Ryan Dwyer on 2012-08-16
Hi,

I received my gazp7 today and am unable to use wifi. The Network Manager applet shows only my wired connection. There is no heading in the menu for wireless connections. Pressing Fn + F11 to toggle wifi does nothing.

I soon noticed many of my /var/log files had incorrect owners (eg.  syslog was owned by messagebus instead of syslog). The syslog was empty as a result, so I reinstalled with a fresh copy of 12.04. The fresh install has the same wifi problems as before.

I've installed all the updates. There are no additional drivers.

Note that this is a 64 bit system.

ryan@laptop:~$ **sudo lshw -C network**
  *-network UNCLAIMED     
       description: Network controller
       product: Centrino Wireless-N 1030
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 1a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7d00000-f7d01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:03:00.2
       logical name: eth0
       version: 0a
       serial: 00:90:f5:d3:b0:0d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=10.0.0.109 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

ryan@laptop:~$ **sudo lspci -v**
...snip...
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 1a)
	Subsystem: Intel Corporation Device 0000
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at f7d00000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 00-00-00-ff-ff-00-00-00
...snip...

ryan@laptop:~$ **uname -a**
Linux laptop 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

ryan@laptop:~$ **lsmod**
Module                  Size  Used by
btusb                  18288  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_via      51398  1 
joydev                 17693  0 
rfcomm                 47604  0 
parport_pc             32866  0 
bnep                   18281  2 
bluetooth             180104  11 btusb,rfcomm,bnep
ppdev                  17113  0 
rts_bpp               353165  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
psmouse                87692  0 
v4l2_compat_ioctl32    17128  1 videodev
serio_raw              13211  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
i915                  472941  3 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
wmi                    19256  0 
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 

ryan@laptop:~$ rfkill list all
(no output)

ifconfig lists only eth0 (wired) and lo.

The driver it uses is apparently iwlwifi, which isn't loaded on boot. If I load it with modprobe it seems to have no effect (except for appearing in lsmod, of course).

ryan@laptop:~$ sudo modprobe iwlwifi
ryan@laptop:~$ lsmod | grep iwl
iwlwifi               332525  0 
mac80211              506816  1 iwlwifi
cfg80211              205544  2 iwlwifi,mac80211
ryan@laptop:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 3036
ryan@laptop:~$ grep iwl /var/log/syslog
ryan@laptop:~$ grep wifi /var/log/syslog
ryan@laptop:~$ dmesg | grep iwl
ryan@laptop:~$ dmesg | grep wifi

I'm considering trying older versions of Ubuntu in a live environment to see if I can get it working. Even if I can, I'd like to get it working with 12.04.

The hardware is certified:
[http://www.ubuntu.com/certification/catalog/component/pci:8086:008A-WIRELESS/](http://www.ubuntu.com/certification/catalog/component/pci:8086:008A-WIRELESS/)

Any ideas?

---

### Post by isantop on 2012-08-16
> **Ryan Dwyer said:**
> Hi,

I received my gazp7 today and am unable to use wifi. The Network Manager applet shows only my wired connection. There is no heading in the menu for wireless connections. Pressing Fn + F11 to toggle wifi does nothing.

I'm considering trying older versions of Ubuntu in a live environment to see if I can get it working. Even if I can, I'd like to get it working with 12.04.

The hardware is certified:
[http://www.ubuntu.com/certification/catalog/component/pci:8086:008A-WIRELESS/](http://www.ubuntu.com/certification/catalog/component/pci:8086:008A-WIRELESS/)

Any ideas?

If you're having the same problem in both installations, then it's likely either the card was bumped loose during shipping or it's a dud card. Either way, we can get you taken care of. Go ahead and open a ticket on our website and we'll get everything taken care of there.

---

### Post by Ryan Dwyer on 2012-09-04
Sorry for bumping, but I'm not a fan of leaving threads without explaining how the issue was resolved (*cough* [http://xkcd.com/979/](http://xkcd.com/979/)).

It was a dud card. I got a new one and it works fine.

---

### Post by cprofitt on 2012-09-04
Awesome to see System76 give such great support... Did they just send you the part?

---

### Post by Ryan Dwyer on 2012-09-05
Sort of. I'm in Australia so it wasn't as simple as a standard warranty replacement. The cost for me to ship the dud wifi card back is more than the cost of buying a new one so I just bought a new one from System76. I was going to buy locally but the few sites I checked don't have that particular card or similar ones. Plus I didn't feel like spending much effort looking for local stores that sell it.

Even though it sucks having to buy a new component, that's understandable considering I'm international. Their support was great. Due to the timezone difference I wasn't awake/able to reply during their business hours so they always replied within their next business day. I would easily buy from them again.

---

