---
title: "Packages versus Compile"
date: 2007-11-15
forum: The Cafe
---

### Post by Rick Myers on 2007-11-15
Information I'm finding suggests that Linux using packages is slower than apps compiled into the kernel.

I'm hoping to gather input from the community on;
1) True or False?
2) If true, how much slower in comparison?


TIA

---

### Post by aysiu on 2007-11-15
Information I'm finding suggests that compiling applications is slower than installing packaged applications.

---

### Post by Rick Myers on 2007-11-15
> **aysiu said:**
> Information I'm finding suggests that compiling applications is slower than installing packaged applications.

Thanks for the quick reply Aysiu.

Can you direct me to supporting information?

---

### Post by ddrichardson on 2007-11-15
What do you mean by apps compiled into the kernel?

---

### Post by SunnyRabbiera on 2007-11-15
compiling depending on your processor can be like watching a snail race...

---

### Post by happysmileman on 2007-11-15
Compiling is much slower at first (i.e. to install) but the resulting program will usually be faster, unless you set options wrong.

By default you should get a noticable speed increase, but not necessarily enough to justify time spent compiling, but if you go to the bothering of editing the C-FLAGS (i.e. march=pentium4 instead of march=i386) you could get a huge speed increase

---

