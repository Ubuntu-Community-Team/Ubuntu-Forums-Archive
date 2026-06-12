---
title: "unstable wireless after .20 kernel update"
date: 2014-03-29
forum: Ubuntu Development Version
---

### Post by NZjelle on 2014-03-29
I'm wondering if I am the only one suffering from this. I'm going nuts because my wireless keeps disconnecting after the last .20 update of the 3.13 kernel. It reconnects itself after a while, but it is annoying. I have been running the alpha of Xubuntu 14.04 since January and among the things that I liked was that its wireless was rock solid. In fact, overall I find that 14.04 is more solid even now than 13.10.

Anyway, I can provide much more info, log files and other stuff, but I first want to know if it's only me.

---

### Post by NZjelle on 2014-03-30
Update: it's not the kernel. I have added the 3.14-rc8 kernel and also tried it while reverting back to the .19 kernel. Problem is the same in all cases. I can briefly connect my wireless, and after a few minutes it disconnects itself. So something else in the configuration somewhere must have changed. Following are extracts from the syslog

```
Mar 30 15:23:12 ZARX1404 wpa_supplicant[969]: wlan0: CTRL-EVENT-SSID-REENABLED id=0 ssid="Thuis9F"
Mar 30 15:23:12 ZARX1404 wpa_supplicant[969]: wlan0: SME: Trying to authenticate with 48:f8:b3:5d:92:8b (SSID='Thuis9F' freq=2457 MHz)
Mar 30 15:23:12 ZARX1404 kernel: [ 1416.821495] wlan0: authenticate with 48:f8:b3:5d:92:8b
Mar 30 15:23:12 ZARX1404 NetworkManager[875]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 30 15:23:12 ZARX1404 kernel: [ 1416.870645] wlan0: send auth to 48:f8:b3:5d:92:8b (try 1/3)
Mar 30 15:23:12 ZARX1404 wpa_supplicant[969]: wlan0: Trying to associate with 48:f8:b3:5d:92:8b (SSID='Thuis9F' freq=2457 MHz)
Mar 30 15:23:12 ZARX1404 kernel: [ 1416.899552] wlan0: authenticated
Mar 30 15:23:12 ZARX1404 kernel: [ 1416.901919] wlan0: associate with 48:f8:b3:5d:92:8b (try 1/3)
Mar 30 15:23:12 ZARX1404 NetworkManager[875]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar 30 15:23:12 ZARX1404 kernel: [ 1416.905018] wlan0: RX AssocResp from 48:f8:b3:5d:92:8b (capab=0x411 status=0 aid=3)
Mar 30 15:23:12 ZARX1404 wpa_supplicant[969]: wlan0: Associated with 48:f8:b3:5d:92:8b
Mar 30 15:23:12 ZARX1404 kernel: [ 1416.915265] wlan0: associated
Mar 30 15:23:12 ZARX1404 NetworkManager[875]: <info> (wlan0): supplicant interface state: associating -> associated
Mar 30 15:23:12 ZARX1404 NetworkManager[875]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Mar 30 15:23:12 ZARX1404 wpa_supplicant[969]: wlan0: WPA: Key negotiation completed with 48:f8:b3:5d:92:8b [PTK=CCMP GTK=TKIP]
Mar 30 15:23:12 ZARX1404 wpa_supplicant[969]: wlan0: CTRL-EVENT-CONNECTED - Connection to 48:f8:b3:5d:92:8b completed [id=0 id_str=]
Mar 30 15:23:12 ZARX1404 NetworkManager[875]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Mar 30 15:23:12 ZARX1404 NetworkManager[875]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Thuis9F'.
Mar 30 15:23:12 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 30 15:23:12 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar 30 15:23:12 ZARX1404 NetworkManager[875]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar 30 15:23:12 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Mar 30 15:23:12 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 30 15:23:12 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Mar 30 15:23:12 ZARX1404 avahi-daemon[880]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.11.
Mar 30 15:23:12 ZARX1404 avahi-daemon[880]: New relevant interface wlan0.IPv4 for mDNS.
Mar 30 15:23:12 ZARX1404 avahi-daemon[880]: Registering new address record for 192.168.1.11 on wlan0.IPv4.
Mar 30 15:23:13 ZARX1404 NetworkManager[875]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Mar 30 15:23:13 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Mar 30 15:23:13 ZARX1404 NetworkManager[875]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Mar 30 15:23:13 ZARX1404 NetworkManager[875]: <info> NetworkManager state is now CONNECTED_GLOBAL
Mar 30 15:23:13 ZARX1404 NetworkManager[875]: <info> Policy set 'Thuis9F' (wlan0) as default for IPv4 routing and DNS.
Mar 30 15:23:13 ZARX1404 NetworkManager[875]: <info> Writing DNS information to /sbin/resolvconf
Mar 30 15:23:13 ZARX1404 dnsmasq[1881]: setting upstream servers from DBus
Mar 30 15:23:13 ZARX1404 dnsmasq[1881]: using nameserver 192.168.1.254#53
Mar 30 15:22:58 ZARX1404 whoopsie[1063]: message repeated 7 times: [ offline]
Mar 30 15:23:16 ZARX1404 whoopsie[1063]: Could not get the list of active connections: Timeout was reached
Mar 30 15:23:16 ZARX1404 whoopsie[1063]: offline
Mar 30 15:23:23 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) successful, device activated.
Mar 30 15:23:23 ZARX1404 dbus[704]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Mar 30 15:23:23 ZARX1404 dbus[704]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Mar 30 15:23:30 ZARX1404 ntpdate[2948]: adjust time server 91.189.94.4 offset 0.025165 sec
Mar 30 15:23:36 ZARX1404 wpa_supplicant[969]: wlan0: CTRL-EVENT-DISCONNECTED bssid=48:f8:b3:5d:92:8b reason=4 locally_generated=1
Mar 30 15:23:36 ZARX1404 NetworkManager[875]: <warn> Connection disconnected (reason -4)
Mar 30 15:23:36 ZARX1404 kernel: [ 1441.455496] cfg80211: Calling CRDA to update world regulatory domain
Mar 30 15:23:36 ZARX1404 kernel: [ 1441.457563] cfg80211: World regulatory domain updated:
Mar 30 15:23:36 ZARX1404 kernel: [ 1441.457566] cfg80211:  DFS Master region: unset
Mar 30 15:23:36 ZARX1404 kernel: [ 1441.457567] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 30 15:23:36 ZARX1404 kernel: [ 1441.457568] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 30 15:23:36 ZARX1404 kernel: [ 1441.457569] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 30 15:23:36 ZARX1404 kernel: [ 1441.457570] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 30 15:23:36 ZARX1404 kernel: [ 1441.457571] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 30 15:23:36 ZARX1404 kernel: [ 1441.457572] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 30 15:23:36 ZARX1404 NetworkManager[875]: <info> (wlan0): supplicant interface state: completed -> disconnected
Mar 30 15:23:36 ZARX1404 wpa_supplicant[969]: wlan0: CTRL-EVENT-SCAN-STARTED 
Mar 30 15:23:36 ZARX1404 NetworkManager[875]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 30 15:23:39 ZARX1404 wpa_supplicant[969]: wlan0: SME: Trying to authenticate with 48:f8:b3:5d:92:8b (SSID='Thuis9F' freq=2457 MHz)
Mar 30 15:23:39 ZARX1404 kernel: [ 1444.543200] wlan0: authenticate with 48:f8:b3:5d:92:8b
Mar 30 15:23:39 ZARX1404 NetworkManager[875]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 30 15:23:39 ZARX1404 kernel: [ 1444.614648] wlan0: send auth to 48:f8:b3:5d:92:8b (try 1/3)
Mar 30 15:23:39 ZARX1404 kernel: [ 1444.640520] wlan0: send auth to 48:f8:b3:5d:92:8b (try 2/3)
Mar 30 15:23:39 ZARX1404 kernel: [ 1444.700287] wlan0: send auth to 48:f8:b3:5d:92:8b (try 3/3)
Mar 30 15:23:40 ZARX1404 kernel: [ 1444.814283] wlan0: authentication with 48:f8:b3:5d:92:8b timed out
Mar 30 15:23:40 ZARX1404 NetworkManager[875]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Mar 30 15:23:40 ZARX1404 wpa_supplicant[969]: wlan0: CTRL-EVENT-SCAN-STARTED 
Mar 30 15:23:40 ZARX1404 NetworkManager[875]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 30 15:23:51 ZARX1404 NetworkManager[875]: <warn> (wlan0): link timed out.
Mar 30 15:23:51 ZARX1404 NetworkManager[875]: <info> (wlan0): device state change: activated -> failed (reason 'SSID not found') [100 120 53]
Mar 30 15:23:51 ZARX1404 NetworkManager[875]: <info> NetworkManager state is now DISCONNECTED
Mar 30 15:23:51 ZARX1404 NetworkManager[875]: <warn> Activation (wlan0) failed for connection 'Thuis9F'
Mar 30 15:23:51 ZARX1404 NetworkManager[875]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 30 15:23:51 ZARX1404 NetworkManager[875]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar 30 15:23:51 ZARX1404 dbus[704]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Mar 30 15:23:51 ZARX1404 avahi-daemon[880]: Withdrawing address record for 192.168.1.11 on wlan0.
Mar 30 15:23:51 ZARX1404 avahi-daemon[880]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.11.
Mar 30 15:23:51 ZARX1404 avahi-daemon[880]: Interface wlan0.IPv4 no longer relevant for mDNS.
Mar 30 15:23:51 ZARX1404 NetworkManager[875]: <warn> DNS: plugin dnsmasq update failed
Mar 30 15:23:51 ZARX1404 NetworkManager[875]: <info> Removing DNS information from /sbin/resolvconf
Mar 30 15:23:51 ZARX1404 dnsmasq[1881]: setting upstream servers from DBus
Mar 30 15:23:51 ZARX1404 dbus[704]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Mar 30 15:23:51 ZARX1404 NetworkManager[875]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> (wlan0): supplicant interface state: scanning -> inactive
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Auto-activating connection 'Thuis9F'.
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) starting connection 'Thuis9F'
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> NetworkManager state is now CONNECTING
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Activation (wlan0/wireless): access point 'Thuis9F' has security, but secrets are required.
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Activation (wlan0/wireless): connection 'Thuis9F' has security, and secrets exist.  No new secrets needed.
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Config: added 'ssid' value 'Thuis9F'
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Config: added 'scan_ssid' value '1'
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Config: added 'bssid' value '48:f8:b3:5d:92:8b'
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Config: added 'psk' value '<omitted>'
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 30 15:23:54 ZARX1404 NetworkManager[875]: <info> Config: set interface ap_scan to 1
Mar 30 15:23:54 ZARX1404 wpa_supplicant[969]: message repeated 3 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Mar 30 15:23:57 ZARX1404 wpa_supplicant[969]: wlan0: SME: Trying to authenticate with 48:f8:b3:5d:92:8b (SSID='Thuis9F' freq=2457 MHz)
Mar 30 15:23:57 ZARX1404 kernel: [ 1462.569435] wlan0: authenticate with 48:f8:b3:5d:92:8b
Mar 30 15:23:57 ZARX1404 NetworkManager[875]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Mar 30 15:23:57 ZARX1404 kernel: [ 1462.618357] wlan0: send auth to 48:f8:b3:5d:92:8b (try 1/3)
Mar 30 15:23:57 ZARX1404 kernel: [ 1462.664072] wlan0: send auth to 48:f8:b3:5d:92:8b (try 2/3)
Mar 30 15:23:57 ZARX1404 kernel: [ 1462.697963] wlan0: send auth to 48:f8:b3:5d:92:8b (try 3/3)
Mar 30 15:23:57 ZARX1404 kernel: [ 1462.730726] wlan0: authentication with 48:f8:b3:5d:92:8b timed out
Mar 30 15:23:57 ZARX1404 wpa_supplicant[969]: wlan0: SME: Trying to authenticate with 48:f8:b3:5d:92:8b (SSID='Thuis9F' freq=2457 MHz)
Mar 30 15:23:58 ZARX1404 wpa_supplicant[969]: wlan0: CTRL-EVENT-SCAN-STARTED 
Mar 30 15:23:58 ZARX1404 wpa_supplicant[969]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Thuis9F" auth_failures=1 duration=10
Mar 30 15:23:58 ZARX1404 NetworkManager[875]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
```



Any suggestions would be greatly appreciated.

---

