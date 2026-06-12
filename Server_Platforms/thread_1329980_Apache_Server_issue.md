---
title: "Apache Server issue?"
date: 2009-11-17
forum: Server Platforms
---

### Post by ductiletoaster on 2009-11-17
Ok my question is why cant i access from my home network my server using its internal ip.

My external Ip is linked to it and u can see the index.html of it that way
but if u type the Servers internal ip such as 192.168.1.185 it doesnt work?

Any suggestions

Ubuntu sever 9.04 apache2

---

### Post by ductiletoaster on 2009-11-17
I solved it... i just need to ad another virtual host to handle it!

---

### Post by madhu.neal on 2009-11-18
[SIZE=4]Hi Can you map your local IP to WAN IP .. 

it should work .

Good luck!

Madhu.[/SIZE]

---

### Post by lvlint67 on 2009-11-18
> **ductiletoaster said:**
> I solved it... i just need to ad another virtual host to handle it!

depending on your needs I feel like there is a way to let it listen on two ips or more (127.0.0.1,wan,lan) but if you just want it to function and the marginal performance gains are unimportant then it sounds like you do indeed have your solution.

---

