---
title: "Deb files on old release"
date: 2015-02-19
forum: Ubuntu/Debian BASED
---

### Post by SL0ltMJGyh on 2015-02-19
Hey guys!

I was wondering if I am able to do some terminal work to install new .deb files on Maverick Meerkat- the newer installation files typically support 12.04 and up. I'm looking to install those on 10.10 if possible... Would I have to unzip the .deb on my other computer (non-ubuntu) and then recompile it? Thx! :cool:

---

### Post by buzzingrobot on 2015-02-19
Essentially, you're looking at backporting packages built for 12.04 and up to a much earlier release.  The issue of  dependencies will loom large. Many d dependencies  required to build a 12.04+ package may not be available in Maverick or not available in a sufficiently recent release.  You can try to build those packages and their dependencies. Of course, dependencies have dependencies. You may find that building a .deb, or installing it, proves impossible due to unresolvable dependency conflicts.

If core components in Maverick -- python, glibc ,etc. -- are too old to support building a 12.04+, you are likely out of luck because practically the entire Mavrick system will essentially depend on the presence of those specific versions of those components.

You can examine packages, changelogs, dependencies for all versions of all Ubuntu packages at packages.ubuntu.com.  

Source is not included in the .deb package used to install software. You'd need to grab the source .deb.

---

