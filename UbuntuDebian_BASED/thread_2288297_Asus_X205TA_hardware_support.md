---
title: "Asus X205TA hardware support"
date: 2015-07-21
forum: Ubuntu/Debian BASED
---

### Post by raviarya on 2015-07-21
FYI: I tried Sparky Linux 32bit as it could be installed directly on X205TA. Surprisingly I never had random freezing with it. I ran it for 30-40 hours and everything was fine.
It came with Kernel 4+ so I directly applied patches for internal wifi card as described on [https://wiki.debian.org/InstallingDebianOn/Asus/X205TA](https://wiki.debian.org/InstallingDebianOn/Asus/X205TA)

Download links:
[http://sparkylinux.org/download/](http://sparkylinux.org/download/)



> **Cpbee said:**
> Add-on: I quickly looked into the syslog and kern.log and see repeated errors for the wlan card.

```
Jul 20 10:38:59 Mantisshrimp kernel: [  323.973118] brcmf_cfg80211_escan: Connecting: status (7)
Jul 20 10:38:59 Mantisshrimp kernel: [  323.973134] brcmf_cfg80211_scan: scan error (-11)
Jul 20 10:40:59 Mantisshrimp kernel: [  443.937486] brcmf_cfg80211_escan: Connecting: status (7)
Jul 20 10:40:59 Mantisshrimp kernel: [  443.937510] brcmf_cfg80211_scan: scan error (-11)

Jul 20 10:32:59 Mantisshrimp kernel: [    8.505130] brcmf_sdio_bus_rxctl: resumed on timeoutJul 20 10:32:59 Mantisshrimp kernel: [    8.505142] brcmf_c_preinit_dcmds: Retreiving cur_etheraddr failed, -52
Jul 20 10:32:59 Mantisshrimp kernel: [    8.505147] brcmf_bus_start: failed: -52
Jul 20 10:32:59 Mantisshrimp kernel: [    8.505158] brcmf_sdio_firmware_callback: dongle is not responding
**Jul 20 10:32:59 Mantisshrimp kernel: [    8.518086] brcmf_sdio_dpc: failed backplane access over SDIO, halting operation**

Crash here!

```


Someone any idea what settings do affect this? Could this be the reason for the random freezes?

---

### Post by john_smith16 on 2015-07-25
I am able to load Live SparkyLinux on USB. I understand WiFi needs some tinkering, how about audio? Does it work for anyone?

---

