---
title: "VMPlayer over vnc has problems with keyboard layout and shift"
date: 2008-08-27
forum: Virtualisation
---

### Post by arobinson on 2008-08-27
I am running the latest vmplayer with a WinXP guest on my desktop Ubuntu box. On that linux box, I am running x11vnc. On my laptop running xvnc4viewer (also tried krdc), I connect to the desktop. All 3 computers use the dvorak keyboard layout. 

Typing in windows in lowercase works fine (the 4 home keys type "aoeu"). When I hold shift down I get "AR>G". If I change the keyboard layout in Windows to Qwerty (using the language bar), I get "asdf" in lower case and "AOEU" with shift down. So it seems that when the shift key is down, the keyboard map is getting applied twice.

If I am at my desktop everything works fine, it is only over vnc that I have this issue.

Anyone know why this may be happening and if there may be a workaround?

This post looks similar, but has no replies:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=895618](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=895618)

---

### Post by powdermonkey1850 on 2008-08-28
I had a similar problem using vnc using the Gnome desktop ... i switched to using fluxbox and it fixed ... this is what the xstartup file looks like found in the home/.vnc folder
note the gnome line iscommented out.  Hope this helps


#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#gnome-session &
exec fluxbox
xstartup (END)

---

