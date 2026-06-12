---
title: "installer hang on configuring bcmwl-kernel-source(i386)"
date: 2014-03-18
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-03-18
self evident, cant install ubuntu if that is in the computer.

---

### Post by sdowney717 on 2014-03-18
yanked out card and installed ubuntu.
Then following this 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)
installed the b43 legacy firmware.
reboot
can see wireless networks

Can not connect to any of my wireless networks

Ideas?

---

### Post by sdowney717 on 2014-03-18
syslog shows odd errors connecting to verizon router
 DHCPv4 request timed out ??

```
Mar 18 12:30:14 scott875-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x688e2441)
Mar 18 12:30:25 scott875-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x688e2441)
Mar 18 12:30:35 scott875-desktop NetworkManager[652]: <warn> (wlan0): **DHCPv4 request timed out.**
Mar 18 12:30:35 scott875-desktop NetworkManager[652]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2031
Mar 18 12:30:35 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Mar 18 12:30:35 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Mar 18 12:30:35 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Mar 18 12:30:35 scott875-desktop NetworkManager[652]: <warn> Activation (wlan0) failed for connection 'verizon router'
Mar 18 12:30:35 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Mar 18 12:30:35 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: failed ->** disconnected (reason 'none'**) [120 30 0]
Mar 18 12:30:35 scott875-desktop NetworkManager[652]: <info> (wlan0): deactivating device (reason 'none') [0]
```

---

### Post by sdowney717 on 2014-03-18
here for the netgear router

```
Mar 18 12:31:54 scott875-desktop avahi-daemon[640]: Registering new address record for fe80::20d:3aff:fe6d:ec4e on wlan0.*.
Mar 18 12:32:04 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) starting connection 'NETGEAR'
Mar 18 12:32:04 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 18 12:32:04 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 12:32:04 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 18 12:32:04 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 12:32:04 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 12:32:04 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 18 12:32:04 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 18 12:32:04 scott875-desktop NetworkManager[652]: <info> Activation (wlan0/wireless): access point 'NETGEAR' has security, but secrets are required.
Mar 18 12:32:04 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar 18 12:32:04 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: get_secret_flags: assertion 'is_secret_prop (setting, secret_name, error)' failed
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> Activation (wlan0/wireless): connection 'NETGEAR' has security, and secrets exist.  No new secrets needed.
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> Config: added 'ssid' value 'NETGEAR'
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> Config: added 'scan_ssid' value '1'
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> Config: added 'bssid' value '00:18:4d:58:f9:a4'
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> Config: added 'auth_alg' value 'OPEN'
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> Config: added 'psk' value '<omitted>'
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> Config: set interface ap_scan to 1
Mar 18 12:32:12 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 18 12:32:12 scott875-desktop wpa_supplicant[680]: message repeated 2 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Mar 18 12:32:13 scott875-desktop wpa_supplicant[680]: wlan0: SME: Trying to authenticate with 00:18:4d:58:f9:a4 (SSID='NETGEAR' freq=2462 MHz)
Mar 18 12:32:13 scott875-desktop kernel: [  203.256701] wlan0: authenticate with 00:18:4d:58:f9:a4
Mar 18 12:32:13 scott875-desktop kernel: [  203.288191] wlan0: send auth to 00:18:4d:58:f9:a4 (try 1/3)
Mar 18 12:32:13 scott875-desktop kernel: [  203.291358] wlan0: authenticated
Mar 18 12:32:13 scott875-desktop kernel: [  203.291642] b43legacy ssb0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
Mar 18 12:32:13 scott875-desktop kernel: [  203.291650] b43legacy ssb0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
Mar 18 12:32:13 scott875-desktop kernel: [  203.292071] wlan0: associate with 00:18:4d:58:f9:a4 (try 1/3)
Mar 18 12:32:13 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 18 12:32:13 scott875-desktop wpa_supplicant[680]: wlan0: Trying to associate with 00:18:4d:58:f9:a4 (SSID='NETGEAR' freq=2462 MHz)
Mar 18 12:32:13 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar 18 12:32:14 scott875-desktop kernel: [  203.496043] wlan0: associate with 00:18:4d:58:f9:a4 (try 2/3)
Mar 18 12:32:14 scott875-desktop kernel: [  203.700040] wlan0: associate with 00:18:4d:58:f9:a4 (try 3/3)
Mar 18 12:32:14 scott875-desktop kernel: [  203.904040] wlan0: association with 00:18:4d:58:f9:a4 timed out
Mar 18 12:32:14 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: associating -> disconnected
Mar 18 12:32:14 scott875-desktop wpa_supplicant[680]: wlan0: CTRL-EVENT-SCAN-STARTED 
Mar 18 12:32:14 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 18 12:32:15 scott875-desktop wpa_supplicant[680]: wlan0: SME: Trying to authenticate with 00:18:4d:58:f9:a4 (SSID='NETGEAR' freq=2462 MHz)
Mar 18 12:32:15 scott875-desktop kernel: [  205.132696] wlan0: authenticate with 00:18:4d:58:f9:a4
Mar 18 12:32:15 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 18 12:32:15 scott875-desktop wpa_supplicant[680]: wlan0: Trying to associate with 00:18:4d:58:f9:a4 (SSID='NETGEAR' freq=2462 MHz)
Mar 18 12:32:15 scott875-desktop kernel: [  205.152123] wlan0: send auth to 00:18:4d:58:f9:a4 (try 1/3)
Mar 18 12:32:15 scott875-desktop kernel: [  205.154257] wlan0: authenticated
Mar 18 12:32:15 scott875-desktop kernel: [  205.154644] b43legacy ssb0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
Mar 18 12:32:15 scott875-desktop kernel: [  205.154653] b43legacy ssb0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
Mar 18 12:32:15 scott875-desktop kernel: [  205.156043] wlan0: associate with 00:18:4d:58:f9:a4 (try 1/3)
Mar 18 12:32:15 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar 18 12:32:15 scott875-desktop kernel: [  205.360018] wlan0: associate with 00:18:4d:58:f9:a4 (try 2/3)
Mar 18 12:32:16 scott875-desktop kernel: [  205.564021] wlan0: associate with 00:18:4d:58:f9:a4 (try 3/3)
Mar 18 12:32:16 scott875-desktop kernel: [  205.768025] wlan0: association with 00:18:4d:58:f9:a4 timed out
Mar 18 12:32:16 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: associating -> disconnected
Mar 18 12:32:16 scott875-desktop wpa_supplicant[680]: wlan0: CTRL-EVENT-SCAN-STARTED 
Mar 18 12:32:16 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 18 12:32:18 scott875-desktop wpa_supplicant[680]: wlan0: SME: Trying to authenticate with 00:18:4d:58:f9:a4 (SSID='NETGEAR' freq=2462 MHz)
Mar 18 12:32:18 scott875-desktop kernel: [  207.388678] wlan0: authenticate with 00:18:4d:58:f9:a4
Mar 18 12:32:18 scott875-desktop wpa_supplicant[680]: wlan0: Trying to associate with 00:18:4d:58:f9:a4 (SSID='NETGEAR' freq=2462 MHz)
Mar 18 12:32:18 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 18 12:32:18 scott875-desktop kernel: [  207.416125] wlan0: send auth to 00:18:4d:58:f9:a4 (try 1/3)
Mar 18 12:32:18 scott875-desktop kernel: [  207.417649] wlan0: authenticated
Mar 18 12:32:18 scott875-desktop kernel: [  207.417908] b43legacy ssb0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
Mar 18 12:32:18 scott875-desktop kernel: [  207.417916] b43legacy ssb0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
Mar 18 12:32:18 scott875-desktop kernel: [  207.420058] wlan0: associate with 00:18:4d:58:f9:a4 (try 1/3)
Mar 18 12:32:18 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar 18 12:32:18 scott875-desktop kernel: [  207.624024] wlan0: associate with 00:18:4d:58:f9:a4 (try 2/3)
Mar 18 12:32:18 scott875-desktop kernel: [  207.828034] wlan0: associate with 00:18:4d:58:f9:a4 (try 3/3)
Mar 18 12:32:18 scott875-desktop kernel: [  208.032050] wlan0: association with 00:18:4d:58:f9:a4 timed out
Mar 18 12:32:18 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: associating -> disconnected
Mar 18 12:32:19 scott875-desktop wpa_supplicant[680]: wlan0: CTRL-EVENT-SCAN-STARTED 
Mar 18 12:32:19 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 18 12:32:20 scott875-desktop wpa_supplicant[680]: wlan0: SME: Trying to authenticate with 00:18:4d:58:f9:a4 (SSID='NETGEAR' freq=2462 MHz)
Mar 18 12:32:20 scott875-desktop kernel: [  210.172840] wlan0: authenticate with 00:18:4d:58:f9:a4
Mar 18 12:32:20 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 18 12:32:20 scott875-desktop wpa_supplicant[680]: wlan0: Trying to associate with 00:18:4d:58:f9:a4 (SSID='NETGEAR' freq=2462 MHz)
Mar 18 12:32:20 scott875-desktop kernel: [  210.184217] wlan0: send auth to 00:18:4d:58:f9:a4 (try 1/3)
Mar 18 12:32:20 scott875-desktop kernel: [  210.187813] wlan0: authenticated
Mar 18 12:32:20 scott875-desktop kernel: [  210.188087] b43legacy ssb0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
Mar 18 12:32:20 scott875-desktop kernel: [  210.188093] b43legacy ssb0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
Mar 18 12:32:20 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar 18 12:32:20 scott875-desktop kernel: [  210.192037] wlan0: associate with 00:18:4d:58:f9:a4 (try 1/3)
Mar 18 12:32:21 scott875-desktop kernel: [  210.396018] wlan0: associate with 00:18:4d:58:f9:a4 (try 2/3)
Mar 18 12:32:21 scott875-desktop kernel: [  210.600023] wlan0: associate with 00:18:4d:58:f9:a4 (try 3/3)
Mar 18 12:32:21 scott875-desktop kernel: [  210.804028] wlan0: association with 00:18:4d:58:f9:a4 timed out
Mar 18 12:32:21 scott875-desktop wpa_supplicant[680]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="NETGEAR" auth_failures=1 duration=10
Mar 18 12:32:21 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: associating -> disconnected
Mar 18 12:32:26 scott875-desktop wpa_supplicant[680]: wlan0: CTRL-EVENT-SCAN-STARTED 
Mar 18 12:32:26 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 18 12:32:32 scott875-desktop wpa_supplicant[680]: wlan0: CTRL-EVENT-SCAN-STARTED 
Mar 18 12:32:33 scott875-desktop wpa_supplicant[680]: wlan0: CTRL-EVENT-SSID-REENABLED id=0 ssid="NETGEAR"
Mar 18 12:32:33 scott875-desktop wpa_supplicant[680]: wlan0: SME: Trying to authenticate with 00:18:4d:58:f9:a4 (SSID='NETGEAR' freq=2462 MHz)
Mar 18 12:32:33 scott875-desktop kernel: [  223.048759] wlan0: authenticate with 00:18:4d:58:f9:a4
Mar 18 12:32:33 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 18 12:32:33 scott875-desktop wpa_supplicant[680]: wlan0: Trying to associate with 00:18:4d:58:f9:a4 (SSID='NETGEAR' freq=2462 MHz)
Mar 18 12:32:33 scott875-desktop kernel: [  223.068172] wlan0: send auth to 00:18:4d:58:f9:a4 (try 1/3)
Mar 18 12:32:33 scott875-desktop kernel: [  223.071752] wlan0: authenticated
Mar 18 12:32:33 scott875-desktop kernel: [  223.072051] b43legacy ssb0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
Mar 18 12:32:33 scott875-desktop kernel: [  223.072059] b43legacy ssb0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
Mar 18 12:32:33 scott875-desktop kernel: [  223.076057] wlan0: associate with 00:18:4d:58:f9:a4 (try 1/3)
Mar 18 12:32:33 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar 18 12:32:33 scott875-desktop kernel: [  223.280434] wlan0: associate with 00:18:4d:58:f9:a4 (try 2/3)
Mar 18 12:32:34 scott875-desktop kernel: [  223.484048] wlan0: associate with 00:18:4d:58:f9:a4 (try 3/3)
Mar 18 12:32:34 scott875-desktop kernel: [  223.688036] wlan0: association with 00:18:4d:58:f9:a4 timed out
Mar 18 12:32:34 scott875-desktop wpa_supplicant[680]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="NETGEAR" auth_failures=2 duration=20
Mar 18 12:32:34 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: associating -> disconnected
Mar 18 12:32:37 scott875-desktop NetworkManager[652]: <warn> Activation (wlan0/wireless): association took too long.
Mar 18 12:32:37 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar 18 12:32:37 scott875-desktop NetworkManager[652]: <warn> Activation (wlan0/wireless): asking for new secrets
Mar 18 12:32:44 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Mar 18 12:32:44 scott875-desktop NetworkManager[652]: <warn> No agents were available for this request.
Mar 18 12:32:44 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Mar 18 12:32:44 scott875-desktop NetworkManager[652]: <info> Marking connection 'NETGEAR' invalid.
Mar 18 12:32:44 scott875-desktop NetworkManager[652]: <warn> Activation (wlan0) failed for connection 'NETGEAR'
Mar 18 12:32:44 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 18 12:32:44 scott875-desktop NetworkManager[652]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar 18 12:32:44 scott875-desktop wpa_supplicant[680]: wlan0: CTRL-EVENT-SCAN-STARTED 
Mar 18 12:32:51 scott875-desktop NetworkManager[652]: <info> (eth1): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Mar 18 12:32:51 scott875-desktop NetworkManager[652]: <info> (eth1): deactivating device (reason 'user-requested') [39]
Mar 18 12:32:52 scott875-desktop NetworkManager[652]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1125
Mar 18 12:32:52 scott875-desktop avahi-daemon[640]: Withdrawing address record for 192.168.1.6 on eth1.
Mar 18 12:32:52 scott875-desktop avahi-daemon[640]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.6.
Mar 18 12:32:52 scott875-desktop avahi-daemon[640]: Interface eth1.IPv4 no longer relevant for mDNS.
Mar 18 12:32:52 scott875-desktop NetworkManager[652]: <warn> DNS: plugin dnsmasq update failed
Mar 18 12:32:52 scott875-desktop dnsmasq[1335]: setting upstream servers from DBus
Mar 18 12:32:52 scott875-desktop NetworkManager[652]: <info> Removing DNS information from /sbin/resolvconf
Mar 18 12:32:52 scott875-desktop NetworkManager[652]: <info> NetworkManager state is now DISCONNECTED
Mar 18 12:31:55 scott875-desktop whoopsie[1002]: message repeated 19 times: [ online]
Mar 18 12:32:52 scott875-desktop whoopsie[1002]: offline
Mar 18 12:32:52 scott875-desktop dbus[535]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Mar 18 12:32:52 scott875-desktop dbus[535]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) starting connection 'verizon router'
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> NetworkManager state is now CONNECTING
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Activation (wlan0/wireless): access point 'verizon router' has security, but secrets are required.
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Activation (wlan0/wireless): connection 'verizon router' has security, and secrets exist.  No new secrets needed.
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Config: added 'ssid' value 'verizon router'
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Config: added 'scan_ssid' value '1'
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Config: added 'auth_alg' value 'OPEN'
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Config: added 'psk' value '<omitted>'
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> Config: set interface ap_scan to 1
Mar 18 12:32:59 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: inactive -> scanning
Mar 18 12:32:59 scott875-desktop wpa_supplicant[680]: message repeated 2 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Mar 18 12:33:00 scott875-desktop wpa_supplicant[680]: wlan0: SME: Trying to authenticate with 00:18:3a:b8:d7:f2 (SSID='verizon router' freq=2412 MHz)
Mar 18 12:33:00 scott875-desktop kernel: [  249.756673] wlan0: authenticate with 00:18:3a:b8:d7:f2
Mar 18 12:33:00 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 18 12:33:00 scott875-desktop wpa_supplicant[680]: wlan0: Trying to associate with 00:18:3a:b8:d7:f2 (SSID='verizon router' freq=2412 MHz)
Mar 18 12:33:00 scott875-desktop kernel: [  249.788151] wlan0: send auth to 00:18:3a:b8:d7:f2 (try 1/3)
Mar 18 12:33:00 scott875-desktop kernel: [  249.790860] wlan0: authenticated
Mar 18 12:33:00 scott875-desktop kernel: [  249.792055] wlan0: associate with 00:18:3a:b8:d7:f2 (try 1/3)
Mar 18 12:33:00 scott875-desktop kernel: [  249.794154] wlan0: RX AssocResp from 00:18:3a:b8:d7:f2 (capab=0x431 status=0 aid=1)
Mar 18 12:33:00 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar 18 12:33:00 scott875-desktop wpa_supplicant[680]: wlan0: Associated with 00:18:3a:b8:d7:f2
Mar 18 12:33:00 scott875-desktop kernel: [  249.800068] wlan0: associated
Mar 18 12:33:00 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Mar 18 12:33:00 scott875-desktop wpa_supplicant[680]: wlan0: WPA: Key negotiation completed with 00:18:3a:b8:d7:f2 [PTK=CCMP GTK=TKIP]
Mar 18 12:33:00 scott875-desktop wpa_supplicant[680]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:18:3a:b8:d7:f2 completed [id=0 id_str=]
Mar 18 12:33:00 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Mar 18 12:33:00 scott875-desktop NetworkManager[652]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'verizon router'.
Mar 18 12:33:00 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 18 12:33:00 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar 18 12:33:00 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar 18 12:33:00 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 18 12:33:00 scott875-desktop NetworkManager[652]: <info> dhclient started with pid 2123
Mar 18 12:33:00 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Beginning IP6 addrconf.
Mar 18 12:33:00 scott875-desktop avahi-daemon[640]: Withdrawing address record for fe80::20d:3aff:fe6d:ec4e on wlan0.
Mar 18 12:33:00 scott875-desktop avahi-daemon[640]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::20d:3aff:fe6d:ec4e.
Mar 18 12:33:00 scott875-desktop avahi-daemon[640]: Interface wlan0.IPv6 no longer relevant for mDNS.
Mar 18 12:33:00 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 18 12:33:00 scott875-desktop dhclient: Internet Systems Consortium DHCP Client 4.2.4
Mar 18 12:33:00 scott875-desktop dhclient: Copyright 2004-2012 Internet Systems Consortium.
Mar 18 12:33:00 scott875-desktop dhclient: All rights reserved.
Mar 18 12:33:00 scott875-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Mar 18 12:33:00 scott875-desktop dhclient: 
Mar 18 12:33:00 scott875-desktop NetworkManager[652]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Mar 18 12:33:00 scott875-desktop dhclient: Listening on LPF/wlan0/00:0d:3a:6d:ec:4e
Mar 18 12:33:00 scott875-desktop dhclient: Sending on   LPF/wlan0/00:0d:3a:6d:ec:4e
Mar 18 12:33:00 scott875-desktop dhclient: Sending on   Socket/fallback
Mar 18 12:33:00 scott875-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x30259f8f)
Mar 18 12:33:01 scott875-desktop avahi-daemon[640]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::20d:3aff:fe6d:ec4e.
Mar 18 12:33:01 scott875-desktop avahi-daemon[640]: New relevant interface wlan0.IPv6 for mDNS.
Mar 18 12:33:01 scott875-desktop avahi-daemon[640]: Registering new address record for fe80::20d:3aff:fe6d:ec4e on wlan0.*.
Mar 18 12:33:03 scott875-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 (xid=0x30259f8f)
Mar 18 12:33:08 scott875-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 (xid=0x30259f8f)
Mar 18 12:33:20 scott875-desktop NetworkManager[652]: <info> (wlan0): IP6 addrconf timed out or failed.
Mar 18 12:33:20 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar 18 12:33:20 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar 18 12:33:20 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Mar 18 12:33:22 scott875-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 (xid=0x30259f8f)
Mar 18 12:33:40 scott875-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 (xid=0x30259f8f)
Mar 18 12:33:45 scott875-desktop NetworkManager[652]: <warn> (wlan0): DHCPv4 request timed out.
Mar 18 12:33:45 scott875-desktop NetworkManager[652]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2123
Mar 18 12:33:45 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Mar 18 12:33:45 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Mar 18 12:33:45 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Mar 18 12:33:45 scott875-desktop NetworkManager[652]: <info> NetworkManager state is now DISCONNECTED
Mar 18 12:33:45 scott875-desktop NetworkManager[652]: <warn> Activation (wlan0) failed for connection 'verizon router'
Mar 18 12:33:45 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Mar 18 12:33:45 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 18 12:33:45 scott875-desktop NetworkManager[652]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar 18 12:33:45 scott875-desktop avahi-daemon[640]: Withdrawing address record for fe80::20d:3aff:fe6d:ec4e on wlan0.
Mar 18 12:33:45 scott875-desktop avahi-daemon[640]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::20d:3aff:fe6d:ec4e.
Mar 18 12:33:45 scott875-desktop avahi-daemon[640]: Interface wlan0.IPv6 no longer relevant for mDNS.
Mar 18 12:33:45 scott875-desktop kernel: [  295.211855] wlan0: deauthenticating from 00:18:3a:b8:d7:f2 by local choice (reason=3)
Mar 18 12:33:45 scott875-desktop kernel: [  295.220382] cfg80211: Calling CRDA to update world regulatory domain
Mar 18 12:33:45 scott875-desktop wpa_supplicant[680]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:18:3a:b8:d7:f2 reason=3 locally_generated=1
Mar 18 12:33:45 scott875-desktop wpa_supplicant[680]: wlan0: CTRL-EVENT-SCAN-STARTED 
Mar 18 12:33:45 scott875-desktop NetworkManager[652]: <warn> Connection disconnected (reason -3)
Mar 18 12:33:45 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: completed -> disconnected
Mar 18 12:33:45 scott875-desktop NetworkManager[652]: <warn> Connection disconnected (reason -3)
Mar 18 12:33:45 scott875-desktop kernel: [  295.233552] cfg80211: World regulatory domain updated:
Mar 18 12:33:45 scott875-desktop kernel: [  295.233562] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 18 12:33:45 scott875-desktop kernel: [  295.233568] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 18 12:33:45 scott875-desktop kernel: [  295.233573] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 18 12:33:45 scott875-desktop kernel: [  295.233578] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 18 12:33:45 scott875-desktop kernel: [  295.233582] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 18 12:33:45 scott875-desktop kernel: [  295.233587] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 18 12:33:47 scott875-desktop avahi-daemon[640]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::20d:3aff:fe6d:ec4e.
Mar 18 12:33:47 scott875-desktop avahi-daemon[640]: New relevant interface wlan0.IPv6 for mDNS.
Mar 18 12:33:47 scott875-desktop avahi-daemon[640]: Registering new address record for fe80::20d:3aff:fe6d:ec4e on wlan0.*.
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> Activation (eth1) starting connection 'Wired connection 2'
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> NetworkManager state is now CONNECTING
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> dhclient started with pid 2245
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Beginning IP6 addrconf.
Mar 18 12:34:31 scott875-desktop avahi-daemon[640]: Withdrawing address record for fe80::20f:b5ff:fef9:f6e on eth1.
Mar 18 12:34:31 scott875-desktop avahi-daemon[640]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::20f:b5ff:fef9:f6e.
Mar 18 12:34:31 scott875-desktop avahi-daemon[640]: Interface eth1.IPv6 no longer relevant for mDNS.
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Mar 18 12:34:31 scott875-desktop dhclient: Internet Systems Consortium DHCP Client 4.2.4
Mar 18 12:34:31 scott875-desktop dhclient: Copyright 2004-2012 Internet Systems Consortium.
Mar 18 12:34:31 scott875-desktop dhclient: All rights reserved.
Mar 18 12:34:31 scott875-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Mar 18 12:34:31 scott875-desktop dhclient: 
Mar 18 12:34:31 scott875-desktop NetworkManager[652]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Mar 18 12:34:31 scott875-desktop dhclient: Listening on LPF/eth1/00:0f:b5:f9:0f:6e
Mar 18 12:34:31 scott875-desktop dhclient: Sending on   LPF/eth1/00:0f:b5:f9:0f:6e
Mar 18 12:34:31 scott875-desktop dhclient: Sending on   Socket/fallback
Mar 18 12:34:31 scott875-desktop dhclient: DHCPREQUEST of 192.168.1.6 on eth1 to 255.255.255.255 port 67 (xid=0x7675e1d2)
Mar 18 12:34:32 scott875-desktop dhclient: DHCPACK of 192.168.1.6 from 192.168.1.1
Mar 18 12:34:32 scott875-desktop dhclient: bound to 192.168.1.6 -- renewal in 43018 seconds.
Mar 18 12:34:32 scott875-desktop NetworkManager[652]: <info> (eth1): DHCPv4 state changed preinit -> reboot
Mar 18 12:34:32 scott875-desktop NetworkManager[652]: <info>   address 192.168.1.6
Mar 18 12:34:32 scott875-desktop NetworkManager[652]: <info>   prefix 24 (255.255.255.0)
Mar 18 12:34:32 scott875-desktop NetworkManager[652]: <info>   gateway 192.168.1.1
Mar 18 12:34:32 scott875-desktop NetworkManager[652]: <info>   nameserver '192.168.1.1'
Mar 18 12:34:32 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Mar 18 12:34:32 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Mar 18 12:34:32 scott875-desktop avahi-daemon[640]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.6.
Mar 18 12:34:32 scott875-desktop avahi-daemon[640]: New relevant interface eth1.IPv4 for mDNS.
Mar 18 12:34:32 scott875-desktop avahi-daemon[640]: Registering new address record for 192.168.1.6 on eth1.IPv4.
Mar 18 12:34:32 scott875-desktop avahi-daemon[640]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::20f:b5ff:fef9:f6e.
Mar 18 12:34:32 scott875-desktop avahi-daemon[640]: New relevant interface eth1.IPv6 for mDNS.
Mar 18 12:34:32 scott875-desktop avahi-daemon[640]: Registering new address record for fe80::20f:b5ff:fef9:f6e on eth1.*.
Mar 18 12:34:33 scott875-desktop NetworkManager[652]: <info> (eth1): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Mar 18 12:34:33 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Mar 18 12:34:33 scott875-desktop NetworkManager[652]: <info> (eth1): device state change: secondaries -> activated (reason 'none') [90 100 0]
Mar 18 12:34:33 scott875-desktop NetworkManager[652]: <info> NetworkManager state is now CONNECTED_GLOBAL
Mar 18 12:34:33 scott875-desktop NetworkManager[652]: <info> Policy set 'Wired connection 2' (eth1) as default for IPv4 routing and DNS.
Mar 18 12:34:33 scott875-desktop dnsmasq[1335]: setting upstream servers from DBus
Mar 18 12:34:33 scott875-desktop dnsmasq[1335]: using nameserver 192.168.1.1#53
Mar 18 12:34:33 scott875-desktop NetworkManager[652]: <info> Writing DNS information to /sbin/resolvconf
Mar 18 12:34:33 scott875-desktop NetworkManager[652]: <info> Activation (eth1) successful, device activated.
Mar 18 12:34:33 scott875-desktop dbus[535]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Mar 18 12:34:33 scott875-desktop dbus[535]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Mar 18 12:34:33 scott875-desktop whoopsie[1002]: message repeated 4 times: [ offline]
Mar 18 12:34:33 scott875-desktop whoopsie[1002]: online
Mar 18 12:34:40 scott875-desktop ntpdate[2325]: adjust time server 91.189.94.4 offset 0.192504 sec
Mar 18 12:34:51 scott875-desktop NetworkManager[652]: <info> (eth1): IP6 addrconf timed out or failed.
Mar 18 12:34:51 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar 18 12:34:51 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar 18 12:34:51 scott875-desktop NetworkManager[652]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Mar 18 12:39:07 scott875-desktop anacron[878]: Job `cron.weekly' started
Mar 18 12:39:07 scott875-desktop anacron[2866]: Updated timestamp for job `cron.weekly' to 2014-03-18
Mar 18 12:39:15 scott875-desktop dbus[535]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Mar 18 12:39:15 scott875-desktop dbus[535]: [system] Successfully activated service 'org.freedesktop.hostname1'
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) starting connection 'verizon router'
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Activation (wlan0/wireless): access point 'verizon router' has security, but secrets are required.
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Activation (wlan0/wireless): connection 'verizon router' has security, and secrets exist.  No new secrets needed.
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Config: added 'ssid' value 'verizon router'
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Config: added 'scan_ssid' value '1'
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Config: added 'auth_alg' value 'OPEN'
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Config: added 'psk' value '<omitted>'
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> Config: set interface ap_scan to 1
Mar 18 12:40:48 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 18 12:40:49 scott875-desktop kernel: [  719.275235] wlan0: authenticate with 00:18:3a:b8:d7:f2
Mar 18 12:40:48 scott875-desktop wpa_supplicant[680]: message repeated 10 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Mar 18 12:40:49 scott875-desktop wpa_supplicant[680]: wlan0: SME: Trying to authenticate with 00:18:3a:b8:d7:f2 (SSID='verizon router' freq=2412 MHz)
Mar 18 12:40:49 scott875-desktop kernel: [  719.285207] wlan0: send auth to 00:18:3a:b8:d7:f2 (try 1/3)
Mar 18 12:40:49 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 18 12:40:49 scott875-desktop wpa_supplicant[680]: wlan0: Trying to associate with 00:18:3a:b8:d7:f2 (SSID='verizon router' freq=2412 MHz)
Mar 18 12:40:49 scott875-desktop kernel: [  719.288681] wlan0: authenticated
Mar 18 12:40:49 scott875-desktop kernel: [  719.292610] wlan0: associate with 00:18:3a:b8:d7:f2 (try 1/3)
Mar 18 12:40:49 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar 18 12:40:49 scott875-desktop wpa_supplicant[680]: wlan0: Associated with 00:18:3a:b8:d7:f2
Mar 18 12:40:49 scott875-desktop kernel: [  719.306557] wlan0: RX AssocResp from 00:18:3a:b8:d7:f2 (capab=0x431 status=0 aid=1)
Mar 18 12:40:49 scott875-desktop kernel: [  719.306930] wlan0: associated
Mar 18 12:40:49 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Mar 18 12:40:49 scott875-desktop wpa_supplicant[680]: wlan0: WPA: Key negotiation completed with 00:18:3a:b8:d7:f2 [PTK=CCMP GTK=TKIP]
Mar 18 12:40:49 scott875-desktop wpa_supplicant[680]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:18:3a:b8:d7:f2 completed [id=0 id_str=]
Mar 18 12:40:49 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Mar 18 12:40:49 scott875-desktop NetworkManager[652]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'verizon router'.
Mar 18 12:40:49 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 18 12:40:49 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar 18 12:40:49 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar 18 12:40:49 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 18 12:40:49 scott875-desktop NetworkManager[652]: <info> dhclient started with pid 3811
Mar 18 12:40:49 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Beginning IP6 addrconf.
Mar 18 12:40:49 scott875-desktop avahi-daemon[640]: Withdrawing address record for fe80::20d:3aff:fe6d:ec4e on wlan0.
Mar 18 12:40:49 scott875-desktop avahi-daemon[640]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::20d:3aff:fe6d:ec4e.
Mar 18 12:40:49 scott875-desktop avahi-daemon[640]: Interface wlan0.IPv6 no longer relevant for mDNS.
Mar 18 12:40:49 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 18 12:40:49 scott875-desktop dhclient: Internet Systems Consortium DHCP Client 4.2.4
Mar 18 12:40:49 scott875-desktop dhclient: Copyright 2004-2012 Internet Systems Consortium.
Mar 18 12:40:49 scott875-desktop dhclient: All rights reserved.
Mar 18 12:40:49 scott875-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Mar 18 12:40:49 scott875-desktop dhclient: 
Mar 18 12:40:49 scott875-desktop NetworkManager[652]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Mar 18 12:40:50 scott875-desktop dhclient: Listening on LPF/wlan0/00:0d:3a:6d:ec:4e
Mar 18 12:40:50 scott875-desktop dhclient: Sending on   LPF/wlan0/00:0d:3a:6d:ec:4e
Mar 18 12:40:50 scott875-desktop dhclient: Sending on   Socket/fallback
Mar 18 12:40:50 scott875-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x3354f735)
Mar 18 12:40:50 scott875-desktop avahi-daemon[640]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::20d:3aff:fe6d:ec4e.
Mar 18 12:40:50 scott875-desktop avahi-daemon[640]: New relevant interface wlan0.IPv6 for mDNS.
Mar 18 12:40:50 scott875-desktop avahi-daemon[640]: Registering new address record for fe80::20d:3aff:fe6d:ec4e on wlan0.*.
Mar 18 12:40:52 scott875-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 (xid=0x3354f735)
Mar 18 12:40:58 scott875-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x3354f735)
Mar 18 12:41:10 scott875-desktop NetworkManager[652]: <info> (wlan0): IP6 addrconf timed out or failed.
Mar 18 12:41:10 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar 18 12:41:10 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar 18 12:41:10 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Mar 18 12:41:11 scott875-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 (xid=0x3354f735)
Mar 18 12:41:31 scott875-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x3354f735)
Mar 18 12:41:34 scott875-desktop dhclient: DHCPREQUEST of 192.168.200.24 on wlan0 to 255.255.255.255 port 67 (xid=0x3354f735)
Mar 18 12:41:34 scott875-desktop dhclient: DHCPOFFER of 192.168.200.24 from 192.168.200.1
Mar 18 12:41:35 scott875-desktop NetworkManager[652]: <warn> (wlan0): DHCPv4 request timed out.
Mar 18 12:41:35 scott875-desktop NetworkManager[652]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 3811
Mar 18 12:41:35 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Mar 18 12:41:35 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Mar 18 12:41:35 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Mar 18 12:41:35 scott875-desktop NetworkManager[652]: <info> Marking connection 'verizon router' invalid.
Mar 18 12:41:35 scott875-desktop NetworkManager[652]: <warn> Activation (wlan0) failed for connection 'verizon router'
Mar 18 12:41:35 scott875-desktop NetworkManager[652]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Mar 18 12:41:35 scott875-desktop NetworkManager[652]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 18 12:41:35 scott875-desktop NetworkManager[652]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar 18 12:41:35 scott875-desktop avahi-daemon[640]: Withdrawing address record for fe80::20d:3aff:fe6d:ec4e on wlan0.
Mar 18 12:41:35 scott875-desktop avahi-daemon[640]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::20d:3aff:fe6d:ec4e.
Mar 18 12:41:35 scott875-desktop avahi-daemon[640]: Interface wlan0.IPv6 no longer relevant for mDNS.
Mar 18 12:41:35 scott875-desktop kernel: [  765.220577] wlan0: deauthenticating from 00:18:3a:b8:d7:f2 by local choice (reason=3)
Mar 18 12:41:35 scott875-desktop wpa_supplicant[680]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:18:3a:b8:d7:f2 reason=3 locally_generated=1
Mar 18 12:41:35 scott875-desktop wpa_supplicant[680]: wlan0: CTRL-EVENT-SCAN-STARTED 
Mar 18 12:41:35 scott875-desktop kernel: [  765.240886] cfg80211: Calling CRDA to update world regulatory domain
Mar 18 12:41:35 scott875-desktop NetworkManager[652]: <warn> Connection disconnected (reason -3)
Mar 18 12:41:35 scott875-desktop NetworkManager[652]: <info> (wlan0): supplicant interface state: completed -> disconnected
Mar 18 12:41:35 scott875-desktop NetworkManager[652]: <warn> Connection disconnected (reason -3)
Mar 18 12:41:35 scott875-desktop kernel: [  765.333743] cfg80211: World regulatory domain updated:
Mar 18 12:41:35 scott875-desktop kernel: [  765.333752] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 18 12:41:35 scott875-desktop kernel: [  765.333758] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 18 12:41:35 scott875-desktop kernel: [  765.333763] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 18 12:41:35 scott875-desktop kernel: [  765.333767] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 18 12:41:35 scott875-desktop kernel: [  765.333772] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 18 12:41:35 scott875-desktop kernel: [  765.333776] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 18 12:41:37 scott875-desktop avahi-daemon[640]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::20d:3aff:fe6d:ec4e.
Mar 18 12:41:37 scott875-desktop avahi-daemon[640]: New relevant interface wlan0.IPv6 for mDNS.
Mar 18 12:41:37 scott875-desktop avahi-daemon[640]: Registering new address record for fe80::20d:3aff:fe6d:ec4e on wlan0.*.
Mar 18 12:42:01 scott875-desktop dbus[535]: [system] Reloaded configuration
Mar 18 12:43:36 scott875-desktop anacron[878]: Job `cron.weekly' terminated (mailing output)
Mar 18 12:43:36 scott875-desktop anacron[878]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Mar 18 12:44:07 scott875-desktop anacron[878]: Job `cron.monthly' started
Mar 18 12:44:07 scott875-desktop anacron[878]: Job `cron.monthly' terminated
Mar 18 12:44:07 scott875-desktop anacron[878]: Normal exit (2 jobs run)
Mar 18 12:44:07 scott875-desktop anacron[6391]: Updated timestamp for job `cron.monthly' to 2014-03-18
Mar 18 12:46:05 scott875-desktop kernel: [ 1034.486096] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Mar 18 12:46:05 scott875-desktop kernel: [ 1034.536471] JFS: nTxBlock = 8192, nTxLock = 65536
Mar 18 12:46:05 scott875-desktop kernel: [ 1034.593174] NTFS driver 2.1.30 [Flags: R/O MODULE].
Mar 18 12:46:05 scott875-desktop kernel: [ 1034.681657] QNX4 filesystem 0.2.3 registered.
Mar 18 12:46:05 scott875-desktop kernel: [ 1034.749360] xor: measuring software checksum speed
Mar 18 12:46:05 scott875-desktop kernel: [ 1034.788015]    pIII_sse  :  4463.000 MB/sec
Mar 18 12:46:05 scott875-desktop kernel: [ 1034.828013]    prefetch64-sse:  4520.000 MB/sec
Mar 18 12:46:05 scott875-desktop kernel: [ 1034.828020] xor: using function: prefetch64-sse (4520.000 MB/sec)
Mar 18 12:46:05 scott875-desktop kernel: [ 1034.908026] raid6: mmxx1     1901 MB/s
Mar 18 12:46:05 scott875-desktop kernel: [ 1034.976043] raid6: mmxx2     2238 MB/s
Mar 18 12:46:05 scott875-desktop kernel: [ 1035.044071] raid6: sse1x1    1105 MB/s
Mar 18 12:46:05 scott875-desktop kernel: [ 1035.112032] raid6: sse1x2    2176 MB/s
Mar 18 12:46:05 scott875-desktop kernel: [ 1035.180035] raid6: sse2x1    2282 MB/s
Mar 18 12:46:05 scott875-desktop kernel: [ 1035.248017] raid6: sse2x2    3236 MB/s
Mar 18 12:46:05 scott875-desktop kernel: [ 1035.248023] raid6: using algorithm sse2x2 (3236 MB/s)
Mar 18 12:46:05 scott875-desktop kernel: [ 1035.248025] raid6: using intx1 recovery algorithm
Mar 18 12:46:05 scott875-desktop kernel: [ 1035.362287] bio: create slab <bio-1> at 1
Mar 18 12:46:05 scott875-desktop kernel: [ 1035.367568] Btrfs loaded
Mar 18 12:46:06 scott875-desktop os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Mar 18 12:46:06 scott875-desktop 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
Mar 18 12:46:06 scott875-desktop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Mar 18 12:46:06 scott875-desktop 05efi: debug: Not on UEFI platform
Mar 18 12:46:06 scott875-desktop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Mar 18 12:46:06 scott875-desktop 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Mar 18 12:46:06 scott875-desktop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Mar 18 12:46:06 scott875-desktop 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Mar 18 12:46:06 scott875-desktop 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
```

---

### Post by sdowney717 on 2014-03-18
For some reason, the wlan0 is not getting an IP configuration from either wireless router.

I disabled ipv6 but did not help
[http://askubuntu.com/questions/342637/wifi-connect-problem](http://askubuntu.com/questions/342637/wifi-connect-problem)

---

### Post by sdowney717 on 2014-03-18
seeing it was not getting a DHCP IP assignment, why anyone know?
I edit the connection to verizon router and it connected after setting manual ip
192.168.200.3  255.255.255.255 192.168.200.1

Slow  says 11 mb/sec

Also nm generated some kind of edit connection error

---

### Post by sdowney717 on 2014-03-18
Still cant connect to netgear router, but 
I reconnected to verizon router after moving antenna and get 48 mb/sec :)

But without DHCP working makes this mn 730 card not so useful :(

What do you think is preventing DHCP from working?

The netgear router shows very weak signal strenght, so might be why it has some trouble
had to post a shot of the good speed

---

### Post by sdowney717 on 2014-03-18
Well, must be buggy firmware, because, it hard locked up the computer.
It had locked up another PC, and now with my plugging, unplugging cables to various wired routers and trying to connect to various wireless routers it hard locked again.
mouse wont move, numlock key wont change state, keyboard unresponsive, etc...

So unless things change, or people have some better firmware or ideas, I will give up again on this card. I gave up on a few years ago too as I had trouble with it. But I think it used to at least work in earlier ubuntu versions. It is from 2003.

---

### Post by ventrical on 2014-03-20
It actually worked fine with amd64 bit install. I had big problems with Precise but it is detecting and installing here with no problem. (I hadn't tried yesterdays daily as of yet).

---

### Post by ventrical on 2014-03-20
Just curious as to what type of box you are running. I have had probs with Dell lappys and Broadcomm drivers detect.

---

### Post by sdowney717 on 2014-03-20
Board is MSI 7529

has 4GB ddr2, E6550 intel core2duo wd2000 hard drive, I put it together.

[http://us.msi.com/product/mb/G31M3L_V2__G31M3LS_V2.html](http://us.msi.com/product/mb/G31M3L_V2__G31M3LS_V2.html)

There are a lot of variations of this broadcom device

mine is 4306 rev 2

14e4:4325 id

uses b43legacy firmware.

Microsoft PCI MN730 PCI with an external antenna on a long cord.

It hangs on either 64 bit or 32 bit scratch installs.

I have tried the card on 2 different mother boards and get the same thing, wont work, hangs installs and also can lock pc.
It locked on me twice when I was plugging in another usb wifi thing, trying to connect disconnect to wireless routers, trying to make it work.

I think it locked even when the only wifi device in the PC.
Makes me think the firmware could be improved.

---

### Post by westie457 on 2014-03-20
A couple of things you can try.

1, Load the drivers in the LiveDE then go for the install. If it does not hang you might have to reinstall the drivers afterwards as well.
or
2. Turn the wireless chip off if possible for the install then put in the correct drivers.


Disclaimer: I hesitated to post this because I am not using the dev release, only going on past experiences from 2 years ago. These suggestions might not work at all.

---

### Post by sdowney717 on 2014-03-20
It is a pci device,so easy to power off plug and unplug it. If was laptop, maybe has a wireless off switch.

---

### Post by sdowney717 on 2014-03-20
I plugged in my old Gateway router and was able to connect to it using the Mn-730 br43 driver.

BUT, I then tried to connect to my Netgear router and the MN-730 can never do it. 

THEN NM crashed, is there a log file to look at?

So yes, for me buggy wireless

---

### Post by sdowney717 on 2014-03-20
I plugged in my old gateway router daisy chained to the netgear router.
And set it next to the PC I am testing.

I reset both, netgear is at 192.168.1.1, gateway is at 192.168.2.1

setup wireless on both.
Internet works wired fine.
I still cant connect to the netgear with the mn730 broadcom device, But I can connect to the gateway wireless with the broadcom device.
I have an RALink 5370, great little usb wifi widget thingy.
I compared the speeds between these two 802.11g devices. The mn-730 br43 driver is 4 times slower than the ralink 5370.
connection speeds at 48 to 54 mb/sec for both of them.
IMO, the br43 driver must be not very good. I am posting this wireless using the ralink 5370 usb thingy.

the ralink 5370 is close to 20, the br43 mn730 close to 4, and verified with many retests.

---

### Post by sdowney717 on 2014-03-20
post now made with br43 broadcom mn730

I am showing connection info and the wireless list of devices.

wlan0 is the mn730, wlan1 the ralink5370

So why cant I connect to the netgear router with either one? who knows. IMO flakey, wireless is flakey.

---

### Post by sdowney717 on 2014-03-20
Ok, obviously something is really weird with the mn-730 br43 driver device.
I reconnected and did speed test, notice the connection ifo says 48 mb/sec.

The download speed is less than the upload speed.
And much worse than the Ralink 5370 usb wifi thingy.

All I can think is driver is not great or the hardware is not very good.

---

### Post by sdowney717 on 2014-03-20
much better results with ralink 5370 usb wifi

---

### Post by ventrical on 2014-03-20
> **sdowney717 said:**
> Ok, obviously something is really weird with the mn-730 br43 driver device.
I reconnected and did speed test, notice the connection ifo says 48 mb/sec.

The download speed is less than the upload speed.
And much worse than the Ralink 5370 usb wifi thingy.

All I can think is driver is not great or the hardware is not very good.


 I think it is hardware problem related.

---

### Post by cariboo on 2014-03-20
On my netbook with a bcm4312 wireless chipset, I always install with out a network connection, then install bcmwl-kernel-source manually using the usb device I did the installation from. I first install dkms and fakeroot, then install the driver from the command line. Doing it this way, I never have a problem with wireless.

---

### Post by ventrical on 2014-03-20
> **sdowney717 said:**
> Board is MSI 7529

has 4GB ddr2, E6550 intel core2duo wd2000 hard drive, I put it together.

[http://us.msi.com/product/mb/G31M3L_V2__G31M3LS_V2.html](http://us.msi.com/product/mb/G31M3L_V2__G31M3LS_V2.html)

There are a lot of variations of this broadcom device

mine is 4306 rev 2

14e4:4325 id

uses b43legacy firmware.

Microsoft PCI MN730 PCI with an external antenna on a long cord.

It hangs on either 64 bit or 32 bit scratch installs.

I have tried the card on 2 different mother boards and get the same thing, wont work, hangs installs and also can lock pc.
It locked on me twice when I was plugging in another usb wifi thing, trying to connect disconnect to wireless routers, trying to make it work.

I think it locked even when the only wifi device in the PC.
Makes me think the firmware could be improved.

Interesting...

I am just thinking if you would could enable <onboard lan> (if it is not already enabled) and see what happens.

 So far sounds to me like the chip set is not talking to the MoBo correctly..

---

### Post by ventrical on 2014-03-20
> **sdowney717 said:**
> Board is MSI 7529

has 4GB ddr2, E6550 intel core2duo wd2000 hard drive, I put it together.

[http://us.msi.com/product/mb/G31M3L_V2__G31M3LS_V2.html](http://us.msi.com/product/mb/G31M3L_V2__G31M3LS_V2.html)

There are a lot of variations of this broadcom device

mine is 4306 rev 2

14e4:4325 id

uses b43legacy firmware.

Microsoft PCI MN730 PCI with an external antenna on a long cord.

It hangs on either 64 bit or 32 bit scratch installs.

I have tried the card on 2 different mother boards and get the same thing, wont work, hangs installs and also can lock pc.
It locked on me twice when I was plugging in another usb wifi thing, trying to connect disconnect to wireless routers, trying to make it work.

I think it locked even when the only wifi device in the PC.
Makes me think the firmware could be improved.

 Also could be ESD from swapping. Another experiment you could try (I have done this) is take the adapter card out and then get some tin foil and short out all the piano fingers. Hold it there for about 10 seconds. What happens sometimes is that and inerrupt or mem adress gate on the PCI board <in the firmware> will lock up. Dell PCI devices are infamous for this <HID> gate lockup. I have work on several different machines and have seen this a few times. It works with CPUs also comming off a failed overclock. CPU will appear to be dead but when you short the all the pin outs on the CPU in will unlock the offending static ram adress. Of course .. these are my some of my own methods .. do at your own risk :) lol

---

### Post by chili555 on 2014-03-20
> uses b43legacy firmware.Are you quite sure? b43legacy firmware is for the old, old b43legacy driver. Is that what you are using? Or are you using plain old b43 and firmware?```
lsmod | grep b43
```Are there any informative clues here?```
dmesg | grep b43
```> was able to connect to it using the *Mn-730 br43 *driver.What driver is that, exactly?

---

### Post by sdowney717 on 2014-03-20
I did the aluminum foil trick, cant hurt.
helpful?
```
pc875@pc875-desktop:~$ lsmod | grep b43
b43legacy             104081  0 
mac80211              546069  4 rt2x00lib,rt2x00usb,rt2800lib,b43legacy
cfg80211              415503  3 mac80211,rt2x00lib,b43legacy
ssb                    51854  1 b43legacy

pc875@pc875-desktop:~$ dmesg | grep b43
[    0.116873] pci 0000:03:08.0: reg 0x14: [io  0xb400-0xb43f]
[   14.679300] b43legacy-phy0: Broadcom 4306 WLAN found (core revision 4)
[   14.724682] b43legacy-phy0: Loading firmware b43legacy/ucode4.fw
[   14.833098] b43legacy-phy0: Loading firmware b43legacy/pcm4.fw
[   14.921289] b43legacy-phy0: Loading firmware b43legacy/b0g0initvals2.fw
[   21.756055] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
pc875@pc875-desktop:~$ 


```

---

### Post by sdowney717 on 2014-03-20
> **chili555 said:**
> What driver is that, exactly?

I got the driver from ubuntu help pages

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

following these instructions for the legacy driver
> 12.04 (Precise Pangolin) - 12.10 (Quantal Quetzal)

Open a Terminal and if you haven't already done so, update your package list:

sudo apt-get update

If you have a b43 card use the command

sudo apt-get install firmware-b43-installer

or, if you need the b43legacy driver, use:

sudo apt-get install firmware-b43legacy-installer

or, if you need a LP-PHY version (e.g BCM4312), use:

sudo apt-get install firmware-b43-lpphy-installer

Restart the computer or reload the b43/b43legacy module as outlined in the Switching between drivers section below (replace b43 with b43legacy where appropriate).

Note: Since 11.10 the package linux-firmware-nonfree also contains b43 firmware (changelog). This may contain a different/newer version of the firmware depending on release.

Back to top

---

### Post by sdowney717 on 2014-03-20
for some odd reason, netgear connection is always a problem. I had traced it down to a dhcp4 timeout in syslog messages.  When I manually configured the wireless, then it could connect using the Ralink 3570 usb, but not the mn-730 pci wifi card.

This screen will always continue to pop up. The netgear wgt624v3 router is about 20 feet away.
I can connect to an old Gateway WGR-250 or a verizon  westell A90-750115-07 router.

Maybe netgear radio is weak.

---

### Post by chili555 on 2014-03-20
I suppose I was confused. I see no reference to MN-730. Mind If I have another peek:```
lspci -nn | grep 0280
```I suspect 'slow' and 'legacy' go hand-in-hand.

---

### Post by sdowney717 on 2014-03-20
> **chili555 said:**
> I suppose I was confused. I see no reference to MN-730. Mind If I have another peek:```
lspci -nn | grep 0280
```I suspect 'slow' and 'legacy' go hand-in-hand.

sure,

```
pc875@pc875-desktop:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11bg Wireless Network Controller [14e4:4325] (rev 02)
pc875@pc875-desktop:~$ 

```

legacy means slow? That is kinda sad. If the card cant work at it's potential, maybe ought to not exist anymore. This thing gave me grief. What to do with it?

---

### Post by sdowney717 on 2014-03-20
This is the card and antenna
camera did not take a good pic.

---

### Post by sdowney717 on 2014-03-20
looking for complaints about slow performance on the 4306 shows this.
He gets better speed on b vs g.
[http://askubuntu.com/questions/99405/bcm4306-slow-speeds-when-set-to-54mbps](http://askubuntu.com/questions/99405/bcm4306-slow-speeds-when-set-to-54mbps)

sad, very sad. I guess little interest because better options available with usb. And the driver is a firmware hack, not open sourced.

---

### Post by chili555 on 2014-03-20
It is a relatively rare device that uses, as you correctly noted, b43legacy firmware. It is a pretty old, hence legacy, chipset. I am not aware of much you can do aside from unloading the drivers for the RT5370 to troubleshoot so there is no conflict to suspect. You might also try a few changes in your router(s). I'd try with and without N speeds enabled. If you are using N and have any choice about channel width in the 2.4 GHz band, I'd experiment with 20 MHz, 40 MHz and auto. If your router selects the channel automatically, I'd experiment with a fixed channel, probably 1 or 11.

You could give it away to a Windows friend and shop for a supported USB in the US$10-15 range. You could also, as a last resort, live with it.

---

### Post by sdowney717 on 2014-03-20
I looked on seven forums and some people were having trouble installing it.
I think it is like history, over and out. 
I had hoped to put it in the boat computer just to get some use out of it and keep the RaLink 5370 here at the house.
But will revise my course and put the RaLink 5370 on the boat. I bought that 5370 off ebay for about $5 and it works really well.

With a smart phone as a hotspot, I was able to have internet out on the Chesapeake Bay. That was kind of interesting.

---

### Post by sdowney717 on 2014-03-20
A coding error????
And then not fixed, what do you make of that?

[http://forum.slitaz.org/topic/problem-with-b43legacy-driver-limiting-connection-speed](http://forum.slitaz.org/topic/problem-with-b43legacy-driver-limiting-connection-speed)
> It's a limitation of the b43legacy driver:

[http://lingrok.org/history/linux-2.6-stable/drivers/net/wireless/b43legacy/xmit.c](http://lingrok.org/history/linux-2.6-stable/drivers/net/wireless/b43legacy/xmit.c)

b43legacy: Fix failure in rate-adjustment mechanism

A coding error present since b43legacy was incorporated into the
kernel has prevented the driver from using the rate-setting mechanism
of mac80211. The driver has been forced to remain at a 1 Mb/s rate.

Signed-off-by: Larry Finger <Larry.Finger@lwfinger.net>
Cc: Stable <stable@kernel.org> [2.6.26], [2.6.25]
Signed-off-by: John W. Linville <linville@tuxdriver.com>

POSTED 1 YEAR AGO #

---

### Post by chili555 on 2014-03-20
It's hard to tell. Many of the hits in Google suggest a patch was submitted way back in 2008. Moreover, it refers to kernels 2.6.xx which are ancient history. More interesting is your iwconfig which reports 48 MB/s or so.

---

### Post by ventrical on 2014-03-21
During the setup process (with trusty) I now do not tic off  install updates and extra drivers while installing through Ubiquity. Your original post suggests that you may have ticed one of these off ? because I only install the broadcom wireless drivers after I am done install from eth0.

 I am assuming you do a clean install without updates or drivers??

---

### Post by chili555 on 2014-03-21
I suggest you install without installing additional drivers. There are a number of Broadcom devices, and yours may well be one, that installs bcmwl-kernel-source and blacklists the native b43 driver. As you've seen, you need the native b43 driver and b43legacy firmware instead. The additional drivers mechanism is not yet quite refined enough to see this correctly. 

I believe, in 13.10 and 14.04, that the firmware for all the b43s including legacy and lpphy, is included in one big package: linux-firmware-nonfree. A nice step forward!

---

### Post by sdowney717 on 2014-03-21
yes, I always clicked the download updates, install extra software during the installs.

The wireless antenna should have the same cord connection as these. They do make several types of ends.

I might just get one with this so I can at least use my nice antenna, $5

I beleive when I bought my antenna was listed as 7db gain.

[http://www.ebay.com/itm/RT5370-Mini-150Mbps-USB-Wireless-Network-Card-WiFi-LAN-Adapter-Antenna-/190835613615?pt=US_USB_Wi_Fi_Adapters_Dongles&hash=item2c6eb05faf](http://www.ebay.com/itm/RT5370-Mini-150Mbps-USB-Wireless-Network-Card-WiFi-LAN-Adapter-Antenna-/190835613615?pt=US_USB_Wi_Fi_Adapters_Dongles&hash=item2c6eb05faf)
Same chip 5370 which does work great for me.

---

### Post by sdowney717 on 2014-03-21
I have an rt5370 without antenna and it always connects to the Gateway daisy chained router, Netgear is odd radio strength low.
The Netgear wgt624v3 is part of what threw me along with an awful mn730 regarding wireless wifi.

I just pluged it into another ubuntu PC and it simply just works.

Think the usb wifi with an antenna jack would help for further away wifi routers?

did another speed test and works very nice.

---

### Post by chili555 on 2014-03-21
> Think the usb wifi with an antenna jack would help for further away wifi routers?I certainly do.

---

### Post by ventrical on 2014-03-21
> **sdowney717 said:**
> yes, I always clicked the download updates, install extra software during the installs.



^^^ There it is ..

---

