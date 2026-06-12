---
title: "Mountmgr Error"
date: 2009-02-09
forum: Wine
---

### Post by Vince4Amy on 2009-02-09
I'm using OpenSuSE With WINE 1.1.4 and I get the following error:

```
err:winecfg:open_mountmgr failed to open mount manager err 2
```

[[IMG]http://img228.imageshack.us/img228/5168/winecfgav5.th.jpg[/IMG]](http://img228.imageshack.us/my.php?image=winecfgav5.jpg)

---

### Post by Vince4Amy on 2009-02-09
Update: This does not happen when I use 1.0.9 which is in the OpenSuSE OSS Repo.

---

### Post by ephemeros on 2009-02-28
Do you have the 'wine' package installed?
I had the same problem on Fedora 10. I installed 'wine-desktop' although this had not 'wine' as a dependency. The config window appeared, it was creating the "~/.wine" and I was able to change other settings, despite the 'wine' package was not installed :).

---

