---
title: "Apache/ssh server"
date: 2009-07-01
forum: Server Platforms
---

### Post by KirKenix on 2009-07-01
Last night i started putting together an Ubuntu server for my own personal use so that i would be able to access files and my printer from anywhere

I read a couple tutorials on how to set up the server; i set up ssh and apache
I opened the remapped and opened 2222 for ssh and 12345 for apache

I can now access everything either through putty or winscp over LAN, but not over the internet; and i'm completely bewildered as to why not! i even set up a noip account to make sure the ip address is static.

---

### Post by KirKenix on 2009-07-01
Also, i dont know if this helps, but i if i use canyouseeme.org to check ports my connection times out. Thanks for any input and help :)

---

### Post by dtoronto on 2009-07-01
I'm not sure I understand what your question is or where your hang up is.  If you have a DNS pointing the domain name to your IP then it is just a matter of configuring your apache2 to direct all traffic to your root directory.

---

### Post by KirKenix on 2009-07-01
I'm sorry if i'm a little bit of a noob but when i try to access my ip address i cant even log into the server, it times out or says that my domain doesnt exist
And then if that fixed the apache issue, would it also fix the ssh issue; they seems connected but i cant find the hole..

---

### Post by KirKenix on 2009-07-01
i thought i'd try to update with more information; so when i try to use winscp or putty i get "Network Error: Connection refused" and i checked my iptables to open the ports, the ports are opened on my router. I can still connect through lan but if use the full public nonlan ip address i get "connection refused" in seconds, i was wondering if its possible that instead of the server having problems recieving my request. Maybe my laptop is being blocked from sending my request; it's running windows vista

---

### Post by Zenze on 2009-07-01
You mentioned LAN you I'm assuming that your server is behind a router.

Did you forward the port on the router to your servers ip?

---

### Post by KirKenix on 2009-07-01
Yes its forwarded at the 192.168.1.2 which the network recognizes it as, should i, is there a way to open it at its internet ipaddress

---

### Post by wojox on 2009-07-01
When you connect using your ip address your connecting to your router.
Which it won't let you by default.
Open port forwarding up like poster above me suggested.

---

### Post by KirKenix on 2009-07-01
maybe i'm misunderstanding something, but the ports are forwarded; they're forwarded on the router, open in iptables, being listened for,but it seems like somehow they're still being blocked?

---

