---
title: "LXPanel 0.3.5 - Multiple panel is supported for this lighteweight desktop panel"
date: 2008-04-17
forum: The Cafe
---

### Post by PCMan on 2008-04-17
LXPanel is the desktop panel of LXDE (Lightweight X11 Desktop Environment) [http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)

The latest development branch is released today.
[http://www.gnomefiles.org/app.php/LXPanel](http://www.gnomefiles.org/app.php/LXPanel)

Multiple panel support is added now.
That means, you can have two panels just like what gnome-panel and xfce4-panel already did.

Here is a screenshot:
[IMG]http://people.linux.org.tw/~pcman/lxde/lxpanel_two_panel.png[/IMG]

So, it's possible to create UI similiar to default ubuntu with lxpanel now.

---

### Post by smartboyathome on 2008-04-17
It looks like it is more possible to create a default UI similar to Xubuntu right now, not Ubuntu. What it really needs is the ability to run GNOME panel applets in it, like XFCE. ;)

---

### Post by firmit on 2008-04-29
> **smartboyathome said:**
> It looks like it is more possible to create a default UI similar to Xubuntu right now, not Ubuntu. What it really needs is the ability to run GNOME panel applets in it, like XFCE. ;)

Hmm - Xfce does not run gnome panel applets per se. Xfce has its own volume-manager etc. However, the System Tray lets you display the gnome-network-applet among other thins, and the update-notifier. 

LXDE may also show this - but not by default - however this is NOT the panel's fault. Every .desktop item have a listing called: OnlyShowIn=GNOME;XFCE;

Simply add LXDE to the list, and restart X. 
Example;
cp /etc/xdg/autostart/update-notifier.desktop  ~/.config/autostart

And add LXDE to OnlyShowIn:
```
[Desktop Entry]
Encoding=UTF-8
Name=Update Notifier
Comment=Update notification daemon
Icon=update-notifier
Exec=update-notifier
Terminal=false
Type=Application
Categories=
OnlyShowIn=GNOME;XFCE;LXDE;
X-Ubuntu-Gettext-Domain=update-notifier

```

Ctrl-Alt-Backspace - login and you'll see :)

---

### Post by Darkhack on 2008-04-29
Looks great.  I'm really happy to see lightweight alternatives.  These days it seems like a lot of programmers don't even consider performance when writing applications.  People sometimes assume that you have to sacrafice features for speed which is false.  Take WebKit versus Trident in rendering engines for example.  WebKit has more features and is several times lighter.

---

### Post by chochem on 2008-05-21
Neat little thing, I must say. I'm using it to reanimate an ancient little laptop. One question: How do I get it to use the default icon theme (tango) rather than it's own icons?

---

