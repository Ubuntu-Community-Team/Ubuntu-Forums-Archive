---
title: "removing the Ubuntu One &quot;check mark&quot; emblem from files and folders"
date: 2011-06-20
forum: Ubuntu One (CLOSED)
---

### Post by Schuby007 on 2011-06-20
Hi,

Is it possible to remove the "ubuntuone-synchronized" emblem from files and folders that are being synchronized with Ubuntu One? Seeing the check mark on all my files and folders is just really annoying and distracts from the thumbnail preview that nautilus provides.

I've tried going into folder properties -> emblems and de-selecting the emblem but it won't let me.

Thanks,
Schuby

---

### Post by jerrrys on 2011-06-20
the only way i have found to change system icons is to find them and replace.  they are mostly located in "icons" and "pixmap" folder.

---

### Post by Schuby007 on 2011-06-20
> **jerrrys said:**
> the only way i have found to change system icons is to find them and replace.  they are mostly located in "icons" and "pixmap" folder.

So then can I replace that particular emblem with nothing or a null emblem?

---

### Post by jerrrys on 2011-06-20
maybe, really not sure about ubuntuone.  there is a way to remove ALL link/sync arrows.  if your interested I'll hunt it down.

EDIT

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+link+arrows&sa=Search&cof=FORID:9#971](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+link+arrows&sa=Search&cof=FORID:9#971)

no hits on sync arrows.

---

### Post by jdorenbush on 2011-11-03
Just remove the emblems from your icon folder in **usr/share/icons/**.

For example, I'm using the Elementary icon theme, so I had to remove these 3 files:
```

**usr/share/icons/elementary/emblems/24/**
[INDENT]emblem-ubuntuone-synchronized.png
emblem-ubuntuone-unsynchronized.png
emblem-ubuntuone-updating.png[/INDENT]

```

---

