---
title: "Segfaults in libc-2.13.so today"
date: 2011-12-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-12-23
Lots of stuff crashing on libc now. Mostly when launching GUI apps, but some unrelated like this one:

[ 1923.794852] ir-keytable[22741]: segfault at 100000000 ip 00007fdeb1210620 sp 00007fff1b90c288 error 4 in libc-2.13.so[7fdeb111a000+195000]

**EDIT:** And somehow this thing makes me loose NFS network:
nfsd: nfsv4 idmapping failing: has idmapd died?

**EDIT:** And it gets worse:
[  656.802696] lightdm[18276] general protection ip:40add4 sp:7fff4a643a70 error:0 in lightdm[400000+27000]

**EDIT: **Really not what you would call of a reasonably stable state. Thanks Santa.
[ 1227.145750] xbmc.bin[13762]: segfault at 38 ip 00007f7fdd3bd554 sp 00007fffa8e5c710 error 4 in libcaca.so.0.99.17[7f7fdd3b5000+22000]

**EDIT:** And, why not, some DBUS errors in the mix too (while updating via apt):
Dec 23 20:18:22 localhost, dbus[1197]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Dec 23 20:18:47 localhost, dbus[1197]: [system] Failed to activate service 'org.freedesktop.PackageKit': timed out

---

