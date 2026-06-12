---
title: "upgrade of package gyp fails"
date: 2013-12-25
forum: Ubuntu Development Version
---

### Post by emk on 2013-12-25
during the last dist-upgrade, I encountered the following problem:

```
Preparing to replace gyp 0.1~svn1654-1 (using .../gyp_0.1~svn1729-3_all.deb) ...
Unpacking replacement gyp ...
dpkg: error processing /var/cache/apt/archives/gyp_0.1~svn1729-3_all.deb (--unpack):
 unable to open '/usr/share/pyshared/gyp-0.1.egg-info/dependency_links.txt.dpkg-new': No such file or directory
No apport report written because the error message indicates an issue on the local system
```

EDIT: Just a purge and reinstall got rid of the problem.

---

