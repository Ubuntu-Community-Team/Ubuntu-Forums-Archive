---
title: "idjc and djplay"
date: 2009-07-18
forum: Ubuntu Studio
---

### Post by johnh10000 on 2009-07-18
Hi I've a few problems:

Firstly djplay starts .. O play a "record" the vu moves up and down like its sopsed to, but no sound comes out.

Secondly idjc which used to workhere now pipes up with

johnh10000@tux:~$ idjc
Internet DJ Console Version 0.7.7
Copyright 2005-2008 Stephen Fairchild
Released under the GNU General Public License V3.0

user chose to create a new profile
copying settings from default profile
cp: omitting directory `/home/johnh10000/.idjc/profiles/default/jingles'
cp: omitting directory `/home/johnh10000/.idjc/profiles/default/profiles'
Language translation: en_GB
/usr/lib/python2.5/site-packages/idjcgui.py:1565: DeprecationWarning: os.popen2 is deprecated.  Use the subprocess module.
  self.mixer_ctrl, self.mixer_rply = os.popen2([ libexecdir + "idjcmixer" ], 4096)
no message buffer overruns
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/idjcgui.py", line 2360, in <module>
    run_instance = MainWindow()
  File "/usr/lib/python2.5/site-packages/idjcgui.py", line 1731, in __init__
    self.mic_select = nice_mic_togglebutton()
  File "/usr/lib/python2.5/site-packages/idjcgui.py", line 225, in __init__
    gtk.ToggleButton.__init__(self, label, use_underline)
RuntimeError: more argument specifiers than keyword list entries (remaining format:'):GtkToggleButton.__init__')
Mixer module has closed
johnh10000@tux:~$ 

any ideas

---

### Post by johnh10000 on 2009-07-18
Well be it in here or the other multimedia forum.  I've done it now.  With point .17.  of icecast.  And idjc.  All I need now is a decent dj player that doesn't click and give my voice eco.

DJpaly persists in not giving me any volume.

Thanks

---

