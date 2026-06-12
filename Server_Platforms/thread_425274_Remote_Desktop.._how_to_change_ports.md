---
title: "Remote Desktop.. how to change ports?"
date: 2007-04-27
forum: Server Platforms
---

### Post by baconstrip on 2007-04-27
Hello all.. I have a few questions about Remote Desktoping.    I have my unbuntu box set up at home to accept remote desktop connections.  It works great on both my other ubuntu box AND my Windows box (using tightVNC) over the network.

Now I want to connect over the internet.   I'm pretty sure the default port is 5900, but I want to change that.  Anyone know what I have to edit to do this?

Second question is this.. a bit of a networking newb question.  When I do get a proper port set up for remote desktop, and the port properly forwarded... how do I type in the address to connect?   My <external IP>:<port> ?

555.555.555.555:2222  ? 

Thanks in advance,
Bacon

---

### Post by elst on 2007-04-28
1) There are a few ways to set remote desktop access, so you probably need to give a few more details about your configuration.

2) If you create an SSH tunnel between your local system and another, you specify  the local port that you assigned in order to go through the tunnel.

---

### Post by baconstrip on 2007-04-29
1) Well I'm currently using the remote desktop options in 7.04 that are just in the system menu.  Unfortunately these options are very limited.  The port it utilizes by default is port 5900.   Would I need to set up another program to utilize a different port or can I just change the port via a text configuration file?

2) I will be looking into utilizing SSH tunneling for added security.. but for now I will just be connecting via the remote desktop options and a VNCViewer.

Port 5900 works just fine, but I have multiple machines on my network that I would like to connect to and only one can utilize the port at a time :)

---

### Post by elst on 2007-05-01
System > Preferences > Remote Desktop?

That option is really for temporarily sharing your current desktop session with someone else for tech support, collaboration etc., although it doesn't make that clear.

Your best option for desktop access from over the Internet is probably NX, or X forwarding with SSH. VNC doesn't encrypt, so isn't suitable for remote access over the Internet unless you use SSH or a VPN with it.

---

