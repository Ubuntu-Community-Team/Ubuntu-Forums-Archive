---
title: "HELP Please! Ignoring file  ignoring file 50 unattended-upgrades.ucf-dist"
date: 2017-03-03
forum: Server Platforms
---

### Post by Bushcraft Bill on 2017-03-03
I get this problem when doing the sudo apt-get update so what do I need to do to fix this problem or is it fixable?

[ATTACH=CONFIG]273965[/ATTACH]

---

### Post by cariboo on 2017-03-03
Change the name of the file to:

```
/etc/apt/apt.conf.d/50unattended-upgrades
```

---

