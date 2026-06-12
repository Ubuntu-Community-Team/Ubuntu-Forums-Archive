---
title: "Guitar Pro 6 and &quot;QGtkStyle was unable to detect the current GTK+ theme&quot;"
date: 2013-03-16
forum: Ubuntu Development Version
---

### Post by xedi on 2013-03-16
I upgraded to 13.04 and as expected Guitar Pro 6 stopped working (did it ever survive an upgrade?). First problem was that it wanted libssl0.9.8 which I fixed by installing libssl0.9.8:i386. Now it's complaining about that ```
QGtkStyle was unable to detect the current GTK+ theme.
Segmentation fault
```

I tried this [solution]("http://askubuntu.com/questions/235155/qgtkstyle-was-unable-to-detect-the-current-gtk-theme") but ```
[FONT=Ubuntu Mono]gtk-theme-name="myTheme"
[/FONT]
``` doesn't work and I'm not sure whether that is the right approach in the first place. Any ideas?

---

### Post by xedi on 2013-03-16
I just found this post: [http://ubuntuforums.org/showthread.php?t=2099140](http://ubuntuforums.org/showthread.php?t=2099140)

Seems like a bug in Ubuntu 13.04 and not a problem of Guitar Pro 6.

---

