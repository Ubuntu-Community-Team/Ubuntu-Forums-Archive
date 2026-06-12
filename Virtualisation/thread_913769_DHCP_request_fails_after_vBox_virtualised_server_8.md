---
title: "DHCP request fails after vBox virtualised server 8.04 is rebooted"
date: 2008-09-08
forum: Virtualisation
---

### Post by aj_watts@optusnet.com.au on 2008-09-08
Here's an interesting one:

I have a Vbox setup:

Intel Quadcore 660:
4GB RAM:
500GB Sata HDD:

Network: Linksys wrtg54 acting as DHCP server

Vbox: 1.6.6
Host: Ubuntu Desktop 8.04.1
Guests: Ubuntu Server 8.04.1 (with ubuntu gnome UI installed), Mythbuntu 8.04.1

Networking is set for DHCP (static IP addressing is not really an option in this build). Bridging and TAP setup seems to be working so far. Both guests grab a DHCP address correctly on the first boot. However, if the guests are rebooted, only the Mythbuntu guest gets refreshed. The server guest fails to get an address.

Watching the DHCP section on the Linksys router, the server is trying to get an address but it never gets issued. Watching the guest (server) boot, the screen shows the trying to get an address but it times out.

An ifconfig on the server guest shows only the loopback interface with an address. ETH0 has no address. The mythbuntu guest gets an address every time.

The only way to resolve the issue so far is to bring down the TAP interfaces and restart networking which is not a very practical option.

Can anyone shed some light on why?

Thanks.......

---

