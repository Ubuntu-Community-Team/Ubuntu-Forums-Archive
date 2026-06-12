---
title: "simple play/pause indicator"
date: 2014-10-24
forum: Ubuntu Application Development
---

### Post by rrob on 2014-10-24
Hello,
I would love simple indicator. Only one button Play/Pause.
Sending same scancode like button on multimedia keyboard.

I install xvkbd and I can send command "xvkbd -text '\[XF86AudioPlay]'" from console which play/pause music.

I also found way how to do it from python:
bashCommand = "xvkbd -text '\[XF86AudioPlay]'"
import subprocess
process = subprocess.Popen(bashCommand.split(), stdout=subprocess.PIPE)
output = process.communicate()[0]

Or do it better way with xtest, send keys directly from python
[https://pypi.python.org/pypi/xtest/1.0](https://pypi.python.org/pypi/xtest/1.0)

And now put it in some script like on:
[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators)

And done.

Can someone help?

---

### Post by tgalati4 on 2014-10-24
What music player do you usually have playing?  Many players have command line control that you can map to physical keys and there is a variety of client-based players with different panel options. 

A simple way would be to put a "Custom Application Launcher" on the panel, style the icon using a play button and put the bash command you gave in the command box.

---

### Post by rrob on 2014-10-24
I do not have extra physical keys. (On laptop)
That's why I want the indicator. To replace a missing hw keys.
Players are mostly integrated in the volume menu.
One directly visible indicator button will be super fast and simple.
And media key is so good because it works with all players, even those who are not integrated in the volume menu.

---

### Post by tgalati4 on 2014-10-25
Well, I tried the Launcher approach and it didn't work.  Nor did using the *xvkbd* command in a the bash terminal.  I had rhythmbox running and on pause.  I think you need a dbus command to send the keystroke to a specific application.  It's not clear to me how to pipe a single key into the default keyboard input.  I'm sure there is a way.  I just don't know it.

---

