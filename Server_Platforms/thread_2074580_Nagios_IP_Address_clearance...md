---
title: "Nagios IP Address clearance.."
date: 2012-10-21
forum: Server Platforms
---

### Post by veesyndicate on 2012-10-21
Hye guys. I want to ask about nagios, is it better to let the ubuntu server which i have configure nagios on it to use loopback address 127.0.0.1 or change it to static ip? for your information, i running the ubuntu server inside my laptop using vmware workstation, and will implement the nagios on real virtual server on my office as soon as possible. What suggestion for my best practices? Thanks

---

### Post by LHammonds on 2012-10-22
You will want Nagios on a static IP address.  That will allow your remote servers (that you monitor) know what IP it should trust to run remote commands as well as firewall rules.  Check my sig for how I setup my Nagios server which monitors all my Windows/Linux servers, PCs, switches and printers.

LHammonds

---

### Post by veesyndicate on 2012-11-04
> **LHammonds said:**
> You will want Nagios on a static IP address.  That will allow your remote servers (that you monitor) know what IP it should trust to run remote commands as well as firewall rules.  Check my sig for how I setup my Nagios server which monitors all my Windows/Linux servers, PCs, switches and printers.

LHammonds


Thanks for suggestion LHammonds. I just follow your guides, it is very helping me. Very clear explanation, and included all the configuration that i need to set. Thank you very much! =)

---

### Post by LHammonds on 2012-11-05
;)

---

