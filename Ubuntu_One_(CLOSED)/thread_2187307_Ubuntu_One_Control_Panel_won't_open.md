---
title: "Ubuntu One Control Panel won't open"
date: 2013-11-11
forum: Ubuntu One (CLOSED)
---

### Post by pobr on 2013-11-11
I installed Ubuntu 13.10 on two different PCs, and both of them (Asus Zenbook UX31E laptop and a desktop) got the same problem with Ubuntu One Control Panel; it won't start. I even logged inn during install, but I can't open the Ubuntu One client. Since I'm already logged in the Ubuntu One-folder is syncing, but the rest of the folders are not selected and can't be accessed.

I've created a bug report, but no activity in two weeks: [https://bugs.launchpad.net/ubuntuone-control-panel/+bug/1244314](https://bugs.launchpad.net/ubuntuone-control-panel/+bug/1244314)

When I try to run it in terminal from the desktop I get:

```
per-olav@desktop-13:~$ ubuntuone-control-panel-qt
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-control-panel-qt", line 34, in <module>
    main.main(sys.argv, install_reactor_darwin=True)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/qt/main/__init__.py", line 161, in main
    installer=installer)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/qt/gui.py", line 137, in start
    installer=installer)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/qt/gui.py", line 49, in __init__
    self.ui.setupUi(self)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/qt/ui/mainwindow_ui.py", line 51, in setupUi
    self.control_panel = ControlPanel(self.centralwidget)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/qt/ubuntuonebin.py", line 39, in __init__
    self.ui.setupUi(self)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/qt/ui/controlpanel_ui.py", line 166, in setupUi
    self.wizard = UbuntuOneWizard()
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/qt/wizard.py", line 179, in __init__
    self.confirm_dialog = AreYouSure(self)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/qt/wizard.py", line 91, in __init__
    ARE_YOU_SURE_HELP.format(support_url=link))
IndexError: tuple index out of range
```

Anyone experienced the same problem, or have a clue what to do? I removed everything and installed Ubuntu One again, but it didn't help.

---

### Post by TFkN8h8 on 2013-11-13
yes, same here. Fresh install on a HP laptop and in Virtualbox.  Syncing is working, but I am not able to open the damn thing. 


Rune

---

### Post by phil smart on 2013-11-16
Same here 32 bit version 13.10. 
Software ware centre lists 2 copies of the control panel both the same and both crash on loading. I made sure I was not installing both copies
Phil

---

### Post by Nichlee on 2013-11-19
Anyone found a solution ?
Cause I am having the exact problem. Running fresh install of 13.10 64bit. I did not log in under installation, so I am not being able to use the ubuntu one at all. The cloud icon do shows up in system icons in the corner, abd allows me to use it, but I still cant open the control panel, and being able to login or whatever..thanks for any help!

---

### Post by pobr on 2013-11-20
No, I have no idea. I even tried it from the start again and reinstalled Ubuntu 13.10 (64-bit here too), but it didn't work. This time I didn't login to Ubuntu One, so no sync. I found out that if you login to the Software Center it will start sync the Ubuntu One folder. Still, it's not a solution.

---

### Post by Irihapeti on 2013-11-20
If you're still having difficulties with Ubuntu One after reinstalling, it may be worth your while getting in touch with the Ubuntu One directly using the Contact form on the website. Note: they're not the fastest at responding.

---

### Post by pobr on 2013-11-26
The bug report has found the problem, and a workaround is to change language back to english. See here: [https://bugs.launchpad.net/ubuntuone-control-panel/+bug/1244314](https://bugs.launchpad.net/ubuntuone-control-panel/+bug/1244314)

---

### Post by axerun on 2014-02-07
Hi.
Will there be a fix for this in 13.10? Anyone?
It pretty annoying, to put it mildly. :-)

Rune

---

### Post by Vladlenin5000 on 2014-02-07
It seems there's a fix already. Please read the latest comments on the bug report (link above in post #7).
You just need to do the usual updates, the fix is in the language pack.

---

### Post by axerun on 2014-02-08
> **Vladlenin5000 said:**
> It seems there's a fix already. Please read the latest comments on the bug report (link above in post #7).
You just need to do the usual updates, the fix is in the language pack.

There seems to be a fix for 14.04 but there is no update availible for 13.10, as far as I can see.

---

