---
title: "Installing LXDE or XFCE on Ubuntu VPS and access via VNC"
date: 2013-12-17
forum: Server Platforms
---

### Post by uzumakifahim on 2013-12-17
Hi experts,

I've a ubuntu 12.04 VPS. Now I want to install LXDE or XFCE (anyone between these two) on that VPS and use the DE from my Ubuntu PC via VNC. I'm not getting any step by step procedure which is working for me. Please help me to do this.

Thanks in advance.

---

### Post by uzumakifahim on 2013-12-17
I've completed every steps on this link successfully, but finally it's not connecting using Remmina.

[https://panel.cinfu.com/knowledgebase/6/GUI-Desktop-XWindows-Gnome-installation-on-Linux-VPS-Server-with-Ubuntu-OS.html](https://panel.cinfu.com/knowledgebase/6/GUI-Desktop-XWindows-Gnome-installation-on-Linux-VPS-Server-with-Ubuntu-OS.html)

---

### Post by steeldriver on 2013-12-17
What actual error / behavior are you getting? If you are trying to connect to a VPS from behind a router you will need to either tunnel the VNC connection over SSH (recommended) or forward the chosen VNC port across your router (not recommended - in fact I'd highly recommend NOT running an open, publicly facing VNC server on your VPS). I don't see any mention of that in the link you posted.

---

### Post by uzumakifahim on 2013-12-17
Actually, I can't connect to VPS using VNC. 

I've entered IP of my VPS with username : root and password for my tightvnc server on my VPS. Then I enabled SSH tunnel and keep the username : root for SSH authentication.

After that when I press connect button, it asks my SSH root password. After entering the password I press Ok.

After a long time, it shows connection failed.

Please check the attached screenshot.

---

### Post by steeldriver on 2013-12-17
try checking the 'tunnel via loopback address' box - if that doesn't work, post back and we can try setting up the tunnel manually via command line (every VNC client presents things differently so it's confusing)

btw it's really not a good idea to enable root ssh - even worse to run an xsession as root

---

### Post by postcd on 2013-12-18
I used this manual: [http://internetlifeforum.com/linux-forums/191-how-install-free-ubuntu-lxde-desktop-vps/](http://internetlifeforum.com/linux-forums/191-how-install-free-ubuntu-lxde-desktop-vps/)
In your case you should make sure vncserver is running / start it.
And also dont forget to add :1 (port) after IP address into vnc client. that are my advices.

---

