---
title: "dhclient no longer renews lease"
date: 2016-02-28
forum: Ubuntu Development Version
---

### Post by Doug S on 2016-02-28
As of yesterdays update, there was an update to isc-dhcp-client 4.3.3-5ubuntu8 from "7", at least partially to address [this bug]("https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1549736"), which does appear to have been fixed.

However, now my system is not renewing the lease of its IP address from my ISP. (while I have static IP adresses, my ISP still requires using dhcp). So today, exactly 24 hours since my last re-boot (the expire time), internet stopped working.

Anybody else observing this issue?

---

### Post by Doug S on 2016-02-29
Bump.

Nobody else observing this?
I can see that my lease is still not renewing, and I will have a problem in about 1 hour and 20 minutes. I'm going to let it happen, just to be sure.

EDIT: My lease lapsed.

EDIT: [link to bug report]("https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1551351")

---

