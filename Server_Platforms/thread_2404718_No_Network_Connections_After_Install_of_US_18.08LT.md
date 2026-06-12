---
title: "No Network Connections After Install of US 18.08LTS"
date: 2018-10-27
forum: Server Platforms
---

### Post by mhumm2 on 2018-10-27
So, like the Title states, I installed US 18.04LTS to my Supermicro X9SCM-F mobo.  After the OS boots without any errors, the IPMI LAN is active, and LAN1 is active, but LAN2 is not active.  Moreover, I have no access to the LAN1.  ifconfig cites only the lo interface for loopback.  Please advise.

mhumm2

---

### Post by darkod on 2018-10-27
Were the network interfaces detected during installation and did you setup static ip on lan1?
Was the network cable plugged in during install?

---

