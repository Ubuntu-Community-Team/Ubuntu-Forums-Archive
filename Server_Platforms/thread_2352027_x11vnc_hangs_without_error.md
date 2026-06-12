---
title: "x11vnc hangs without error"
date: 2017-02-08
forum: Server Platforms
---

### Post by aashidham on 2017-02-08
[FONT=arial]I've been able to start an Xorg server with Xdummy at :345. However, when I try to run x11vnc on :345, I never get a printout that tells me where the VNC server is located or what port it runs on. Instead the x11vnc process only prints one line and hangs there:[/FONT]
[FONT=arial]

07/02/2017 16:20:37 x11vnc version: 0.9.13 lastmod: 2011-08-10  pid: 13505
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I've tried accessing port 5900 (where the VNC server is ostensibly located), but no process is hosting anything at that port.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I'm running on Ubuntu 14.04 LTS. Here is my Xorg invocation (provided by Xdummy):[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]env LD_PRELOAD=/tmp/Xdummy.aashidham/345/Xdummy.so Xorg :345  -config xdummy_modified_xconfig.conf_345
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Here is my x11vnc invocation:[/FONT]
[FONT=arial]x11vnc -display :345 -nopw
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Whats going on? x11vnc works fine when it is on an Xorg server started with startx.
[/FONT]

---

