---
title: "[SOLVED] Gazelle V3 Beeps on resume from HIbernate"
date: 2008-07-18
forum: System76 Support
---

### Post by AusIV4 on 2008-07-18
Since Hardy came out, my Gazelle Value 3 has hibernated and resumed much more reliably. The only problem is that sometimes it will beep - loudly and repeatedly - upon resuming. I've tried a number of fixes, such as muting the speakers on hibernate, but I still have the problem.

This has been bearable during the summer, but during the school year I take my laptop to class, and I can't have it beeping loudly if a professor is lecturing by the time it finishes booting up.

---

### Post by thomasaaron on 2008-07-18
Two things to try...

1. System > Prefs > Power Mgt > General Tab.
Deselect the "Beep on Error" checkbox.

2. System > Prefs > Sound > Sound Tab.
Set "Error Message" and "Warning Message" to No Sound.
Under the "System Beep" tab, deselect the checkbox.

If one of these does not fix it, there is probably a setting in gconf-editor that will. I'll try to figure it out if these don't work.

Also, what version of Hardy are you using? 32-bit? 64-bit?

---

### Post by AusIV4 on 2008-07-18
I've made the suggested changes, and I've had two hibernates/resumes without the beeping. This looks hopeful, but it didn't beep every time to begin with, so it's not a sure thing yet.

Incidentally, I run 64 bit Ubuntu Hardy.

[EDIT]
After several more resumes, I'm convinced that the fix worked.

Thanks.

---

