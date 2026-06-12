---
title: "udp outbound packets - should I be concerned about these ?"
date: 2009-02-24
forum: Server Platforms
---

### Post by mistypotato on 2009-02-24
I have iplist/ipblock set up on my server.

I see entries outbound for some firms I am unfamiliar with was wondering if anyone had any comment on them.

The packet destinations are to one of the following....

VelocityNetworks,Inc
PerdueUniversity
DVLabs,Inc
CoreExpress3
WKL.L.C.
PhyberCommunications-MediaDefender


I guess my real question is does anyone know if these are normal sites contacted for ubuntu updates etc or does anyone know if these are indications of something suspicious going on?

thx

---

### Post by koenn on 2009-02-24
do you know what udp port they're going to ?

it's probably not updates because they'd use tcp.
It might be simply your computer syncing its clock with time servers on the internet. The port number should give an indication of what service/application is causing this.

---

### Post by 3L33T on 2009-02-24
> **mistypotato said:**
> I have iplist/ipblock set up on my server.



I'm not familiar with iplist/ipblock.   I use NTOP.  It shows me the originating LAN ip addresses who contacted the remote sites.

---

### Post by freerkkalsbeek on 2009-02-24
With  netstat your able to connect the outgoing connections to processes. That could give you a hint on the purpose of the connections.

Be specially aware for connections to ports 6666/6667 which are standard IRC ports and typically often used by rootkits.

Since it's UDP I suspect DNS traffic (port 53 udp/tcp)

Regards,
Freerk

---

