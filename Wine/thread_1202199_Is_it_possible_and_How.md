---
title: "Is it possible and How?"
date: 2009-07-02
forum: Wine
---

### Post by wubiubiubi on 2009-07-02
Mainly I play Guild Wars on wine and what with the regressions if the past few versions I need to downgrade to 1.1.21. I have 1.1.24. Is it possible to downgrade directly or do I need to purge Wine altogether from my computer and then reinstall 1.1.21?

---

### Post by jhoeijao on 2009-07-02
> **wubiubiubi said:**
> Mainly I play Guild Wars on wine and what with the regressions if the past few versions I need to downgrade to 1.1.21. I have 1.1.24. Is it possible to downgrade directly or do I need to purge Wine altogether from my computer and then reinstall 1.1.21?

My suggestion is downgrade your wine get .deb package from here [http://wine.budgetdedicated.com/archive/](http://wine.budgetdedicated.com/archive/).

**[COLOR=Black]Remove wine[/COLOR]**

```
sudo apt-get remove wine
```
[B]
Delete wine
[/B]            -to remove your previous configuration

```
rm -rf ~/.wine
```

Note: Deleting wine means deleting all the programs installed through the use of wine.

---

### Post by cogadh on 2009-07-02
You don't actually need to delete your .wine directory when you downgrade Wine, you just need to uninstall the Wine binaries (sudo apt-get remove wine) then manually install the older package.

---

