---
title: "[SOLVED] Package Removal"
date: 2008-01-20
forum: Slackware and derivatives
---

### Post by MarCustomized on 2008-01-20
I'm trying to 'clean' by Slackware 12 install by removing all the excess packages, but I can't figure out how to remove them because they aren't directly named or referenced in the package list.

I'd like to get rid of Noatun, Juk, and KsCD, but I don't know what package they are included in.:-k

---

### Post by saulgoode on 2008-01-21
You can GREP the files in /var/log/packages to get a listing of the packages. Use the '-l' (lowercase 'L') switch if you just want to list the package name (and not all the files).

```
saul@tesla:$ for i in noatun juk kscd;do grep $i /var/log/packages/* -l;done
/var/log/packages/kdeaccessibility-3.5.6-i486-3
/var/log/packages/kdeaddons-3.5.6-i486-3
/var/log/packages/kdeartwork-3.5.6-i486-3
/var/log/packages/kdebase-3.5.6-i486-3
/var/log/packages/kdemultimedia-3.5.6-i486-3
/var/log/packages/kdeutils-3.5.6-i486-3
/var/log/packages/kdevelop-3.4.0-i486-3
/var/log/packages/amp-0.7.6-i386-1
/var/log/packages/kdeaccessibility-3.5.6-i486-3
/var/log/packages/kdebase-3.5.6-i486-3
/var/log/packages/kdemultimedia-3.5.6-i486-3
/var/log/packages/libnjb-2.2.5-i486-3
/var/log/packages/kdeaccessibility-3.5.6-i486-3
/var/log/packages/kdeartwork-3.5.6-i486-3
/var/log/packages/kdemultimedia-3.5.6-i486-3
```

---

### Post by MarCustomized on 2008-01-22
Thanx.  I said forget it and just installed Zenwalk 5.:)

---

