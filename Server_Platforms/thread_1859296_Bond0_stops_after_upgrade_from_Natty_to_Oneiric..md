---
title: "Bond0 stops after upgrade from Natty to Oneiric."
date: 2011-10-13
forum: Server Platforms
---

### Post by kelargo on 2011-10-13
I upgraded my server (not workstation) from Natty to Oneiric.
I had a bonded interface in Natty that worked. After the upgrade is doesnt work.

Specifically, The interface bond0 does come up. I am able to ping that interface. but I'm not able to transmit over the interface.
I can not ping my default gateway anymore.
The server's NICs are connected to a cisco switch which shows the channel group as "up".
I see both inbound and outbound traffic on the switch.

I'm not sure where to start to troubleshoot this, since everything appears to be restored after the upgrade.

The only change is the upgrade from Natty to Oneiric.

---

### Post by kelargo on 2011-10-13
PS -  I'm using LACP

---

### Post by kelargo on 2011-10-13
this is really confusing..

The server is showing up in the switch's arp table:
but from the switch, I can' ping the server.  No access lists in the switch.

Did the upgrade to Oneiric enable a firewall by default?  Have to go look at the server. When I ran tcpdump on Bond0, all I saw were LACP messages.

> [FONT="Courier New"]#sh arp 
Protocol  Address          Age (min)  Hardware Addr   Type   Interface
Internet  192.168.0.50            0   0030.48bb.2431  ARPA   Vlan160
Internet  192.168.0.1             9   001c.f058.f2e7  ARPA   Vlan160[/FONT]


and the MAC table on the switch shows the server's MACs. 

> [FONT="Courier New"]#sh mac-address-table              
          Mac Address Table
-------------------------------------------

Vlan    Mac Address       Type        Ports
----    -----------       --------    -----
 160    0030.48bb.2430    DYNAMIC     Po1
 160    0030.48bb.2431    DYNAMIC     Po1[/FONT]


---

