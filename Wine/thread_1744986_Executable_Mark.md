---
title: "Executable Mark"
date: 2011-04-30
forum: Wine
---

### Post by tm-chex on 2011-04-30
Is There a way to permanently mark all EXE files as Executable? I'm trying to load some of my windows games into wine and it wont allow me to install them since they aren't marked as executable, And I cant mark them as executable since they're read-only (from being on the CD)

---

### Post by cogadh on 2011-05-01
You don't need to mark them as executable. Use the terminal to run them via Wine and you bypass the executable bit check:
```
wine /media/<cd mount name>/setup.exe
```

---

### Post by tm-chex on 2011-05-03
thank you!

---

