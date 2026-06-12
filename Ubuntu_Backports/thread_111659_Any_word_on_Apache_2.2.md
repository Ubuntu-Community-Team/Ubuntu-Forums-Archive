---
title: "Any word on Apache 2.2?"
date: 2006-01-02
forum: Ubuntu Backports
---

### Post by spectre_25gt on 2006-01-02
Does anyone know if there are plans to release a package for Apache 2.2 yet? I've been fussing around with trying to get mod_jk for Apache 2.0 for a while now, but it looks like there's no support for it on breezy for some reason. Apache 2.2 has a new connector called ajp_proxy that looks promising. I'm hoping it might actually bring some order to configuring Tomcat with Apache 2.

---

### Post by theQmaster on 2006-01-30
Apache 2.2 was released but it will take awhile to get it into distros.

My main questions are how easy will be to move from 2.0.54 to 2.2... and how the tomcat will handle the new ajp_proxy.

I use mod_jk and 2.0.5x for a good while and looks fine.

Q
Visit a Royalty Free Stock Site
[www.goodstockimages.com](www.goodstockimages.com)

---

### Post by spectre_25gt on 2006-01-30
Thanks for the info. I got it working a while back, actually. I eventually found a good place to get the source and compile from.

---

### Post by theQmaster on 2006-01-30
[QUOTE=spectre_25gt]Thanks for the info. I got it working a while back, actually. I eventually found a good place to get the source and compile from.[/QUOTE]


Can you share, I'd like to try it too. I got a bunch of question though

1. What about the mods, can you use the old ones as well ?
2. Is it faster than the 2.0.xx ?
3. Did you manage to configure ajp_proxy without problem ? 
4. Did you override the 2.0.5x implementation or just installed in a different folder ?

Any hints will do.

Thanks,
Q

---

