---
title: "Need help setting up a bridge for OpenVPN"
date: 2011-02-03
forum: Server Platforms
---

### Post by cremnob on 2011-02-03
I have an Ubuntu VPS running 10.10 x86_64

This is what is in my /etc/network/interfaces right now.
```
auto eth0
iface eth0 inet static
    address 67.202.x.x
    gateway 67.202.x.1
    netmask 255.255.255.0
auto lo
iface lo inet loopback
```

My server.conf
```

port 1194
proto udp
dev tap0
ca ca.crt
cert server.crt
key server.key
dh dh1024.pem
ifconfig-pool-persist ipp.txt
server-bridge 10.8.0.4 255.255.255.0 10.8.0.50 10.8.0.100
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 208.67.222.222"
push "dhcp-option DNS 208.67.220.220"
keepalive 10 120
tls-auth ta.key 0 # This file is secret
cipher BF-CBC        # Blowfish (default)
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3

```

I can get the VPN server running and everything connects fine from the client. I just don't know how to tunnel all the traffic through the VPS because it involves making the bridge which I'm having trouble with. What exactly am I supposed to put in /etc/network/interfaces?

---

### Post by salvo84 on 2011-06-04
this should help. scroll down to the bottom where it talks about bridging.
[https://help.ubuntu.com/10.10/serverguide/C/network-configuration.html]("https://help.ubuntu.com/10.10/serverguide/C/network-configuration.html")

although in 10.10 I have been having issues getting it to bridge properly when I have two nics bonded together. since you just have one nic the above should get you in the right direction. try googling "ubuntu openvpn bridge". I've found alot of different guides and setups to help me out :)

edit: found this link that should be helpful: [http://www.serverubuntu.it/openvpn-bridge-configuration]("http://www.serverubuntu.it/openvpn-bridge-configuration")

---

