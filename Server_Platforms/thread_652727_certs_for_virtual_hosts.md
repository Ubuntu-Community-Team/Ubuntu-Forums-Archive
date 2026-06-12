---
title: "certs for virtual hosts"
date: 2007-12-29
forum: Server Platforms
---

### Post by godlike on 2007-12-29
Hey guys i just installed a postfix server for vhosts following this guide  [http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10)

Anyways i dont know if its possible or not but is there any way to make multiple certs when all the vhosts reside on one ip?

---

### Post by kidders on 2007-12-30
Hi there,

Not if you're only running one Postfix server. There would be no way for it to know which cert to use.

---

