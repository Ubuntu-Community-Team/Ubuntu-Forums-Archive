---
title: "LAN to LAN OpenVPN"
date: 2016-03-04
forum: Server Platforms
---

### Post by Random20220612 on 2016-03-04
Hi,

I need help with the tutorial posted in [this]("http://www.tuser.nl/2011/01/20/lan-to-lan-openvpn/") blog about open vpn lan to lan setup over ubuntu servers.
I have openvpn server running without problems and I can connect with the clients but I'am confused with "lan to lan" setup.

In the cloud server I have this server1.conf file:
```
local       1234
dev         tun1
proto       udp
port        1195
server 192.168.93.0 255.255.255.0
push "route 192.168.94.0 255.255.255.0"
route 172.30.20.0 255.255.255.0
client-to-client
dh          dh2048.pem
ca          ca.crt
cert        server.crt
key         server.key
keepalive   10 120
comp-lzo
persist-tun
persist-key
client-config-dir ccd
verb   5
status openvpn-status.log
ifconfig-pool-persist ipp.txt
user nobody
group nogroup
```

ccd ("client2" file) with:
```
iroute 172.30.20.0 255.255.255.0

```
The CA and KEY generated for cloud server and the Certificates and Keys for Clients.

So I want to connect from my ubuntu local server, with openvpn running, as client, to my ubuntu cloud server, with openvpn running. 

In the local server I have client2.conf file:

```
client
dev tun1
nobind
proto tcp
remote 1234 1195
persist-key
persist-tun
ca ca.crt
cert client2.crt
key client2.key
comp-lzo
verb 3

```

The ca.crt, client2.key and client2.crt are generated in the cloud server and copied to local server.

But, I can't connect lan to lan, I'am loading the conf in both servers (client2.conf and server1.conf) but I can't connect because I think the setup is not complete yet.
The static routes can't be added yet, maybe because there is no contact between servers:

In the local server:

```
# route add -net 192.168.93.0 netmask 255.255.255.0 gw 192.168.94.15
SIOCADDRT: La red es inaccesible
```

In the cloud server:

```
# route add -net 192.168.93.0 netmask 255.255.255.0 gw 172.30.20.1
SIOCADDRT: No existe el proceso
```


[B]Any idea please?
[/B]

Thanks
Marcelo.-

---

### Post by darkod on 2016-03-04
LAN to LAN is usually connecting gateways on both networks. Not "client" to "server".

Depending what you actually want to do, you can make a direct LAN to LAN vpn much simpler.

The config you posted is client-server setup. So do you want to try fixing this one or try a lan to lan?

---

### Post by Random20220612 on 2016-03-04
Hello,

I have client to server running fine, but now I need setup LAN to LAN and I'm confused with the correct procedure.
Can you help me with lan to lan setup please?

---

### Post by darkod on 2016-03-04
You can also use client to server, it might be easier because you already know it. There will always be only one client, but that doesn't matter.

I also haven't done lan to lan so I can't help too much right now (low on free time). I had one tutorial bookmarked but I see now the page has been removed so I can't give you a link.

If you are making multiple connections just make sure you are using different vpn subnets because they all need to be different from each other. For example you can't connect a client to two different vpn servers if both their vpn subnets are identical.

---

### Post by SeijiSensei on 2016-03-04
You want to use a simple, shared-key configuration.  Read this:  [http://openvpn.net/static.html](http://openvpn.net/static.html)

Use a custom port so it won't interfere with the client/server connections.  I usually choose ports > 10000 like 54321.

I have one machine in my home network that has a tunnel to one of my cloud servers at Linode.  That machine has multiple tunnels to other locations and handles routing among them.

---

