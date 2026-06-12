---
title: "Secondary DHCP server configuration with Named update ?"
date: 2009-02-15
forum: Server Platforms
---

### Post by zeevikn on 2009-02-15
Hi.

I'm happily using DHCP3 server and Named (Bind9), allowing the DHCP3 server to dynamically update the Named server.

For redundancy, I want a second backup server.
Configuring a slave Named server is easy (and done )
configuring another DHCP server is relatively easy.

Sync between all 4 entities is my question.

1) How to update the two Named servers? Can I configure the DHCP server to update both servers ?
I can set the secondary DHCP server to update the master Named server, which will update the slave Named server. But, what happens when the master server is down ?

2) Sync between the two DHCP server (not sure it is required, as the DHCP client can select from two different sources, and the DHCP servers verify the address not used)

TIA,
Zeevik.

(posted earlier on networking forum, but I guess this is the place to ask)

---

