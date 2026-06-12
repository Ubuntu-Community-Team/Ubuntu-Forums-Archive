---
title: "OpenVPN server issue"
date: 2012-01-09
forum: Server Platforms
---

### Post by fhmayn on 2012-01-09
Hello,

Since December, i'm trying to configure an openVPN Server on my VPS (XenEurope, offer 512RAM, on Ubuntu.

But the problem is every time i set my server up, i can create some user, run these users, etc... but a few days latter, i can connect to my server but there is no internet connexion. At this point, i can't create new users, i have to uninstall/install openvpn and do all the process....
Do you have an idea to solve that issue? 
I use "easy-rsa" for openVPN.

My server.conf

> # Serveur TCP/443
mode server
proto tcp
port 443
dev tun
# Cles et certificats
ca ca.crt
cert server.crt
key server.key
dh dh1024.pem
tls-auth ta.key 0
cipher AES-256-CBC
# Reseau
server 10.8.0.0 255.255.255.0
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 4.4.4.4"
push "dhcp-option DNS 8.8.8.8"
keepalive 10 120
# Securite
user nobody
group nogroup
chroot /etc/openvpn/jail
persist-key
persist-tun
comp-lzo
# Log
verb 3
mute 20
status openvpn-status.log
log-append /var/log/openvpn.log


My client.conf 
> 
# Client
client
dev tun
proto tcp-client
remote A.B.C.D 443
resolv-retry infinite
cipher AES-256-CBC
# Cles
ca ca.crt
cert myvpn.crt
key myvpn.key
tls-auth ta.key 1
# Securite
nobind
persist-key
persist-tun
comp-lzo
verb 3

A.B.C.D is solved with
> wget -qO- whatismyip.org

I don't think it's because of OpenVpn, maybe because of Ubuntu (my version is 10.04)

---

