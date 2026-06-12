---
title: "isc-dhcp failover, why use omapi?"
date: 2014-09-21
forum: Server Platforms
---

### Post by richard51 on 2014-09-21
Note: I don't use the **omshell** for controlling my **isc-dhcp** servers.

I have implemented failover on my primary and secondary **isc-dhcp** servers, and this is working fine. I haven't included an **omapi-key**, as I am not sure why it is required (*if at all*) in a failover situation, other than to force a partner-down state, which would require a script. Am I right in thinking, that setting up **omapi** in **dhcpd.conf **is only beneficial if you use scripts, or is there some **automatic** failover communication when using the **omapi-key**... is failover communication more secure if the key is present (*i.e encrypted*)?

---

