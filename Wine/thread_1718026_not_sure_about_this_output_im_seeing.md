---
title: "not sure about this output im seeing"
date: 2011-03-30
forum: Wine
---

### Post by tysonh80 on 2011-03-30
I'm installing Wow on my laptop.  I was running the patcher and left the house for a minute.  I came back and the laptop went into standby mode and when it came out it wouldn't do any more downloading.  I restarted and tried downloading again and got some strange out acting like the internet connection was timing out.  I took a screen shot for anyone can see it.

---

### Post by kostkon on 2011-03-30
You could try cleaning your windows temp folder in
```
~/.wine/drive_c/windows/temp
```
whereas ~/ means your home folder, i.e. /home/xxx/.wine/drive_c/window/temp
(enable the *View &#8594; Show Hidden files* option to access the .wine hidden folder from nautilus) and then try again with the patcher.

---

