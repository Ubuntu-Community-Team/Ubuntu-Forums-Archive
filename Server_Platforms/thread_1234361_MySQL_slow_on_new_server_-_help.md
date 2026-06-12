---
title: "MySQL slow on new server - help"
date: 2009-08-07
forum: Server Platforms
---

### Post by GHowlerson on 2009-08-07
Hi all,

I hope someone can help with this, I'm tearing my hair out!

We've just migrated one of our sites from an old FreeBSD server to a new Ubuntu server. The old server was old, slow hardware, and running 4.1.19. The new server is much higher spec, running Ubuntu and 4.1.19.

In terms of performance, Apache runs brilliantly on the new server, much faster than the old. But MySQL runs very slowly on the new server. This is particularly noticeable for selects from large tables.

The only thing I've done to my.cnf so far is to add skip-name-resolve, which a lot of people seem to recommend doing. This hasn't made any difference.

Any idea what I could try next?

---

### Post by enz1m3 on 2009-08-09
Try this script: [http://www.day32.com/MySQL/](http://www.day32.com/MySQL/)

---

