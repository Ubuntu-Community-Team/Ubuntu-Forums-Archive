---
title: "How to set VNC Password?"
date: 2009-02-20
forum: Server Platforms
---

### Post by jw6597 on 2009-02-20
I have installed vnc4server and opened up ports 5500, 5800, 5900. I am able to connect within the LAN using Vinagre and outside the LAN from a MAC using Chicken of VNC. However, I am not being prompted to enter a password. I had run:

sudo vncpasswd /root/.vncpasswd  

and created the password. Any ideas?

Thanks,
jw

---

### Post by Thirtysixway on 2009-02-21
This isn't a solution to your problem, but why did you install vnc server?  Are you using desktop or server version?

Desktop version comes witha remote desktop application.  System > Preferences > Remote Desktop

---

### Post by jw6597 on 2009-02-23
What you are pointing out:

System > Preferences > Remote Desktop

Looks like the configuration options for allowing a remote connection for that specific desktop. I am using Vinagre (VNC) on my laptop to remote into the Ubuntu Server Edition (VNC server).

---

