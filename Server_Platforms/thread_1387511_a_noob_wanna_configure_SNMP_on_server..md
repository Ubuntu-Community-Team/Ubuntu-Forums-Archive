---
title: "a noob wanna configure SNMP on server."
date: 2010-01-21
forum: Server Platforms
---

### Post by cataztrophe on 2010-01-21
hello there,
finnaly i can run my ubuntu server 9.04 well, thnx to this great member of ubuntuforums.org :popcorn:

now, i wanna i wannna install SNMP on my system, but after i do that, when i wanna connect with another client, it give me error like this :
```
no response received
SNMPv1_Session (remote host: "10.100.7.179" [10.100.7.179].161)
                  community: "public"
                 request ID: 862383236
                PDU bufsize: 8000 bytes
                    timeout: 2s
                    retries: 5
                    backoff: 1)
 at /usr/share/perl5/SNMP_util.pm line 629
SNMPWALK Problem for 1.3.6.1.2.1.1 on public@10.100.7.179::::::v4only
 at /usr/bin/cfgmaker line 957
WARNING: Skipping public@10.100.7.179: as no info could be retrieved
```
10.100.7.179 is my client, i allready install snmp agent on it. but why still eror then? plz give some help. thnx before :D

---

### Post by cataztrophe on 2010-01-23
can anyone help me plzzz....:(:(

really need your hand guys:popcorn:

---

### Post by rocketsami on 2011-11-27
If you have a device specially firewall then you have to allow the traffic to and from the device you want to monitor .I do not think it is the problem of snamp or mrtg.Mine was solved only by allowing all traffic from mrtg machine to the device i was trying to monitor (cisco 3825).Well you can be specific but i allow all IP traffic. Try it this way bro.

---

### Post by jonobr on 2011-11-28
Any chance your agent doesn't support SNMPV1?
Most devices support SNMPV2 and V1 has by and large been forgotten and is incompatible with V2.
The message structure especially header dont conform to that of V2.

To get around this incompatibility, you would need use a proxy or a NMS that understands both,


SNMPV3 is out there a long time and introduces a lot better security but seems not to be used as V3

Additional-Just noticed, last post from the user cataztrophe is nearly 2 years old..........
Im sure he has moved on

---

