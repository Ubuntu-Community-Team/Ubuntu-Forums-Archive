---
title: "Making Dev Server Available Outside of LAN"
date: 2009-09-02
forum: Server Platforms
---

### Post by theGlitch on 2009-09-02
So I've recently built a server out of an old PC that I'd like to use a dev server. I set it up with Ubuntu Server 8.10 with LAMP and openSSH. It's connected to my LAN and I am able to access it fine within the LAN. It's currently connected to a Netgear MR814 through a cat5 that leads to a switch that splits the connection between 2 boxes (dev server and a gaming PC).

However my neighbor will be working on some of my projects, so I'd like to have the server available to him. I've searched through the forum and have found no direct steps to opening up the dev server without completely dropping my router's firewall.

Any help would be greatly appreciated

---

### Post by cdenley on 2009-09-02
[http://portforward.com/english/routers/port_forwarding/Netgear/MR814/Apache.htm](http://portforward.com/english/routers/port_forwarding/Netgear/MR814/Apache.htm)
[http://portforward.com/english/routers/port_forwarding/Netgear/MR814/SSH.htm](http://portforward.com/english/routers/port_forwarding/Netgear/MR814/SSH.htm)

---

### Post by hessiess on 2009-09-02
If you are going to have multiple users using the machene, you need to set it up as a sccure shaired hoasting server. i.e. each user should be completly independent of all outher users, and have no way of editing each outhers files. This can be acheved using a sftp user per web root, and chmodding all the files in that root to 760. You will also need to run PHP as suexec+CGI/Fast_CGI and NOT mod_PHP as it always runs as the apache user, breaking your inter-user sccurity.

---

### Post by theGlitch on 2009-09-03
Thank you both!

---

