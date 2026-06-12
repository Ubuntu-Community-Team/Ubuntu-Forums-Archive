---
title: "VNC Client disconnect everytime a new window is being spawed."
date: 2010-06-29
forum: Server Platforms
---

### Post by vsharma on 2010-06-29
Hello,
 
I have installed Ubuntu 10.04 server edition on a HP DL380 Proliant G5 server. After the installation, I installed ubuntu-desktop and gdm packages as I wanted a graphical user interface to run a few development tools. I also installed tightvncserver package so that the server could be accessed remotely from another computer. 
 
Everything seems to have installed without any issues. 
 
I configured the tightvncserver started the vncserver by issuing the following command: 
vncserver :1 -geometry 1024x786 -depth 16 -pixelformat rgb565
 
The server started without any issues. The problem that I am having is that when I connect from a remote computer via tightvncclient I am being disconnected everytime I run synaptic package manager to install any new packages or sometimes when I am trying to spaw a new terminal window. 
 
I looked at the log from /var/log/messages. I see that there is a segfault being reported by xtightvnc. 
 
kernel: [340025.759605] Xtightvnc[9714]: segfault at 7fff8f4df000 ip 000000000044e4f1 sp 00007fff8f4dd480 error 6 in Xtightvnc[400000+17e000]
 
Does anyone else have this problem? Please help if you know what the issue could be and how to resolve it. Any help is greatly appreciated.
 
Thank you.

---

