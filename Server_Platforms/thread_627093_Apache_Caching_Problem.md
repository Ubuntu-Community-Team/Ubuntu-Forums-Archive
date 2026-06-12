---
title: "Apache Caching Problem"
date: 2007-11-29
forum: Server Platforms
---

### Post by biosonik on 2007-11-29
Hey,

I have a standard apache server set up, bit of PHP, sql, ftp...the usual.

I also have mod_userdir and mod_rewrite loaded. Now when I change anything on my website (change php files) the changes are not reflected in a browser.

-----EDIT-----
I've figured out its actually PHP that seems to be caching the files. How do you switch this off?

Thanks
-Vince

P.S. I have checked the apache log, nothing of interest in it.

---

### Post by twistedtwig on 2007-11-30
are you sure it is apache and not ur browser??? have you done CTRL + F5?

---

