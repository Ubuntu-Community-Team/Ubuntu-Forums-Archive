---
title: "HowTo: Start games directly from GDM"
date: 2006-06-09
forum: Tutorials
---

### Post by Zeroedout on 2006-06-09
Hello all. This howto will tell you how to start a game right from the sessions menu of GDM. I do this because I run Xgl and compiz, and the performance of games while they are running is pretty shitty. What this does is instead of starting a window manager, and then starting a game, you can start the game directly. It's extremly easy to do, saves some memory when playing the game, and makes using Xgl/compiz and gaming on the same box much easier. I'm also a memory whore, and figure, if I can save a few megs by not using a window manager at all, why not?

All you have to do is create a game.desktop entry in /usr/share/xsessions . So for example we'll use quake4.
Open a terminal and go to /usr/share/xsessions
```
cd /usr/share/xsessions
```

Use a text editor of your choice and create a quake4.desktop file.

```
sudo gedit quake4.desktop
```

Now create the Entry.
```
[Desktop Entry]
Encoding=UTF-8
Name=Quake4
Comment=Start Quake 4 straight
Exec=quake4
TryExec=quake4
Type=Application

```

And there we go. Restart GDM ```
sudo /etc/init.d/gdm restart
``` and it should appear under sessions.

I Hope this basic howto was at least somewhat usefull. Enjoy

---

### Post by Padreic on 2012-12-07
Hey,

I tried to do this with LightDM and Lord of the Rings Online. I am using Ubuntu 12.10. However, it doesn't show up in the selection menu in LightDM.
Here is my file:
```
sudo cat /usr/share/xsessions/DHDRO.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Der Herr der Ringe Online
Comment=Der Herr der Ringe Online spielen  
Exec=pylotro
Type=Application
```

Any help is much appreciated.

---

