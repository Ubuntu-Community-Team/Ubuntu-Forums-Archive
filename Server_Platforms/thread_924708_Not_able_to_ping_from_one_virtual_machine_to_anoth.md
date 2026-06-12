---
title: "Not able to ping from one virtual machine to another"
date: 2008-09-19
forum: Server Platforms
---

### Post by akshata on 2008-09-19
Hi,
    I have installed ubuntu on both instances of Sun virtual box that  downloaded. I am able to access internet on both my virtual machines. I statically changed the ip address of both my virtual machines so that they are in teh same subnet. Inspite of this i am not able to ping each other. It returs with a destination unreachable error. is this error related to firewall or nat? If so what changes should i make so that they are able to reach each other?
Could someone please help me out..

---

### Post by pdwerryhouse on 2008-09-21
What sort of networking are you using for virtualbox? If it is the "Internal Networking" option, then you won't be able to get them to talk to one another at all.

Your best bet is to use Host networking and give them real ip-addresses on your network, or use NAT and put them on a bridged interface.

---

