---
title: "Ubuntuone installer freezes"
date: 2012-04-27
forum: Ubuntu One (CLOSED)
---

### Post by escaflowne on 2012-04-27
I just installed Ubuntu 12.04. Then I want to setup Ubuntu One but the installer freezes at this line.


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/ubuntuone-installer/ubuntuone/installer/gui.py", line 357, in finished
    GLib.spawn_command_line_async('ubuntuone-control-panel-gtk')
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: Failed to execute child process "ubuntuone-control-panel-gtk" (No such file or directory)


I tried to install ubuntuone-control-panel-gtk package but failed.

ubuntuone-control-panel-gtk : Depends: python-aptdaemon.gtkwidgets but it is not going to be installed or python-aptdaemon-gtk but it is not going to be installed

Please help.

---

