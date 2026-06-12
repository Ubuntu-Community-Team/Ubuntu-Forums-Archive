---
title: "DHCP lease file"
date: 2018-01-27
forum: Server Platforms
---

### Post by sniper8752 on 2018-01-27
I am running Ubuntu server 16.  I am using isc-dhcp-server for DHCP.  I noticed in my dhcpd.leases file, that there are redundant IPs with the same device.  Is this normal?

---

### Post by wildmanne39 on 2018-01-27
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by SeijiSensei on 2018-01-28
Check the expiration dates. I think you'll see that the redundant entries have expired. At least that's what I recall when I had the same question as you some years back.

---

