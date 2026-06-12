---
title: "Squid, can browse but no email clients..."
date: 2006-05-19
forum: Server Platforms
---

### Post by Elijah on 2006-05-19
I was instructed to implement a delay pool'ed squid proxy to limit the bandwidth of each PC. That was successful. Now we need to force all users to use the proxy by shutting down all connections from our router except for our proxy server. And then set dhcp's default gateway to our proxy server. 

That works but ... now our email clients (evolution, thunderbird) doesn't work ... it simply tries to connect there forever. I've setup proxy settings for those clients but it still doesn't work . :-k  Help?

Edit: I realized I needed something like an iptables rule to redirect & forward all ssl/https/emailClient requests to use a direct connection instead ... is this right? what kind of iptable rule shall I use to make all requests to point to our router instead? (192.168.100.3).

---

### Post by Elijah on 2006-05-23
Nevermind, solved it. Setted up a new iptable rule :

-A POSTROUTING -p tcp -m tcp --dport 995 -j SNAT --to 192.168.100.2
-A POSTROUTING -p tcp -m tcp --dport 443 -j SNAT --to 192.168.100.2

Thanks for the help though.

---

### Post by greymoose58 on 2006-08-04
Elijah,

I'm having exactly the same problem. Can you tell me where to put those new rules you used to see if that will solve the it for me too?

Cheers.

---

