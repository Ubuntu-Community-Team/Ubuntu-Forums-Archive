---
title: "VNC error"
date: 2009-03-29
forum: Server Platforms
---

### Post by rawandnet on 2009-03-29
I have install VNC client and VNC server. I can connect from computer A to B, but can't connect desktop from B to A. I get error (unable connet to secket: no route to host (113).

any Idea why is that?

thaks

---

### Post by HermanAB on 2009-03-29
You need to install the server on both machines. On one of them, it is either not running or the firewall is blocking the communications.

However, if both machines are running Linux, then you would be better off with SSH instead.  Install the ssh-server package.  SSH can do everything VNC does, only better.

---

