---
title: "cryptsetup: use a keyfile on the root partition"
date: 2013-11-26
forum: Security
---

### Post by gregor-6 on 2013-11-26
hi,

i try on a test workstation if it is possible to use a keyfile to open a encrypted system(root) partition. first i create a ubuntu 13.10 installation with an unencrypted /boot partition and an encpryted / partition. with a passphrase i have no problem to unlock and use the system. now i generated a keyfile and added it to /etc/crypttab. when i run update-initramfs i get the following warning:
"cryptsetup: WARNING: target system uses a key file, skipped"
is it possible to use a keyfile in such scenario?

king regards
gregor

---

