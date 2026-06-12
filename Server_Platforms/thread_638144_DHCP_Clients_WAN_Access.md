---
title: "DHCP Clients WAN Access"
date: 2007-12-11
forum: Server Platforms
---

### Post by WIGGMPk on 2007-12-11
First off, im unfortunatly at work right now so providing info may be limited. Although I do have Webmin and SSH access to the server.

------ THIS CONFIGURATION WORK PREVIOUSLY -----

MODEM ---- SERVER ---- ACCESS POINT ---- CLIENTS

_Modem_
Cable Modem

_Server_
Ubuntu Gutsy Gibbon Server - amd64
eth0 - TO MODEM (Gets IP from ISP DHCP)
eth1 - TO ACCESS POINT (Serves DHCP Requests)

_Access Point_
Linksys WRT54GS (Flashed with OpenWRT Firmware)
WAN Port Assigned to Switch
DHCP Forwarder set to eth1 Address

_Clients_
iMAC - MAC OSX Tiger
Laptop - Ubuntu Gutsy Gibbon Desktop - amd64

There are other clients that are not attached to this access point yet.

------------------------------------------------------------------------------------------

The situation that im having is with the Laptop.

It can do the following:
Connect to the Access Point (Wirelessly/Wired)
Recieve an IP from eth1 (Wirelessly/Wired)

It can NOT do the following:
**ALL** WAN/LAN websites get page cannot be displayed
Ping eth1 static address (returns with network unreachable)
Ping google.com / google's IP (returns with host name unknown / network unreachable)

The iMAC however is operating perfectly fine.
The Server is also operating perfectly fine.

Things I have tired:
```
sudo /etc/init.d/networking stop
sudo ifconfig eth1 192.168.1.125
sudo route add default gw 192.168.1.1
```

This does not work, out of sheer hope I decided to change to a CLASS B IP address and try a 172.20.192.1 configuration for eth1 on the Server. Again, the iMAC works and the Laptop does not (except for getting an IP)

Why can this laptop talk to the server and get an IP but go no where else? Why can it NOT ping the server less then 5 seconds after getting an IP from  it? I am confused, I have reinstalled twice on the laptop and have also booted with the LIVECD several times.

My firewall rules are not outragious. But they do drop incoming requests by default. Ill post those rules below because I have them handy. However I do not think this effects my situation.

**_Firewall Rules:_**
**_Packet Filtering:_**
**Incoming Packets (INPUT) - Default Action "DROP"**
Accept - If input interface is eth1
Accept - If input interface is lo
Accept - If input interface is eth0 and state of connection is ESTABLISHED, RELATED
Accept - If protocol is TCP and destination port is 10000
Accept - If protocol is TCP and destination port is 22

**Forwarded Packets (FORWARD) - Default Action "DROP"**
Accept - If input interface is eth1 and output interface is eth0
Accept - If input interface is eth0 and output interface is eth1 and state of connection is ESTABLISHED, RELATED

**Outgoing Packets (OUTPUT) - Default Action "ACCEPT"**
There are no rules defined for this chain.

**_Network Address Translation:_**
**Packets Before Routing (PREROUTING) - Default Action "ACCEPT"**
Accept - If input interface is eth1
Accept - If input interface is lo
Accept - If input interface is eth0 and state of connection is ESTABLISHED, RELATED

**Outgoing Packets (OUTPUT) - Default Action "ACCEPT"**
There are no rules defined for this chain.
[B]
Packets After Routing (POSTROUTING) - Default Action "ACCEPT"[/B]
Masquerade - If output interface is eth0


If I need to provide more information, I will happily supply it. Im about to shoot myself.

Thanks in advance.

---

