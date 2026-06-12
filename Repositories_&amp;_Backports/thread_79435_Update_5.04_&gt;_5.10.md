---
title: "Update 5.04 &gt; 5.10"
date: 2005-10-20
forum: Repositories &amp; Backports
---

### Post by windeburg on 2005-10-20
I'd like to update my UBUNTU from 5.04 to the actual 5.10.
Do I need to change the servers in **"/etc/sources.list"**
or do I only have to type:
*sudo apt-get distupgrade*?

If i have to change the Repository-Servers, can you tell me, where i can get thier adresses?


would be happy for help!

Jonas

---

### Post by adwait on 2005-10-20
You will just need to change all the references from "hoary" to "breezy" in the /etc/apt/sources.list and let the rest of the lines remain the same. Then perform dist-upgrade.

---

### Post by windeburg on 2005-10-20
Thank you very much!

I'll try so!

Jonas

---

