---
title: "Want to Remove Wine"
date: 2009-11-17
forum: Wine
---

### Post by Rakhal Bandhu on 2009-11-17
When running program under Wine machine hangs. Tried to uninstall Wine from uninstall option, but not possible. Seeking suggestions.

---

### Post by Bunnybugs on 2009-11-17
> **Rakhal Bandhu said:**
> When running program under Wine machine hangs. Tried to uninstall Wine from uninstall option, but not possible. Seeking suggestions.

Go to the synaptic package manager (System>Administration>Synaptic Packagemanager) and search for 'Wine'

Un-check the box before wine, and press apply!

Follow the instructions on screen, and wine will be removed!

Good Luck!

---

### Post by Rakhal Bandhu on 2009-11-17
Thanks for the tips. I will try and post the result.

---

### Post by beastrace91 on 2009-11-17
```
sudo apt-get remove wine --purge-all
```

^ that will uninstall Wine and remove any files it may have added/created on the system.

~Jeff

---

