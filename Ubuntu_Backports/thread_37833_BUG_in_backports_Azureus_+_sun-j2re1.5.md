---
title: "BUG in backports? Azureus + sun-j2re1.5"
date: 2005-05-28
forum: Ubuntu Backports
---

### Post by jobezone on 2005-05-28
**BUG in backports? Azureus + sun-j2re1.5**

This strange thing happened to me in Hoary, which happened when I first installed azureus and after that sun-j2re1.5 .

When installing azureus from backports, it installed the sun-j2sdk1.5 package, but this package created a broken link.
It linked /usr/lib/j2sdk1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so which doesn't exist to /etc/alternatives/firefox-javaplugin.so (which itself then links to /usr/lib/mozilla-firefox/plugins/libjavaplugin.so) .

I only noticed this after installing the sun-j2re1.5 package also from backports. Java worked fine, but I didn't have the java plugin in firefox. It did not replace the faulty link that sun-j2sdk1.5 created with its plugin.

To make it work, I had to manually remove /etc/alternatives/firefox-javaplugin.so and do ```
 sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /etc/alternatives/firefox-javaplugin.so 
```

I don't know if this would happen if I had installed sun-j2re1.5 first, and then sun-j2sdk1.5 , and I'm going to repost this message in the backports forum.

P.S.-the new version of [http://www.ubuntuguide.org](http://www.ubuntuguide.org) has now almost completely replaced marillat, using the backports.

---

### Post by jdong on 2005-05-29
Yeah, I'm working on updated Java packages.

this is actually because of a bug in the "java-package" program that generates .debs.

sun-j2re1.5 creates correct symlinks, but sun-j2sdk1.5 doesn't. I'm building new Java packages.

---

