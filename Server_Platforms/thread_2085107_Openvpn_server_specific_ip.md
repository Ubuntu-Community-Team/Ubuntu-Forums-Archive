---
title: "Openvpn server specific ip"
date: 2012-11-17
forum: Server Platforms
---

### Post by ruvil on 2012-11-17
Hi

I have a bit of a problem.

I have configure my ubuntu server to act as a openvpn server and all that works just fine and dandy. The only problem i have is with my ip addresses.

My network configuration is as following:

eth0 with ip x.x.x.x
eth0:1 with ip y.y.y.y
eth0:2 with ip z.z.z.z etc etc

I want all clients that connects to the server to have the y.y.y.y outgoing ip, and not the ip of eth0.

How should i proceed with this?

I tried to configure the server.conf of openvpn with "local y.y.y.y" but that didn't work, and i have tried the following iptables configuration:
iptables -t nat -A POSTROUTING -j SNAT --to-source y.y.y.y

That does not seem to work either.

Does anybody have any idea about what i might do wrong?


Cheers

---

### Post by SeijiSensei on 2012-11-17
Can't you just reverse the assignments so that eth0 gets the y.y.y.y address and the aliased interface gets x.x.x.x?

---

### Post by ruvil on 2012-11-17
That's possible but then i would have to change the configuration for all my other applications as well, apache, sendmail etc so i don't think it's a possible solution. Somehow it should be possible to get this going anyway...

---

### Post by sandyd on 2012-11-17
> **ruvil said:**
> Hi

I have a bit of a problem.

I have configure my ubuntu server to act as a openvpn server and all that works just fine and dandy. The only problem i have is with my ip addresses.

My network configuration is as following:

eth0 with ip x.x.x.x
eth0:1 with ip y.y.y.y
eth0:2 with ip z.z.z.z etc etc

I want all clients that connects to the server to have the y.y.y.y outgoing ip, and not the ip of eth0.

How should i proceed with this?

I tried to configure the server.conf of openvpn with "local y.y.y.y" but that didn't work, and i have tried the following iptables configuration:
iptables -t nat -A POSTROUTING -j SNAT --to-source y.y.y.y

That does not seem to work either.

Does anybody have any idea about what i might do wrong?


Cheers
Try
```

iptables -t nat -A POSTROUTING -s 172.17.0.0/24 -j SNAT --to-source y.y.y.y

```
Where 172.17.0.0/24 is your openvpn subnet

---

### Post by ruvil on 2012-11-17
Thanks, but unfortunately it does not seem to work. Maybe i'm missing something in my server.conf?

```

local y.y.y.y
port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key
dh dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway def1"
push "dhcp-option DNS 8.8.8.8"
keepalive 10 120
comp-lzo
persist-key
persist-tun
status openvpn-status.log
verb 3

```

---

### Post by SeijiSensei on 2012-11-17
> **ruvil said:**
> That's possible but then i would have to change the configuration for all my other applications as well, apache, sendmail etc so i don't think it's a possible solution. Somehow it should be possible to get this going anyway...

I don't see why.  You will still have both interfaces active with the same IP addresses.  Requests for SMTP and HTTP traffic will still arrive in the right place and get handled the same way as before.  I've used aliased interfaces, and as far as I could tell the assignment of IP addresses was entirely arbitrary.

I think you should just try reversing the assignments.  If something doesn't work, you could switch them back pretty quickly.  I seriously do not think you would see any effects on your current services.

---

