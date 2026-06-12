---
title: "[SOLVED] Windows &amp;quot;flickers&amp;quot; inside VMware Server"
date: 2008-06-10
forum: Virtualisation
---

### Post by diablo75 on 2008-06-10
I was helping someone via a VNC session a while back and they had this one XP virtual machine running inside VMware that just ran really really slow, with choppy audio and Windows XP would flicker a lot.  You'd have the start menu open, and a couple seconds later, it would seem like Explorer would crash, the task bar would disappears for a second, come back pretty quickly, on occasion the desktop background would flip out too.  All the while, no error messages being produced by Windows.

I'm asking him to produced a list of software he's installed on his virtual machine since creating it, because I think he's installing something malicious or borderline beta in his machine after the fact, and blaming VMware.  Just a guess...

What do you guys think?

---

### Post by Shazaam on 2008-06-10
Is VMware Tools installed on the XP guest?

---

### Post by diablo75 on 2008-06-11
> **Shazaam said:**
> Is VMware Tools installed on the XP guest?

Yes.  The last time this happened, I uninstalled and reinstalled VMware tools but it didn't solve the problem...

---

### Post by diablo75 on 2008-06-11
**SOLVED!**

He had this themeing/skinning software running that was having a fit with the Autofit Guest option enabled.  Disabling this, and using the "Fit Guest Now" for occasional resizing instead, fixed the problem!
:guitar:

---

