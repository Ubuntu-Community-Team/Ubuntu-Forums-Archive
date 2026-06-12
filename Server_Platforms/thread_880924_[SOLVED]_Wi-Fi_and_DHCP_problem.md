---
title: "[SOLVED] Wi-Fi and DHCP problem"
date: 2008-08-05
forum: Server Platforms
---

### Post by PryGuy on 2008-08-05
Hello there! I've got a ICS/File/DHCP server and I want to make a Wi-Fi hotspot on it. I have installed madwifi fine, I configured it and I can see the wireless network from my notebook. But I cannot make DHCP server work on both eth0 and ath0 interfaces. I think that dhcp3 can offer DHCP leases to one interface only. I think that I theoretically can make another rule with different range of IPs for another interface, but is that possible to share the same IP range for different interfaces?
Thank you!

---

### Post by cdenley on 2008-08-05
> **PryGuy said:**
> Hello there! I've got a ICS/File/DHCP server and I want to make a Wi-Fi hotspot on it. I have installed madwifi fine, I configured it and I can see the wireless network from my notebook. But I cannot make DHCP server work on both eth0 and ath0 interfaces. I think that dhcp3 can offer DHCP leases to one interface only. I think that I theoretically can make another rule with different range of IPs for another interface, but is that possible to share the same IP range for different interfaces?
Thank you!

How do you have the network interfaces configured? It sounds like you might want to bridge the wired and wireless interfaces.

---

### Post by PryGuy on 2008-08-06
Thank you for the hint! Will try it out this evening! The only question I have is which interfaces should I marry? I've got eth0 (LAN), eth1(Internet), ppp0(a PPTP tunnel) and ath0(wi-fi). That's probably will be eth0 and ath0?

---

### Post by StickyStyle on 2008-08-06
You correct, dhcpd will only listen on one interface at a time.  
There are a few traditional ways on handling this; one is to run a copy of dhcpd bound to each interface with that networks config file, the second is to setup a dhcp relay agent on the second interface.  I would recommend the second route of a relay agent (package dhcp3-relay) as the first method is going to require you to muck around with the init scripts  and is more of a hack in the ubuntu world.  The dhcp relay agent will sit running on your second interface (the one dhcpd is not bound to) and listen for dhcp requests, when it gets one it relays it to the dhcpd daemon which in turn sends it back to the relay agent, and the relay agent fires it back to the client.

---

### Post by PryGuy on 2008-08-08
Thanks, I've solved it, bridging helped! Thank you!

---

