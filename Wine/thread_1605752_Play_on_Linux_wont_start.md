---
title: "Play on Linux wont start"
date: 2010-10-25
forum: Wine
---

### Post by pieman711 on 2010-10-25
When I tried to run POL today it said it needed to check updates and then just closed. Running it from the applications menu did nothing. I ran it from terminal and got this output:
Traceback (most recent call last):
  File "/usr/share/playonlinux/python/mainwindow.py", line 471, in <module>
    app = PlayOnLinuxApp()
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7978, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7552, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/share/playonlinux/python/mainwindow.py", line 462, in OnInit
    self.frame = MainWindow(None, -1, "PlayOnLinux")
  File "/usr/share/playonlinux/python/mainwindow.py", line 51, in __init__
    self.texte_update = wx.StaticText(self.panel_update, -1, _("An updated version of PlayOnLinux is available.")+" ("+sys.argv[2]+")",pos=(35,0))
IndexError: list index out of range

I quickly googled list index out of range and used gedit to change sys.argv[2] in */usr/share/playonlinux/python/mainwindow.py* to sys.argv[1]. It now boots but I haven't tried using it to install games. I'm not a programmer other than playing with Basic when I was a teenager and have no idea what the problem was and what exactly I've done here. Has anyone else had a similar problem? Does my fix here seem safe enough to carry on with, or is there a better way around it?

---

### Post by jimmyfi on 2010-10-27
I reinstalled play on linux and works now.. kinda odd that it started to give that error after latest pol patch o.O

---

