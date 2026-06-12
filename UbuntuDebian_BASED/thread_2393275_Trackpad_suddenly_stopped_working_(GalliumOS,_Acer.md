---
title: "Trackpad suddenly stopped working (GalliumOS, Acer chromebook 14)"
date: 2018-06-01
forum: Ubuntu/Debian BASED
---

### Post by doxbox on 2018-06-01
My trackpad suddenly became unresponsive, I can't seem to figure out exactly why.
It looks like a Synaptic bug, but I am still relatively new to Linux and am not really sure what to do.

When I try dmesg this gets printed to the terminal:

```
...:1b.0/sound/card1/input10[    4.802901] kvm: disabled by bios
[    4.813098] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.818537] kvm: disabled by bios
[    4.837973] kvm: disabled by bios
[    4.839808] intel_rapl: Found RAPL domain package
[    4.839811] intel_rapl: Found RAPL domain core
[    4.840852] cht-bsw-rt5645 cht-bsw-rt5645: snd-soc-dummy-dai <-> media-cpu-dai mapping ok
[    4.840915] cht-bsw-rt5645 cht-bsw-rt5645: snd-soc-dummy-dai <-> deepbuffer-cpu-dai mapping ok
[    4.840954] compress asoc: snd-soc-dummy-dai <-> compress-cpu-dai mapping ok
[    4.842835] cht-bsw-rt5645 cht-bsw-rt5645: rt5645-aif1 <-> ssp2-port mapping ok
[    4.871940] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    4.910438] input: chtrt5650 Headset as /devices/platform/808622A8:00/cht-bsw-rt5645/sound/card0/input11
[    5.250008] i2c_designware 808622C1:05: controller timed out
[    5.250366] elan_i2c i2c-ELAN0000:00: writing cmd (0x0005) failed: -110
[    5.250438] elan_i2c i2c-ELAN0000:00: device reset failed: -110
[    5.250500] elan_i2c i2c-ELAN0000:00: device initialize failed: -110
[    6.155151] cgroup: new mount options do not match the existing superblock, will be ignored
[    6.225833] zram: Added device: zram0
[    6.280971] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.280975] Bluetooth: BNEP filters: protocol multicast
[    6.280984] Bluetooth: BNEP socket layer initialized
[    6.308072] zram0: detected capacity change from 0 to 6134771712
[    6.337979] i2c_designware 808622C1:05: controller timed out
[    6.338266] elan_i2c i2c-ELAN0000:00: writing cmd (0x0005) failed: -110
[    6.338273] elan_i2c i2c-ELAN0000:00: device reset failed: -110
[    6.338277] elan_i2c i2c-ELAN0000:00: device initialize failed: -110
[    6.355782] Adding 5990984k swap on /dev/zram0.  Priority:-1 extents:1 across:5990984k SSFS
[    6.641788] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    6.644201] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[    6.644449] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[    6.714202] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[    6.714466] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[    6.740410] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    6.899870] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    7.426039] i2c_designware 808622C1:05: controller timed out
[    7.426325] elan_i2c i2c-ELAN0000:00: writing cmd (0x0005) failed: -110
[    7.426330] elan_i2c i2c-ELAN0000:00: device reset failed: -110
[    7.426333] elan_i2c i2c-ELAN0000:00: device initialize failed: -110
[    7.467073] elan_i2c: probe of i2c-ELAN0000:00 failed with error -110
[   13.913973] wlp2s0: authenticate with 14:91:82:91:ce:30
[   13.921362] wlp2s0: send auth to 14:91:82:91:ce:30 (try 1/3)
[   13.925175] wlp2s0: authenticated
[   13.926755] wlp2s0: associate with 14:91:82:91:ce:30 (try 1/3)
[   13.932183] wlp2s0: RX AssocResp from 14:91:82:91:ce:30 (capab=0x1431 status=0 aid=3)
[   13.937592] wlp2s0: associated
[   13.937799] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[   13.951531] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 14:91:82:91:ce:30
...
```

Is there something wrong with the trackpad where its not sending firmware updates to the computer?
Is it a driver issue?

I am rather lost and have spent extensive time trying other solutions posted on here with no luck unfortunately.

I am using an Acer Chromebook 14 with GalliumOS.
I tried a hard reset, a powerwash, and factory reset desperately, but it didn't seem to make any difference.

I also made sure my synaptic package is up to date as well.


Any help or guidance is appreciated!! 
thanks.

---

### Post by jeremy31 on 2018-06-01
*Thread moved to **Ubuntu/Debian BASED**.*

---

