---
title: "Slow boot after enabling WiFi connection"
date: 2014-07-25
forum: Server Platforms
---

### Post by ljbade2 on 2014-07-25
I am setting up a fresh install of new server.

It was booting quickly (less than 30 seconds) before, but now if takes much longer.

It happened after configuring the WiFi.

Basically:
[LIST=1]
[*]Install 14.04 Server from USB with OpenSSH
[*]Log on
[*]Set static IP on Ethernet in interfaces config
[*]Reboot
[*]SSH into server
[*]Install linux-firmware package
[*]Reboot
[*]Enable WiFi in interfaces config
[*]Reboot
[/LIST]

The hardware:
Mobo: Asus H81M-E with BIOS 2001
CPU: Intel Celeron G1840T
RAM: 2x2GB DDR3 Patriot
HDD: WD Red 1TB
WiFi: Intel Wireless 7620

My /etc/interfaces:
```
auto loiface lo inet loopback


auto p3p1
iface p3p1 inet static
address 192.168.20.200
netmask 255.255.255.0
gateway 192.168.20.1
dns-nameservers 192.168.20.1


auto wlan0
iface wlan0 inet static
wpa-ssid blah
wpa-psk blah
address 192.168.20.210
netmask 255.255.255.0
gateway 192.168.20.1
dns-nameservers 192.168.20.1

```

The last of dmesg:
```
[   16.490340] Intel(R) Wireless WiFi driver for Linux, in-tree:[   16.490342] Copyright(c) 2003-2013 Intel Corporation
[   16.490383] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[   16.490522] iwlwifi 0000:02:00.0: irq 50 for MSI/MSI-X
[   16.579548] r8169 0000:03:00.0 p3p1: link down
[   16.579566] r8169 0000:03:00.0 p3p1: link down
[   16.579606] IPv6: ADDRCONF(NETDEV_UP): p3p1: link is not ready
[   16.636444] cfg80211: World regulatory domain updated:
[   16.636447] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.636448] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.636449] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.636450] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.636451] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.636452] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.738985] iwlwifi 0000:02:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[   16.917567] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   17.147254] EXT4-fs (sda2): mounting ext2 file system using the ext4 subsystem
[   17.149160] EXT4-fs (sda2): mounted filesystem without journal. Opts: (null)
[   17.265685] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   17.265753] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   17.266003] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   17.485610] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   17.851100] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   17.984875] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   17.985108] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   17.996612] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.264122] r8169 0000:03:00.0 p3p1: link up
[   18.264129] IPv6: ADDRCONF(NETDEV_CHANGE): p3p1: link becomes ready
[   22.015854] wlan0: authenticate with 00:60:64:4d:38:c8
[   22.016927] wlan0: No basic rates, using min rate instead
[   22.017973] wlan0: send auth to 00:60:64:4d:38:c8 (try 1/3)
[   22.019846] wlan0: authenticated
[   22.019964] wlan0: associate with 00:60:64:4d:38:c8 (try 1/3)
[   22.025169] wlan0: RX AssocResp from 00:60:64:4d:38:c8 (capab=0x431 status=0 aid=4)
[   22.028118] wlan0: associated
[   22.028131] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   22.028158] cfg80211: Calling CRDA for country: TW
[   22.030385] cfg80211: Regulatory domain changed to country: TW
[   22.030387] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.030389] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   22.030390] cfg80211:   (5270000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   22.030391] cfg80211:   (5735000 KHz - 5815000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  137.691602] audit_printk_skb: 6 callbacks suppressed
[  137.691605] type=1400 audit(1406283842.974:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=940 comm="apparmor_parser"
[  137.691610] type=1400 audit(1406283842.974:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=940 comm="apparmor_parser"
[  137.691613] type=1400 audit(1406283842.974:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=940 comm="apparmor_parser"
[  137.691906] type=1400 audit(1406283842.974:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=940 comm="apparmor_parser"
[  137.691909] type=1400 audit(1406283842.974:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=940 comm="apparmor_parser"
[  137.692060] type=1400 audit(1406283842.974:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=940 comm="apparmor_parser"
[  137.711976] type=1400 audit(1406283842.994:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=942 comm="apparmor_parser"
```

Any idea what the sudden jump from 22 to 137 seconds is?

---

### Post by ljbade2 on 2014-07-25
Seems to be caused by having both Ethernet and WiFi at the same time.

So I disabled Ethernet from the file and it now boots much faster.

---

### Post by ljbade2 on 2014-07-25
Also I have discovered that 802.11n support in current Ubuntu 14.04 is *very* broken. It is laggy, slow and disconnects a lot: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1293569](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1293569)

Have to use "options iwlwifi 11n_disable=1" in /etc/modprobe.d/iwlwifi.conf to get a good connection.

---

### Post by TheFu on 2014-07-25
Having multiple interfaces on the same subnet is confusing to the network stack - if you want to troubleshoot this further, please post the output from **route** when both interfaces are active.  If you can, I'd have the wifi on a different subnet, then the confusion will be solved.

I have an issue with slow boot times regardless of whether it is wifi or ethernet connected on my netbook.  I think it is because the ethernet port is on the end of a USB3 adapter (the netbook doesn't have wired ethernet) and wasn't designed/tested to run Ubuntu/Linux.

---

### Post by ljbade2 on 2014-07-26
I see, yeah I guess it doesn't make sense.

I don't actually need both Ethernet and WiFi, it was more a temporary thing to connect to the server to configure the WiFi.

Now that it is working fine on WiFi (with 11n disabled) I think I will just leave the Ethernet unplugged.

---

### Post by TheFu on 2014-07-26
So ... solved or what?

---

