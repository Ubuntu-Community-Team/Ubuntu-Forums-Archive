---
title: "VPN &amp; Mail Server"
date: 2006-06-23
forum: Server Platforms
---

### Post by simplesimon on 2006-06-23
I run a small company out of two home offices. I would like to be able to link both sites to a ubuntu server at one site which has our working files on it and also to be used as an email server.  The computers that will connect to it will be running XP.  Can this be achieved using VPN through the ADSL router at one site?  If the server is connected to the router can I connect through a windows network and one site and though VPn from the other site?  I don't know if this is clear but I am new to this and want some advice, firstly can it be done, and secondly help on setting up the ubuntu server, samba, postfix etc.

---

### Post by lamego on 2006-06-23
VPNs do required some expertise to setup and are usually required when you need to share more network resources or a full network.
If you only need a file server it is ok to just have a plain network connection as long you use an encrypted protocol for the file serving service.
You could install openssh on the ubuntu server and the windows computers would be able to access the files using an  secure ftp client like FileZilla or WinSCP.

---

