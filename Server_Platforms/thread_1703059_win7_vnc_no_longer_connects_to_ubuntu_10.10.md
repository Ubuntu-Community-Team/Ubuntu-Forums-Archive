---
title: "win7 vnc no longer connects to ubuntu 10.10"
date: 2011-03-08
forum: Server Platforms
---

### Post by Foeburner on 2011-03-08
All of a sudden, I could not connect to my ubuntu 10.10 server from Windows 7 using vnc this morning. 

When I open vnc on windows 7 and hit connect, it goes away like its going to connect but never pops up the screen. If I try to connect to my other ubuntu server, it connects quick and I'm able to navigate in it. 

I tried reinstalling vnc on ubuntu with no luck.

---

### Post by arrrghhh on 2011-03-08
You're using VNC on ubuntu server?

server comes without a GUI... so I don't see why you would want to use VNC on a server.

Can you still ssh to the box?  Have you made sure the service is running on the server?  No firewall or other network changes?

---

### Post by Foeburner on 2011-03-08
I have the gui installed to help my remote buddies navigate. I'll be shipping them this server and they're complete noobs when it comes to linux. 

Yes I can SSH and i dont see the service running. I'm not sure what cmd to use to restart it either. I googled this and keep getting results for xtightvnc, uvnc, grdc, vino, vinagre... and none say which is the default one.

---

### Post by arrrghhh on 2011-03-09
> **Foeburner said:**
> I have the gui installed to help my remote buddies navigate. I'll be shipping them this server and they're complete noobs when it comes to linux. 

Yes I can SSH and i dont see the service running. I'm not sure what cmd to use to restart it either. I googled this and keep getting results for xtightvnc, uvnc, grdc, vino, vinagre... and none say which is the default one.

Probably best to just install the -desktop version if they're newbies to Linux and they don't want to learn CLI.

But, what version of vnc did you install?  Most common for servers I would think is x11vnc, but there are others...

---

### Post by Foeburner on 2011-03-09
I didn't physically installed vnc, I just went to system > preference > remote desktop. 

My buddies will have to learn CLI soon because they're a tech help desk for Polycom and will be using this for many projects. For now, I'll ease them into linux with a gui.

---

### Post by Foeburner on 2011-03-10
Since this thread was forgotten about, I just wiped my box and reinstalled ubuntu again. 

Sorry for those that are having this issue. I couldnt find a fix for it either.

---

