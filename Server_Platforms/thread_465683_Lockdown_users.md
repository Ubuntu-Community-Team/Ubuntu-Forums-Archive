---
title: "Lockdown users"
date: 2007-06-06
forum: Server Platforms
---

### Post by spirre on 2007-06-06
Hi, 
Does anyone know howto make ubuntu to only show users own running processes when the user makes ps uax like you can set in bsd with the config: security.bsd.see_other_uids=0

---

### Post by mrsno on 2007-06-06
Hi spirre, im not sure how to do this apart from gresecurity, kernel patches can enable the equivalent of using sysctl security.bsd.see_other_uids=0 and other options, check [http://www.grsecurity.net/wiki/index.php](http://www.grsecurity.net/wiki/index.php) to see the features/information.

If it does then you would need to apply the patches to the kernel source, rebuild the kernel and then boot into it, check [http://wiki.ubuntu.com](http://wiki.ubuntu.com) for kernel building information :)

hope this helps.

---

