---
title: "too many security"
date: 2010-08-26
forum: Security
---

### Post by ilna on 2010-08-26
Everybody has 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security

in it's sources.list. OTOH here firefox related security ppa is suggested:

[http://www.ubuntugeek.com/how-to-install-firefox-3-6-9-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-install-firefox-3-6-9-in-ubuntu-10-04-lucid.html)

Does it mean official security archive is unsufficiently secure? :)

---

### Post by FuturePilot on 2010-08-26
That PPA is kind of a staging area for Firefox security updates. When Mozilla releases a security update to Firefox, packages get built in that PPA. Eventually they trickle down into the Ubuntu Security updates archive.

---

### Post by ilna on 2010-08-26
> **FuturePilot said:**
> That PPA is kind of a staging area for Firefox security updates. When Mozilla releases a security update to Firefox, packages get built in that PPA. Eventually they trickle down into the Ubuntu Security updates archive.
Whay not directly?

And, well, there are other widely spreaded application. Must we (raw users) try to find dedicated intermediate ppas for each of them?

Please, be sure, I don't claim. Just want to understand best user's way :)

---

### Post by Bachstelze on 2010-08-26
> **ilna said:**
> Whay not directly?



So the packages can be tested for regressions (i.e. making sure the fix doesn't introduce other bugs).

---

### Post by FuturePilot on 2010-08-26
> **ilna said:**
>  Must we (raw users) try to find dedicated intermediate ppas for each of them?


No. They are mainly for testing to make sure no regressions occur. When everything checks out OK, you get the updates through the normal update process.

---

### Post by ilna on 2010-08-26
Thanks to all for clarification!

---

