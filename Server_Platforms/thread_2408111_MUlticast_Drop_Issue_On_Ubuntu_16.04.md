---
title: "MUlticast Drop Issue On Ubuntu 16.04"
date: 2018-12-14
forum: Server Platforms
---

### Post by psingh2930 on 2018-12-14
Hello Team,

We have installed an Ubuntu 16.04 LTS on our system to receive multicast packets but we are facing issue with IGMP connection. OUr server leaves the IGMP connection in every 2-3minutes due to which it leaves the UDP packets as well.
The server has 3-4 interface configured.

We tried to resolve the issue by modifying rp_filter to 0 for that interface. Changed the IGMP version to 2.
But nothing worked out. Can you please let us know is there any specific settings to be done to keep the IGMP connection on and stable.

---

### Post by QIII on 2018-12-14
Moved to Server Platforms.

Just to be sure you understand: the Ubuntu Forums is a peer-to-peer end-user forum.

---

