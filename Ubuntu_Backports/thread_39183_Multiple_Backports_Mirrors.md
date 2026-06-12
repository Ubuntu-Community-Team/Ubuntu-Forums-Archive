---
title: "Multiple Backports Mirrors?"
date: 2005-06-03
forum: Ubuntu Backports
---

### Post by Jormundgand on 2005-06-03
Will I be positively or negatively affected if I use multiple backports mirrors in my sources.list? I'm currently using mirrormax but I wonder if it'd be worth using multiple mirrors.

---

### Post by jdong on 2005-06-03
Using multiple mirrors would only confuse the heck out of APT.

So no, using multiple mirrors is not wise. APT doesn't handle them like YUM, which uses multiple mirrors as fallback URL's.

---

### Post by ShaneAu on 2005-06-04
[QUOTE=Jormundgand]Will I be positively or negatively affected if I use multiple backports mirrors in my sources.list? I'm currently using mirrormax but I wonder if it'd be worth using multiple mirrors.[/QUOTE]
 For different thigns I suppose that would be fine, for like hoary-backports use mirror A and hoary-extras using mirror B.

I don't see how that could cause any confusion?

- Shane.

---

