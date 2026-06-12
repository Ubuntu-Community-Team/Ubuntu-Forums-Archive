---
title: "Packaging : Suppressing Editor in dpkg-source --commit"
date: 2012-09-11
forum: Ubuntu Application Development
---

### Post by openfly on 2012-09-11
Trying to suppress the editor from opening when doing a dpkg-source --commit.

Tried the -q quiet mode flag.  No success.

Tried specifying the patch filename and directory.  Again no success.

Any ideas?

About a hairs breadth away from interrupting the exec call for the editor with a shared library.  Help would be appreciated.

---

