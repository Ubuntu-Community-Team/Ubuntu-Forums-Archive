---
title: "libtxc-dxtn error"
date: 2013-12-30
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-12-30
I get an error during an update of Trusty. Anyone else ?

```

E: libtxc-dxtn-s2tc0: 52.1739:subprocess installed post-installation script returned error exit status 2

```

```

Errors were encountered while processing:
 libtxc-dxtn-s2tc0:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libtxc-dxtn-s2tc0:i386 (0~git20131104-1) ...
update-alternatives: error: alternative path /usr/lib/x86_64-linux-gnu/libtxc_dxtn_s2tc.so.0 doesn't exist
dpkg: error processing libtxc-dxtn-s2tc0:i386 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libtxc-dxtn-s2tc0:i386


```

---

### Post by brainwash on 2013-12-30
Known issue. The fix should arrive soon.

[https://launchpad.net/bugs/1264926](https://launchpad.net/bugs/1264926)

---

### Post by ventrical on 2013-12-30
> **brainwash said:**
> Known issue. The fix should arrive soon.

[https://launchpad.net/bugs/1264926](https://launchpad.net/bugs/1264926)

Thanks for the reply :)

Edit: Fixed!

---

