---
title: "Backport: readahead-1.0.1-1~4.10ubp1"
date: 2005-01-24
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-24
Synopsis
Readahead caches commonly used files during early system startup (i.e. DHCP time, NTP time, Hotplug time) where the hard drive isn't doing much. That way, it can speed system startup.

Hoary introduced readahead, and I want to see if Warty can benefit, too.


Backporting Process
The source archive directly came from Hoary.

Packaging Status:
i386 -- Staging at revision 8.
amd64 -- Not packaged
ppc -- Not packaged



Beta tester notes:

---

### Post by jdong on 2005-01-24
Functional for me under i386. I'm gonna mark it stable by Friday.

---

