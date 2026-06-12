---
title: "reinstall an XP box with ubuntu and transfer domain membership to new OS?"
date: 2009-08-05
forum: Security
---

### Post by NoMojoMofo on 2009-08-05
I have a windows machine that is part of a Windows security domain.  I want to reinstall the host but try and 'transfer' the membership in the domain to the new OS  (ubuntu).  

Anyone tried / figured out / suggest a way to do this?

---

### Post by HermanAB on 2009-08-05
You cannot quite do that.  

You can install Ubuntu and configure Samba Winbind to log onto Windows, but the domain administrator has to do a domain 'join' operation on the client machine.  

If you are the domain administrator, then no problem.

---

