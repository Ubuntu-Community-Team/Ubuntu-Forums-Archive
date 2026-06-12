---
title: "GUI with PuTTy login?"
date: 2007-10-26
forum: Server Platforms
---

### Post by HaloFreak69 on 2007-10-26
i have recently installed Ubuntu server on my pc and have gotten Ubuntu desktop to work with it. while i have Ubuntu GUI running on my host, how can i get it to run on another computer logging in? I have searched everywhere, and if I ever found something explaining it, it was too complicated. can anyone give me a step by step process?:confused:
Any suggestions greatly appreciated

---

### Post by whit on 2007-10-26
Putty is just a terminal login. If you want to view the desktop, You might look at a VNC - see [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402) - or if your other system runs X, look at enabling remote use of the desktop session using xhost and so on.

---

### Post by HermanAB on 2007-10-26
You can run X applications using PuTTY, if you have an X server running first.  See Xming on Sourceforge.  This is more powerful than VNC.

---

