---
title: "Question about events on port"
date: 2011-03-06
forum: Security
---

### Post by ltchronic302 on 2011-03-06
I'm using FireStarter as my host firewall and whenever I'm connected to the internet and browsing or just playing around on facebook, even sometimes when not even doing anything I get hits on port 59226 from ip's like 24.191.220.1 74.102.172.92. What is this port used for exactly, does anyone know?

---

### Post by Rubi1200 on 2011-03-07
Please post the output of the following command:

```
sudo lsof -i -n -P
```

Are you using BitTorrent clients or server software or remote desktop software?

---

