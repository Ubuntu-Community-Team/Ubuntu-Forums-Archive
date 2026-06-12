---
title: "SSH not routing through openvpn"
date: 2013-01-08
forum: Server Platforms
---

### Post by sandyd on 2013-01-08
For some reason, when I am logged into a OpenVPN server through networkmanager, the ssh client (ssh) does not access the ssh server using the VPN.

Instead, it somehow slips by, and just uses the normal internet to connect to the server, which is impossible as I have a ip address whitelist for ssh.

route:
```
0.0.0.0         172.17.0.5      0.0.0.0         UG    0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
172.17.0.1      172.17.0.5      255.255.255.255 UGH   0      0        0 tun0
172.17.0.5      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
198.23.165.156  192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
```

My router uses 192.168.1.0/ 255.255.255.0

---

### Post by hawkmage on 2013-01-08
WHat is the IP adress of the SSH Server?  

If routes have the same metric the order of precedence is more specific to least.   If it is in the 192.168.1.0/24 or 192.168.122.0/24 network then there are routes for those that are more specific than the default route to the tunnel.

---

### Post by sandyd on 2013-01-08
nvm *cough*
Just realized that SSH and OpenVPN were on the same IP address :O

Changing the OpenVPN address caused success

---

