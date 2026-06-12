---
title: "KVM installed with Ubuntu 9.04 server GUI?"
date: 2009-09-03
forum: Server Platforms
---

### Post by crate on 2009-09-03
Good Day to all Ubuntu Circle,

First of all HI! to everyone, and glad to be here.

I am abit new to Ubuntu, especially Ubuntu server.
I won't go into a life story here, but I am cheap, very cheap
with pc resources, I knose what youse guys were thinking.
lol

So here's the thing I recently installed Jaunty (normal installation), with the Virtualization option.  So KVM is installed, then I began following the numerous guides there but realized how am I going to bring up my Windows VMs if server has no GUI

So my question is do I sudo apt-get install gnome-desktop which I read as one way to get the GUI or ...?
Hoping you guys can fill the dots there.

And before I get flamed and someone says install Ubuntu Desktop if I want a GUI please remember the fifth line.

Thanks alot guys.

---

### Post by juancarlospaco on 2009-09-05
1-Install openssh-server on the server
2-Install Convirt on ubuntu desktop *(use the lastest version avaliable from the website)*
3-Manage your headless server from the desktop with Convirt GUI

---

