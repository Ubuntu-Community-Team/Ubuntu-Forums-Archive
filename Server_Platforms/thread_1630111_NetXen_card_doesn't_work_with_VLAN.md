---
title: "NetXen card doesn't work with VLAN"
date: 2010-11-24
forum: Server Platforms
---

### Post by BizonGod on 2010-11-24
Hello!
 I have HP DL380 G7 with NC522SFP NIC (Qlogic QLE3142-CU-CK) and
Netgear GSM7352S-200 switch.
 When using integrated 1Gbps NICs I configured few VLANs on 
switch and on NICs. All worked good. When I switched do 10Gbps NIC,
it seems VLAN doesn't work - all packets goes to raw device.
 I'm enclosing ifconfig, interfaces.
 What can be wrong?

After looking on tcpdump -e I can see vlan marked packets on
eth1, unmarked on eth1.50. On eth5 comes marked too, but
nothing goes to eth5.50

It seems is some bridge related thing.
When not using bridge (used for VM) it works ok.


Thanks
Karol

---

