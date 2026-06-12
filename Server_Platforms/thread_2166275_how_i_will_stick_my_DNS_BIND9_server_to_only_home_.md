---
title: "how i will stick my DNS BIND9 server to only home networking"
date: 2013-08-08
forum: Server Platforms
---

### Post by Profark on 2013-08-08
I have completely configured DNS BIND9 server on ubuntu server 12.xx
but i think it is working as open DNS how i will avoid this 
**[SIZE=2][SIZE=3]Senario[/SIZE][/SIZE]**
I have 4 computers having IPs 
[LIST]
[*]**winpc1**=192.168.1.50
[*]**winpc2**=192.168.1.51
[*]**winpc3**=192.168.1.52
[/LIST]
I have one **LINUX Server **having IP 192.168.1.30 static obviously 
My **Router **Address is 192.168.1.1
Now these Boxes are connected via Router's Ports
every one can ping each other DNS BIND9 doing caching as well all goes well but......
[B]How i will stick my DNS to only this network so that no other PC can access it 
[/B]
I mean what Should i add to named.conf.local ????

---

### Post by Cheesemill on 2013-08-08
If you haven't port forwarded the DNS ports in your router then your DNS server is already restricted to your local network.

---

