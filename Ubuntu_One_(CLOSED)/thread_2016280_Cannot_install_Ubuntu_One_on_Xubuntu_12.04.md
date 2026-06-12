---
title: "Cannot install Ubuntu One on Xubuntu 12.04"
date: 2012-07-04
forum: Ubuntu One (CLOSED)
---

### Post by shuiruge on 2012-07-04
I tried to install the Ubuntu One on Xubuntu 12.04. I run "ubuntuone-installer" in my terminal, but it displayed:

[COLOR=#FF0000]aptdaemon.errors.TransactionFailed: Transaction failed: None
 The following packages have unmet dependencies:

ubuntuone-control-panel-qt: Depends: python (< 2.8) but 2.7.3-0ubuntu2 is to be installed
                            Depends: python-ubuntuone-control-panel (= 3.0.0-0ubuntu1) but 3.0.0-0ubuntu1 is to be installed
                            Depends: ubuntuone-control-panel (= 3.0.0-0ubuntu1) but 3.0.0-0ubuntu1 is to be installed
                            Depends: ubuntuone-control-panel-common (= 3.0.0-0ubuntu1) but 3.0.0-0ubuntu1 is to be installed

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/ubuntuone-installer/ubuntuone/installer/gui.py", line 373, in finished
    GLib.spawn_command_line_async(CONTROL_PANEL_COMMAND)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: Failed to execute child process "ubuntuone-control-panel-qt" (No such file or directory)[/COLOR]

I have installed these below:
python
Depends: python-ubuntuone-control-panel
Depends: ubuntuone-control-panel
Depends: ubuntuone-control-panel-common
But it still won't work!

I'm a new guy. Is there anyone who used to meet this circumstance??
Thank you.

---

### Post by DMGrier on 2012-07-04
you have to install all these,

desktopcouch-ubuntuone
python-ubuntuone
python-ubuntuone-client
python-ubuntuone-control-panel
python-ubuntuone-storageprotocol
ubuntuone-client
ubuntuone-client-dbg
ubuntuone-client-gnome
ubuntuone-control-panel
ubuntuone-control-panel-gtk
ubuntuone-couch

---

