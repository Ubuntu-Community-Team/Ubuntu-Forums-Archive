---
title: "software-centre fails to run"
date: 2013-03-25
forum: Ubuntu Development Version
---

### Post by stinkeye on 2013-03-25
Software-centre fails to run if chrome is installed.
Appears to be a python 2.7 error.
[https://bugs.launchpad.net/ubuntu/+source/python2.7/+bug/1159636](https://bugs.launchpad.net/ubuntu/+source/python2.7/+bug/1159636)

---

### Post by rburkartjo on 2013-03-25
tks for the headsup. have same problem

---

### Post by craig10x on 2013-03-25
Same here...just tried to open it...synaptic package manager is fine...ubuntu software center is "no go"...

---

### Post by SkylineGTR on 2013-03-25
Same here also.

---

### Post by dino99 on 2013-03-25
if you run it from a terminal, which error(s) do you get ?

---

### Post by voodoomurphy on 2013-03-25
Same here. THis is the error from the terminal:chris@linux:~/.cache$ sudo software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 128, in <module>
    from softwarecenter.ui.gtk3.app import SoftwareCenterAppGtk3
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 37, in <module>
    import webbrowser
  File "/usr/lib/python2.7/webbrowser.py", line 505, in <module>
    register_X_browsers()
  File "/usr/lib/python2.7/webbrowser.py", line 489, in register_X_browsers
    register(browser, None, Chrome(browser))
NameError: global name 'Chrome' is not defined

---

### Post by ventrical on 2013-03-25
Todays updates gave me an error also about software center .. failure to download certain items .. but it still works.

---

### Post by mc4man on 2013-03-25
fixed in python2.7 (2.7.4~rc1-2ubuntu2)

---

### Post by voodoomurphy on 2013-03-25
Uninstalling Chrome (which I never use anyway) fixes it

---

### Post by craig10x on 2013-03-25
> **mc4man said:**
> fixed in python2.7 (2.7.4~rc1-2ubuntu2)

Yep...ran some afternoon updates and the fix was there...software center working fine again...
debian testing was never like this...if something broke, it might not be fixed for quite a long time...you usually had to end up trying to fix it yourself...

---

### Post by rburkartjo on 2013-03-25
yup was fixed with the last set of updates.

---

