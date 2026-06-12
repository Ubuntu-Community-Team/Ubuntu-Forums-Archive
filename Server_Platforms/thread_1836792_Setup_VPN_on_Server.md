---
title: "Setup VPN on Server"
date: 2011-08-31
forum: Server Platforms
---

### Post by GuitarRocker2562 on 2011-08-31
Hey everybody,

I just started college and I really hate being on the institutions Internet. Also I was pretty much the admin guy at home. Back at home I am running a nice web server / backup server for the house. I want to setup VPN on this server so that I can connect my laptop (at college) to my LAN at home to bypass the college Internet and to be able to securely access my samba share at home. Can somebody point me to some articles on how to setup a VPN (from scratch)? It would be greatly appreciated. 

P.S. Using Ubuntu 11.04.

---

### Post by kgatan on 2011-08-31
I havnt tried so many diffrent kinds of VPN software but i installed Open VPN AS yesterday and it works great so far.
Setup is straight forward and configuration is done through web gui.
 
You can download the deb package from openvpn.net.
 
Only problem with the AS version as far as i know is that you can only have 2 concurrent connections. If you need more connections you need to buy licenses or use the open version which i hear is complicated to setup.
 
PPTP is also a VPN software which is supposed to be quite easy to setup. Search google for PPTPD guides. Package is avalible from the rep.

---

### Post by Lars Noodén on 2011-09-01
Search for material on [OpenVPN](https://help.ubuntu.com/community/OpenVPN).

---

