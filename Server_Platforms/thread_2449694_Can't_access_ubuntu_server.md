---
title: "Can't access ubuntu server"
date: 2020-09-01
forum: Server Platforms
---

### Post by ozarif2006 on 2020-09-01
We have web server running on ubuntu 14.04 server. This server randomly blocks access from user PC. I can ping other server on the same network but not this server. As a temporary solution i changed the ip address and it works. The firewall is switched off. 
Is there any way to find out why this server refuse connection.

---

### Post by mastablasta on 2020-09-01
it's in the logs. auth.log and maybe some others as well.

check /var/log

---

### Post by ozarif2006 on 2020-09-08
checked /var/auth.log and can't find.

---

### Post by ozarif2006 on 2020-09-09
i had another ip blocked by ubuntu server. this time I use the same blocked ip and assigned to another pc2. now pc2 is blocked. I can ping the pc2 from the ubuntu server but now from the pc2.
I also ran tcpdump on ubuntu and it reply back but still no communication from pc2.

---

### Post by mastablasta on 2020-09-10
so an IP connection is blocked. are you using maybe some fail2ban or similar service that blacklisted the IP indefinitely and is keeping it in jail?

---

### Post by SeijiSensei on 2020-09-10
Are you sure you don't have an IP conflict on your network with two machines having the same address?

Your servers do use static IP assignments, right? Never rely on DHCP to assign addresses to servers.

---

### Post by ozarif2006 on 2020-09-11
No we dont use such software unless it bundled with OS.
> **mastablasta said:**
> so an IP connection is blocked. are you using maybe some fail2ban or similar service that blacklisted the IP indefinitely and is keeping it in jail?

---

### Post by ozarif2006 on 2020-09-11
Initially i suspected duplicate ip. but one i am testing is the only ip address. This PC i can ping from the server but not from PC to server. While doing ping test from the server, i removed the network cable to see if there is another device with same ip but not.


> **SeijiSensei said:**
> Are you sure you don't have an IP conflict on your network with two machines having the same address?

Your servers do use static IP assignments, right? Never rely on DHCP to assign addresses to servers.

---

### Post by SeijiSensei on 2020-09-11
Is the server running iptables? Is it blocking ICMP (ping) requests?

---

### Post by Frogs Hair on 2020-09-13
Support request moved to *Server Platforms*.

---

### Post by ozarif2006 on 2020-09-13
Firewall is OFF.

---

