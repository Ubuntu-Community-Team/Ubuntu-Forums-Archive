---
title: "Encapsulate (&quot;tunnel&quot;) local outgoing packets using IPsec"
date: 2009-02-12
forum: Security
---

### Post by arrowheart on 2009-02-12
Can I encapsulate an outgoing IP packets using IPsec with different src/dst ip addresses using strongSwan? For example, the local host is 192.168.1.20. An application generates an IP packets destined to 192.168.1.21, but when the packet is passed to IPsec, it is encapsulated (tunneled) using an src ip address of 192.168.1.30 and a dst. address of 192.168.1.31? How can I use ip xfrm or other tools to make it?

Thanks a lot!

---

