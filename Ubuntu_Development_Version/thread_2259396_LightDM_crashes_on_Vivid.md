---
title: "LightDM crashes on Vivid"
date: 2015-01-04
forum: Ubuntu Development Version
---

### Post by syntaxerror74 on 2015-01-04
I think I'm not the only one who has experienced this...
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1401094](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1401094)

Something going wonky in g_hash_table_iter_next(). Unfortunately, the only way out seems to compile trunk release yourself, because as usual, the working version is kept behind the developers' backs until several weeks later.
Whatever, this is no trivial bug, but a major issue (it actually segfaults) because it will always trigger Apport at system startup.

---

