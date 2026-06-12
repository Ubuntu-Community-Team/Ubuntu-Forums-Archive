---
title: "/usr/bin/krandrstartup gone, breaks KDE"
date: 2013-03-11
forum: Ubuntu Development Version
---

### Post by cole.mickens on 2013-03-11
Hm, is this because I turned on proposed?

kde-workspace-bin seems to have removed /usr/bin/krandrstartup but /usr/bin/startkde relies on it.

---

### Post by ventrical on 2013-03-11
> **cole.mickens said:**
> Hm, is this because I turned on proposed?

kde-workspace-bin seems to have removed /usr/bin/krandrstartup but /usr/bin/startkde relies on it.

I have it here and proposed is turned off.

---

### Post by cole.mickens on 2013-03-11
Gr. Turned on Proposed. Got the kernel that will boot my computer. Few hours later, broke my DE. All in a day's fun testing.

---

### Post by ventrical on 2013-03-11
You're not alone. Happened to me quite a few times now :)

---

### Post by smartboyhw on 2013-03-12
Please install kde-workspace-randr. Someone in the Kubuntu Developer Team broke it (sorry, but not me)

---

### Post by cole.mickens on 2013-03-12
No problem at all, thanks for the quick reply with solution! I assume the kde-workspace-bin package will be updated to include a dependency on that?

---

