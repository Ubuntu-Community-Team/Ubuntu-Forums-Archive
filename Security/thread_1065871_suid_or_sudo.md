---
title: "suid or sudo"
date: 2009-02-10
forum: Security
---

### Post by abracadaver on 2009-02-10
**Sorry... Please ignore. Just read the description of this forum.  Will post in the general.**



I need to execute the tc (traffic control) from the iproute2 package via some web scripts.  Would it be better to use the suid on tc or add the www-data user to sudoers for tc with no passwd?

TIA,
-Shawn

---

### Post by The Cog on 2009-02-10
My feeling ios that you should add just the specific user/command combinations you need to sudoers.

---

