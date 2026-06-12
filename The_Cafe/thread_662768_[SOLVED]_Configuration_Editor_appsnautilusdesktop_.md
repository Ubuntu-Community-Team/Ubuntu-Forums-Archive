---
title: "[SOLVED] Configuration Editor: apps/nautilus/desktop - what file does it edit"
date: 2008-01-09
forum: The Cafe
---

### Post by mdpalow on 2008-01-09
I'm curious to know which file is edited when you:

Run Configuration Editor
go to: apps/nautilus/desktop
put a check mark for home_icon_visible (and a few others in there)

I can't find the file it's updating.

Anyone know which file AND PATH is being updated?

Thanks in advance...

---

### Post by p_quarles on 2008-01-09
Probably this one:
```
~/.gconf/apps/nautilus/desktop/%gconf.xml
```

---

### Post by mdpalow on 2008-01-09
geez... I was in that area too, but got my folders mixed up and missed it completely.

Yep, that's it. Thank you for your help.

---

