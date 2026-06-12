---
title: "bind9 instalation"
date: 2008-05-27
forum: Server Platforms
---

### Post by phillhs on 2008-05-27
Hi, 

I'm running hardy server, and am trying to setup a DNS/DHCP server, but have a couple of problems, firstly I am unable to install bind9, when I try i get :

```

root@quinn:~# apt-get install bind9 dnsutils
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package bind9 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  dnsutils
E: Package bind9 has no installation candidate

```

secondly, I need to know what I need to install for the dhcp server package, I tried searching using aptitude's search facility but found it not very helpfull.

Cheers.

Phill.

---

### Post by windependence on 2008-05-27
First off, most people never should need to run their own DHCP or DNS server unless they have many many computers to manage. You may be under the impression you need to run these when you really don't. A lot of people think they have to run their own nameservers to host their own sites. You don't have to do this if you use your domain registrar's nameservers. DHCP is usually provided by your router, so usually you don't need this either. 


What are you planning to do with this server?


-Tim

---

### Post by phillhs on 2008-05-27
> **windependence said:**
> First off, most people never should need to run their own DHCP or DNS server unless they have many many computers to manage. You may be under the impression you need to run these when you really don't. A lot of people think they have to run their own nameservers to host their own sites. You don't have to do this if you use your domain registrar's nameservers. DHCP is usually provided by your router, so usually you don't need this either. 


Well.... since I am part of the team that manages the departmental computers of a large UK university (we have somewhere in the region of 600-700 machines), I'd say that yes I have a large number of machines :) 

Though they are already DNS/DHCPd of our SuSE 10 servers...

> 
What are you planning to do with this server?


In this case trying to set up a cluster of machines of which the master / gateway node will be DNS/DHCP for the nodes in the cluster, just to make things easier, and have a single point of administration, the cluster in question has 24 nodes, so doing it with config files does become a real headache.

I know what I'm doing with DNS/DHCP once I get the severs installed, in terms of configuring them I'm just having problems getting the damn things installed :)

Cheers.

Phill.

---

### Post by windependence on 2008-05-27
> **phillhs said:**
> Well.... since I am part of the team that manages the departmental computers of a large UK university (we have somewhere in the region of 600-700 machines), I'd say that yes I have a large number of machines :) 

Though they are already DNS/DHCPd of our SuSE 10 servers...



In this case trying to set up a cluster of machines of which the master / gateway node will be DNS/DHCP for the nodes in the cluster, just to make things easier, and have a single point of administration, the cluster in question has 24 nodes, so doing it with config files does become a real headache.

I know what I'm doing with DNS/DHCP once I get the severs installed, in terms of configuring them I'm just having problems getting the damn things installed :)

Cheers.

Phill.

No problem Phill, you actually DO have a great need for this. We just get so many people here that think they need a DHCP/DNS server for 5 machines. :) Have you considered clustering the DHCP/DNS servers as well? otherwise you will have a single point of failure.

-Tim

---

### Post by windependence on 2008-05-27
Oh, forgot to mention. For your problem try doing:


```
sudo apt-get install dnsutils

```

HTH

-Tim

---

