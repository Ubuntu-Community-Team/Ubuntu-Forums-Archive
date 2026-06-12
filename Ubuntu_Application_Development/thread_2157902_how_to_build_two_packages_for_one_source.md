---
title: "how to build two packages for one source?"
date: 2013-06-27
forum: Ubuntu Application Development
---

### Post by A117 on 2013-06-27
I followed ubuntu packaging guide.
in debin/control, it's like,
```
Source: ezcommon
...
Section: libs
...

Package: ezcommon-dev
Section: libdevel
...

Package: ezcommon
Section: libs
...
```
then i "bzr builddeb -S"
"pbuilder-dist precise build aaa_2.7-0ubuntu1.dsc"
"dput ppa:bon-ami/ezcommon ..."

it seems only one ezcommon-dev package is generated. how to check and correct this please?
thank you.

---

