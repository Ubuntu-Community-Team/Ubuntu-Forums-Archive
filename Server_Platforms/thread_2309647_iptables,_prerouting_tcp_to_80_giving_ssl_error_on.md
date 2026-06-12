---
title: "iptables, prerouting tcp to 80 giving ssl error on the client"
date: 2016-01-12
forum: Server Platforms
---

### Post by sukru2 on 2016-01-12
Hi
My ubuntu server's ip is 172.16.99.3

at the same vlan there is a computer and its ip is 172.16.99.20 and gateway is 172.16.99.3.

in this vlan i want to redirect all tcp connections to ubuntu's 80th port.

I am using this command : /sbin/iptables -t nat -A PREROUTING -p tcp -j REDIRECT --to-port 80

so when a user try to connect to web, he is redirecting to apache web server, its working fine.

But when I try to go to [www.google.com](www.google.com), facebook.com or mynet.com from client it's giving an error: ERR_SSL_PROTOCOL_ERROR

I ve prerouted the 443th port to 80 and now if i write the adress like [www.google.com:443](www.google.com:443) it is working again but when i write just [www.google.com](www.google.com) its giving the same error.

Can anybody help me pls.
Thanks.

---

