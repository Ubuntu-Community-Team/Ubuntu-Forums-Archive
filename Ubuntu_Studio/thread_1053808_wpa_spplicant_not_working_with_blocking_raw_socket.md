---
title: "wpa_spplicant not working with blocking raw socket"
date: 2009-01-29
forum: Ubuntu Studio
---

### Post by syuga on 2009-01-29
Hi folks,

I am using a wpa_supplicant for fedora with madwifi driver to simulate multiple wireless clients. It creates multiple virtual interfaces over a physical wireless i/f.

Each virtual wireless client is a process and opens a raw socket connection to receive/send 802.11 packets.

The problem I am facing is that each process has to poll the socket, to check if a packet matching its MAC address has arrived. It only works if the socket is non-blocking. If I make the socket blocking and use select(), none of the process receive any packets over raw socket. I am not able to figure out the reason for this behaviour and also you may agree that polling is a clumsy design. Appreciate if someone could shed some light on this behaviour and suggest better ideas to overcome this problem.

Thanks,
syuga

---

