---
title: "Ata-over-Ethernet questions."
date: 2009-11-09
forum: Server Platforms
---

### Post by mysteron on 2009-11-09
Hi.

I'm trying out Ata-over-Ethernet in Ubuntu 9.10 x86-64, and have some questions.

eth1 is the nic I want to use for AoE, is

```
auto eth1
iface eth1 inet manual
```

enough to get ubunut to start up eth1 ip-less?

Do I need to do anything more than tell /etc/default/aoetools that it should look for shared resources from eth1?

eth0 is used for external networking connections, and I have to use eth1 for AoE.

Feedback will be greatly appreciated.


Thx,
/mysteron

---

### Post by becvert on 2009-11-09
is eth1 your NIC on the AoE client?

---

### Post by mysteron on 2009-11-10
> **becvert said:**
> is eth1 your NIC on the AoE client?

Yes, eth1 is the NIC on the AoE client.


/mysteron

---

### Post by becvert on 2009-11-13
did it work?

---

