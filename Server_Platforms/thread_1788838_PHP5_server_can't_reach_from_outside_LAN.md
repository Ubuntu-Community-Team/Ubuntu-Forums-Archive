---
title: "PHP5 server can't reach from outside LAN"
date: 2011-06-23
forum: Server Platforms
---

### Post by LaserBoi on 2011-06-23
I have just installed ubuntu Server with Apache2, PHP5, MySQL and PhpMyAdmin.
Everything works fine when I access the server on the LAN. I have forwarded port 80 in my router to the LAN ip of this server. (I have other windows based web servers so I am familiar with port forwarding) however when I try to access the server from the true static IP outside the LAN I cannot reach it and the connection just times out with the Ubuntu server connected if I use canyouseeme it says port 80 is closed. If I replace the Ubuntu server with another server I can reach this just fine from outside and canyouseeme says the port is open. So I am pretty darn sure the router is correct and that there is some config problem with the Ubuntu box, but I cannot find it. the ports.conf file has listen 80 in it and the apache2.conf includes the ports.conf file.
Please help. Thanks
<M>

---

### Post by dapperdanny77 on 2011-06-23
```

## to see which ports are listening on your system
>netstat -vatn |grep LISTEN

tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN     
.
.
.

## shows the process listen on port 80
>lsof -i :80

COMMAND  PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
apache2 3043     root    3u  IPv4  13274      0t0  TCP *:www (LISTEN)
apache2 3048 www-data    3u  IPv4  13274      0t0  TCP *:www (LISTEN)

## shows iptables firewall rules on your machine
>sudo iptables -L

```

try above commands to see if apache ist listening correctly and is reachable from outside (iptables)

---

### Post by LaserBoi on 2011-06-29
I have solved this issue now. 
I have multiple iP's but I can only use port 80 on one of them. Now that I have found that I use the correct real IP and I can access from the outside. 
Thanks,
<M>

---

