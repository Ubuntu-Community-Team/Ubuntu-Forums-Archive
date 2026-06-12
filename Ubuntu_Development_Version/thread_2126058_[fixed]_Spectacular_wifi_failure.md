---
title: "[fixed] Spectacular wifi failure"
date: 2013-03-15
forum: Ubuntu Development Version
---

### Post by deaconmacmillan on 2013-03-15
looks like an update fixed this for me. Thanks!


while working ok on the install usb drive when I try to use the wireless after installing, the signal cuts out and the the network icon dissappears about once every two seconds. then re-connects then fails and dissappears again.

here is some of the log file at the time

```
: <info> WiFi hardware radio set enabled
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> WiFi enabled by radio killswitch; enabled by state file
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> WWAN enabled by radio killswitch; enabled by state file
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> WiMAX enabled by radio killswitch; enabled by state file
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Networking is enabled by state file
Mar 16 09:18:48 leatherback NetworkManager[5861]: <warn> failed to allocate link cache: (-10) Operation not supported
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (eth0): carrier is OFF
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (eth0): preparing device.
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (eth0): deactivating device (reason 'managed') [2]
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/eth0
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (wlan0): using nl80211 for WiFi device control
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (wlan0): driver supports Access Point (AP) mode
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8192ce' ifindex: 3)
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (wlan0): preparing device.
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar 16 09:18:48 leatherback NetworkManager[5861]: <warn> failed to allocate link cache: (-10) Operation not supported
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (easytether0): carrier is ON
Mar 16 09:18:48 leatherback NetworkManager[5861]: <error> [1363393128.409453] [nm-device-ethernet.c:443] update_permanent_hw_address(): (easytether0): unable to read permanent MAC address (error 0)
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (easytether0): new Ethernet device (driver: 'easytether' ifindex: 4)
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (easytether0): exported as /org/freedesktop/NetworkManager/Devices/2
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (easytether0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (easytether0): preparing device.
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (easytether0): deactivating device (reason 'managed') [2]
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Added default wired connection 'Wired connection 2' for /sys/devices/virtual/net/easytether0
Mar 16 09:18:48 leatherback NetworkManager[5861]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Mar 16 09:18:48 leatherback NetworkManager[5861]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (wlan0) supports 4 scan SSIDs
Mar 16 09:18:48 leatherback NetworkManager[5861]: <warn> Trying to remove a non-existant call id.
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (wlan0): supplicant interface state: starting -> ready
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (easytether0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Auto-activating connection 'Wired connection 2'.
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (easytether0) starting connection 'Wired connection 2'
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (easytether0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (easytether0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (easytether0) Stage 1 of 5 (Device Prepare) started...
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (easytether0) Stage 2 of 5 (Device Configure) scheduled...
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (easytether0) Stage 1 of 5 (Device Prepare) complete.
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (easytether0) Stage 2 of 5 (Device Configure) starting...
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (easytether0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (easytether0) Stage 2 of 5 (Device Configure) successful.
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (easytether0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (easytether0) Stage 2 of 5 (Device Configure) complete.
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (easytether0) Stage 3 of 5 (IP Configure Start) started...
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (easytether0): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (easytether0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> dhclient started with pid 5864
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (easytether0) Beginning IP6 addrconf.
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (easytether0) Stage 3 of 5 (IP Configure Start) complete.
Mar 16 09:18:48 leatherback dhclient: Internet Systems Consortium DHCP Client 4.2.4
Mar 16 09:18:48 leatherback dhclient: Copyright 2004-2012 Internet Systems Consortium.
Mar 16 09:18:48 leatherback dhclient: All rights reserved.
Mar 16 09:18:48 leatherback dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Mar 16 09:18:48 leatherback dhclient: 
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (wlan0): supplicant interface state: ready -> completed
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (wlan0) supports 4 scan SSIDs
Mar 16 09:18:48 leatherback dhclient: Listening on LPF/easytether0/ea:8b:b2:ca:11:39
Mar 16 09:18:48 leatherback dhclient: Sending on   LPF/easytether0/ea:8b:b2:ca:11:39
Mar 16 09:18:48 leatherback dhclient: Sending on   Socket/fallback
Mar 16 09:18:48 leatherback dhclient: DHCPDISCOVER on easytether0 to 255.255.255.255 port 67 interval 3 (xid=0xb2ad527)
Mar 16 09:18:48 leatherback dhclient: DHCPREQUEST of 192.168.117.2 on easytether0 to 255.255.255.255 port 67 (xid=0xb2ad527)
Mar 16 09:18:48 leatherback dhclient: DHCPOFFER of 192.168.117.2 from 192.168.117.1
Mar 16 09:18:48 leatherback dhclient: DHCPACK of 192.168.117.2 from 192.168.117.1
Mar 16 09:18:48 leatherback dhclient: bound to 192.168.117.2 -- renewal in 2147483648 seconds.
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (easytether0): DHCPv4 state changed nbi -> preinit
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (easytether0): DHCPv4 state changed preinit -> bound
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info>   address 192.168.117.2
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info>   prefix 24 (255.255.255.0)
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info>   gateway 192.168.117.1
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info>   nameserver '8.8.8.8'
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info>   nameserver '8.8.4.4'
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (easytether0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Auto-activating connection 'open Network'.
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (wlan0) starting connection 'open Network'
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 16 09:18:48 leatherback NetworkManager[5861]: <info> Activation (easytether0) Stage 5 of 5 (IPv4 Commit) started...
Mar 16 09:18:49 leatherback ntpdate[5807]: sendto(91.189.94.4): Connection timed out
```

---

### Post by tgalati4 on 2013-03-15
Your network stack appears to be working.  Perhaps you are getting interference from a neighbor?  How many wifi's do you see when you click on the wireless network icon?

---

### Post by deaconmacmillan on 2013-03-15
there are several networks in the area, but It works on quantal, mint and every other os I have tried. stranger even yet is it works on the live invironment.

---

### Post by serdotlinecho on 2013-03-17
> **deaconmacmillan said:**
> there are several networks in the area, but It works on quantal, mint and every other os I have tried. stranger even yet is it works on the live invironment.

I confirmed this bug, happened to me also. When i switch to my neighbours network, it will connect but for only like 2-3 seconds. Then it will disconnect and reconnect again, disconnect and reconnect again. Here's my wireless network card and i'm using the open source driver:

```
~&#10095; lspci | grep Network
05:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```

---

### Post by nomenkultur on 2013-03-17
open your router logs and you will see 'authentication failed' etc etc

---

### Post by teachop on 2013-03-17
My case may not be related since my laptop is not Broadcom but... my Ralink RT5390 Wifi started bouncing last night.  It had been stable with 13.04 up until now.  My laptop is running the Xubuntu 13.04 version.

---

### Post by deaconmacmillan on 2013-03-17
leaving it to bounce for about 5 minutes sometimes settles things down. If i run an update sometimes it connects. I think the live environment works because it is pre patch of death for that wireless card.

---

