---
title: "Ubuntu needs advanced mouse settings!!"
date: 2019-04-27
forum: Ubuntu, Linux and OS Chat
---

### Post by petersonak47-b on 2019-04-27
It is ridiculous that in the middle of 2019 the mouse settings are so basic and do not change almost anything in the mouse options. There is no option to remove mouse acceleration, something that even Windows XP has, if you need to remove the mouse acceleration for example is the biggest complication in the internet tutorials and that often does not work. the mouse options do not have basic speed information. It has almost no difference from fast to slow. FPS players flee the system because of this, designers who need precision and more. It's time to put your hand in the dough and do something about it. There is a lot more to improve, I am an enthusiastic user and I decided to create this thread to see if we have some solutions. And do not come up with tutorials or stuff like that, or if you want a third-party program for mouse options exists on Linux, that's going to be sad and comical at the same time, thanks if you've read up here and sorry for my English,

---

### Post by TheFu on 2019-04-28
Mouse settings are configurable using whatever mouse driver config took you might have.  I don't really use mice, but for the touchpad, my laptop uses the **synclient** tool to set specific features.  It is not a GUI. There are over 60 different options that it controls. A few of them:
```

    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0513479
    CoastingSpeed           = 20
    CoastingFriction        = 50
```
I've never looked for a GUI to control all the settings.

BTW, nobody here works for Canonical.  If you want support from the company, then you'll need to file a bug report using their bug reporting tool.
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)  Might want to reword the bug to be a little nicer.  I'm fairly certain that if you created the GUI of your dreams to control all the mouse settings and got it into Debian, they'd use it.

---

### Post by him610 on 2019-04-28
Unless you insist on using Ubuntu, you could install Xubuntu that has a Mouse and Touchpad utility in Settings.

---

### Post by mastablasta on 2019-04-29
> **petersonak47-b said:**
> It is ridiculous that in the middle of 2019 the mouse settings are so basic and do not change almost anything in the mouse options. There is no option to remove mouse acceleration, something that even Windows XP has, if you need to remove the mouse acceleration for example is the biggest complication in the internet tutorials and that often does not work. the mouse options do not have basic speed information. It has almost no difference from fast to slow. FPS players flee the system because of this, designers who need precision and more. It's time to put your hand in the dough and do something about it. There is a lot more to improve, I am an enthusiastic user and I decided to create this thread to see if we have some solutions. And do not come up with tutorials or stuff like that, or if you want a third-party program for mouse options exists on Linux, that's going to be sad and comical at the same time, thanks if you've read up here and sorry for my English,


the gnome user interface is made under philosophy where only minimal options are there for the user so they would not be overwhelmed with options. this is often good because it makes a new OS simple to use and is easy to get around. the options are still there but might often involve "3rd party" app or CLI. 

KDE is the opposite - the GUI interface has as many options as possible. often settings come in simple and advanced mode that opens up numerous buttons, tick boxes... this can be overwhelming for some. but some "power users" that prefer to talk with PC via GUI rather that in CLI (in foreign language no less) KDE is the way to go.


@[COLOR=#000000]him610 - Xubuntu is based on GTK, so it is very likely that if you knew the package form the settings app you could install only that interface in Ubuntu.[/COLOR]

---

### Post by DuckHook on 2019-05-01
> **mastablasta said:**
> …it is very likely that if you knew the package form the settings app you could install only that interface in Ubuntu.
XFCE4 mouse panel is run with *xfce4-mouse-settings* which in turn is part of *xfce4-settings*.  In a default Ubuntu install, it drags in the following dependencies:```
  greybird-gtk-theme libexo-1-0 libexo-2-0 libexo-common libexo-helpers libgarcon-1-0 libgarcon-common
  libxfce4ui-1-0 libxfce4ui-2-0 libxfce4ui-common libxfce4util-bin libxfce4util-common libxfce4util7
  libxfconf-0-2 xfconf xubuntu-icon-theme
```…which is a lot for such a simple utility, but not an outrageous amount either.

@OP

The default gnome mouse utility is rather anemic, but, like mastablasta said, gnome is trying to go the less-is-more route. A (very) few extra controls are available in gnome-tweaks, but it isn't much. Still, better than nothing.

---

### Post by rbmorse on 2019-05-02
I own a Razer Mamba Gaming mouse and there are a number of GUI and CLI utilities for controlling Razer mice settings in the repository, although I have not installed any of them because I'm fine with the defaults.

You didn't tell us what kind of mouse you use, but you might check the repo or with the hardware manufacturer to see if they offer tools that work with Linux.

---

