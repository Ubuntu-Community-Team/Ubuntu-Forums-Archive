---
title: "intel 4965abgn wireless + 10.04 = help please!"
date: 2010-08-15
forum: Server Platforms
---

### Post by Avraham0 on 2010-08-15
hi

i'm trying to replace my router with an ubuntu box, but i can't get my wireless card to work!
posting some outputs about the problem!

(its an Intel 4965ABGN card, seems like i'm using the newest firmware version according to [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/))

```
root@gsejt:~# iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"valami"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```

```
root@gsejt:~# iwlist wlan0 scan
wlan0     No scan results
```

```
root@gsejt:~# lspci -v
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Device 1102
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at dfc00000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number d1-98-66-ff-ff-3b-1f-00
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn
```

```
root@gsejt:~# dmesg | grep wlan0
[   11.919801] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.348766] device wlan0 entered promiscuous mode
```

```
root@gsejt:~# dmesg | grep iwlagn
[   11.115574] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   11.115584] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   11.115707] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.115722] iwlagn 0000:02:00.0: setting latency timer to 64
[   11.115777] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   11.157569] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 4 802.11a channels
[   11.157673] iwlagn 0000:02:00.0: irq 29 for MSI/MSI-X
[   11.444769] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   11.537477] iwlagn 0000:02:00.0: loaded firmware version 228.61.2.24
```

in my interfaces file i have:

```
iface wlan0 inet manual
wireless-mode master
wireless-essid valami
wireless-channel 1
```

any help appreciated, i'm struggling with this problems for days now.. :confused:

thank you!

---

