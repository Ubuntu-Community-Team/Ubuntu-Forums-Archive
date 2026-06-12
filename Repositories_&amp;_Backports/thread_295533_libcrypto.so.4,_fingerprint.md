---
title: "libcrypto.so.4, fingerprint"
date: 2006-11-08
forum: Repositories &amp; Backports
---

### Post by amanita on 2006-11-08
Hi, our local credit union has Internet banking for Linux (no support) I have generated keys but they want me to do "FingerPrint". I guess they want some special library which is not in Synaptic.(Edgy Eft 64)

Terminal shows:
~/Desktop/Fio./fgp fiohb.pub.key -

./fgp: error while loading shared libraries: libcrypto.so.4: cannot open shared object file: No such file or directory

Any ideas, please?

---

### Post by amanita on 2006-11-09
anyone :(

---

### Post by amanita on 2006-11-11
For anyone who needs libcrypto.so.4 and libssl.so.4 (32bits) just download from [http://packages.debian.org/](http://packages.debian.org/) package libssl0.9.7_0.9.7e-3sarge4_i386.deb
and extract libssl.so.9.7, libcrypto.so.0.9.7
and link them e.g.

sudo ln -s /home/xxxuser/libcrypto.so.0.9.7 /home/xxxuser/libcrypto.so.4

This should work...

---

