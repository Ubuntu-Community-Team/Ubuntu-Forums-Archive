---
title: "no systray icons (tested: tomboy/skype/hamster/indicator-multiload)"
date: 2013-09-10
forum: Ubuntu Development Version
---

### Post by miobrad on 2013-09-10
dear forum,
i can no confirm that no systray icons are shown on my all new install of 13.10 on my lenovo thinkpad x201t.
i have installed skype/tomboy/hamster/indicator-multiload and started them all from the dash. i looked for each
with ps ax an know that they are running:

```
 
1613 ?        Sl     1:39 indicator-multiload
5061 ?        Sl     0:00 /usr/bin/python /usr/bin/hamster-indicator
8212 ?        Sl     0:03 mono /usr/lib/tomboy/Tomboy.exe --search
8364 ?        Sl     0:05 skype

```

yet, no icons.

thanks for any comments/hints and all the hard work!!!

---

### Post by howefield on 2013-09-10
As per your skype thread, probably...


[https://bugs.launchpad.net/unity/+bug/974480](https://bugs.launchpad.net/unity/+bug/974480)

---

### Post by miobrad on 2013-09-10
what to do? try a workaround or wait? i wonder, many people will have the same problem - right?! a big thing.. or is it just going to be fixed by the developers (if i understood right it is the developres of each program that have to fix it...)

---

### Post by Beren Camlost on 2013-09-10
A workaround was posted here: [https://bugs.launchpad.net/unity/+bug/974480/comments/42](https://bugs.launchpad.net/unity/+bug/974480/comments/42)

---

### Post by mc4man on 2013-09-10
tomboy has an app indicator, currently works fine
indicator-multiload has an app indicator, also works fine
hamster has a seperate indicator package named "hamster-indicator", works fine
(screen shows all 3
skype, don't know, don't feel like installing

As far as the systray in unity, that ppa will likely have saucy packages come release or so

(I keep a current saucy unity build with systray enabled in a ppa but also have changes the launcher expo icon to work for 1x4 workspaces so of overall limited value... & having a systray enabled has no effect of whether app indicators show or not, I only really use for vlc whose app indicator is crap

---

