---
title: "unetbootin doesn't use the gtk theme for qt"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by lucazade on 2012-04-13
Unetbootin doesn't use the gtk theme for qt apps.
also trying to apply the gtk theme via qt4-qtconfig doesn't help.

[https://bugs.launchpad.net/ubuntu/+source/unetbootin/+bug/980823](https://bugs.launchpad.net/ubuntu/+source/unetbootin/+bug/980823)

any confimations or clue why it is happening?

---

### Post by dino99 on 2012-04-13
hm, why do you try to mix them ? you're breaking my logic cells here :(

---

### Post by Xgen on 2012-04-13
Have you tried qtconfig as root...'gksu /usr/bin/qtconfig-qt4'? The Unebootin qtk theme works for me.

---

### Post by mc4man on 2012-04-13
> **Xgen said:**
> Have you tried qtconfig as root...'gksu /usr/bin/qtconfig-qt4'? The Unebootin qtk theme works for me.

That would seem to be it - even though as a User the default (Desktop Settings) is normally the same as GTK+ for qt4 apps not so for root qt4 apps inc. a root qtconfig-qt4

---

