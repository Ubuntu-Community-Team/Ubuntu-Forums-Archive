---
title: "runtime error in 0.4x"
date: 2006-08-16
forum: Ubuntu System Panel
---

### Post by -fin on 2006-08-16
hello.

I just upgraded from 0.30 to 0.40, with a problematic outcome ... (have i mentioned that 0.30 worked great - although a key combination to show it would be cool ;))

i'm running an up-to-date gentoo 2006.0 (or .1? i forgot) system, with all the dependencies ("import"-statements in the source) installed

when i start usp, i get the following error:
```
finlap bin # usp run-in-window
Dir exist
Dir exist
Dir exist
Place added - /root/.usp/places/nautilus-home.desktop
Place added - /root/.usp/places/nautilus-computer.desktop
Place added - /root/.usp/places/network-scheme.desktop
Traceback (most recent call last):
  File "/usr/bin/usp", line 1755, in ?
    menu_factory(app, None)
  File "/usr/bin/usp", line 1735, in menu_factory
    MenuWin(applet, iid)
  File "/usr/bin/usp", line 1551, in __init__
    self.mainwin = MainWindow(self)
  File "/usr/bin/usp", line 175, in __init__
    self.PopulatePlugins()
  File "/usr/bin/usp", line 281, in PopulatePlugins
    MyPlugin.content_holder.show()
AttributeError: 'NoneType' object has no attribute 'show'

```

as i'm no python developer, i could not debug it - could anyone help me with this?

---

### Post by chanders on 2006-08-16
Try completly removing USP, and then install 0.41 (in the new release section of this forum)... let me know how it goes...

---

### Post by -fin on 2006-08-17
worked.

i removed USP, all files in the original .deb and the gconf-keys, rebooted and then re-installed it

thanks :)

(sry for bothering)

---

### Post by chanders on 2006-08-17
> **-fin said:**
> worked.

i removed USP, all files in the original .deb and the gconf-keys, rebooted and then re-installed it

thanks :)

(sry for bothering)

Glad you got it working!

---

### Post by mat on 2006-08-27
FWIW, in the current devel version I've added code that will discard bogus plugins instead of throwing this kind of errors.

---

