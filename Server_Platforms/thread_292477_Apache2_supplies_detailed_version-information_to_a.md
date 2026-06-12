---
title: "Apache2 supplies detailed version-information to attackers"
date: 2006-11-03
forum: Server Platforms
---

### Post by JGZimmerle on 2006-11-03
Hi!

The default configuration of the apache2 package makes apache report detailed information about installed software versions of web-related packages to potential attackers. This could simply be prevented by putting the line

ServerTokens Prod

into the default apache2.conf of the apache2 package.

---

### Post by MJN on 2006-11-04
Rather than hiding what you're running, you might want to instead concentrate on making sure what your are running doesn't have any vulnerabilities.

(If you are going to do what you've done, you might also want to have a **ServerSignature Off **directive as well.)

Mathew

---

