---
title: "Ubuntu One won't start after new installation"
date: 2012-05-21
forum: Ubuntu One (CLOSED)
---

### Post by Android the Andrew on 2012-05-21
I'm running on a fresh install of Oneiric x64 on an Asus UX50V laptop, and I'm having a hard time getting Ubuntu One to start. I've installed all the related modules and dependencies, as best as I can tell, but running 'ubuntuone-client' only says "command not found," and 'ubuntuone-control-panel-gtk' gets this error message:

> Traceback (most recent call last):
  File "/usr/bin/ubuntuone-control-panel-gtk", line 33, in <module>
    from ubuntuone.controlpanel.gui.gtk import main
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/gtk/__init__.py", line 28, in <module>
    from ubuntuone.controlpanel.gui.gtk.gui import main
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/gui/gtk/gui.py", line 52, in <module>
    from ubuntuone.controlpanel import (DBUS_BUS_NAME, DBUS_PREFERENCES_PATH,
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/backend.py", line 35, in <module>
    from ubuntuone.controlpanel import sd_client, replication_client
  File "/usr/lib/python2.7/dist-packages/ubuntuone-control-panel/ubuntuone/controlpanel/sd_client/__init__.py", line 25, in <module>
    from ubuntuone.platform import tools
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/linux/tools.py", line 27, in <module>
    from ubuntuone.platform.linux.dbus_interface import (
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 36, in <module>
    from ubuntuone.syncdaemon.interaction_interfaces import (
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 24, in <module>
    from ubuntuone.syncdaemon.action_queue import Download, Upload
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/action_queue.py", line 54, in <module>
    from ubuntu_sso.utils import timestamp_checker
ImportError: cannot import name timestamp_checker

What's going on?

---

### Post by vic_xyz on 2012-05-22
I can confirm the same problem.
First,   I've updated it to the last version, then nothing works. I've tried removing old config and reinstalling it, but the same problem...

I've tried to launch it on new user (as I thought it was still some old settings conflicting), but the same result...



FIXED!


Updated **ubuntu-sso-client** too....and everthing works again! Pfuu...

---

### Post by Android the Andrew on 2012-05-22
Aha!
Upgrading 'ubuntu-sso-client' did the trick. Thanks!

---

### Post by uniomni on 2012-06-06
Worked for me too, thanks

---

