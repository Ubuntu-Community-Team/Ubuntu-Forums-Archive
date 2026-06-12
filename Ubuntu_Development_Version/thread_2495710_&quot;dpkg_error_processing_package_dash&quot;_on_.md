---
title: "&quot;dpkg error processing package dash&quot; on upgrade to 24.04"
date: 2024-02-28
forum: Ubuntu Development Version
---

### Post by Irihapeti on 2024-02-28
I upgraded my Surface Go 3 from jammy to noble a couple of evenings ago.

I got an error
```

Removing 'diversion of /usr/share/man/man1/sh.1.gz to /usr/share/man/man1/sh.distrib.1.gz by dash'
Removing 'diversion of /bin/sh to /bin/sh.distrib by dash'
This should never be reached
dpkg: error processing package dash (--configure):
installed dash package post-installation script subprocess returned error exit status 1

```
and the upgrade aborted, leaving the machine in an unbootable state.

Fortunately, I was able to boot into single user mode, and 'fix broken packages' completed the upgrade. Since then, the machine has behaved well – no lasting damage done. 

Has anyone else seen this, or have any idea what it's about? Should I report a bug, and if so, where exactly?

---

