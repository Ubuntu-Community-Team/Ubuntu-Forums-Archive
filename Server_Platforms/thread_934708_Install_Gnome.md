---
title: "Install Gnome?"
date: 2008-09-30
forum: Server Platforms
---

### Post by Dissident85 on 2008-09-30
Hi all, I have ubuntu server installed and I wanted to install the Gnome Desktop environment. Now i think I would do this using the command 
```
sudo apt-get install x-window-system
```
Well I know that’s how I would do it in debian (with out the sudo) 

But my question is how would I configure it not to start the window system on start up, and only when I invoke the command
```
startx
```?? 

Is that posible?

---

### Post by Vegan on 2008-09-30
If you are hard up for a GUI, use the desktop version of Ubuntu.

---

### Post by Dissident85 on 2008-10-01
> **Vegan said:**
> If you are hard up for a GUI, use the desktop version of Ubuntu.

Well I am not so "hard up" for the GUI, I would just like it as an option for times when I have physical access to the server.

And 1, I don’t want to have to reinstall ubuntu as I have it already configured. and 2, if I am not mistaken if I install the desktop edition it will automatically load up the Gnome window manager at start-up, which I don’t want.

---

### Post by aysiu on 2008-10-01
I think as long as you don't install GDM, KDM, WDM, or XDM, you'll have to type *startx* to get out of the console (which is the behavior you want, right?)

---

### Post by eppo on 2008-10-01
otherwise, what you could do is install tightvncserver and your favorite wm, i used fluxbox.
because i do everything remotely.

---

### Post by Sycron on 2008-10-01
I do things remotely. That's a good,useful and simple innovation.

---

### Post by lykwydchykyn on 2008-10-01
I'm not sure if there is the x-window-system package on Ubuntu, I generally just install xorg, it has the same effect.  xorg plus the WM/DE of your choice.

---

### Post by aysiu on 2008-10-01
> **lykwydchykyn said:**
> I'm not sure if there is the x-window-system package on Ubuntu, I generally just install xorg, it has the same effect.  xorg plus the WM/DE of your choice.
*x-window-system-core* is what it used to be called in older versions of Ubuntu. It's now called *xorg*.

---

### Post by Dissident85 on 2008-10-01
> **aysiu said:**
> I think as long as you don't install GDM, KDM, WDM, or XDM, you'll have to type *startx* to get out of the console (which is the behavior you want, right?)

yes, that’s what I am wanting to do. but how do I exclude those packages when installing xorg?

---

### Post by aysiu on 2008-10-01
> **Dissident85 said:**
> yes, that’s what I am wanting to do. but how do I exclude those packages when installing xorg?
You don't have to. *xorg* isn't related to any of the display managers.

---

### Post by lykwydchykyn on 2008-10-01
gdm is a dependency (indirectly) of gnome, though, so if you install the gnome package you'll get gdm.  Even if you end up installing it, you can just disable it by deleting the S99gdm symlink from /etc/rc2.d.  There's a handy command that can do it to, but it eludes me just now...

---

### Post by windependence on 2008-10-02
sudo apt-get install gnome-desktop

Still, you should manage your server remotely or from the CLI. GUIs are for desktops. ;)

-Tim

---

### Post by aysiu on 2008-10-02
> **windependence said:**
> sudo apt-get install gnome-desktop

Still, you should manage your server remotely or from the CLI. GUIs are for desktops. ;)

-Tim
There's no package called *gnome-desktop*

You can install *gnome*, *gnome-core*, *gnome-desktop-environment*, or *ubuntu-desktop*, though.

---

### Post by windependence on 2008-10-02
Sorry, my bad:

```
apt-get install x-window-system-core xserver-xorg gnome-desktop-environment
```

-Tim

---

