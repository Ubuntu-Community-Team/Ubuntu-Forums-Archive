---
title: "downgrade seamonkey?"
date: 2013-12-14
forum: Ubuntuzilla
---

### Post by danjde on 2013-12-14
Hi friends,
yesterday I've upgraded seamonkey from 2.20 to 2.23 by apt on ubuntuzilla repo and the contextual menu is disappeared;

is it possible to downgrade the package?

many thanks

---

### Post by nanotube on 2013-12-14
> **danjde said:**
> Hi friends,
yesterday I've upgraded seamonkey from 2.20 to 2.23 by apt on ubuntuzilla repo and the contextual menu is disappeared;

is it possible to downgrade the package?

many thanks

Hi,

Well... I don't know what you mean by "contextual menu disappeared". If you explain what you mean, and maybe post some screenshots of what you expect and what is actually happening, it is possible we might be able to solve the problem without changing seamonkey versions. I am running 2.23 from ubuntuzilla, and haven't seen any issues myself...

But if you insist, you can just go and grab the 2.20 deb from ubuntuzilla project file host:
[http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/s/seamonkey-mozilla-build/](http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/s/seamonkey-mozilla-build/)
(be sure to get one for the correct architecture, 32bit or 64bit...), then force-install the .deb, using "dpkg -i --force <packagefilename.deb>"

---

### Post by vasa1 on 2013-12-14
+1 to what *nanotube* wrote. Also, you could ask around at Mozillazine where they have a Seamonkey forum: [http://forums.mozillazine.org/viewforum.php?f=51](http://forums.mozillazine.org/viewforum.php?f=51) and experienced users hangout there.

---

