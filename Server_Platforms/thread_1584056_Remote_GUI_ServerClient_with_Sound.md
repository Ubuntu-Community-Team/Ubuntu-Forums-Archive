---
title: "Remote GUI Server/Client with Sound"
date: 2010-09-28
forum: Server Platforms
---

### Post by XanTrax on 2010-09-28
Hi,

I am looking for a client/server application that can allow me to have remote GUI access (eg: VNC) but with the ability to use sound.

I see that TeamViewer has a linux application out now but for my company, it would compromise security protocol because it reaches out to the TeamViewer servers to do any work.  

Basically, we have applications that require a GUI and we need to hear sounds from them if they throw an alert (the app is a monitoring tool).  

We are running a VNC server on it currently and when our monitoring machine was on Windows, TightVNC was able to get the sound...that is not the case with any Linux client so I am wondering if there is actually one that exists.

Thank you.

---

### Post by bluefrog on 2010-09-29
have a look at freenx (nomachine). it may do that

---

### Post by XanTrax on 2010-09-29
Thank you, will do so now and let you know what I find.

---

### Post by XanTrax on 2010-09-29
Doesn't seem like a bad fit but its almost overkill as this looks like it overwrites the entire X window system with its own.

I guess I was more or less just looking for a VNC client that can enable sounds.  The Xvnc server daemon forwards the sounds fine (as seen when we used the windows TightVNC client) so I may just end up throwing in wine and seeing how TightVNC works.

Thanks for the suggestion!

---

