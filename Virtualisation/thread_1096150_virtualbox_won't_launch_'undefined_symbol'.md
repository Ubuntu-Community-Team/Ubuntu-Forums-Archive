---
title: "virtualbox won't launch: 'undefined symbol'"
date: 2009-03-14
forum: Virtualisation
---

### Post by cliffskoog on 2009-03-14
Any help here?
Running 8.04, with newest virtualbox in repo - same as on their site.
I get:
VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: /usr/lib/libQtGui.so.4: undefined symbol: _ZN23QCoreApplicationPrivate19checkReceiverThreadEP7QObject

Searches seem to point to a bug in qt4. Any ideas?
Thanks

---

### Post by cliffskoog on 2009-03-14
SOLVED:
Following the spirit and sense indicated by a reply in the VirtualBox forum, I found I had both libqtcore4 and libqt4-core installed. I removed the first and reinstalled the second, and lo, virtualbox launches.

---

