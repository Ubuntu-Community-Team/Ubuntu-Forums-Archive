---
title: "Ubuntu Server + ubuntu-desktop + VNC help"
date: 2010-03-18
forum: Server Platforms
---

### Post by cutegelo on 2010-03-18
Hi,

I've been browsing the forums for so long until I gave up searching so, I registered and decided to ask.

I have a server collocated in Dallas with Ubuntu 9.10 Server installed. I managed to install gnome using sudo **apt-get install ubuntu-desktop** command. Then here's my problem. How can I view the gnome? I tried VNC, x11vnc, freeNX, X and other lots of stuff. I found a lot of guides and most of them are outdated.

I would be wonderful if someone can advice me on what to do.

thanks in advance ;)

---

### Post by Jeff Anthony on 2010-03-19
You may need to open port 5900 on the server's firewall or set up a reverse vnc server on the client connection.

---

### Post by cutegelo on 2010-03-19
i know it's not the port because i tried to disable the whole firewall just to figure things out..

---

### Post by HermanAB on 2010-03-19
You are very fortunate that VNC is blocked by your hosting service.  It is the easiest way to get your server hacked.  So whatever you do, don't use VNC.  If you have a VNC server running already, kill the damned thing.

Install ssh-server (it is very likely already installed).

Use the SSH client to connect like this:
$ ssh -X -C -c blowfish user@server "gedit /etc/fstab"

or like this:
$ ssh -X -C -c blowfish user@server gnome-panel
and go click happy.

---

### Post by cutegelo on 2010-03-19
ok, everything is working now but not with vnc. I'm using freeNX now:popcorn:

---

