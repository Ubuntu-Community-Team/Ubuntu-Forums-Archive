---
title: "VPN and Remote Network Drive"
date: 2010-05-28
forum: Server Platforms
---

### Post by signature16 on 2010-05-28
I am wondering how to setup a remote disk on my server so that I can remotely access files on my Windows laptop through the "Map Network Drive" feature.  

How do I go about doing something like this?

---

### Post by dipeshmehta on 2010-05-28
You may configure VPN, check OpenVPN ([www.openvpn.net](www.openvpn.net)), its pretty good, easy to setup and stable & secure.

You may also check: [http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-9.10](http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-9.10)

Dipesh

---

### Post by spynappels on 2010-05-29
Do you want to access a folder on the server, or on another computer on the same LAN as the server? 

If on the server itself, you only need to set up your VPN tunnel (I would suggest using OpenVPN in routed mode for this) and then map the (Samba) share using the VPN interface IP Address on the server and the server share name (\\10.8.0.1\Share).

If you want to access a Samba share on another computer on the same LAN subnet as the server, that same setup will work but you need to push a route to the VPN Client and use the LAN IP of the machine the share is on.

---

