---
title: "HU Grub2"
date: 2019-01-15
forum: Ubuntu Development Version
---

### Post by zika on 2019-01-15
```
Setting up grub-pc (2.02+dfsg1-5ubuntu9) ...+ cached_available_ids=
+ case "$1" in
+ . /usr/share/debconf/confmodule
++ '[' '!' '' ']'
++ PERL_DL_NONLAZY=1
++ export PERL_DL_NONLAZY
++ '[' '' ']'
++ exec /usr/share/debconf/frontend /var/lib/dpkg/info/grub-pc.postinst configure 2.02+dfsg1-5ubuntu8
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 20
dpkg: dependency problems prevent configuration of grub2:
 grub2 depends on grub-pc (= 2.02+dfsg1-5ubuntu9); however:
  Package grub-pc is not configured yet.


dpkg: error processing package grub2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 grub-pc
 grub2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Boot is OK but not in a newest Grub2... ;)
```
sudo mv /var/lib/dpkg/info/grub-pc.postinst /var/lib/dpkg/info/grub-pc.postinst.zika
```is one of possible solutions...
It worked for me, no promises for others... ;)

---

