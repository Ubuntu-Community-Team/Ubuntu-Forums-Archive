---
title: "Matching issues with dl_vlan and arp packets"
date: 2014-05-08
forum: Virtualisation
---

### Post by tommyprep on 2014-05-08
Hi,

I have a simple setup 

Box1 --- (Port-1) OVS (Port-2) ---- Box2

All the 3 machines are in Virtual Box.
Additionally I have installed OVS-1.11.0 in the middle box.

My test case to send the tagged Arp request/reply from Box1 to Box2.
My rule is simple in_port=1,dl_vlan=10,dl_type=0x806,actions=strip_vlan,output:2


2 Issues I am facing :-
  a. Arp Request from Box1 to Box2 is not matching the rule (packet can be seen port Port-1)
  b. The arp response from Box1 to Box2 is not even coming in tcpdump for box2 (packet not seen on Port-1).

Untagged Arp request seems fine. Anyone seen any issues on similar lines.

---

