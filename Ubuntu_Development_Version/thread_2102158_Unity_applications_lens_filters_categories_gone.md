---
title: "Unity applications lens filters categories gone?"
date: 2013-01-06
forum: Ubuntu Development Version
---

### Post by serdotlinecho on 2013-01-06
Well, i'm not using app lens filter categories that often or i just search anything i want like using keywords eg; internet, video, music, pictures etc. But anyway, here's the recent unity-applications-lens on 13.04:

[IMG]http://i.imgur.com/kIKeR.png[/IMG]

---

### Post by serdotlinecho on 2013-01-07
Silly me, the apps lens filter categories is available again after today's update. :P
But i have a problem with alacarte on cinnamon desktop.
Has anyone had a similar problem?

```
 $ /usr/bin/alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 23, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 32, in <module>
    from Alacarte.MenuEditor import MenuEditor
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 23, in <module>
    from Alacarte import util
  File "/usr/share/alacarte/Alacarte/util.py", line 25, in <module>
    from gi._glib import GError
ImportError: cannot import name GError
```

---

### Post by dino99 on 2013-01-07
alacarte is also broken, since a while on RR i386 (gnome-classic)

[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/1086369](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/1086369)

---

