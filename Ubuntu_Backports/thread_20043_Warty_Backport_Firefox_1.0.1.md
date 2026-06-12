---
title: "Warty Backport: Firefox 1.0.1"
date: 2005-03-14
forum: Ubuntu Backports
---

### Post by jdong on 2005-03-14
**Synopsis**
This is probably the last backport for Warty. Firefox 1.0.1 resolves (sort of) the IDN spoofing security issue.

**Backporting Process**
The source archive directly came from Debian Sid. Hoary is now under a freeze, so I couldn't get this latest version from Hoary!

**Packaging Status:**
i386 -- Staging at revision 81
amd64 -- Not packaged
ppc -- Not packaged

**Beta tester notes:**
Watch locales...

---

### Post by nocturn on 2005-03-15
Thank you Jdong.

Do you know if Hoary will get the 1.0.1 too? (since it is a security fix)?

---

### Post by jdong on 2005-03-15
yep, it has :)

---

### Post by jdong on 2005-03-15
Ok, Hoary got an official Firefox 1.0.1 update, and I've recompiled that for Warty. It's currently uploading as revision 84.

---

### Post by ember on 2005-03-18
O.k. I think I found a bug. I recently upgraded to FF 1.0.1 and with that version I am no longer able, to save files when clicking on links.
It does work to use "save target as ..." as well as opening it directly in the associated program.

I used the latest version UBP with Firefox-Gnome-Support and the german language pack.

Can anyone confirm that error?

P.S.: The error disappears, if I force firefox back to version 1.0-2.

---

### Post by jdong on 2005-03-23
I can confirm this; but I'll push this to the stable branch to fix the waaay outstanding security issues!

Hoary has an upgraded Firefox -- I'm gonna package that next.

---

### Post by jdong on 2005-03-23
According to ubuntu-users, we're gonna get Firefox 1.0.2 in Hoary very soon.

I'll backport this to Warty.

---

