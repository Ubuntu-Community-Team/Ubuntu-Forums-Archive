---
title: "Vino set to another Windowsmanager"
date: 2007-01-19
forum: Server Platforms
---

### Post by drakedog on 2007-01-19
How to configure vino-server to use Windowsmanager Beryl? I use the standard configuration of Ubuntu Gnome, which means i have not installed vncserver or/and vnc-java yet. Is it possible to use vino like it is default with Windowsmanager Beryl?

---

### Post by n3ko on 2007-02-02
Hi! I've the same problem: with beryl on my desktop vino displays only black screen. I've tried x11vnc too, (it was all right with xgl and beryl 0.1.3).
i've upgraded to edgy with new beryl and rendering on nvidia. x11vnc shows the display, can move the mouse, but no more (type or click).
killall beryl solved the problem with vino and x11vnc too. all works just fine. (beryl-manager fall backs to metacity)
When i go back to my workstation, just need to restart beryl. :)

---

### Post by krunge on 2007-02-19
The -noxdamage option to x11vnc seems to be needed on OpenGL
things like beryl, MythTV, etc.  More info: [http://www.karlrunge.com/x11vnc/#faq-beryl]("http://www.karlrunge.com/x11vnc/#faq-beryl")

---

