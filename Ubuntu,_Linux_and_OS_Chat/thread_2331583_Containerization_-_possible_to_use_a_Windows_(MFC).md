---
title: "Containerization - possible to use a Windows (MFC) app within Linux?"
date: 2016-07-23
forum: Ubuntu, Linux and OS Chat
---

### Post by chad_b2 on 2016-07-23
My apology in advance for some ignorant questioning...

Instead of using WINE or Virtualbox, is it possible to use a relatively-simple Windows XP/Vista app by containerizing it within a Linux install? If so, or a MicroXP VM sans-VMWare/Virtualbox could be linked to a Linux program by terminal ops, what program(s) would you recommend aside from Docker?

The MFC app is just a simple GUI built in MS C++ Visual Studio, that receives data through a C++ API installed locally. The GUI has dropdown menus, input field strings & the like for creating conditional statements based off of that incoming data and then sets wait/execute instructions that are pushed back through the C++ API and to the remote server the API connects to.

I've briefed through an article each for Rancher and Ubuntu LXD, but seems those are supplemental to what Docker is built off of.

---

### Post by Jeffrey_Sloan on 2016-07-23
The only OS that can run in a Linux container (whether openvz, lxc/lxd or docker) is Linux. For windows, you'd have to run a full VM. If you could run the app itself under wine/crossover in Linux, it might be possible to run the app under wine/crossover in a Linux container. I think that would definitely be a first if you succeeded there.

---

### Post by chad_b2 on 2016-07-25
Hello Jeff, thank you for explaining that clearly!

---

