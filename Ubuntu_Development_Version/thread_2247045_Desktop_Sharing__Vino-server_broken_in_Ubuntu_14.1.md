---
title: "Desktop Sharing / Vino-server broken in Ubuntu 14.10?"
date: 2014-10-05
forum: Ubuntu Development Version
---

### Post by philhughes on 2014-10-05
Is any one else having problems with Desktop Sharing in Ubuntu 14.10? I find that I can connect to a 14.10 desktop, but the update of the display is frozen in the VNC client. I see the desktop, with launcher and panel, but the time is stuck. Clicking on an app in the launcher does start the app, but the app does not appear on the VNC client screen. This happens when logging in using either Remmina on Ubuntu 14.04 on UltraVNC from a Windows 8.1 PC.

---

### Post by tcmbackwards on 2014-10-11
I have the same problem. It's reminiscent of when Ubuntu switched to Compiz and broke xdamage, the vnc server never learned which parts of the screen had changed so it could send the updates to the client.

This isn't the same thing however, I've tried running vino-server and x11vnc with and without xdamage or forcing full screen updates and it does the same thing every time, the display comes up but no updates to the screen. The inputs are being accepted, if you close and reopen the client it shows all the windows you clicked on. It's just not updating the screen in real time.

It's just not possible to use a VNC server in utopic right now.

---

### Post by philhughes on 2014-10-12
I just got around to doing a fresh install of the latest daily build, but got the same behaviour. I was going to file a bug against vino-server, but seeing as you said it also happens with x11vnc, it looks like the problem is elsewhere.

---

### Post by philhughes on 2014-10-15
Bug report submitted:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1381483](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1381483)

---

