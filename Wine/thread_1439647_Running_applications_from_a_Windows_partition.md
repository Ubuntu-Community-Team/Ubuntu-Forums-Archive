---
title: "Running applications from a Windows partition"
date: 2010-03-26
forum: Wine
---

### Post by farruinn on 2010-03-26
I would like to be able to use wine, installed on my Ubuntu partition, to run the programs on my Windows XP partition.  I can get stuff to run, actually, but since wine keeps its own registry, most things run into problems.

Can this be done?

---

### Post by farruinn on 2010-03-26
Ah, it was actually easier than I expected to export the registry keys I needed from within Windows, and then copy them into ~/.wine/system.reg.

---

### Post by asdfoo on 2010-03-26
> **farruinn said:**
> Ah, it was actually easier than I expected to export the registry keys I needed from within Windows, and then copy them into ~/.wine/system.reg.

be warned that running programs directly from your windows partition is not supported and you are at risk of corrupting your windows install.

it is recommended to install software using Wine.

---

