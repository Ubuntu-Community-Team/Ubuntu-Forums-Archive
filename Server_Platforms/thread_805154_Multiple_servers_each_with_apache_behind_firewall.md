---
title: "Multiple servers each with apache behind firewall"
date: 2008-05-23
forum: Server Platforms
---

### Post by kingbarry on 2008-05-23
I have a fixed IP, and am using Ubuntu server & shorewall to filter and forward http from net to loc

   I had only the one server running named virtual webs, and that worked fine. The server was 192.168.2.5

   Now I have to add two more servers ( ancient webs ) on the local lan ( 192.168.2.x ) and serve their webs thru the same firewall.

   ie - now I have 3 servers , each with their own apache servers and each with one or more web url addresss. 

   how do I direct traffic in this setup ?

   ie if url = webx.com -> 192.168.2.5
               weby.com -> 192.168.2.7
               webz.com -> 192.168.2.9

looks easy, should be doable - but can't figer it out - help

---

### Post by billy_boy_ on 2008-05-23
Hello, 

i think you should use a DNSs server to do that.

---

