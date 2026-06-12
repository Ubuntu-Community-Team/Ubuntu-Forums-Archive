---
title: "Fileshare and remote access linux to windows"
date: 2009-09-14
forum: Server Platforms
---

### Post by sam.dale on 2009-09-14
Hi. 
I'm really new at this and need your help. 
I got to pcs. Windows and now Linux. I wanna be able to filseshare and maybe remote access windows pc from my linux pc.. 
Can any one help me here ? :confused::confused::confused:
I need detaled instructions or something i can google.

Thanks a lot :)

---

### Post by CoolHand on 2009-09-14
For remote access I suggest you look into vnc.  You can run the tightvnc server/client for free and terminal server client works well connecting to it once you install the client on the linux box.  If you want to run the linux box from windows you can do that as well.  Use the tightvnc client on windows and on linux go to system/preferences/remote desktop to set up the linux side.


As for shares, if you are sharing a folder on the windows box all you need is a samba client.  Nautilus I believe can handle this now the way ubuntu is shipped.  Try this in your file manager on the linux box.  smb://[ip of your win pc]/directory

Hope that helps.

---

