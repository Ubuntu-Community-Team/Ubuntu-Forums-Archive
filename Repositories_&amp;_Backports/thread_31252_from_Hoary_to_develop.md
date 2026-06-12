---
title: "from Hoary to develop"
date: 2005-05-02
forum: Repositories &amp; Backports
---

### Post by scaltro on 2005-05-02
I've installed the stable hoary distro, but i would change to the testing version. What i've to do? I have to change my repository? What's the mirror?
Tnks

---

### Post by Leif on 2005-05-02
Change all references to hoary in your /etc/apt/sources.list file to breezy. then sudo apt-get update and sudo apt-get dist-upgrade. You really shouldn't do this unless you know how to fix problems and are in genereal very knowledgeable about linux. Breezy is in early development and things, including your whole system, can break.

---

