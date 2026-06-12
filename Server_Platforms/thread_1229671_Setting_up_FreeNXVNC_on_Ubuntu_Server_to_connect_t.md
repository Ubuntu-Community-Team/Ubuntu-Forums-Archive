---
title: "Setting up FreeNX/VNC on Ubuntu Server to connect to Windows machines on the LAN"
date: 2009-08-02
forum: Server Platforms
---

### Post by nerr on 2009-08-02
I'm going to be leaving for college in the fall, but since I'm also the full-time sysadmin for our home network, there will inevitably be times when I'm away and something goes terribly wrong, and I'll be the only one capable of fixing it.  I'd like to install a server of some kind on Ubuntu that I'm able to create an SSH tunnel to, and then navigate to the Windows machines on the LAN to control them remotely and be able to fix any problems that arise.

I have zero experience configuring any sort of system like this, but if possible, I'd just like my setup to work like the following:

1) SSH from laptop to home server
2) Navigate from home server to client Windows machines on LAN
3) Remote control client machines 1 - 5 at will.

It'd be nice if I could access these as easily as VNC "displays", e.g. mydomain.com:0-4 or whatever those numbers would end up being.

Advice is appreciated!  I'd prefer not to have to set up a VNC server on every machine, and then deal with the port forwarding mess.

---

### Post by bmathis on 2009-08-02
The way I do it for my moms house is this: I have a headless ubuntu desktop setting in the closet with ssh port forwarded to it. I then use X forwarding with ssh to either run Remoted Desktop Viewer, if you have VNC setup on the windows machines, or Terminal Server Client to use the built-in RDP server on xp pro machines. From there, you can jump on any of the machines on the remote network at will and fix what ever problem they have. All this without having to forward ports to each computer and you're using a secure connection with SSH.

---

### Post by HermanAB on 2009-08-02
I cannot recommend VNC.  It is slow, insecure and seems to be the main reason systems get hacked.  Windows XP comes with Remote Desktop Protocol (RDP) - MS bought RDP from Citrix.  It is secure and it works very well. 

RDP by default runs on port 3389/TCP (you can change it in the Registry).  You can connect to RDP from Linux using rdesktop.

---

