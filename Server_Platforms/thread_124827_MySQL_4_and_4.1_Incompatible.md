---
title: "MySQL 4 and 4.1 Incompatible?"
date: 2006-02-02
forum: Server Platforms
---

### Post by quietglow on 2006-02-02
**Here's the scenario:**

Running Mysql 4.1 on a windows box and have fairly complex database--some forums etc. I want to migrate to running the same database on a Breezy box. The official repos for Breezy contain Mysql 4.0. If I do a mysqldmp on the windows box, I cannot import that dump into a stock Breezy Mysql 4.0 database without a zillion errors. If I uninstall the Mysql 4.0 and install the 4.1 on the Breezy box from the extended repos, the database dump imports fine, but Mysql no longer talks to php etc. properly--i.e. it looks broken. 

**So my questions:**

Is there really a problem exporting from Mysql 4.1 and importing into 4? Is there anyway to "export" in such a way that I won't have the problem? 

I suppose I could try to figure out what the heck the problem is when I upgrade, but that looks pretty difficult from this standpoint--I want to explore other options for sure. 

Thanks so much for your help.

---

