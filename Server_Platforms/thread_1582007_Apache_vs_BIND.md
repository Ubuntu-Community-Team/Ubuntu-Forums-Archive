---
title: "Apache vs BIND"
date: 2010-09-25
forum: Server Platforms
---

### Post by aubertine on 2010-09-25
Hi,

For the past month, I was experimenting with Proxmox and VMs. I set up one VM to forward traffic from port 80 to the other machines using Apache (see code below). 

**Problem is** that I wasn't successful at forwarding ssh or other traffic besides traffic on port 80.
**Question is** whether it makes more sense to set up BIND on a dedicated DNS VM to forward all requests to the right VM? Or do I just need to learn to tweak Apache?

```

ServerName ...
ProxyRequests on
ProxyPreserveHost on
<Proxy *>
Order deny,allow
Allow from all 
</Proxy>
ProxyPass / http://192.168.1.203/
ProxyPassReverse / http://192.168.1.203/

```

---

### Post by CharlesA on 2010-09-25
Apache isn't a proxy server, it's an HTTP/HTTPS server.

What exactly are you trying to do?

---

### Post by SeijiSensei on 2010-09-25
> **CharlesA said:**
> Apache isn't a proxy server, it's an HTTP/HTTPS server.

What exactly are you trying to do?

+1

BIND isn't one either.  It provides domain name services.  It's neither equivalent to, nor competitive with, Apache.

---

### Post by BkkBonanza on 2010-09-26
If you're setting this up as a **reverse proxy** to handle multiple web servers on one port then I'd suggest using nginx. It's light weight and well suited as a reverse proxy - much lighter than Apache, and easy to setup.

You can't reverse proxy ssh or any protocol that doesn't have a destination hostname in the connection "request headers". HTTP does, so the proxy can decide where to forward it to. Mail protocols can as well. ssh is encrypted so the destination domain is not visible and so it's impossible to determine where it needs to go.

Bind won't help you if the incoming connections all have the same destination IP already. The only way I know to handle something like ssh is to have different ports for different target servers and then use port forwarding for each one. You can forward with port change so that each server still uses port 22. But on the public facing gateway the ports would be different.

Reverse proxying is protocol dependent - it needs to look at protocol headers rather than just tcp/ip packet headers.

---

### Post by aubertine on 2010-09-26
Hi all! Thanks the clarification! Didn't know that a SSH request do not carry destination info in its header and therefore cannot be run via the Apache Proxy. And good to know what BIND does.

Thanks again! This thread's resolved.

---

