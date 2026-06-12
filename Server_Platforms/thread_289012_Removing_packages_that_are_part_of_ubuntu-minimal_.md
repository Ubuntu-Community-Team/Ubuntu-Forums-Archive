---
title: "Removing packages that are part of ubuntu-minimal or similar"
date: 2006-10-30
forum: Server Platforms
---

### Post by edeca on 2006-10-30
I've just installed Ubuntu Server from the alternative CD.  I'm trying to figure out whether it is safe to remove packages that I know I do not need.  There are plenty of examples, but many of these are included in ubuntu-minimal, which I guess is a "virtual" package file.

Because of this, running apt-get remove <foo> removes ubuntu-minimal as well.  Is it safe to remove these packages?  Will future updates be impacted by me removing ubuntu-minimal?

Thanks.

---

### Post by skymt on 2006-10-30
It's safe to remove meta-packages like ubuntu-minimal or ubuntu-desktop. The only downside is that if the metapackage changes in an upgrade (like ubuntu-desktop installing F-Spot in Edgy, not in Dapper), you won't automatically get the change.

---

### Post by edeca on 2006-10-30
Thanks.  I'll remove the packages and keep a list of them, then put the meta-package back if I ever upgrade.  I can always remove them all again later :)

---

