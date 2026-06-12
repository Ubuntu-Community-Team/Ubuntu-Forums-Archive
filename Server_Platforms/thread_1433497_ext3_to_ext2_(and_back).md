---
title: "ext3 to ext2 (and back)"
date: 2010-03-19
forum: Server Platforms
---

### Post by rocknrollmouse on 2010-03-19
If I start with an ext3 disk, then remove journalling by running:
```
[FONT="Courier New"][COLOR="Blue"]tunefs -O /dev/md0 [/COLOR][/FONT]
```
effectively making an ext2 system.  
Does this remove the information held for ext3?  
So that I could then run: 
```
[COLOR="Blue"][FONT="Courier New"]tunefs -j /dev/md0 [/FONT][/COLOR]
```
re-enabling journalling, but with a *clean journal*?

---

