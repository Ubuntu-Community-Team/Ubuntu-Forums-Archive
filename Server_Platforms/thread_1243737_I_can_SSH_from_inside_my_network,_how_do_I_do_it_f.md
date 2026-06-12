---
title: "I can SSH from inside my network, how do I do it from outside?"
date: 2009-08-18
forum: Server Platforms
---

### Post by Maheriano on 2009-08-18
I SSH into my box using the local IP which is something like 10.0.0.3 and it works fine. But I'm wondering how I can SSH into it from outside my network using my external IP. I know I need to forward that IP on my router to the internal IP of the computer I want to use but is that it?

Is there a document I can read about securing this then?

---

### Post by jfmanamtr on 2009-08-18
You would need to forward the port you use for the SSH (by default 22) through your router. And how you do that would depend on what router you have. After that you would just need an SSH client for the connection (putty is a good bet if the PC that you will connect from is a Windows PC). If you need any help you can post here & I will try to help you out. As far as securing the SSH, I used [this]("https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html"). It is the guide for Ubuntu Server, but it should work even on the Desktop Version

~John

---

### Post by Maheriano on 2009-08-18
Sweet, thanks. Port forwarding is all I had to do. Now to secure it.

---

