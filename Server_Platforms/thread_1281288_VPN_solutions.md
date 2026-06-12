---
title: "VPN solutions"
date: 2009-10-03
forum: Server Platforms
---

### Post by sunstriker on 2009-10-03
Hi!

i would like to get access to my office from home, preferable with a Windows / Mac OSX built-in VPN (like L2TP). I need access to the whole LAN, not only the VPN Server.
What are my options if I want to stick with open source?

---

### Post by DC^ on 2009-10-03
With Ubuntu you can make an VPN.

Take an look at Ubuntu Server with OpenVPN.
Guide's and How to's you can find here [https://help.ubuntu.com/](https://help.ubuntu.com/).

When you have questions about VPN you can ask it here on the forum.

Succes!

---

### Post by Lars Noodén on 2009-10-03
If you're looking for VPN software, you can make ad-hoc VPNs with SSH.  If you want a more permanent VPN then OpenVPN, as DC^ wrote above, is probably your best option.

[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
[http://openvpn.net/index.php/open-source.html](http://openvpn.net/index.php/open-source.html)
[http://manpages.ubuntu.com/manpages/hardy/man8/openvpn.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/openvpn.8.html)

If security is a goal, then IPSec or SSL are your two options.  If insecurity is the goal then go with PPTP, L2TP or one of the other protocols.  

What problem are you trying to apply a VPN 'solution' to?

---

### Post by sunstriker on 2009-10-05
I'm running a lot of virtual servers at the office. when i'm at home (I work a lot from home) I connect via SSH to one linux server and ssh into other servers from there. I use a Win 2003 server to get a remote desktop connection. 
So I would like to access my whole network using a VPN from my home pc.

---

### Post by openfly on 2009-10-05
You should be able to setup an ssh tunnel set for accessing something vmware infrastructure client... if it's a vi3/4 installation you are virtualizing off of.  Otherwise openvpn is probably the way to go.

---

