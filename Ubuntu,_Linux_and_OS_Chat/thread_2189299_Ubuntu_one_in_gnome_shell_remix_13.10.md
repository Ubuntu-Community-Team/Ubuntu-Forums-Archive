---
title: "Ubuntu one in gnome shell remix 13.10"
date: 2013-11-21
forum: Ubuntu, Linux and OS Chat
---

### Post by masterbrumm on 2013-11-21
Anyone know if Ubuntu one should work in gnome shell remix 13.10 , just made a new gnome remix install , added ubuntu one from software center . but nothing happens when i try to run it. Is there a fix for this problem ? If not its back to Unity for me i guess.

This is what i get when im trying to run it

aslmyk@aslmyk-13:~$ ubuntuone-control-panel-gtk
ubuntuone-control-panel-gtk: kommando ikke funnet
aslmyk@aslmyk-13:~$ ubuntuone-control-panel-qt
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

---

