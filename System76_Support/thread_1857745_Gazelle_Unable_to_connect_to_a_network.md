---
title: "Gazelle Unable to connect to a network"
date: 2011-10-10
forum: System76 Support
---

### Post by davidk9 on 2011-10-10
Hi,

I've had my Gazelle Professional (Ubuntu 11.04) since June and it's never had an issue. Recently however (last few weeks), its networking performance has been extremely poor. It stopped being able to negotiate a connection with the wireless network at my school (unprotected) and the connection at my apartment (wpa2) is extremely slow (usually about 30k/s) and frequently drops. To work around this issue, I've been connecting via eth0 at school. Tonight however, my wired connection is also failing after restarting the network manager service and the laptop itself.

It looks like the NICs are able to communicate with the devices they are attempting to connect to because it shows small amounts of network traffic but a successful connection is not established.

Any suggestions?

I'm hoping I accidentally changed a setting in the network manager without realizing it, but I'm not sure what it would be.

---

### Post by davidk9 on 2011-10-11
I suspect that this may be an issue with IPv6 addressing. I am able to obtain an IPv6 address for eth0, but have had no success with my wireless connection.

---

### Post by isantop on 2011-10-13
Is your router set up to handle IPv6 addressing? I would recommend disabling it on your internal network.

---

### Post by davidk9 on 2011-10-13
My router is not set up to handle IPv6. I actually haven't gotten a chance to test it because I've been busy with school. The campus network is generally reliable for both wired and wireless connections. I have not been able to connect to this network via either wired or wireless IPv4, but am able to connect with poor performance wired with IPv6.

I'm in the process of backing up my data for an 11.10 fresh install. Hopefully the issue will go away following the upgrade.

Thanks.

---

### Post by davidk9 on 2011-10-15
I'm currently testing the networking capabilities of my laptop from bootable 11.10 flash drive. The wired connection seems to work but I am unable to connect to a wireless network.

The following is the output of "cat /var/log/syslog | grep wlan0 | tail -20"
```
Oct 15 18:54:43 ubuntu avahi-daemon[2709]: New relevant interface wlan0.IPv6 for mDNS.
Oct 15 18:54:43 ubuntu avahi-daemon[2709]: Registering new address record for [mac address] on wlan0.*.
Oct 15 18:54:43 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 15 18:54:51 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 15 18:54:52 ubuntu kernel: [ 1645.875304] wlan0: no IPv6 routers present
Oct 15 18:55:01 ubuntu NetworkManager[2753]: <info> (wlan0): IP6 addrconf timed out or failed.
Oct 15 18:55:01 ubuntu NetworkManager[2753]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Oct 15 18:55:01 ubuntu NetworkManager[2753]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Oct 15 18:55:01 ubuntu NetworkManager[2753]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Oct 15 18:55:01 ubuntu NetworkManager[2753]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Oct 15 18:55:01 ubuntu NetworkManager[2753]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Oct 15 18:55:01 ubuntu NetworkManager[2753]: <warn> Activation (wlan0) failed for access point ([my campus network])
Oct 15 18:55:01 ubuntu NetworkManager[2753]: <warn> Activation (wlan0) failed.
Oct 15 18:55:01 ubuntu NetworkManager[2753]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 15 18:55:01 ubuntu NetworkManager[2753]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Oct 15 18:55:01 ubuntu NetworkManager[2753]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct 15 18:55:01 ubuntu NetworkManager[2753]: <info> (wlan0): deactivating device (reason 'none') [0]
Oct 15 18:55:01 ubuntu NetworkManager[2753]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 15640
Oct 15 18:55:01 ubuntu kernel: [ 1655.408179] wlan0: deauthenticating from 00:22:90:92:d2:6f by local choice (reason=3)
Oct 15 18:55:02 ubuntu NetworkManager[2753]: <info> (wlan0): supplicant interface state: completed -> disconnected

```

I suspect this post may be more general to Ubuntu and may not necessarily be specific to my System76 laptop.

---

