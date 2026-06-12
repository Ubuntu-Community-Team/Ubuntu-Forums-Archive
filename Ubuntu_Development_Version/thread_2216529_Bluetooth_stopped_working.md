---
title: "Bluetooth stopped working"
date: 2014-04-12
forum: Ubuntu Development Version
---

### Post by daniel-holz91 on 2014-04-12
Since some days bluetooth on my tablet stopped working. For some reason it is blocked by rfkill by default.

I can get it to work with

```
rfkill unblock bluetooth
sudo hciconfig hci0 reset
```

but fail to run these commands on startup automaticaly or to find the source of the problem.

At first I thought it might be laptop-mode-tools but the module bluetooth isn't active.

---

