---
title: "rosegarden settngs"
date: 2010-07-07
forum: Ubuntu Studio
---

### Post by raymondvillain on 2010-07-07
Running 64 bit Ubuntu Studio 10.04.  Trying to set up Rosegarden.  The tutorial refers to example files and default files, both with .rg suffixes.  I cannot find them anywhere.

Have things changed, or do I need to look harder to find or download them?

---

### Post by Pablo_F on 2010-07-07
File . > open doesn't show an "Examples" folder?

Otherwise, check the folder:

/home/user/.local/share/rosegarden/examples/

(.local is a hidden directory. Show hidden in your file browser)

If they are not there, open a terminal and write:

$ locate *.rg

to locate rg files in the whole system.

---

