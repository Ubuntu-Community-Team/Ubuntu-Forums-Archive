---
title: "update-alternatives"
date: 2007-10-25
forum: Ubuntu Brainstorm
---

### Post by Kow on 2007-10-25
I find it amusing that ubuntu + build-essential installs gcc 3.4, 4.1 and 4.2 yet there is no default update-alternatives configuration created for it (I have to do it myself.) This is easy to do and it seems like a great idea. The average user wont need this but I'm sure there are numerous developers using ubuntu who would find this addition a time saver. Not to mention this should be a really easy and quick addition (perhaps add a helper script to debian/rules for gcc packages?)

This shouldn't mess up the debs being compiled against a gcc version other than 4.2 because gcc-4.2 should be explicitly set in debian/rules.

---

