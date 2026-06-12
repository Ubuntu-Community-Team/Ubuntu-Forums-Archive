---
title: "ubuntu on web browser"
date: 2007-11-09
forum: Server Platforms
---

### Post by aznboy on 2007-11-09
Hi, is there a way to connect to my home ubuntu desktop using a web browser since I can't install anything on my office desktop.  The only I can do is use a web broswer, email, and office apps at work so I can't use vnc there and all plugs are disable by admin so no usb boot.

I think I read about somehow you can do that with linux but not sure.

---

### Post by charmcity on 2007-11-09
Sure,

You can use VNC -- true that when you log in to ports 5900-5910 you need to use for example RealVNC application 

but if you have your VNC server running on your linux box you should be able to reach it via the web by going to ports 5800+  VNC comes with a built in Java Based web server.  Key is to go to 5800/1 rather than 5900/1 -- Should work.

Good Luck!!
Tom

---

