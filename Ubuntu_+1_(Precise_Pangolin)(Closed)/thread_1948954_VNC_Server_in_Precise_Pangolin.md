---
title: "VNC Server in Precise Pangolin"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by seanlano on 2012-03-29
I'm currently experimenting with Precise on a laptop set-up as a fileserver. I previously had 10.04 running on it, which I replaced with 12.04. 
I used to have "tightvncserver" set up so that I could ssh into the machine and bind some ports and start the VNC server with "vncserver :1" and then on another computer connect with "vncviewer localhost:2". This worked fine. 

Whenever I do this on Precise, I can get a VNC window, but it says *failed to load session "ubuntu"* in a little grey window within the VNC client, which only has one option - logout. 

What do I need to put in the VNC config file to get a VNC connection in Precise?

---

### Post by Aenima99x on 2012-03-29
I've found that the most reliable option for me was setting up x11vnc (which allows for connections at the lightdm login).
[Good tutorial on setting it up here, scroll down for the English instructions]("http://www.dannratemal.de/?p=450"). Hope this helps.

---

