---
title: "1 DHCP server on multiple interfaces"
date: 2020-03-17
forum: Server Platforms
---

### Post by jxm92 on 2020-03-17
Hi,

I have 3 interfaces: eth0, eth1 & wlan0.
the eth0 is used for WAN, but I want to use the eth1 & wlan0 interfaces on 1 LAN.
How do I do that? So far I have the Wifi Hotspot working, can get IP and Internet connection, but on the eth1 interface there is no ip given.
I've been searching for a solution but I only find how to make both work on different IP ranges, but I want both to work on the same IP range, like a router would.

Previously I wanted to bridge eth0 and eth1 in a way that both are on the same WAN and the wlan0 on a different LAN, but I couldn't understand how to make bridge interfaces work.

I'm kinda new on this, not a total begginer but usually I configure this with an "easy tool" or an easy-to-understand guide, and I haven't found one for this.

I want to understand how hostapd, dnsmasq, dhcpcd and ifup work together in a simple way, once I understand that, the technical stuff will be easy to understand.

Thanks

---

### Post by SeijiSensei on 2020-03-18
You could try setting

```
INTERFACES="eth1 wlan0"
```

in /etc/default/isc-dhcp-server as described in [https://help.ubuntu.com/community/isc-dhcp-server#dhcp3-server_and_multiple_interfaces](https://help.ubuntu.com/community/isc-dhcp-server#dhcp3-server_and_multiple_interfaces).

I've not done this, so I can't endorse this approach based on experience.

---

