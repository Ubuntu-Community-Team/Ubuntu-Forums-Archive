---
title: "Gnome-tweak-took fails to launch"
date: 2013-02-16
forum: Ubuntu Development Version
---

### Post by Baldrick_NZ on 2013-02-16
It initalises but goes no further.

Here's the result when run in terminal. Any ideas how to fix?

```
baldrick@baldrick:~$ gnome-tweak-tool
Traceback (most recent call last):
  File "/usr/bin/gnome-tweak-tool", line 75, in <module>
    MainWindow()
  File "/usr/lib/python2.7/dist-packages/gtweak/mainwindow.py", line 41, in __init__
    model)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 55, in __init__
    self._on_search_cancel)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 167, in __init__
    self._on_changed(self._entry)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 183, in _on_changed
    secondary_icon_sensitive=False)
SystemError: error return without exception set

```

I've tried to make theme adjustment settings using Ubuntu Tweak, but it would appear that they can't be done without the Gnome Tweak Tool installed & operational.

Cheers.

---

### Post by ft_ on 2013-02-16
[http://ubuntuforums.org/showthread.php?t=2115328](http://ubuntuforums.org/showthread.php?t=2115328)

---

### Post by zika on 2013-02-16
> **Baldrick_NZ said:**
> It initalises but goes no further.

Here's the result when run in terminal. Any ideas how to fix?

```
baldrick@baldrick:~$ gnome-tweak-tool
Traceback (most recent call last):
  File "/usr/bin/gnome-tweak-tool", line 75, in <module>
    MainWindow()
  File "/usr/lib/python2.7/dist-packages/gtweak/mainwindow.py", line 41, in __init__
    model)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 55, in __init__
    self._on_search_cancel)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 167, in __init__
    self._on_changed(self._entry)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 183, in _on_changed
    secondary_icon_sensitive=False)
SystemError: error return without exception set

```

I've tried to make theme adjustment settings using Ubuntu Tweak, but it would appear that they can't be done without the Gnome Tweak Tool installed & operational.

Cheers.Ricotz's testing and both G3 PPAs up-to-date
```
:~$ gnome-tweak-tool 
Traceback (most recent call last):
  File "/usr/bin/gnome-tweak-tool", line 75, in <module>
    MainWindow()
  File "/usr/lib/python2.7/dist-packages/gtweak/mainwindow.py", line 41, in __init__
    model)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 55, in __init__
    self._on_search_cancel)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 167, in __init__
    self._on_changed(self._entry)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 183, in _on_changed
    secondary_icon_sensitive=False)
SystemError: error return without exception set
```

---

