---
title: "Server can't see the DNS on the remote server connected using OpenVPN."
date: 2010-04-07
forum: Server Platforms
---

### Post by jusufd on 2010-04-07
Hi,

My Ubuntu server remotely connected to Windows OpenVPN server that also host the DNS. This Ubuntu server can't recognize any entry of the DNS. When I ping any entry it always fail. Did I need to add something on my OpenVPN config. Can you guys help me out? 

Here is my OpenVPN client configuration:
#-------------------------
client
dev tun
proto udp
remote 65.223.123.456 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca2.crt
cert server2.crt
key server2.key
comp-lzo
verb 3
#-------------------------

Thanks.

---

### Post by KB1JWQ on 2010-04-07
cat /etc/resolv.conf

What DNS servers live there?  The remote ones (good!) or the local ones (bad!)?

---

### Post by cdenley on 2010-04-07
[http://openvpn.net/archive/openvpn-users/2006-10/msg00217.html](http://openvpn.net/archive/openvpn-users/2006-10/msg00217.html)
[http://openvpn.net/archive/openvpn-users/2006-10/msg00218.html](http://openvpn.net/archive/openvpn-users/2006-10/msg00218.html)

---

