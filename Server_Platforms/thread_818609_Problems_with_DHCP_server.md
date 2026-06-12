---
title: "Problems with DHCP server"
date: 2008-06-04
forum: Server Platforms
---

### Post by xzased on 2008-06-04
Hi. I want to "bypass" my sonicwall and move dhcp and dns services to my server. My public IP is 216.x.x.x and my internal is 10.x.x.x on the sonicwall. I have set eth1 as 216.x.x.x and eth0 as 10.2.1.1 and installed dhcp and dns services, but when I hook it up it doesnt work... I dont know what Im missing. I have the wan connected to eth1 and eth0 to the switch (dunno if this is right though:confused:)On my dhcp config I have set 10.2.1.1 as default gateway, search domain as none, primary name server is opendns... I just dont know what Im doing wrong....

---

### Post by quelx on 2008-06-04
When you say *bypass* do you mean take it out of the picture all together or will it still be connected to your cable/dsl/T1/modem/whatevergetsyouontheInternet?

---

### Post by xzased on 2008-06-04
yep, I mean taking it out of the picture :guitar:

---

### Post by quelx on 2008-06-04
> **xzased said:**
> yep, I mean taking it out of the picture :guitar:

Have you installed any routing/NAT/firewall tools?

If not you probably need to have a looksee
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

---

