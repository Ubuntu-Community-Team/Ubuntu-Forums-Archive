---
title: "MAAS with external DHCP?"
date: 2012-05-30
forum: Server Platforms
---

### Post by Tovam on 2012-05-30
After installing Juju on my server, I get an error "ERROR Unexpected Error interacting with provider: 409 CONFLICT". From what I gathered, this means the nodes can't get commissioned because they cannot find the MAAS DHCP server. Makes sense, I already have a DHCP server running on the network, so I didn't want to install another one just for MAAS.

According to [https://wiki.ubuntu.com/ServerTeam/MAAS]("https://wiki.ubuntu.com/ServerTeam/MAAS"), it is possible to handle MAAS with a DHCP server you don't control, but they never mentioned how this is done.

Does anyone know how to approach this, and set up MAAS without installing the MAAS-DHCP package?
Thanks.

---

