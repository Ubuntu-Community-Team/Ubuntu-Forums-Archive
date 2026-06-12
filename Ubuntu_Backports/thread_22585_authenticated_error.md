---
title: "authenticated error"
date: 2005-03-28
forum: Ubuntu Backports
---

### Post by Technoviking on 2005-03-28
How do you get rid of the following message when using a non-supported Ubuntu repository (i.e. backports):

WARNING: The following packages cannot be authenticated!

---

### Post by jdong on 2005-03-28
Our repository is not GPG signed. I'm depending on the anal berkeleydb backend to foil any attempt to modify the database.

If anyone finds a  decently easy way to get rid of this warning (other than turning off APT::Authenticate altogether), please let me know!

---

