---
title: "Replication issue in entire networks after deploying the Ubuntu Server"
date: 2015-06-25
forum: Server Platforms
---

### Post by new900 on 2015-06-25
Hi Guys,
      After deploying the Ubuntu 14.04.2 LTS web Server we had some internet replication problem with our entire network. the internet will get down. even i couldn't able to browser internet explorer from other client system also, at the same time while disconnecting the Ubuntu server from the network all connection will work's fine. please some one help us..:confused::confused::confused:   

[IMG]http://prntscr.com/7l3b4n[/IMG]


[IMG]http://prntscr.com/7l3bjh[/IMG]

Regards
Praveen

---

### Post by darkod on 2015-06-25
What is internet replication? You mean internet access?
Introducing a web server does not influence the internet access, in general. Can you give us more details of all roles the ubuntu server has? Only web server?

First thing that comes to my mind is IP conflict. If the ubuntu server has identical ip as another (important) machine. That can block the network. Make sure that is not the case.

---

### Post by new900 on 2015-06-29
yes we couldn't able to access the internet... 

we are trying to deploys Ubuntu webserver only with lamp service. we are clearly checked there is no IP conflict because we've registered the server mac address in our firewall...

---

### Post by darkod on 2015-06-29
Registering a mac address in a firewall is not related to ip conflict in the lan.

Can you post the ifconfig output of the server? And also the dhcp server settings?

Make sure the ubuntu server ip is outside the dhcp range. Also from a workstation in the lan with the ubuntu server connected try:
ping the router (gateway) ip
ping 8.8.8.8
ping yahoo.com

That should show you if you have routing or dns problem.

---

