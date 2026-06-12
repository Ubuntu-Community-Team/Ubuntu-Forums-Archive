---
title: "Problem with apache2 ([error] an unknown filter was not added: includes)"
date: 2007-10-22
forum: Server Platforms
---

### Post by gizm0 on 2007-10-22
I have just updated my Ubuntu to 7.10. Upgrade was flawless, but now my apache2 says "[error] an unknown filter was not added: includes" in /var/log/apache2/error.log. 

Anybody know resolution for this error?

---

### Post by MJN on 2007-10-22
It sounds like the SSI module mod_include isn't enabled - do so with **sudo a2enmod include**.
 
Mathew

---

