---
title: "Has anyone had trouble w/ box-look.org lately?"
date: 2012-04-24
forum: The Cafe
---

### Post by decktrio on 2012-04-24
I can't see any of the pages on [S][box-look.org]("http://box-look.org/")[/S] **all [openDesktop.org:]("http://opendesktop.org/") sites** properly. Has anyone else experienced this?

---

### Post by Bandit on 2012-04-25
Having issues for a while now with gnome-look also not showing up and some cases not being found.

---

### Post by desnaike on 2012-04-26
I had the same problem for days but just on a whim I changed dns servers from isp's to opendns works like a charm.

---

### Post by decktrio on 2012-04-26
> **desnaike said:**
> I had the same problem for days but just on a whim I changed dns servers from isp's to opendns works like a charm.
Thanks! I already use opendns' servers, but this made me think to clear the dns cache.
```
sudo /etc/init.d/dns-clean start
```OR
```
sudo aptitude install nscd
]sudo /etc/init.d/nscd restart
```I guess the website had trouble (or was undergoing maintenance) for a period of time. It's working fine now.

---

