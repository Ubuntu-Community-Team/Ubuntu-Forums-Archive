---
title: "Openvpn and custom server"
date: 2012-06-26
forum: Server Platforms
---

### Post by thomasw81 on 2012-06-26
Hello,

I need some advice on my server running precise 12.04. Currently I have the following setup:

eth0: connected to internet
wlan1: setup with hostapd, creating a wireless access point
tun0: openvpn

So basically when wifi clients connect and enter the appropriate wpa passphrase internet access is granted. internet traffic is forwarded to eth0 using iptables masquerading. 

I installed and configured openvpn and produced certificates for the clients. Connecting from remote or lan works fine, I can access the local network via the VPN.
    
My question is: how can I bridge tun0 to wlan1to make it possible for clients to connect and have internet access through the vpn?

edit: sorry! I posted too soon. I forgot to push dns server. everything working fine now.

As allways, a short break fixed my issue ;-P

---

