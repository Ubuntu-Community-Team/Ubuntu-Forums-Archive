---
title: "VNCServer opens 100 sessions/displays"
date: 2011-04-13
forum: Server Platforms
---

### Post by dlmaldet on 2011-04-13
Please excuse me for some of my ignorance as I am a new Linux user. I am setting up a server with Ubuntu Server edition. It is has 4gb of ram and had been working great the first week or so but something strange started happening about the same time I installed MythTV. After that, the server would slow down considerably and the ram being used would go from about 400megs up to all of the 4gb and use about 2gb or swap. After much research and investigating, I've narrowed it down to the vncserver starting up all 100 displays/sessions even if I try to specify one with : vncserver :1. I can't figure out how to just open one. Any help is appreciated.

---

### Post by ruffEdgz on 2011-04-13
Its hard to say how to help you with this problem since there are many VNC Server applications that you could have downloaded. I would suggest reading this KB page from ubuntu about VNCServers and if I can guess which VNC server you downloaded, read more about **tightvncserver**:

[https://help.ubuntu.com/community/VNC/Servers#tightvncserver](https://help.ubuntu.com/community/VNC/Servers#tightvncserver)

If that isn't the one you downloaded, then read the rest of the article and see if it gives you more info. If you still can't find your answer on that, hit us back at this forum with more information about what VNCServer you are using so we can help more.

---

### Post by dlmaldet on 2011-04-13
Yes, you are correct...it is tightvncserver that I've installed. I read the link you provided and it didn't seem to help me. I tried using "tightvncserver :1" with no luck. I then thought about trying :99 and that only caused the session to start at 99 then move to 1 and 2 and so on through all 100.

---

### Post by egpetrich on 2011-04-14
Two thoughts:
[LIST]
[*]Can you use "tightvncserver -kill" to shut down some of the extra servers? I'd like to determine if you can kill the servers and if they stay dead. (As a side note: It would be *really* kludgy, but you could always let all of the servers be created and then kill the ones you don't want.)
[*]Do you have a "~/.vnc/xstartup" script? If so, what are its contents? (Wondering if there's a recursive call to "tightvncserver" somewhere....)
[/LIST]

---

