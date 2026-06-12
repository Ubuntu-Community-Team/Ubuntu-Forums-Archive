---
title: "OpenVPN bridging setup help"
date: 2011-01-17
forum: Server Platforms
---

### Post by rogtek on 2011-01-17
Hello everyone.
 
For some time now I am trying to setup an OpenVPN server in bridged mode (Ubuntu 10.04 Lts). The goal is for the clients to be able to reach all the servers behind Openvpn server's lan. I have followed the official OpenVPN guide for Ubuntu 10.04.
 
My network setup is:
Private lan: 10.90.90.0-255 255.255.255.0
Gateway: 10.90.90.1
Openvpn server ip: 10.90.90.8
Gateway public ip: 79.xxxxxxxxx
I have forward port 1195 to the Vpn server through my gateway firewall.
Besides that no other firewall is running.
 
I can connect and ping the server both from windows and ubuntu clients. The difference is that from windows I can reach the private lan but not from ubuntu clients.
 
Any suggestions please?

---

