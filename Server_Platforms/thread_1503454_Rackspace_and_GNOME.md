---
title: "Rackspace and GNOME"
date: 2010-06-06
forum: Server Platforms
---

### Post by Norami on 2010-06-06
Does anyone know of any good articles for setting up VNC on a rackspace Ubuntu cloud server? I've got ubuntu-desktop installed, and installed tightvncserver. I still can't connect through VNC viewer, though. Any help would be appreciated.

---

### Post by mbn18 on 2010-10-11
> **Norami said:**
> Does anyone know of any good articles for setting up VNC on a rackspace Ubuntu cloud server? I've got ubuntu-desktop installed, and installed tightvncserver. I still can't connect through VNC viewer, though. Any help would be appreciated.

First install X / Gnome / KDE on the server with vnc support

On the server side:
```
vncserver :20 -depth 8 -geometry 800x600 -name WHATEVER
```

on the client side:
```
ssh -x -L 5920:localhost:5920 user_name@SERVER_HOST
```

In a new local shell, run:
```
vncviewer localhost:5920
```

---

### Post by HermanAB on 2010-10-11
Howdy,

VNC is mostly a Windows thing and is not a good idea on Linux.  Unless maybe if you are setting up a honeypot and want it to get hacked.  

You should rather learn how to use SSH properly, since it can do most everything VNC does and much more. Ferinstance:
$ ssh -X -C -c blowfish user@server gnome-panel

That works from Windoze with Cygwin as well.

---

