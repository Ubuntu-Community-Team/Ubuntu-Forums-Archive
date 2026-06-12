---
title: "This x server thing"
date: 2009-12-28
forum: Server Platforms
---

### Post by Stratosmacker on 2009-12-28
Hey im fairly new to the world of unix, linux, and ubuntu. Im pretty handy with windows but after seeing what you could do with unix and linux i got myself a mac and my other computers run ubuntu. Now i know that the x server has something to do with the gui of mu system, but does anyone have a good explanation thats not to out there of what it is and what xdmcp is (remote?).

---

### Post by lykwydchykyn on 2009-12-28
Wikipedia has a good article on X: [http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

Essentially, X is a client/server system.  The X server talks to the hardware and draws the graphical output on your display.  The X clients are programs that you run which have graphical output -- applications, desktop environments, window managers, etc.  The client sends its graphical output to the server, which draws it on the screen.

The client and server don't have to be on the same system, hence things like forwarding X applications over ssh, or XDMCP.  With XDMCP you are basically rendering all the client applications for a session on a remote machine on your local X server.

clear as mud?

---

