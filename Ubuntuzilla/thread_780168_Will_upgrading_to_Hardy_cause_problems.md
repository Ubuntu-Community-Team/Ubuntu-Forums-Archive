---
title: "Will upgrading to Hardy cause problems?"
date: 2008-05-03
forum: Ubuntuzilla
---

### Post by Garzo on 2008-05-03
I'm planning to upgrade from Gutsy to Hardy in the next week, and I noticed that Ubuntuzilla does not work with Hardy as it uses Firefox 3 beta. When I upgrade, will my system default to the Ubuntu Firefox package and give me Firefox 3, or will it be overridden by Ubuntuzilla. If it is the latter, how do I switch back to the Ubuntu package until the official packages get ahead of the Ubuntu ones?

Thanks,

Garzo.

---

### Post by nanotube on 2008-05-03
you can run 
```
ubuntuzilla.py -a remove -p firefox
```
which will switch you back to ubuntu's version, and then the upgrade should not run into any problems, since ubuntu's stuff will be restored.

---

