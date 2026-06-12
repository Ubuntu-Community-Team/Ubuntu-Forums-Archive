---
title: "Setting up a VPN"
date: 2008-09-23
forum: Server Platforms
---

### Post by andrewortman on 2008-09-23
Hi,

I'm running ubuntu on my personal server that is connected to a 100mbit dedicated line. I live in the dorms now and they seemed to block off most of my internet capabilities such as streaming video and music. In order to "secure" my network, and network with my computers at home I want to set up a vpn on this server.

UDP is low on the QA on the routers in my dormitory, so a TCP  connection would be a preferred choice. I want to be able to set my mac up to connect to the VPN easily (with the built in VPN settings on leopard).

I have tried SSH tunneling, and that is currently what I am using to even browse youtube.. But I want a solution that not only connects me up to my computers at home, but also traps all internet connections from my mac and tunnels them through my server.

I am fairly experienced with linux and ubuntu, but getting a hang of VPNs is taking me a while. Are there any VPN solutions for ubuntu out there that is fairly easy to set up? Are there any guides online that some of you found helpful?

Thank you,
Andrew

---

### Post by pdwerryhouse on 2008-09-23
OpenVPN is your best bet. By default, it uses udp, but can be easily configured to use tcp instead.

---

### Post by jamesrfla on 2008-09-23
To get openvpn do ```
sudo apt-get install openvpn
```

---

