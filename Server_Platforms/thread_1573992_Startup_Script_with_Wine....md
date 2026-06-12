---
title: "Startup Script with Wine..."
date: 2010-09-13
forum: Server Platforms
---

### Post by but2002 on 2010-09-13
I'm using a Linux VPS with Ubuntu 9.10 and I have a set of commands that I need to issue on boot


```
export DISPLAY=:1
Xvfb :1 -screen 0 1024x768x16 &
fluxbox -display :1 &
su cewebsite
cd ~/server1
wineconsole haloceded.exe -port 2302 &
cd ~/server2
wineconsole haloceded.exe -port 2304 &
```

If I put this in a startup script, only Xvfb starts up, and fluxbox never does.

I can put it in a manual .sh file, then fluxbox starts up, but when it gets to su cewebsite, the sh script stops executing..

So I have the first part in a .sh script that's executed manually then I manually start up the servers.

I want all of this to be automated on boot, any ideas/suggestions?

---

### Post by LightningCrash on 2010-09-20
wouldn't it be better to have everything from fluxbox on down in an .xinitrc file?

that could be the issue

---

