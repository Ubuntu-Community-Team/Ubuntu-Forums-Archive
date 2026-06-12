---
title: "Cannot suspend"
date: 2024-01-23
forum: Security
---

### Post by mwl2024 on 2024-01-23
For quite a while now, my Laptop has not been able to go into sleep mode.

When I close the lid, the screen turns dark, and it seemingly tries to go into sleep. However, it gets stuck in the process. Things such as power button stay illuminated and keyboard lights still turn on when I press the key. The only thing that apparently resolves the issue is a hard reset (keeping the power button pressed).

The same happens with `systemctl suspend`. 

I don't even where to look (that is, which logs) to figure where it gets stuck. I hope this forum can provide some help in identifying the problem.

```

[FONT=monospace][COLOR=#000000]$ lsb_release -a [/COLOR]
No LSB modules are available. 
Distributor ID: Ubuntu 
Description:    Ubuntu 22.04.3 LTS 
Release:        22.04 
Codename:       jammy
[/FONT]
```

---

