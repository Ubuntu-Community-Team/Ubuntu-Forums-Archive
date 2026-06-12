---
title: "How to configure routing for 2 HTTPS Servers ?"
date: 2012-11-16
forum: Server Platforms
---

### Post by pgp_protector on 2012-11-16
Right now we have one DSL Line into the Office (Small office setup)

The DSL -> Modem -> Netgear Router (Router acts as DHCP Server)

Right now the Router forwards Port 80 to the Ubuntu Box.
and via UPnP forwards Port 443(HTTPS) & 4125(RWW) to the Windows Home Server.

The Windows Homer server calls "home" to configure the remote access to ourname.homeserver.com 

We then use the ourname.homeserver.com with a CNAME lookup to forward traffic from subdomain.ourdomain.com to Our Linux Server.

So far so good,  All the above is actually working, and any ports I need for other applications (Like Metor) get forwarded to the Linux server as expected.


Now the issue.

We want to secure our subdomain.ourdomain.com  but that port is forwarded to the Windows Home server ??

What do I need to do to configure the Ubuntu Box so that any HTTPS or HTTP traffic request from inside our outside the local network for ourname.homeserver.com gets sent to the Windows Home server while all other traffic is handled by the Linux Box ??

Or is this not really feasible?

---

### Post by darkod on 2012-11-16
So, you want to configure the router to forward ports 443 and 4125 to your ubuntu server and then the ubuntu server to forward that traffic immediately to the windows server?

---

### Post by pgp_protector on 2012-11-16
> **darkod said:**
> So, you want to configure the router to forward ports 443 and 4125 to your ubuntu server and then the ubuntu server to forward that traffic immediately to the windows server?

Correct, Though I could have 4125 forward directly to the Windows Server as I don't think Ubuntu would ever be using port 4125.

---

### Post by sandyd on 2012-11-16
> **pgp_protector said:**
> Right now we have one DSL Line into the Office (Small office setup)

The DSL -> Modem -> Netgear Router (Router acts as DHCP Server)

Right now the Router forwards Port 80 to the Ubuntu Box.
and via UPnP forwards Port 443(HTTPS) & 4125(RWW) to the Windows Home Server.

The Windows Homer server calls "home" to configure the remote access to ourname.homeserver.com 

We then use the ourname.homeserver.com with a CNAME lookup to forward traffic from subdomain.ourdomain.com to Our Linux Server.

So far so good,  All the above is actually working, and any ports I need for other applications (Like Metor) get forwarded to the Linux server as expected.


Now the issue.

We want to secure our subdomain.ourdomain.com  but that port is forwarded to the Windows Home server ??

What do I need to do to configure the Ubuntu Box so that any HTTPS or HTTP traffic request from inside our outside the local network for ourname.homeserver.com gets sent to the Windows Home server while all other traffic is handled by the Linux Box ??

Or is this not really feasible?

something like
```

iptables -t nat -A PREROUTING -s 10.0.0.0/8 -p tcp --dport 80 -j DNAT --to ip-address-of-windows-server:80
```
```

iptables -t nat -A PREROUTING ! -s 10.0.0.0/8 -p tcp --dport 80 -j DNAT --to ip-address-of-windows-server:80
```

replace 10.0.0.0/8 with your subnet mask and network

---

