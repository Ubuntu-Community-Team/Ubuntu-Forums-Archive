---
title: "LAN in LAN and samba share"
date: 2015-12-05
forum: Server Platforms
---

### Post by qubaa on 2015-12-05
Network look like this
ISP
|
|
Ubuntu Server 192.168.1.1 
| | |
| | ubuntu with samba 192.168.1.20
| |
| |
|client 192.168.1.10
|
          client router (TPLINK) with IP from ubuntu 192.168.1.30 and  his own adresses 172.0.1.1 (plug in into WAN) -------- and his computer 172.0.1.2


Client 192.168.1.10 see share on 192.168.1.20
Ping from 172.0.1.2 to 192.168.1.1 is working.
Client from 172.0.1.2 cant see share on 192.168.1.20

If there any way to get samba share from 172.0.1.2???

---

### Post by darkod on 2015-12-05
How about ping from 172.0.1.2 to 192.168.1.20?

If the ping to 192.168.1.1 is working in theory it should be able to ping and use the samba server too. But something might be wrong (missing) with the routing. You just have to follow the traffic flow, and also test by pinging each next step, to check if you can reach the destination or where does it break if not.

I didn't understand the part about client 192.168.1.30. Is it a router (machine doing routing), or just a client. According to the described, 192.168.1.30 is a router too, which means you have two routers between 172.0.1.2 and the samba server, right? Three routers if you count 192.168.1.1 too.

---

### Post by qubaa on 2015-12-05
1. All clients got IP from ubuntu server (I corrected the picture)
2. Client 192.168.1.30 has router (TP-LINK). Router got IP from ubuntu server, but because its connected to WAN port on client router, has own adress.
3. Ping from 172.1.0.2 is not working to 192.168.1.20

---

### Post by darkod on 2015-12-05
Sorry, but I am still confused. Where is the 172.0.1.x network? On remote location? If it is, why the connection to the local network is not done to the local router, 192.168.1.1? This is under the assumption 192.168.1.1 is doing the routing for 192.168.1.x (default gateway).

You rarely connect a remote network to a specific client on the local network, because in such case that client needs to do routing too (which converts it into a router of a kind). I think that's where your routing breaks, on the local client connected to the 172.0.1.x. From your updated picture you removed the 192.168.1.30 but if that client has IPs in both networks, you should put them both so that it can show connections to both networks.

Is possibly client 192.168.1.30 off-site too? The statement "client has router" still confuses me. The client can't have a router. It is either a router or a client. It either has only 192.168.1.30 as a client or it has for example both 192.168.1.30 and 172.0.1.1 on two network cards and it acts as default gateway for 172.0.1.x. That makes it a router. Would this be a TP-LINK device?

---

### Post by qubaa on 2015-12-05
Sorry.
Now should be (picture xcorrected again)
User has a TPLINK router. That make that: TPLINK is client to my local network but user is client for TPLINK :)
Ohhh... now is this clear?

---

### Post by darkod on 2015-12-05
Yes, now it's much clearer... :)

Have you tried running trace route from 172.0.1.2 to 192.168.1.20 and see if that gives you the exact hop where it breaks? If the client is windows the command is tracert, in linux it's traceroute (you might need to install it).

Now only one piece of information is missing: who does the routing for 192.168.1.x? The ubuntu box 192.168.1.1 or some ISP router? What is the default gateway on your 192.168.1.x clients?

I think you might only need a static route on the TP-LINK which will say which router to use to reach 192.168.1.20.

---

### Post by SeijiSensei on 2015-12-06
If 192.168.1.1 is the gateway router for the other hosts in the 192.168.1.0/24 network, then as darkod suggests you probably just need a static route on that box for the 172 network.

On 192.168.1.1 try this:
```
sudo ip route add 172.0.1.0/24 via 192.168.1.30
```

That 172.0.1.0 subnet is a strange choice.  It's not an official "private" network.  Private addresses that start with 172 can range from 172.16.0.0 through 172.31.255.255.  In fact, a "whois" lookup shows that the range 172.0.0.0 through 172.15.255.255 belongs to AT&T.

---

### Post by qubaa on 2015-12-06
> **darkod said:**
> Yes, now it's much clearer... :)

Have you tried running trace route from 172.0.1.2 to 192.168.1.20 and see if that gives you the exact hop where it breaks? If the client is windows the command is tracert, in linux it's traceroute (you might need to install it).

Now only one piece of information is missing: who does the routing for 192.168.1.x? The ubuntu box 192.168.1.1 or some ISP router? What is the default gateway on your 192.168.1.x clients?

I think you might only need a static route on the TP-LINK which will say which router to use to reach 192.168.1.20.

1. Routing is made on ubuntu box 192.168.1.1
```

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
  address 91.xxx.xxx.xxx
  netmask 255.255.255.252
  gateway 91.xxx.xxx.xxx
  dns-nameservers 91.xxx.xxx.xxx, 91.xxx.xxx.xxx


# The secondary network LAN
auto eth1
iface eth1 inet static
  address 192.168.1.1
  network 192.168.1.0
  netmask 255.255.255.0
  broadcast 192.168.1.255
  dns-nameservers 192.168.1.1

```

2. Default gateway is 192.168.1.1 (ubuntu server).

Thank you very much for the advices. I will try both methods.

---

