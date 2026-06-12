---
title: "openvpn routing, cant ping vpn client from lan"
date: 2010-05-02
forum: Server Platforms
---

### Post by qstraza on 2010-05-02
Hello everyone,

I am playing with openvpn, and I got stuck.
I am using ubuntu server for openvpn server, which has 2 physical NICs, one is directly on internet and other is LAN, where few pcs are connected on.

As vpnclient im using laptop with kubuntu.


```

      LAN             SERVER   
(192.168.2.0/24) <-> eth0=192.168.2.1,          <-,
                     tun0=10.3.3.1              <->X<-> internet/VPN <-> Laptop (10.3.3.7)
                     eth1=89.212.x.x(internet)  <-'

```

I set openvpn server as tun0 (10.3.3.1).


From laptop I can ping server and all LAN pcs
From server I can ping laptop,
but I cannot ping laptop from LAN pcs

While sniffing tun0 on laptop I get the following results
When I ping laptop (10.3.3.7) from server (10.3.3.1)
I get normal request/reply
```
request src: 10.3.3.1 dst: 10.3.3.7
reply src: 10.3.3.7 dst: 10.3.3.1
```

But when pinging from LAN pc (192.168.2.2), I get request from server's internet IP and not from LAN pc's IP (192.168.2.2) and ofc no reply.
```
request src: 89.212.x.x dst: 10.3.3.7

```

And also I can ping from 192.168.2.2 to 10.3.3.1

On server I used
```

iptables -A INPUT -i tun0 -j ACCEPT
iptables -A FORWARD -i tun0 -j ACCEPT

```

What do I have to do? I think I need to redirect traffic on server with iptables, but I am not sure how.

---

### Post by spynappels on 2010-05-02
You need to enable IP forwarding in the server and also place a static route forwarding all 10.3.3.0/24 traffic with 192.168.2.1 as the gateway.

---

### Post by qstraza on 2010-05-02
> **spynappels said:**
> You need to enable IP forwarding in the server and also place a static route forwarding all 10.3.3.0/24 traffic with 192.168.2.1 as the gateway.

Thanks for the reply, ip forwarding is enabled (on server)

I added route like this:
```
sudo route add -net 10.3.3.0 netmask 255.255.255.0 gw 192.168.2.1
```

After that, I could not ping from/to anywhere,
any other ideas?

---

### Post by Scunizi on 2010-05-02
You forgot the /24 at the end of the 10.3.3.0 address

---

### Post by qstraza on 2010-05-02
> **Scunizi said:**
> You forgot the /24 at the end of the 10.3.3.0 address

I am pretty sure that stating "/24" or "netmask 255.255.255.0" is the same

```
route add -net 10.3.3.0/24 gw 192.168.2.1
```

well I tried it anyway but the results are the same

---

### Post by qstraza on 2010-05-03
I have found the problem and the solution,

This rule was in a way
```
iptables -t nat -A POSTROUTING -s 192.168.2.0/24 -j SNAT --to-source=$IP
```

I changed it to
```
iptables -t nat -A POSTROUTING -s 192.168.2.0/24 -d ! 10.3.3.0/24 -j SNAT --to-source=$IP
```

And now it works

Any suggestions how can this be resolved nicer?

---

