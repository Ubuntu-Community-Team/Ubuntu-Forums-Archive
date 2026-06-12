---
title: "IP and Mac addresses for thin clients"
date: 2009-01-23
forum: Virtualisation
---

### Post by xesusmx on 2009-01-23
Hi! I'm Running a DHCP server in Ubuntu, How can i get the IP and Mac Adresses for each client?

Thank u :)

---

### Post by dcstar on 2009-01-25
> **xesusmx said:**
> Hi! I'm Running a DHCP server in Ubuntu, How can i get the IP and Mac Adresses for each client?

Thank u :)

```
arp -a
```

will show you all external connections with this info.

---

