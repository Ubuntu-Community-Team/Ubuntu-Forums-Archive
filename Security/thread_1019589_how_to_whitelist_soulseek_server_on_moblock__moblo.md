---
title: "how to whitelist soulseek server on moblock / mobloquer ?"
date: 2008-12-23
forum: Security
---

### Post by kraymore on 2008-12-23
I'm wondering if anyone can tell me how to whitelist the soulseek server on moblock / mobloquer ?  

thank you

---

### Post by Kilbasar on 2009-05-26
Hi!

```
sudo echo 'Soulseek:208.76.170.50' >> /etc/blockcontrol/allow.p2p
sudo /etc/init.d/blockcontrol restart
```

This is almost definitely needed if you run museek or nicotine on a system with moblock.

---

