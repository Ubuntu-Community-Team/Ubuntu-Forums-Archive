---
title: "Foward traffic with openvpn"
date: 2009-04-25
forum: Server Platforms
---

### Post by nikomax on 2009-04-25
Hi there,

I am trying to setup an openvpn server that will allow me to forward all my traffic from my Windows box, through it to the web and back.

I have been following the [HOWTO]("http://openvpn.net/index.php/documentation/howto.html") on the openvpn site and can now connect to the openvpn server from the GUI client on Windows.

As far as I am aware all that is left to do is to some how make the server forward the traffic.

I used this iptables code given by the HOWTO but see no difference when trying to load a web page from windows All that happens is that the connection times out.

I have been looking for the past 2 days now and while there is a lot to look at none of it has helped, especially seeing as I dont understand Iptables fully.

Here is the conf files from both the Server and the Client with out the comments.

Server::
```

port 1194
proto tcp
dev tun
ca /etc/openvpn/easy-rsa/2.0/keys/ca.crt
cert /etc/openvpn/easy-rsa/2.0/keys/server.crt
key /etc/openvpn/easy-rsa/2.0/keys/server.key  # This file should be kept secret
dh /etc/openvpn/easy-rsa/2.0/keys/dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway def1"
keepalive 10 120
persist-key
persist-tun
status openvpn-status.log
verb 3

```

Client::
```

client
dev tun
proto tcp
remote niko-niko.co.uk 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert niko.crt
key niko.key
mp-lzo
verb 3

```

This is the code given by the HOWTO to deal with iptables:
```

iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE

```

Also as I have seen this is other posts I edited /etc/sysctl.conf so net.ipv4.ip_forward=1

I really hope that someone can help with with this, not just to get it working but to help me understand what is going on as well.

Thanks

---

