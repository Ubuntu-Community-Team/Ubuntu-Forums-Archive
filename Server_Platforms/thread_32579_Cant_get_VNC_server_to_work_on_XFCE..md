---
title: "Cant get VNC server to work on XFCE."
date: 2005-05-08
forum: Server Platforms
---

### Post by DaturaX on 2005-05-08
Recently, i dumped Gnome for XFCE. I installed vncserver using apt-get
```

When i run vncserver 
New 'X' desktop is davenix:1

Starting applications specified in /etc/X11/Xsession
Log file is /home/dave/.vnc/davenix:1.log

```

When i do a ps-aux, the process is there running
```
dave      6404  0.5  1.3   4604  2512 pts/1    S    01:33   0:00 Xrealvnc :1 -desktop X -auth /home/dave/.Xauthority -rfbwait

```
When i check the logged file, vnc was is running
```
09/05/05 01:33:36 Xvnc version 3.3.7 - built Oct 28 2004 23:57:28
09/05/05 01:33:36 Copyright (C) 2002-2003 RealVNC Ltd.
09/05/05 01:33:36 Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
09/05/05 01:33:36 All Rights Reserved.
09/05/05 01:33:36 See http://www.realvnc.com for information on VNC
09/05/05 01:33:36 Desktop name 'X' (davenix:1)
09/05/05 01:33:36 Protocol version supported 3.3
09/05/05 01:33:36 Listening for VNC connections on TCP port 5901

```

Now I am trying to access vnc using vnc viewer 4 on a windowsxp system, it gives me the error *unable to connect to host: Connection refused(10061)*

Now I am starting to feel like a noob.

---

### Post by Firetech on 2005-05-08
Try adding :0 after the hostname on the Windows computer (E.G. "ubuntu:0"), it might be that.

---

### Post by LordHunter317 on 2005-05-08
It'd be :1, not :0.  Knowning how you're connecting exactly would help though.

---

### Post by DaturaX on 2005-05-08
I tried adding :0 to the hostname and am able to connect. It prompts me for my password but I cant do anything after that. This is what I get on my vnc.

[IMG]http://www.imagehosting.us/imagehosting/showimg.jpg/?id=435072[/IMG]

I am running XFCE on the ubuntu box. The client accessing the VNC is a windows machine running VNC Viewer Enterprise Edition 4.0

---

