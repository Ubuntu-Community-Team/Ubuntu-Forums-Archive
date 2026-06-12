---
title: "session-installer  fails"
date: 2017-05-05
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-05-05
If trying to open a file that requires a gst plugin not default installed a session-installer? window pops up but does nothing. A session-installer+ process appears to briefly run.

Ex.
> $ totem '/home/doug/Videos/amostviolentyear-clip1_h1080p.mov' 
** Message: Missing plugin: gstreamer|1.0|totem|H.264 (Main Profile) decoder|decoder-video/x-h264, level=(string)4, profile=(string)main, max-input-size=(int)234123 (H.264 (Main Profile) decoder)
/usr/lib/python3/dist-packages/sessioninstaller/core.py:47: PyGIWarning: Gst was imported without specifying a version first. Use gi.require_version('Gst', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gst
/usr/lib/python3/dist-packages/sessioninstaller/core.py:48: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk
Falling back to package information
CRITICAL:Could not find any packages to operate on
** Message: No installation candidate for missing plugins found.

---

