---
title: "Best way to view KVM virtual machine remotely using windows/mac ?"
date: 2009-11-23
forum: Server Platforms
---

### Post by photoman355 on 2009-11-23
Hi 

I'm trying to find out the best way to allow windows/mac to connect to a virtual machine hosted on my ubuntu server.  

I can connect to the VM remotely over SSH using an Ubuntu Client and Virt-viewer however the computers I need to connect to the VM are windows and mac systems.  

What's the best way to do this?

I'm guessing that i'd need to install SSH based software on the pc/mac, are there any good tutorials you can point me to?

---

### Post by photoman355 on 2009-11-24
Bump

---

### Post by photoman355 on 2009-11-24
For those who are interested I've found a solution.

I'm using a VNC server on the virtual machine which runs on startup and connecting to it with a VNC viewer on the PC/Macs.  Very simple to implement.  

For PC 

[http://www.tightvnc.com/](http://www.tightvnc.com/)  
[http://www.uvnc.com](http://www.uvnc.com)
[http://www.realvnc.com](http://www.realvnc.com)

For Mac

[http://sourceforge.net/projects/cotvnc/](http://sourceforge.net/projects/cotvnc/)

---

