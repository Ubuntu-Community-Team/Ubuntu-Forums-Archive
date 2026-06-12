---
title: "Ubuntu 12.04 Automatically Re-installs Rhythmbox after it has been removed?"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by SemiExpert on 2012-04-13
I removed Rhythmbox through the Software Center last month, so it came as a surprise when Rythmbox reappeared as the default music player this morning.  History in Software Center shows that an installation for Rhythmbox yesterday, April 12.  I can only assume that the re-installation occured through an update?

---

### Post by dino99 on 2012-04-13
its due to a metapackage named ubuntu-desktop, which install the ubuntu default packages apps list. So if you does not want some of them to be installed/reinstalled, then uninstall ubuntu-desktop first.

---

### Post by SemiExpert on 2012-04-13
> **dino99 said:**
> its due to a metapackage named ubuntu-desktop, which install the ubuntu default packages apps list. So if you does not want some of them to be installed/reinstalled, then uninstall ubuntu-desktop first.

 That makes perfect sense.  Many thanks.

---

