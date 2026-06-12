---
title: "Domain Name System"
date: 2008-08-25
forum: Security
---

### Post by Camilia on 2008-08-25
A fatal flaw with the Domain Name System is being exploited in Internet attacks.  Read this at CNet. Will this affect us with linix

---

### Post by y@w on 2008-08-25
Well.. yes.. it's a design flaw with DNS as a whole. There's patches out for bind for all distros. Just apply your patches :)

---

### Post by mattydee on 2008-08-26
I've recently applied the Bind patch to my Ubuntu DNS server. Now, I can see that source port randomization is occurring, but does applying the patch clear the DNS cache automatically? (Just in case the cache had already been compromised).

One would think it ought to, but I thought I'd ask hoping somebody has a definite answer on this. 

Thanks

---

### Post by joebeasley on 2008-08-26
Restarting bind after patching will clear the cache.

---

