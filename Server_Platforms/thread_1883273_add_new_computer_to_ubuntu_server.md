---
title: "add new computer to ubuntu server"
date: 2011-11-18
forum: Server Platforms
---

### Post by Qutaibah on 2011-11-18
hi I want help in ubuntu server 
I cant post or do anything in ubuntu forum 
how can I add computer to ubuntu server 
I mean to make network 
I am working on my ubuntu server to make a network on and set users with other PCs using hub but I faced many problem 
-how can I set domain controller on other PC as login choice ?

-how can I determine that this IP refers to this specific PC ?
I mean when I connect the net line with hub or router and the other line to server connecting on the same hub/router what I will do after ....
- I confagrate the dns and there zones and static IPs and resolve

the problems 
1-when I write "domainname" on terminal gave me "(none)" although I put in /etc/resolv.conf my domain name and ip address of my dns that is the same of my ip of server
2-when reboot my system the erase that I edit in resolv.conf and put the ip of my router in nameserver 

pleeeeeeeeeeeeease help me

---

### Post by volkswagner on 2011-11-18
> **Qutaibah said:**
> 
...
2-when reboot my system the erase that I edit in resolv.conf and put the ip of my router in nameserver 
...


Are you running a desktop version or do you have network manager installed?  I believe what you are explaining is normal behavior of NetworkManager.

---

