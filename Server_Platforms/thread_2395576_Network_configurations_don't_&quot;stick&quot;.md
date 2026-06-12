---
title: "Network configurations don't &quot;stick&quot;"
date: 2018-07-03
forum: Server Platforms
---

### Post by jonathanese on 2018-07-03
I'm running the latest Ubuntu Server as of today. I have a server acting as a router, DHCP server, and DNS server. I'm managing it using WebMin.


Anyway, each time I reboot my computer, my entire network is down until I explicitly go to the server itself and do **netplan apply. **At that point, I can ssh in and then go into WebMin>Linux firewall and apply my packet filtering and packet alteration profiles. As far as I know, both are set to be configured at bootup, yet I still have to configure them at every reboot in order to keep my network up. So it gets to be a pain.

Anyone know what's going on here?

EDIT 1: OK, so I installed persistent iptables which should help with the firewall setting. Apparently my **netplan appl** problem is a known issue. Know any workarounds?

---

### Post by wildmanne39 on 2018-07-03
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by LHammonds on 2018-07-04
Do you have any desktop environment on this server that could be conflicting with NetPlan?

Reference: [Netplan does not apply at startup](https://askubuntu.com/questions/1019146/netplan-does-not-apply-at-startup)

LHammonds

---

### Post by jonathanese on 2018-07-04
Nope. Just Webmin and Pihole.

---

