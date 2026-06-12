---
title: "gtk2-engines-pixbuf Installation Error"
date: 2013-03-25
forum: Ubuntu Development Version
---

### Post by celluloid on 2013-03-25
Anyone else seeing this with today's updates?

```
(Reading database ... 327770 files and directories currently installed.)
Preparing to replace gtk2-engines-pixbuf:amd64 2.24.16-1ubuntu2 (using .../gtk2-engines-pixbuf_2.24.17-0ubuntu1_amd64.deb) ...
Unpacking replacement gtk2-engines-pixbuf:amd64 ...
dpkg: error processing /var/cache/apt/archives/gtk2-engines-pixbuf_2.24.17-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/gtk2-engines-pixbuf/AUTHORS', which is different from other instances of package gtk2-engines-pixbuf:amd64
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gtk2-engines-pixbuf_2.24.17-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by alphacrucis2 on 2013-03-25
Me too

---

### Post by victor9098 on 2013-03-25
Same here, tried uninstalling the packages and then reinstalling. It seemed to work, but after a restart an error report launched saying the package had not been installed correctly.

---

### Post by mc4man on 2013-03-25
I didn't see any issue with 2.24.17-0ubuntu1 but there is a new build for those that did - 2.24.17-0ubuntu2
Try that one if available or wait till it is (avail. here on main server

---

### Post by Toz on 2013-03-25
Seems to have fixed itself. Update successful here now after similar errors.

---

