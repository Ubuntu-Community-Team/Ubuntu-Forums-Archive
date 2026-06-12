---
title: "How to install Japanese language support in Wine"
date: 2009-02-03
forum: Wine
---

### Post by BuntuFirstTimer on 2009-02-03
I installed wine and I can't manage to find a way to make my Japanese Microsoft-based program work on Wine.

Is there a way by any chance?

---

### Post by Ferrat on 2009-02-03
There are ways but they are hard and takes work (atleast they did when I did it for.. ehh.. some japanese games :-\") 

But yeah it should be doable, tried google? or searching winehq?

---

### Post by BuntuFirstTimer on 2009-02-03
Perhaps WINE needs an integrated language support in the future.

---

### Post by alexftw. on 2013-03-21
it may be a bit late, but here is a solution:

```
LANG="ja_JP.UTF-8" <application>
```

this enables japanese character support (only for this one app you want to run)

for example: ```
LANG="ja_JP.UTF-8" wine some.exe
```

---

