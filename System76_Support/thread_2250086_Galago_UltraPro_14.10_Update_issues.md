---
title: "Galago UltraPro 14.10 Update issues"
date: 2014-10-26
forum: System76 Support
---

### Post by moschops on 2014-10-26
I updated to 14.10 this week and have done the recommended update of the System76 sources.list, update system reboot but I'm still seeing some new problems.  I don't know if they are hardware specific or not, this is my only non-server Ubuntu system.

Here's what I'm seeing:

1. No 5Ghz Wifi - just refuses to connect where it used to with no problem. Same router on 2.4Ghz and it is fine.
2. Battery life display is inconsistent - just after I turn the machine on it reads 12 hours, sometimes that sticks around, then it is back to something more realistic but what I think is actually too low - says < 2 hours on a freshly charged battery with display dimmed down.  Granted it is a 1 year old battery now, but I used to get a reading of almost 3 hours fresh off charge before the update
3. Random video funkiness - on login with a remote Dell 30" LCD display that screen shows some weird blockiness and then reverts to normal (hard to describe without a picture, but it's vaguely cubist).  Sometimes while or after playing video I'll be left with flashing bands either side of the web browser (Chrome) window that persist until I move another window over them.

and this one isn't new but I was hoping it would be fixed since the new kernel allegedly had some Synaptics touchpad fixes.

4. Touchpad still doesn't support palm detection.  I've seen this listed as a feature of the hardware but no setting I can find either advertised or behind the scenes will make it work.  

My feeling is 1 and 2 may be driver related.  4 - Ilive in hope.  3 is probably some Ubuntu wide Intel integrated video external monitor support/HDMI glitch... I hope.

Just thought I would put these out there in case any other people are seeing them or someone has some suggestions.

---

### Post by vinnywright on 2014-10-26
did you actually install the driver's from system76 or just add the PPA and update the packages available list?

you will half to manually install them. 

hear is the system76 upgrade guide page .
[http://knowledge76.com/index.php/Version_Upgrade](http://knowledge76.com/index.php/Version_Upgrade)

VINNY

---

### Post by moschops on 2014-10-31
Yes I did install:

$ dpkg --list | grep system76
ii  system76-driver                                             14.10.1                                                all          Universal driver for System76 computers

ii == installed.

Battery indicator seems to have settled down, maybe it had to relearn the battery capacity?

5Ghz Wifi is still dead to the world.  Here is the output I got when trying to connect to it...

> Oct 30 22:29:47 oscar2 dnsmasq[4755]: setting upstream servers from DBus
Oct 30 22:29:47 oscar2 kernel: [59049.238117] cfg80211: Calling CRDA to update world regulatory domain
Oct 30 22:29:47 oscar2 kernel: [59049.249848] cfg80211: World regulatory domain updated:
Oct 30 22:29:47 oscar2 kernel: [59049.249851] cfg80211:  DFS Master region: unset
Oct 30 22:29:47 oscar2 kernel: [59049.249851] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Oct 30 22:29:47 oscar2 kernel: [59049.249853] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct 30 22:29:47 oscar2 kernel: [59049.249854] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct 30 22:29:47 oscar2 kernel: [59049.249856] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct 30 22:29:47 oscar2 kernel: [59049.249857] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct 30 22:29:47 oscar2 kernel: [59049.249858] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> NetworkManager state is now DISCONNECTED
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Activation (wlan0) starting connection 'Heart Of Platinum'
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> NetworkManager state is now CONNECTING
Oct 30 22:29:47 oscar2 dbus[1172]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <warn> Connection disconnected (reason -3)
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> (wlan0): supplicant interface state: completed -> disconnected
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <warn> Connection disconnected (reason -3)
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Activation (wlan0/wireless): access point 'Heart Of Platinum' has security, but secrets are required.
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Activation (wlan0/wireless): connection 'Heart Of Platinum' has security, and secrets exist.  No new secrets needed.
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Config: added 'ssid' value 'Heart Of Platinum'
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Config: added 'scan_ssid' value '1'
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Config: added 'auth_alg' value 'OPEN'
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Config: added 'psk' value '<omitted>'
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 30 22:29:47 oscar2 dbus[1172]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 30 22:29:47 oscar2 wpa_supplicant[2371]: wlan0: CTRL-EVENT-SCAN-STARTED 
Oct 30 22:29:47 oscar2 NetworkManager[1334]: <info> Config: set interface ap_scan to 1
Oct 30 22:29:49 oscar2 ntpd[30781]: Deleting interface #3 wlan0, 10.0.0.22#123, interface stats: received=2, sent=5, dropped=0, active_time=10 secs
Oct 30 22:29:49 oscar2 ntpd[30781]: 91.189.94.4 interface 10.0.0.22 -> (none)
Oct 30 22:29:49 oscar2 ntpd[30781]: 204.2.134.164 interface 10.0.0.22 -> (none)
Oct 30 22:29:49 oscar2 ntpd[30781]: 54.235.96.196 interface 10.0.0.22 -> (none)
Oct 30 22:29:49 oscar2 ntpd[30781]: 107.170.242.27 interface 10.0.0.22 -> (none)
Oct 30 22:29:49 oscar2 ntpd[30781]: 216.66.0.142 interface 10.0.0.22 -> (none)
Oct 30 22:29:49 oscar2 ntpd[30781]: peers refreshed
Oct 30 22:29:50 oscar2 wpa_supplicant[2371]: wlan0: SME: Trying to authenticate with 90:94:e4:2a:55:72 (SSID='Heart Of Platinum' freq=5220 MHz)
Oct 30 22:29:50 oscar2 kernel: [59052.222985] wlan0: authenticate with 90:94:e4:2a:55:72
Oct 30 22:29:50 oscar2 kernel: [59052.226928] wlan0: send auth to 90:94:e4:2a:55:72 (try 1/3)
Oct 30 22:29:50 oscar2 NetworkManager[1334]: <info> (wlan0): supplicant interface state: disconnected -> authenticating
Oct 30 22:29:50 oscar2 wpa_supplicant[2371]: wlan0: Trying to associate with 90:94:e4:2a:55:72 (SSID='Heart Of Platinum' freq=5220 MHz)
Oct 30 22:29:50 oscar2 kernel: [59052.238700] wlan0: authenticated
Oct 30 22:29:50 oscar2 kernel: [59052.239973] wlan0: associate with 90:94:e4:2a:55:72 (try 1/3)
Oct 30 22:29:50 oscar2 wpa_supplicant[2371]: wlan0: Associated with 90:94:e4:2a:55:72
Oct 30 22:29:50 oscar2 kernel: [59052.240756] wlan0: RX AssocResp from 90:94:e4:2a:55:72 (capab=0x11 status=0 aid=1)
Oct 30 22:29:50 oscar2 kernel: [59052.242356] wlan0: associated
Oct 30 22:29:50 oscar2 NetworkManager[1334]: <info> (wlan0): supplicant interface state: authenticating -> associated
Oct 30 22:29:50 oscar2 wpa_supplicant[2371]: wlan0: WPA: Key negotiation completed with 90:94:e4:2a:55:72 [PTK=CCMP GTK=TKIP]
Oct 30 22:29:50 oscar2 wpa_supplicant[2371]: wlan0: CTRL-EVENT-CONNECTED - Connection to 90:94:e4:2a:55:72 completed [id=0 id_str=]
Oct 30 22:29:50 oscar2 NetworkManager[1334]: <info> (wlan0): supplicant interface state: associated -> completed
Oct 30 22:29:50 oscar2 NetworkManager[1334]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Heart Of Platinum'.
Oct 30 22:29:50 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 30 22:29:50 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Oct 30 22:29:50 oscar2 NetworkManager[1334]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 30 22:29:50 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 30 22:29:50 oscar2 NetworkManager[1334]: <info> dhclient started with pid 30818
Oct 30 22:29:50 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Beginning IP6 addrconf.
Oct 30 22:29:50 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct 30 22:29:50 oscar2 dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct 30 22:29:50 oscar2 dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct 30 22:29:50 oscar2 dhclient: All rights reserved.
Oct 30 22:29:50 oscar2 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Oct 30 22:29:50 oscar2 dhclient: 
Oct 30 22:29:50 oscar2 NetworkManager[1334]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct 30 22:29:50 oscar2 dhclient: Listening on LPF/wlan0/b4:b6:76:a0:18:f1
Oct 30 22:29:50 oscar2 dhclient: Sending on   LPF/wlan0/b4:b6:76:a0:18:f1
Oct 30 22:29:50 oscar2 dhclient: Sending on   Socket/fallback
Oct 30 22:29:50 oscar2 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x2fd9f8da)
Oct 30 22:29:52 oscar2 ntpd[30781]: Deleting interface #6 wlan0, fe80::b6b6:76ff:fea0:18f1#123, interface stats: received=0, sent=0, dropped=0, active_time=13 secs
Oct 30 22:29:52 oscar2 ntpd[30781]: peers refreshed
Oct 30 22:29:53 oscar2 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 (xid=0x2fd9f8da)
Oct 30 22:29:54 oscar2 ntpd[30781]: Listen normally on 7 wlan0 fe80::b6b6:76ff:fea0:18f1 UDP 123
Oct 30 22:29:54 oscar2 ntpd[30781]: peers refreshed
Oct 30 22:29:54 oscar2 ntpd[30781]: new interface(s) found: waking up resolver
Oct 30 22:29:59 oscar2 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x2fd9f8da)
Oct 30 22:30:08 oscar2 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19 (xid=0x2fd9f8da)
Oct 30 22:30:10 oscar2 NetworkManager[1334]: <info> (wlan0): IP6 addrconf timed out or failed.
Oct 30 22:30:10 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct 30 22:30:10 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct 30 22:30:10 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct 30 22:30:27 oscar2 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x2fd9f8da)
Oct 30 22:30:35 oscar2 NetworkManager[1334]: <warn> (wlan0): DHCPv4 request timed out.
Oct 30 22:30:35 oscar2 NetworkManager[1334]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 30818
Oct 30 22:30:35 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Oct 30 22:30:35 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Oct 30 22:30:35 oscar2 NetworkManager[1334]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct 30 22:30:35 oscar2 NetworkManager[1334]: <info> NetworkManager state is now DISCONNECTED
Oct 30 22:30:35 oscar2 NetworkManager[1334]: <warn> Activation (wlan0) failed for connection 'Heart Of Platinum'
Oct 30 22:30:35 oscar2 NetworkManager[1334]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Oct 30 22:30:35 oscar2 NetworkManager[1334]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct 30 22:30:35 oscar2 NetworkManager[1334]: <info> (wlan0): deactivating device (reason 'none') [0]
Oct 30 22:30:35 oscar2 kernel: [59097.530902] wlan0: deauthenticating from 90:94:e4:2a:55:72 by local choice (Reason: 3=DEAUTH_LEAVING)
Oct 30 22:30:35 oscar2 wpa_supplicant[2371]: wlan0: CTRL-EVENT-DISCONNECTED bssid=90:94:e4:2a:55:72 reason=3 locally_generated=1
Oct 30 22:30:35 oscar2 NetworkManager[1334]: <warn> Connection disconnected (reason -3)
Oct 30 22:30:35 oscar2 NetworkManager[1334]: <info> (wlan0): supplicant interface state: completed -> disconnected
Oct 30 22:30:35 oscar2 wpa_supplicant[2371]: wlan0: CTRL-EVENT-SCAN-STARTED 
Oct 30 22:30:35 oscar2 kernel: [59097.541404] cfg80211: Calling CRDA to update world regulatory domain
Oct 30 22:30:35 oscar2 NetworkManager[1334]: <warn> Connection disconnected (reason -3)


---

