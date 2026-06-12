---
title: "UFW -Unable to acccess port after rule"
date: 2013-02-12
forum: Security
---

### Post by testmiss on 2013-02-12
Hi,

I have a question regarding restricting access through ufw on port 80(http):

When I issue the command sudo ufw allow 80, I can access my web page from any where.

But I only want one of my computers (192.168.1.101) to access my webpage and NOT everyone.  So I issued the command:

ufw allow from 192.168.1.101 to any port 80.

But I cannot access from any of the computers, including the computer with the IP, 192.168.1.101.

I also tried the commands, but with no luck:

 ufw allow from 192.168.1.101 to any port 80 proto tcp
 ufw allow from 192.168.1.101 to any port 80 proto udp

What am I doing wrong here. Can someone help me?

---

