---
title: "automatix"
date: 2007-09-02
forum: The Cafe
---

### Post by nonewmsgs on 2007-09-02
i have read the pros and cons and can someone tell me why the everything except the nonfree codecs arent available under the add/remove?

---

### Post by JawsThemeSwimming428 on 2007-09-02
I think it is for legal matters. The codecs are illegal in some countries and therefore Canonical does not want to distribute them directly thought their OS.

---

### Post by nonewmsgs on 2007-09-02
i understand the nonfree codecs part, but i want to know about the other video players, lightscribe programs, java, keyboard shortcuts like windows, etc

---

### Post by p_quarles on 2007-09-02
Those things are all there, you just need to enable the repositories. This can be done in System >> Administration >> Software Sources (the "Windows-user friendly" way) or by editing /etc/apt/sources.list (the Linux way). 

As for why those repositories aren't automatically enabled: the applications in those repos aren't supported by Canonical. So, by default, a new installation only points you in the direction of stuff that *is* supported.

---

