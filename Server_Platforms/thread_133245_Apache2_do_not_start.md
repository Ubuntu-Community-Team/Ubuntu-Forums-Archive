---
title: "Apache2 do not start"
date: 2006-02-19
forum: Server Platforms
---

### Post by Spikextrem on 2006-02-19
Apache 2 doesn't seem to react on anything.

I try /etc/init.d/apache2 start

and nothing seems to be moving.... no [ok] or [failed] indicated, nothing!

I suspect the initialisation script to be corrupt or something. I try a apt-get remove and apt-get install  but didn't solve the problem. :-k

---

### Post by Spikextrem on 2006-02-19
solved.

purged installation three time, reinstalled three times... installed apache2 and worked... go figure

---

