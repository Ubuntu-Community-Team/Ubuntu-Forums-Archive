---
title: "Authenticate MySQL only from certain pages?"
date: 2007-04-02
forum: Server Platforms
---

### Post by tomplast on 2007-04-02
I am wondering if there is any way to configure MySQL so it only will accept connections from a certain page (like dbcons.php), does anyone knows how to do this?

---

### Post by astrogazer on 2007-04-02
The only(I think!) mechanisms that MySQL can use to control 
access are user authenitication and/or client IP.

---

### Post by tomplast on 2007-04-02
> **astrogazer said:**
> The only(I think!) mechanisms that MySQL can use to control 
access are user authenitication and/or client IP.

Perhaps it's possible to patch MySQL and maybe PHP to make this work. I think it would be great in some situations.

---

