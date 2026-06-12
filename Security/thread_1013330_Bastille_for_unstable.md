---
title: "Bastille for unstable?"
date: 2008-12-16
forum: Security
---

### Post by docfx on 2008-12-16
I've tried installing bastille, but get an error stating:
```
Server is not running a stable version of Debian GNU/Linux
```

on my Hardy 8.04.1 server and thus won't allow me to run and harden the server.

There appears to be a version of Bastille for stable and for unstable Debian at [http://packages.debian.org/search?keywords=bastille](http://packages.debian.org/search?keywords=bastille)

This site suggests I add a line to sources.list, but after I do it either is not recognizing the change or is defaulting to the previous ubuntu repository as it tells me that my bastille version is already the newest version.

So how do I...
1) uninstall the current version of bastille 
and 
2) apt-get the correct version of bastille from the other repository
or 
3) upgrade to a stable version of Debian?

Inquiring minds wanna know?

I suppose I could manually harden this beast, but that seems silly to not use the tools available. 

I think I got a similar message when trying to install SELinux, so any help would be appreciated.

---

### Post by wowgold5hk on 2008-12-18
After 10 years of discussion and planning, China will launch fuel tax reforms in the New Year, part of an effort to streamline its price systems.It will be just the latest market-oriented major policy move that China has undertaken in its three decades of reform and opening up.Thursday was the 30th anniversary of that drive, and during those three decades gross domestic product (GDP) grew by more than 9 percent on average annually, a rare feat in global economic history.But the celebration of these achievements was overshadowed by the world financial crisis, which is deepening and spreading globally, devastating financial systems in developed countries and darkening world economic prospects._____________[kevlar bulletproof vests](http://www.yoocart.com/productHtml/bullet-proof-vest37_page1.html)[Pe bulletproof vests](http://www.yoocart.com/productHtml/bullet-proof-vest37_page1.html)[Stab-bulletproof vests](http://www.yoocart.com/productHtml/bullet-proof-vest37_page1.html)[bullet proof vest](http://www.yoocart.com/productHtml/bullet-proof-vest37_page1.html)[tactical body armor](http://www.yoocart.com/productHtml/bullet-proof-vest37_page1.html)

---

### Post by Titan8990 on 2008-12-18
Ubuntu is not Debian. It is its own spin-off distro of debian. Likely you will need a tested and supported version of Debian in order to get that install properly (speaking from my experience with a similar app). It is not a good idea to add Debain repositories to your sources.list as it has potential to break your system via updates.


So either:

A) Install debian and use the Debian package

B) Compile it yourself: [http://sourceforge.net/projects/bastille-linux/](http://sourceforge.net/projects/bastille-linux/)

---

### Post by docfx on 2008-12-20
thanks for the reply... guess I'll go harden it manually... 

Seems odd for Bastille (and/or SELinux) to be in the ubuntu respository only to not be able to install them because they're unsupported...

---

### Post by cariboo on 2008-12-20
Have you tried the Batille package that is available in the repositories?

Jim

---

