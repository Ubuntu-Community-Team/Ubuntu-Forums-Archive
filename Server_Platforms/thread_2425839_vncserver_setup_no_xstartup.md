---
title: "vncserver setup: no xstartup?"
date: 2019-08-31
forum: Server Platforms
---

### Post by hadenough on 2019-08-31
Just installed 19.04 on a headless box, but I can't get a usable vnc session. I installed tigervncserver, and I'm connecting with RealVNC from Windows. The connection is fine, but tigervncserver doesn't come with a default xstartup. I've tried:


[LIST]
[*]My standard Centos6/7 xstartup, which runs gnome-session (I also use tigervnc on Centos, with RealVNC on Windows) 
[*]half-a-dozen other ones from the net, where lots of people were complaining about this on earler Ubuntu versions 
[/LIST]

None of them work. I get either a black or grey screen, or vncserver fails with a missing file somewhere. A basic xstartup of
```

#!/bin/sh   
unset SESSION_MANAGER
gnome-session&
```

just produces a black screen.

Was tigervncserver a bad choice? Does anything else come with an xstartup? Or can someone post a working xstartup? I don't actually care if it's Gnome or not, as long as it's usable. Thanks.

---

### Post by volkswagner on 2019-08-31
Server edition does not come with a GUI, so no need for VNC.
Just use SSH from Putty or terminal program of your choice.

Servers run from text configuration files, so there is no
need for a mouse or the overhead of desktop/window manager.

---

### Post by hadenough on 2019-08-31
I'm running a server, not the Server Edition software. I've got Gnome running on a locally-connected VGA monitor, which I need to dump.

---

### Post by volkswagner on 2019-08-31
You posted in server edition forum. Perhaps a moderator can move to desktop/video or more appropriate sub forum.

---

