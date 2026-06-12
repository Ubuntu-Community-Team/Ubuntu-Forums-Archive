---
title: "Backups (Déjà Dup) Error ~/.cashe ~/.dbus"
date: 2016-04-06
forum: Ubuntu Development Version
---

### Post by izznogooood on 2016-04-06
I keep getting an error about not being able to backup some files in ~/.dbus and ~/.cache.

Now ~/.cache according to documentation is ignored by default and I've added ~/.dbus to ignore list.

Anyone else?

---

### Post by izznogooood on 2016-04-11
I still have this error showing up every morning and its a annoying...

[ATTACH=CONFIG]268300[/ATTACH][ATTACH=CONFIG]268301[/ATTACH]

Ill file a bug report if this is new ;).

---

### Post by dFlyer on 2016-04-11
> **izznogooood said:**
> I still have this error showing up every morning and its a annoying...

[ATTACH=CONFIG]268300[/ATTACH][ATTACH=CONFIG]268301[/ATTACH]

Ill file a bug report if this is new ;).

 Check the owner ship of the ~/.cache/.dbus file. Chances are it's root. I get this at time and to correct the problem I just delete the .dbus directory if it belongs to root in my directory.

---

### Post by izznogooood on 2016-04-11
Yes its owned by root, but i assume it s there for a reason ;). (Not that I've checked).

My point is according to documentation it should not enter that directory at all :/?

I filed a bugrepport: [https://bugs.launchpad.net/ubuntu/+source/deja-dup/+bug/1568950](https://bugs.launchpad.net/ubuntu/+source/deja-dup/+bug/1568950)

If you can confirm this, that would be great. :D

---

