---
title: "Nautilus Elementary PPA?"
date: 2010-10-29
forum: The Cafe
---

### Post by Cam! on 2010-10-29
Using Terminal commands or a PPA, how can I safely install Nautilus Elementary?

---

### Post by nilarimogard on 2010-10-29
```
sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
sudo apt-get update
sudo apt-get dist-upgrade
nautilus -q
```

In Ubuntu 10.10 you MUST use "dist-upgrade" instead of just "upgrade" because Nautilus Elementary must install some extra dependencies.

---

