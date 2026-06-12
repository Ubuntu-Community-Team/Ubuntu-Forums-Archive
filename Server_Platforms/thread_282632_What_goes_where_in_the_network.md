---
title: "What goes where in the network?"
date: 2006-10-23
forum: Server Platforms
---

### Post by lPrentice on 2006-10-23
Hello,

This may be a stupid question but, forgive me, I'm new to network administration.

I have a mixed Windows/Linux network. Currently a Windows box is handling DHCP and DNS; a Linux box is handling SAMBA, CUPS, NTS, SSH, and a local development web server. In the near future I'd like to add externally accessable production services, including web, mail, forums, etc. 

I'd like to reconfigure my network so that I have one or more Ubuntu Server-based boxes running the servers that need to be exposed to the Internet (the network edge box(s); and second Ubuntu Server-based box running servers that support my local LAN (the network support box).

As I map out the various servers that I'd like to support in my network now and in the future, what criteria should I use to decide whether the server should be in the nework edge box or the network support box?

Many thanks,

LRP

---

### Post by Soarer on 2006-10-23
It's not a stupid question. :)
THe basic idea is to put all externally accessible stuff on a server in a DMZ. So, from the outside (Internet) to the inside (LAN) you would have:

Internet > Firewall1 > DMZ Server > Firewall2 > Lan Server > Lan PCs.

For Firewall1 you could use the one built into your router, allowing in the ports you need (25 for mail, 21 IIRC for FTP, 80 and maybe 443 for www). You run these services on the DMZ server.

Firewall2 could be run on the external facing ethernet connection of the LAN server. All incoming ports would be blocked, but allow necessary outgoing. Pass through web traffic from LAN to Internet on the DMZ server (or better run a Web Proxy like Squid on it).

Either way you will need at least 2 ethernet cards in both the DMZ server and the LAN server. Run DHCP, SAMBA, CUPS and anything which doesn't need incoming external access etc. on the LAN server.

---

### Post by lPrentice on 2006-10-23
Many thanks, Soarer!

LRP

---

