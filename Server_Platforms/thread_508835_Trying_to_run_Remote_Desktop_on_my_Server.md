---
title: "Trying to run Remote Desktop on my Server"
date: 2007-07-24
forum: Server Platforms
---

### Post by Sneo on 2007-07-24
Im trying to set up remote desktop access to my server, well basically I went and installed GNOME and what not.. However, when I try to connect to the server I get this:

```
root@SAX001:~# vncviewer localhost::21
VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
Error: Can't open display: 
root@SAX001:~# 
root@SAX001:~# vncviewer localhost::5900
VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
Error: Can't open display: 

```

Anyone got any idea whats going on?

---

### Post by astralsin on 2007-07-24
i dont mean to spam, but this explains how to do just what you're trying to do.

[http://www.astralsin.com/archives/open-source-applications/build-a-home-server-keep-the-gui-but-ditch-the-monitor/](http://www.astralsin.com/archives/open-source-applications/build-a-home-server-keep-the-gui-but-ditch-the-monitor/)

---

