---
title: "iptables issue"
date: 2011-02-10
forum: Server Platforms
---

### Post by em_ubu on 2011-02-10
Hello,

I'm trying to do transparent proxy for all my internal LAN minus 2 PCs.
In my iptables rules I have a REDIRECT rule: 
> iptables -t nat -A PREROUTING -i $LAN -p tcp --dport 80 -j REDIRECT --to-port 8080which works fine.
Now, those 2 PCs I want them to have access to port 80 without being redirected to 8080.
I know that it works fine with on PC if I exclude it's IP, but can I do it with 2?

To make it even more fun, I'm trying to block the MAC address (not the ip). But if IP is the only option, I'm fine.

thanks!

---

