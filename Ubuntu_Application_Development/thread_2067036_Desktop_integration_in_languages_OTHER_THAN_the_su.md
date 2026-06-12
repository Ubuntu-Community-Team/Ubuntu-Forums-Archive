---
title: "Desktop integration in languages OTHER THAN the supported ones?"
date: 2012-10-06
forum: Ubuntu Application Development
---

### Post by papillion on 2012-10-06
Hello Everyone,

I'm developing an Ubuntu app in RealStudio. I'd like to be able to use some of the cool API's like desktop notifications, CouchDB, etc but I only see a few languages supported. Is there a way to hook into these from 'unsupported' languages? If so, is there any doc out there on how to do so?

Thanks!
Anthony

---

### Post by mhall119 on 2012-10-06
Any language that can access GObject or DBus will be able to integrate with the Unity desktop.

---

