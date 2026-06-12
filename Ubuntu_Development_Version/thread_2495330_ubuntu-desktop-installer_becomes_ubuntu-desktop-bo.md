---
title: "ubuntu-desktop-installer becomes ubuntu-desktop-bootstrap"
date: 2024-02-15
forum: Ubuntu Development Version
---

### Post by corradoventu on 2024-02-15
In the new ISO ubuntu-desktop-installer becomes ubuntu-desktop-bootstrap
with sources.list replaced by sources.list.d/ubuntu.sources and software-properties-gtk unable to manage the new format: 
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2053228](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2053228)

---

### Post by MAFoElffen on 2024-02-17
As I remember just before we first started testing Ubuntu Dev Noble Dailys (when it first actually worked)... I just checked my started threads. It was the last part of Dev Mantic testing...

Wasn't there a previous related bug with the Dev Mantic source.list where it didn't create /etc/apt/sources.list file, and it was found in /etc/apt/sources.list.d/ as another file, that was in a completely different format, that I asked if that was a major change in how Ubuntu sources worked?

RE: [https://ubuntuforums.org/showthread.php?t=2491429](https://ubuntuforums.org/showthread.php?t=2491429)

@coradoventu --
After I reported that, you filed the bug report, and I joined it:
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2033949](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2033949)

Is this a regression issue of that? Just wondering.

---

### Post by corradoventu on 2024-02-18
My previous bug bug/2033949 is closed but does not solve the problem,
Jeremy Bícha (jbicha) wrote 13 hours ago: 			
This did not fix the issue, but the issue is now being tracked at LP: #2053228
so the new bug is:
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2053228](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2053228)

---

### Post by MAFoElffen on 2024-02-18
Dang. Okay. Joined the new one.

---

