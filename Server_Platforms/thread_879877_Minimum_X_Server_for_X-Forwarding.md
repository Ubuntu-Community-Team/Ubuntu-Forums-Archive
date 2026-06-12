---
title: "Minimum X Server for X-Forwarding"
date: 2008-08-04
forum: Server Platforms
---

### Post by steve_c on 2008-08-04
I have an Ubuntu 8.04 Server install.

My clients need occasional access to graphical applications that require the resources of our servers. They do not, however, have physical access to the servers so a full blown desktop is overkill.

I would like to know what are the minimum packages I would be required to install on the server so that their clients (Ubuntu Desktop workstations) can run an application via X-Forwarding on the server.

They will need 3D hardware rendering so I've installed an ATI video card, and I'm already aware I'll need the restricted-drivers-manager-server and the proprietary fglrx package.

Do I just need xserver-xorg-core, or do I install the whole xserver-xorg? It's not the worst thing ever if I install too much, but I'm aiming to write down best practices for installing new servers for future people in my position and would ideally like to keep it as stripped down as possible.

Thank you for your help.

---

### Post by croto on 2008-08-04
As far as I understood, your clients want to run programs on the server and use their desktop display and keyboard, right? 

I assume they would ssh into the server to be able to run programs there. If that's the case, the graphical applications running on the server will connect to the X11 server *running on the clients*. That is, the server doesn't need to have the X11 server, just the applications your client will need. The X11 server should be installed on the clients.

---

### Post by StickyStyle on 2008-08-04
I have found that the xbase-clients package on the server grabs the necessary libraries to run a forwarded session.  It also drops on things like xterm (which obviously depends on the necessary libraries) which is useful anyways.  Its a pretty small package also.

---

### Post by comeleon99 on 2008-08-05
The minimum required to get x forwarding working on ubuntu server is 

```
sudo apt-get install xauth
```

---

