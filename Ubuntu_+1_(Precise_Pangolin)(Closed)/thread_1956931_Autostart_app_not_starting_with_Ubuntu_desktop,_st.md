---
title: "Autostart app not starting with Ubuntu desktop, starts twice with Gnome desktop"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by w-sky on 2012-04-11
Hi there.

After I installed the application "ClipIt", a clipboard manager that is supposed to start automatically with system start, everthing was fine at first.

I was using the Gnome 3 desktop during installation and ClipIt was magically added to autostart programs.

Later I was using the Ubuntu (3D) desktop on the same machine and then ClipIt did not start automatically. So I manually added it to the list of autostart programs using system configuration and there adding the ClipIt command line.

So everything was fine too with the Ubuntu desktop. Though later I am using the Gnome 3 desktop again and now ClipIt starts twice during system start! No huge problem because I can end one instance, but the most awkward thing is that there is no control for autostart programs with Gnome 3 (or I can not find it).

---

### Post by mc4man on 2012-04-11
Pretty simple - 
when clipit installs it places a file in /etc/xdg/autostart, (clipit-startup.desktop

However it has a line in it that prevents it from being started in a ubuntu (Unity) session
> OnlyShowIn=GNOME;XFCE;LXDE;
Whether intentional or an oversight don't know

When you add a startup then all sessions will use so you get 2 instances in GS

So you could - 
delete the file in /etc/xdg/autostart
or
disable/remove the startup you created & edit the line, I'd try this

```
sudo gedit /etc/xdg/autostart/clipit-startup.desktop

```
```
OnlyShowIn=GNOME;XFCE;LXDE;Unity;
```

Or just remove the line altogether in the .desktop

Edit: just in case you think I may of mistyped  - when placed in a line in a .desktop,  "Unity" is correct, "UNITY" is not

---

