---
title: "connecting remotely and glxinfo, glxgears issues"
date: 2011-04-04
forum: Server Platforms
---

### Post by cormu7 on 2011-04-04
Hello,

I am currently running Ubuntu 10.04 Linux server. I have been running into issues lately trying connect remotely to the server and using commands like  "glxgears", "glxinfo", etc.

When I am at my machine/server, and i can run these commands and have no problems or error messages.

However, when I connect to the server remotely from a windows computer, using NX or VNC, I get the following messages using the following commands:

> % glxgears
Error: couldn't get an RGB, Double-buffered visual
and

>  % glxinfo
name of display: :2000:0
Error: couldn't find RGB GLX visual or fbconfig
Is there something simple that i'm missing here??.  Is there a setting or something that must be set when connecting remotely?  Any help would greatly be appreciated.

thanks,

cor

---

### Post by cormu7 on 2011-04-07
any ideas?

Has anyone else experienced similar problems with freeglut, glx when connecting remotely to a server?

cor

---

