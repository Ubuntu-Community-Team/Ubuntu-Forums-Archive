---
title: "Firefox 44 buggy on some sites"
date: 2016-01-26
forum: Ubuntu Development Version
---

### Post by fthx on 2016-01-26
Hi,

I use Gnome shell.
E.g., extensions.gnome.org does not display some text. It's not the only site, by far.
Do you experience the same bug ?

---

### Post by fthx on 2016-01-27
I tried to change fonts, gtk theme and to create a new profile, but no changes.
It *could* be a JS bug, as it happens on some other websites using JS.
Anyone ?

---

### Post by dino99 on 2016-01-27
do you get errors via gnome-tweak ?
extensions.gnome.org often bugs here with chromium; i does not use firefox, so i does not know about it.

---

### Post by fthx on 2016-01-27
There are errors in Firefox (console), but maybe not related to this bug.
Through Virtualbox I use Xenial too and I do not get this bug (in Gnome Shell or Unity).
I tried to use a void guest session, same bug happens.

My virtual Xenial has Unity installed too, that's the only difference.
So : ???

---

### Post by fthx on 2016-01-27
I tried to downgrade FF to previous version 43, and it solves the issue.
So it's FF 44 related, but maybe linked to personal settings (in system, cf void guest session affected too).

---

### Post by fthx on 2016-01-27
OOOOKKKK.
I reinstalled fontconfig to regenerate font config, and it's ok now.
Don't know why, though... Just intuition.

---

