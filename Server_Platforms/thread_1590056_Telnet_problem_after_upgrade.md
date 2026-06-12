---
title: "Telnet problem after upgrade"
date: 2010-10-07
forum: Server Platforms
---

### Post by vnq on 2010-10-07
Hallo,
we have a sever on which we made an upgrade from Ubuntu 8.04 to Ubuntu 10.04

We use telnet to access from one local machine to another in our local LAN, but after the upgrade, when we try to connect to our server from a client on LAN we receive the following error:

Trying <Server IP  address>...
Connected to server.our.domain
Escape character is '^]'.
telnetd: All terminal ports in use.
Connection closed by foreign host.

Is there any known issue about problems in telnetd and Ubuntu 10.04?
Thank you very much for your help!

---

### Post by viralmeme on 2010-10-07
> **vnq said:**
> telnetd: All terminal ports in use
Is telnetd running as root?

---

