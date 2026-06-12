---
title: "connect to vncserver, getting gray screen"
date: 2005-10-24
forum: Server Platforms
---

### Post by taipeiben on 2005-10-24
I'm trying to connect to my computer running ubuntu from a windows xp box, but I'm getting only a gray screen on my vnc client.  In Fedora I just had to uncomment:

unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc

in a xstartup file.  I've been trying to follow: [http://www.ubuntuforums.org/showthread.php?t=2323](http://www.ubuntuforums.org/showthread.php?t=2323) but I still can't seem to get rid of that gray screen.

---

### Post by markthecarp on 2005-10-24
[QUOTE=taipeiben]I'm trying to connect to my computer running ubuntu from a windows xp box, but I'm getting only a gray screen on my vnc client.  In Fedora I just had to uncomment:

unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc

in a xstartup file.  I've been trying to follow: [http://www.ubuntuforums.org/showthread.php?t=2323](http://www.ubuntuforums.org/showthread.php?t=2323) but I still can't seem to get rid of that gray screen.[/QUOTE]

See what /etc/X11/xinit/xinitrc is calling. I have ```
exec /home/username/.vnc/xinitrc
``` in /etc/vnc.conf and ```
# exec gnome-session
exec fluxbox
``` in the user's file.

I generally make my vnc sessions in fluxbox. The grey screen is most likely twm. The default window manager for X. Left or right click and hold for a menu, experiment here it's been awhile since I used twm. Fluxbox and blackbox, hell even fvwm2 can be quite nice. 

Ah, you're viewing from windows, you'll need an X server for windows or the java version. FreeNX looks cool but there's no current package for Ubuntu.

-mark

---

