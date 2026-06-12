---
title: "Remove entery from Registry"
date: 2009-09-03
forum: Wine
---

### Post by ChaosLacky on 2009-09-03
I was installing a program but the installer crashed.  It won't install again because it thinks the program is already installed, which I believe is because it is still in the registry.  The uninstall won't work either,   Is their anyway to remove all entries from a specific program from the Wine registry?

---

### Post by ackanao on 2009-09-03
What program you're trying to install?

I think the safest thing to do is to delete "**~/.wine**" folder and recreate it again:

```
winecfg
```

If you think that problem is in registry use ```
regedit
``` command to modify your registry settings.

---

