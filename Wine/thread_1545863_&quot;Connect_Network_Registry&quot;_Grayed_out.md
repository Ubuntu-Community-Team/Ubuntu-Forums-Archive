---
title: "&quot;Connect Network Registry&quot; Grayed out"
date: 2010-08-04
forum: Wine
---

### Post by blagosphere on 2010-08-04
Wine provides a handy regedit for its own registry however when going to the "registry" button i came across a problem. I cannot connect to a remote registry because the "connect Network Registry" button is grayed out. Could i get some help?

Thanks

---

### Post by asdfoo on 2010-08-05
> **blagosphere said:**
> Wine provides a handy regedit for its own registry however when going to the "registry" button i came across a problem. I cannot connect to a remote registry because the "connect Network Registry" button is grayed out. Could i get some help?

Thanks

I checked the source code.  That function isn't implemented yet.

Out of interest, why do you want to do this?  I might be able to offer some alternative help.

---

### Post by blagosphere on 2010-08-05
> Out of interest, why do you want to do this?  I might be able to offer some alternative help. 

Well i was looking into remote controlling other systems (XP) that may not have the "allow remote control" option already enabled. I learned that by a simple regedit of one entry will enable the feature and it is easier to do it remotely than to physically go to the system.

---

### Post by asdfoo on 2010-08-05
> **blagosphere said:**
> Well i was looking into remote controlling other systems (XP) that may not have the "allow remote control" option already enabled. I learned that by a simple regedit of one entry will enable the feature and it is easier to do it remotely than to physically go to the system.

If you want to request the feature, you can file a bug at [http://bugs.winehq.org](http://bugs.winehq.org)

---

