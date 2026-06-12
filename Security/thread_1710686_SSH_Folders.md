---
title: "SSH Folders"
date: 2011-03-20
forum: Security
---

### Post by Tabu.it on 2011-03-20
Hi,
Is possible to allow a user to browse only some folders?
For example i want userA(admin) to navigate all system and userB to navigate only his home folders and a directory under /media?

Could i chmod all folders to 770? (/etc, /var and so on) or the +r for others is required for some application to work?

Thank You

---

### Post by HermanAB on 2011-03-20
Howdy,

Yes, using groups is the best way, but you can also use ACLs.

---

