---
title: "Ubuntu Server / Router"
date: 2011-04-01
forum: Server Platforms
---

### Post by DaltonXJ on 2011-04-01
Not sure if this belongs here or not.
 
What I am trying to do is use the Ubuntu box as a Server / Router.
 
Ubuntu server 10.10 Maverick
 
I have a HP Proliant DL360 G3 Server with win2003 Server on it. I need to setup the Ubuntu as a router for the 2 nics on the HP and route through my Ubuntu box from my netgear and internet.
 
questions?
 
how many nics I need in the Ubuntu box?
 
I have Ubuntu Server installed already!
 
Will I need to reinstall Server to add the other nic cards?
 
I have a crap load of nic cards!
 
What software will I need to install?
 
Is it already installed?
 
Please help!!!
 
very new to Ubuntu Server!! no GUI.. would prefer not to install a gui... server integrity...

---

### Post by volkswagner on 2011-04-02
You can user Ubuntu server for your router.  You really only need two network cards (1 bind to WAN, 1 Bind to LAN).  You connect the WAN NIC to your modem, or you can connect to your router.

If connecting directly to your modem, you would set the card to get DHCP if your ISP gives you a dynamic ip address.  If they give you a static ip then you can set the NIC to static with your ISP's info for ip, network, and gateway.

The second NIC you can attach to a switch for connecting to all you LAN devices.

You should not need to re-install the operating system if you add hardware.

Have you looked int [pfsense]("http://www.pfsense.org/") vs. using Ubuntu as the OS?  Ubuntu Server may be overkill.

---

### Post by kevinthecomputerguy on 2011-04-02
[http://woodel.com](http://woodel.com)

---

### Post by DaltonXJ on 2011-04-03
thanks for the info guys but also want this to be a server for storage as well.. need it to be a router for the HP DL360 to get networking capabilities...
 
ok now I got Ubuntu 10.10 Maverick running on a desktop...
 
info below....
 
**System hostname: **linuxserv1
**Operating system: **Ubuntu Linux 10.10
**Webmin version: **1.540
**Time on system: **[Sun Apr 3 12:26:34 2011]("https://192.168.1.12:10000/time/")
**Kernel and CPU: **Linux 2.6.35-22-generic-pae on i686
**Processor information: **AMD Duron(tm), 1 cores
**System uptime: **1 hours, 02 minutes
**Running processes: **[104]("https://192.168.1.12:10000/proc/")
**CPU load averages: **0.05 (1 min) 0.11 (5 mins) 0.09 (15 mins)
**CPU usage: **0% user, 0% kernel, 0% IO, 100% idle
**Real memory: **622.20 MB total, 129.02 MB use
**Virtual memory: **1.78 GB total, 0 bytes used
**Local disk space: **71.59 GB total, 5 GB used
 
ok now I need to know how to add another NIC for the HP DL360 to be able to get it connected..
 
and do I need a straight cable or crossover cable??
 
do I need 2 nic's for the HP DL360 or 1??

---

### Post by volkswagner on 2011-04-03
> **DaltonXJ said:**
> thanks for the info guys but also want this to be a server for storage as well.. need it to be a router for the HP DL360 to get networking capabilities...
 
 
ok now I need to know how to add another NIC for the HP DL360 to be able to get it connected..
 
and do I need a straight cable or crossover cable??
 
do I need 2 nic's for the HP DL360 or 1??

You should not have your file server acting as your router, unless you are not using it as the firewall (using separate firewall)

I am not following you.  Why do you need the DL360 set as a router, to get "connected"?  If you already have a router for you network, why not just have the DL360 act as a file server?

Seems an earlier post you mentioned Netgear.  Is this your router?

Please explain why you need the DL360 to be the router.  Are you planning on getting rid of your Netgear?  Are you trying to create separate networks?

If you want your Server to be the router you will need two NIC's  Your network would look like below with "Computer 1=DL360"
[IMG]http://0.tqn.com/d/compnetworking/1/7/l/3/wired-diagram-3.jpg[/IMG]

If you can keep your router, you can use one NIC in your server and have it share files with other LAN devices.  Like below.  If you router is wireless then the Access point and router can be combined (one device).
[IMG]http://0.tqn.com/d/compnetworking/1/7/i/3/hybrid-diagram-1.jpg[/IMG]

---

### Post by DaltonXJ on 2011-04-03
ok sorry for the confusion..
 
here is what I have..
 
hardware..
 
cable modem
Netgear router (4-port,Wireless access point)
4 - wireless laptops
2 - wireless desktops
1 - wire (cat5 going to Ubuntu box to other end of house.)(only have 1 wire)
1 - wired Ubuntu box (want to use for file server and router for DL360 server)
1 - HP DL360 Server

---

### Post by volkswagner on 2011-04-03
Ah, I think I get it.  You want your wired Ubuntu box to share it's connection to the server box.

First off, you could simply get a network switch for $20-$30 to get additional LAN ports from the one wire you have now.  You could even use any old router you may have, and just use the switch portion (not the WAN jack).

I don't think Router is the best term to use here.  You want to share the connection.

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by DaltonXJ on 2011-04-03
yes that is correct..
 
reason i'm useing linux box is cheep free and reliable  LOL

---

### Post by DaltonXJ on 2011-04-03
AKKKK!!!!  followed the steps in [https://help.ubuntu.com/community/In...nectionSharing](https://help.ubuntu.com/community/In...nectionSharing) 
for the Ubuntu internet gateway method (iptables). I restarted the network and it didn't restart. so I halted. and restarted box and now won't reboot...
 
 
OK reinstall 5 coming up  ...  I'll get it to work here soon
 
 
 
:popcorn:

---

### Post by DaltonXJ on 2011-04-04
OK got 10.10 setup..
 
was going through the woodel.com steps all was doing good till went to login to the samba...  takes me to the /no_auth page...  help!!!!!
 
 
where did I screw up??
 
 
or what did I miss

---

### Post by DaltonXJ on 2011-04-06
OK Server crashed..... Installed Ubuntu 10.10 Desktop ver.
 
you can close this thread!!!!!!!!!!!!!!!!!

---

