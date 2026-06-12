---
title: "How to ssh into a VPS then connect to a VPN on the VPS and stay connected?"
date: 2017-03-01
forum: Server Platforms
---

### Post by sirsyorrz on 2017-03-01
I would like to have my VPS from digitalocean be connected to a VPN, the problem is once i start the VPN i lose connection as the VPS's IP changes.

I'm using OpenVPN and using one of the free VPNs I am also using putty to connect from my windows laptop.

---

### Post by volkswagner on 2017-03-02
Please post your server and client configs.

I'm not sure what "and using one of the free VPNs" means.

You may need to add a static route if you are using "route all traffic through tun" on the
VPN config.

Why do you want to route ALL traffic through VPN on your VPS?

---

### Post by sirsyorrz on 2017-03-02
I figured it out, I just have to route add -host my.ip gw vps.original.ip

---

