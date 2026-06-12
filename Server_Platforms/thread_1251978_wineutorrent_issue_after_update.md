---
title: "wine/utorrent issue after update"
date: 2009-08-28
forum: Server Platforms
---

### Post by gobbledigook on 2009-08-28
Hi!

i just updated to 9.04 and after i did a reboot and started vncserver (tightvnc) i opened a session and tried to start utorrent but it bugs out! 

here's what i get:
```

server@server:~$ wine utorrent
Xlib:  extension "Generic Event Extension" missing on display ":1.0".
fixme:heap:HeapSetInformation 0x110000 0 0x46fdfc 4
server@server:~$ 

```

it pauses for a while and then an empty dialogue box pops up which disappears when i click in the middle of it. I think its the dialogue box from utorrent which says "if you paid for this you were ripped off!" 

my xstartup file looks like:

```

#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
/etc/X11/Xsession

```

any ideas greatly appreciated :)

Dan,

---

### Post by zemon_ on 2009-08-29
Try adding the exe on the end

```
wine utorrent.exe
```

---

