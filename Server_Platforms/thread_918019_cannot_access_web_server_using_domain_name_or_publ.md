---
title: "cannot access web server using domain name or public ip"
date: 2008-09-12
forum: Server Platforms
---

### Post by ray84514 on 2008-09-12
i use Vmware to install ubuntu 8.04 server, and setup web server(apahce,php,mysql), i have a problem that i cannot access web server using domain name or public ip.

i had sign up a free domain of no-ip.com and use router DDNS function, then i also set port forwarding in the router. i had tested my site, host from internet can access my web server and i also can access it using private ip, but i cannot access it using domain name or public ip.......

why? can anyone help me? thanks a lot...............

---

### Post by qstraza on 2008-09-12
So domain name is pointed to the right ip, right?
You probably need to forward from xp to the vmware-ubuntu.

Well i dont understand this:
> i had tested my site, host from internet can access my web server and i also can access it using private ip, but i cannot access it using domain name or public ip.......

How did you excess your server from internet if not with public ip/domain?
Please explain your problem little more detailed maybe with ips (fake)...
So we will able to help faster.;)

---

### Post by ray84514 on 2008-09-12
> **qstraza said:**
> So domain name is pointed to the right ip, right?
You probably need to forward from xp to the vmware-ubuntu.

Well i dont understand this:


How did you excess your server from internet if not with public ip/domain?
Please explain your problem little more detailed maybe with ips (fake)...
So we will able to help faster.;)

thanks for your help
firstly, how to forward from xp to the vmware-ubuntu?

then..
my problem is that, my web server seems run correctly, hosts from internet can access it using domain name(such as [www.example.com:8080](www.example.com:8080))
but i had problem that i can not access it using [www.example.com:8080](www.example.com:8080) or real ip(such as 218.102.101.88) in winxp, i just can use private ip to access my web server. i want to know that why i can not access [www.example.com:8080](www.example.com:8080) but others can.

is it existing nat loopback problem? i don't konw what's wrong. because every things looks right. domain name can point to right ip, my friend helps me to test my web server, he can access it use [www.example.com:8080](www.example.com:8080).it means web server doesn't have problems.

-------------------------------
in ubuntu,
i can ping [www.example.com](www.example.com) and tracert it successfully.


but in winxp,
i try to ping [www.example.com](www.example.com) in win xp, result is that "ping request could not find host name [www.example.com](www.example.com)..... "
i also tracert [www.example.com](www.example.com), result is that "uuable to reslove target system name www.example.com"....

i found some nat loopback solution, it suggest me to edit .../ect/hosts file in winxp. after edited it, i solved the porblem, but i think it is meaningless...it is just hardcoding of domain name translate to ip address in winxp.

---

### Post by cariboo on 2008-09-12
IF it works why bother trying to find another solution. I do the same thing on my internal network, as I access the other computers on the network by hostname rather than ip address.

Jim

---

### Post by ray84514 on 2008-09-12
of course, that is solution. but i don't think it can help me to solve real problem. because my friend also uses ubuntu 8.04 to setup web server, but he does't have this problems. we use same model router and same config. i really want to know the real reason....

---

### Post by windependence on 2008-09-13
Actually, adding it to the hosts file IS the solution if you have a router that does not support NAT loopback which is most of them out there. By accessing the external address from within your LAN, you are trying to do NAT loopback which your router doesn't know what to do with. The normal solution is either to add it to your hosts file or set up a DNS server, which is a lot of work unless you have many many computers on your LAN.

-Tim

---

