---
title: "x11vnc working on ubuntu desktops but not ubuntu server"
date: 2011-08-25
forum: Server Platforms
---

### Post by grand_tale on 2011-08-25
Hey guys,

I've been using openssh and x11vnc inside my home to connect between my ubuntu systems, but this week I built a server with Ubuntu Server 11.04 64bit on it with ubuntu-desktop installed. I followed the same procedure as for the other ubuntu machines with setting up x11vnc and openssh and they work fine, but the same procedure doesn't work for server. 

I can access my ubuntu desktops from the server but not the other way around, desktop to server. i even tried to choose no ssl/ssh encryption, just "none". but that doesn't even work. some window pops up and it looks like its trying to connect but then the last entry is something about "sleep 5". Upper in the output it says ""**Pseudo-terminal will not be allocated because stdin is not a terminal.**"

I'm not very good at coding and (hence the reason for the gui) so please try to make it simple if possible. I only use the server for gns3 and virtual routers that's all. 

Thanks guys

Edit. Oh and I did the settings in Remote Desktop to be able to  access/control it and put in the password. Remote Desktop is set up the same on the other ubuntu machines too.

---

### Post by Bachstelze on 2011-08-25
IIRC, x11vnc requires you to have an X server running, and lets you connect to it. If you want to VNC to a server that does not have an X server running, I recommend using TightVNC Server instead, which will create the X display for you when you start it.

---

