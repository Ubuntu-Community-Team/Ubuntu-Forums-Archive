---
title: "? about mysql upgrade"
date: 2007-12-28
forum: Server Platforms
---

### Post by cerealtx on 2007-12-28
i work for a guy who leases a server and dosn't know jack about what he owns and he has outdate MySql and i need to update it to run on database scripts, if i upgrade MySQL will that erase the exsisting databases? or should i back up all 50 or so of them?

---

### Post by Maxtorm on 2007-12-29
It's good practice to regularly (at least daily) backup active databases. It certainly would make sense to before upgrading the database engine. However, to answer your original question, the upgrade should not erase any of the existing data.

---

