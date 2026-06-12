---
title: "Gnome-tweak-tool crash at startup"
date: 2013-02-12
forum: Ubuntu Development Version
---

### Post by ft_ on 2013-02-12
Hi,

```
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

I do not know the upgrade which cause that.

---

### Post by P-I H on 2013-02-12
Happened to me too.
I am using unity and installed unity-tweak-tool instead.
I could change theme and icons to what I want. It has also a feature, Hotcorners, that's quite OK.

---

### Post by jinjorge on 2013-02-12
funny thing - I can't get unity tweak tool to work.  It crashes on startup every time.

[https://bugs.launchpad.net/unity-tweak-tool/+bug/1118896](https://bugs.launchpad.net/unity-tweak-tool/+bug/1118896)

[https://bugs.launchpad.net/unity-tweak-tool/+bug/1122258](https://bugs.launchpad.net/unity-tweak-tool/+bug/1122258)

J

---

### Post by Sc0rian on 2013-02-13
funny, I get the exact same problem.

I'm running the latest raring ringtail and on gnome 3.6.

It was working fine, but just re-installed gnome and now it bugs out with the exact same message.

---

### Post by dino99 on 2013-02-13
issue reported :

[https://bugs.launchpad.net/ubuntu/+source/gnome-tweak-tool/+bug/1123372](https://bugs.launchpad.net/ubuntu/+source/gnome-tweak-tool/+bug/1123372)

---

### Post by Cavsfan on 2013-02-13
> **dino99 said:**
> issue reported :

[https://bugs.launchpad.net/ubuntu/+source/gnome-tweak-tool/+bug/1123372](https://bugs.launchpad.net/ubuntu/+source/gnome-tweak-tool/+bug/1123372)

I seen this and tried to open it and bazing got this same error. Reported it on this bug.
It says it is affecting 11 people.

---

### Post by sgage on 2013-02-13
> **Cavsfan said:**
> I seen this and tried to open it and bazing got this same error. Reported it on this bug.
It says it is affecting 11 people.

I added my "me too" to the bug report.

---

### Post by zika on 2013-02-14
+1

---

### Post by VinDSL on 2013-02-14
Me too...

---

### Post by tad1073 on 2013-02-14
same here

---

### Post by celluloid on 2013-02-14
Same here - added "me too" to bug report.

---

