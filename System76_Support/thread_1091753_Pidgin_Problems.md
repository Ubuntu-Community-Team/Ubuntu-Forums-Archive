---
title: "Pidgin Problems"
date: 2009-03-09
forum: System76 Support
---

### Post by mannljm on 2009-03-09
I have recently started to have issues with the pidgin program on my pangolin running ubuntu 8.10. The program starts but almost immediately becomes unresponsive consuming up to 100% of the CPU. It will come back after some time then almost immediately become unresponsive again. When I run XP in VirtualBox on the same machine I have no such problems with pidgin. I would rather not run XP in VirtualBox just to use pidgin. Any suggestions would be appreciated.
Thanks,

---

### Post by thomasaaron on 2009-03-09
Try re-installing pidgin....

First, jot down all of your buddies, as we should probably get rid of the config files too.

```
sudo rm -r .pidgin
sudo apt-get --purge remove pidgin
sudo apt-get install pidgin
```

---

### Post by mannljm on 2009-03-10
Thanks Tom, that seems to have resolved the issue. Just one point, the directory to remove is .purple.

---

### Post by thomasaaron on 2009-03-10
Yes, it is.
Why do they have to be so non-conformist? :D

---

### Post by jjacobs2 on 2009-03-11
[http://developer.pidgin.im/wiki/WhatIsLibpurple](http://developer.pidgin.im/wiki/WhatIsLibpurple)
purple is actually the core of the IM program.  Pidgin is just the GUI.  Libpurple is used with other GUIs as well so it's not just semantics.  Perhaps you can even switch GUIs and keep your settings from purple.

---

### Post by thomasaaron on 2009-03-11
Ahhh! That makes more sense now. You learn something new every day around here.

---

