---
title: "Good http proxy or squid help."
date: 2007-04-26
forum: Server Platforms
---

### Post by bobjr777 on 2007-04-26
Right now i am using squid but i dont want it cacheing everything. how can i easly turn it off. i know i can recompile but that will though off ubuntu wont it? if i cant turn off cacheing does anyone know of a good http proxy that you can make require a login.

---

### Post by briealeida on 2007-05-16
Read through squid.conf and you'll see that you can control what is cached. If you're looking at not caching a certain type of traffic or traffic from certain IPs, you're good to go. For the latter, you want to create a urlgroup. The conf file is well documented enough that you can find your way from there.

---

