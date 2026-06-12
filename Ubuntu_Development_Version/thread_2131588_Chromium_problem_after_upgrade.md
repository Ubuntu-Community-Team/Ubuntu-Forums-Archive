---
title: "Chromium problem after upgrade"
date: 2013-04-02
forum: Ubuntu Development Version
---

### Post by Lucretius on 2013-04-02
Hi all...

 Just upgraded to 13.04 this morning and everything seems spot on, however there is a problem with the buttons on Chromium. They have all moved to the right hand side.

I installed Ubuntu tweak to try and move them back but it gives me this error when I try to load the window settings page

Distribution: Ubuntu 13.04 raring
Application: Ubuntu Tweak 0.8.3-1~precise1
Desktop:ubuntu

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/main.py", line 498, in _load_module
    page = module()
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/tweaks/window.py", line 64, in __init__
    if len(close_pattern.findall(button_value)) == 1 and 'close' in button_value:
TypeError: expected string or buffer

When I try typing gconftool-2 --set /apps/metacity/general/button_layout --type string ":close,maximize,minimize" into the terminal, the buttons just swap places but stay on the right hand side of the window.

Any help would be appreciated.

Cheers :)

---

### Post by dino99 on 2013-04-02
you should clean your system, and/or completly upgrade : ubuntu-tweal is 0.8.4+ into raring, and yours is a "precise" one, so the python complaints are expected.

it also seems you have not made a fresh install since ages; so again clean the system to purge oldish settings/broken symlinks/...

---

### Post by cariboo on 2013-04-02
Check to see if you have Settings-> Appearance->Use system title bar and borders checked, if it is unchecked the buttons are on the right

---

### Post by Lucretius on 2013-04-02
Hi...

A system clean using ubuntu tweak did the trick.

Windows menu works now and I can swap from left and right side again

Many thanks for the advice :)

---

