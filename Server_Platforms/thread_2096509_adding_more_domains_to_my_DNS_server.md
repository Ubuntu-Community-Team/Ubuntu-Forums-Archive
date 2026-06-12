---
title: "adding more domains to my DNS server"
date: 2012-12-20
forum: Server Platforms
---

### Post by Toriku on 2012-12-20
when adding domains to my DNS server, do I need to add more master zones with their own db file? Or must I do it differently? The tutorials online aren't very clear about that.

> zone "example.com" {
	type master;
        file "/etc/bind/db.example.com";
};

---

### Post by darkod on 2012-12-20
I don't use DNS much, but I would say separate zones for each domain (forward and reverse), and separate zone files also.

---

### Post by Toriku on 2012-12-20
yep, that seems to work just fine

---

