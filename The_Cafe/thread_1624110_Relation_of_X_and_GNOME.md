---
title: "Relation of X and GNOME"
date: 2010-11-17
forum: The Cafe
---

### Post by Oxwivi on 2010-11-17
What exactly are they, how do they differentiate?

Will just installing X packages be enough to give me a functional DE?

---

### Post by 3Miro on 2010-11-17
X gives you the abilities to use the Video card to draw pictures on the screen. On top of that you have either GTK or QT that are toolkits to let you draw consistent elements (like windows, menus buttons). Then you have the DE KDE, which is based on QT or Gnome, XFCE and LXDE which are based on GTK. The DE comes with panels, menus, applets and a bunch of background processes that mange sound, drag/drop features between different windows and so on. You also have the window managers that live on top of the DE that place windows, draw windows decorations and create effects.

If you just install X, you can run a very very very basic DE, with basically only three terminals, but you can start other graphical applications (like Firefox).

---

### Post by Oxwivi on 2010-11-17
So basically, X provides programs with their own spaces in the monitor, and GNOME adds uses the ability and places more stuff?

On just X would there be any panel or menus?

---

### Post by cariboo on 2010-11-17
You still need a window manager, it doesn't have to be gnome or QT. I ran a system for years with just [wmaker]("http://windowmaker.org/").

---

### Post by Oxwivi on 2010-11-17
Is it in the Ubuntu repo? Would the X packages in the Ubuntu installers be enough for a functional DE?

---

### Post by Paqman on 2010-11-17
> **Oxwivi said:**
> Is it in the Ubuntu repo? Would the X packages in the Ubuntu installers be enough for a functional DE?

No. X itself doesn't contain any graphical interface bits. The minimum you could install to get a usable Gnome desktop would be the packages xorg and gnome-core. Personally i'd chuck in a few extras like gdm and a theme. You can play around with this kind of thing by installing a command line system using the minimal or alternate images.

There are minimal versions of Gnome, KDE, LXDE, etc, all ready-packaged in the repos. The trick is knowing exactly what packages you need to install. That's why I wrote the script in my sig, it does all the work for you.

---

### Post by Spice Weasel on 2010-11-17
Try out lwm for a window manager:

When they say lightweight, *they mean it*.

[http://www.jfc.org.uk/software/lwm.html](http://www.jfc.org.uk/software/lwm.html)

If you install X, you can use any graphical application you install.

Trouble is, you won't be able to move the windows around - that's where the wm comes in.

I recommend for a really lightweight desktop just having lwm and tint2/bmpanel for a panel.

There would be no panels or menus with just bare X11. Just a "root window" with no icons (or "desktop"), the ability to run graphical applications, a couple of basic programs and the mouse pointer.

The applications launched on start up are held in the ~/.xinitrc text file.

Here's an example ~/.xinitrc

```

#!/bin/bash
xsetroot -solid steelblue & # Sets the desktop background colour (The default is HORRIBLE!)
lwm & # The window manager
bmpanel & # The panel
firefox &
urxvt # Terminal emulator, when you close this X11 exits.

```

X11 is launched with the "startx" command on the terminal.

---

### Post by Oxwivi on 2010-11-18
So, X package + *wm = functional DE.

Noted.

---

