---
title: "Why doesn't Ubuntu have the ndiswrapper gui?"
date: 2009-04-02
forum: The Cafe
---

### Post by JacobRogers on 2009-04-02
Why doesn't Ubuntu have the ndiswrapper gui by default?  Is it proprietary software or something?


Or am I being totally silly and not seeing it?

---

### Post by mocoloco on 2009-04-02
No, it's not included by default.  You can install it from synaptic, ndisgtk
Now that you bring that up, it seems it would be a good idea to include it in the LiveCD environment.  Some logic could be setup that if no ndiswrapper drivers are setup then ndiswrapper and it's gui should be excluded from a desktop install (or uninstalled at the end, like they do with ubiquity and language packs and stuff).

---

### Post by cariboo on 2009-04-02
Ndisgtk is not installed, but it is on the LiveCD, just make sure the cd is enabled in System-->Administration-->Software Sources.

To find it on the LiveCD navigate to /pool/main/n

Jim

---

