---
title: "Help with Ubuntu Server 17.10 OpenVPN service"
date: 2017-10-25
forum: Server Platforms
---

### Post by daenir on 2017-10-25
I've been trying to be able to have remote access to my server with the help of OpenVPN.
I followed this guide (yes I know it's for 16.04 but I could not find anything else):
[https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-16-04)

But it didn't work. Is there any specific guide from where I could learn it for my version of Ubuntu Server?

---

### Post by daenir on 2017-10-27
Bump

---

### Post by slickymaster on 2017-10-27
Thread moved to **Server Platforms** for a better fit

---

### Post by Tadaen_Sylvermane on 2017-10-27
I don't have experience with 17.10. The only advice I can give you however is that it is far from ideal to use the latest release on a server that you expect 99% uptime from. Always stick with the LTS. That way it is stable, reliable, and you can find the info needed to configure it fairly easy.

---

### Post by SeijiSensei on 2017-10-27
The simplest method is to set up a point-to-point static tunnel as described here:  [http://openvpn.net/static.html](http://openvpn.net/static.html)

Make the publicly-visible machine the server, and connect to it by including the "remote" directive in the client's OpenVPN configuration.

---

