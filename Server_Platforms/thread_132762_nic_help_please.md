---
title: "nic help please"
date: 2006-02-18
forum: Server Platforms
---

### Post by GNUoob on 2006-02-18
hi all,

i have a server running with 3 nics in it. 
eth 0 is mboard integrated
eth 1 is pci gig line running to garage router
eth 2 is pci 10/100 is connected to my cable modem switch

i have multi addresses from comcast and was trying to setup a web server.
right now im trying to get the system to run through the eth 2 for accessing the internet. it is able to surf but it goes through eth 1 which i dont want. i gave eth1 a static address for my local network. comcast gives me a dhcp address for  eth2 but i want my machine to use that exclusivly for serving. its not doing it right now.
67.164.210.137 is the ip that is given by comcast. 
for some reason when i go through the networking gui in administration it keeps using the eth1 as the default. i dont want that since my router is not setup to cross traffic and i want the box live on the net.

can anyone help me?

---

### Post by GNUoob on 2006-02-19
bump in hopes of a response :)

---

### Post by GNUoob on 2006-02-20
[QUOTE=GNUoob]bump in hopes of a response :)[/QUOTE]

:)

---

### Post by GNUoob on 2006-02-21
Am i being ignored or is ignorance the stable here?

---

### Post by GNUoob on 2006-02-22
bump with a hopefull smile

---

### Post by jamesr on 2006-02-22
looking at your question it may be that others, like myself, do not fully understand your configuration. Is it as follows

internet
   |
Cable modem
   |
eth2
PC  eth0 not used
eth1
  |
router
  |
rest of network

---

### Post by GNUoob on 2006-02-23
internet
|
cable modem(multiple ips=4)
|
switch_4_ports
#1-#2-#3-#4(ips)

#1ip goes to router through rj45
#2ip goes to ubuntu box(3 nics)
-------------ubuntu box nic0=notused
-------------ubuntu box nic1=router_ip#2(static ip i gave it from router)
-------------ubuntu box nic2=switch port#2(gets ip from comcast dhcp)

---

### Post by jamesr on 2006-02-23
Are you saying 

internet
|
cable modem(multiple ips=4)
|
switch_4_ports
#1-      #2-      #3-     #4(ips)
|            |
router     |
|            |
nic1       nic2      nic0
static    com dhcp
Ubuntu box

 why not move the router onto nic0 and use ipchains etc on the Ubuntu box. Using the ubuntu as a router and a web server . I believe I seen a similar set up on  [http://www.aboutdebian.com/lan.htm]("http://www.aboutdebian.com/lan.htm"). I am not an expert on ipchains just enough to be dangerous. So I hope the link helps

---

### Post by GNUoob on 2006-02-23
i wanted the ubuntu out live on the net serving as a game server and also able to share files with my internal lan

i have another machine live on the net(xp) that is setup the same way and is functioning just fine.

---

