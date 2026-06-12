---
title: "DNS server requirements"
date: 2010-07-04
forum: Server Platforms
---

### Post by Vegan on 2010-07-04
I have Bind on the machine at present, but I was wondering how much disk would be needed to make it a full DNS server that could act in place of a dead upstream service.

---

### Post by hictio on 2010-07-04
How many domains are we talking about?
Are you logging the requests?
Usually, again, unless you are running DNS for a hundred domains or more, drive space is not one of the concerns.

---

### Post by Vegan on 2010-08-15
How about everything?

---

### Post by Bachstelze on 2010-08-16
> **Vegan said:**
> How about everything?

You can't do that.  No server hosts everything. Even without taking disk space into account, just building the list would take considerable time (and might generate enough traffic to get your server blacklisted).

---

