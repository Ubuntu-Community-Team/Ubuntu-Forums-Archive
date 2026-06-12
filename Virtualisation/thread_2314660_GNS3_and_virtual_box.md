---
title: "GNS3 and virtual box"
date: 2016-02-22
forum: Virtualisation
---

### Post by matt18 on 2016-02-22
I am going to be building a new box that will be dedicated to running only GNS3 and virtual box. 

Main questions:

How much faster is ubuntu( using cinimin or even lxde desktop) at running these two programs vs on a windows machine?

My goal is to have at least a firewall, 3 or 4 routers running ospf, bgp and maybe eigrp and then 4 VM's running. How much RAM should i get and what CPU is going to be able to keep up with the machines and the network?

I stopped using virtual box 3 years ago because i could never get any of my VM's to run full screen and it was bugging me so bad. Have they fixed this? My desktop will most likely not have a GPU in it, just onboard video.

Is it possible for my laptop to do all of this? it is running win 10. it has 12gb ram and a dual core amd

thanks

---

### Post by christiaan3 on 2016-02-23
Answering a part of your question. Virtual box did fix a lot of their stuff. If you want to use full screen you should install guest additions. If you don't how to install this, you can reply on this and I will explain it to you. An ubuntu machine basically doesn't need more than 2GB ram so you will be good with that. If you put your virtual box on bridging mode you should be good with your routing protocols too, since this makes your VM figure as a normal part of the network. Basic CPU settings are pretty much fine. I run 3 VM's with virtual box on a PC with 12 GB ram and an eight core processor. This works without any problems. I think you will be able to make your virtual machines work like that. The choice of running it on Windows or Linux is up to you. Personally I run my VM's on a windows machine because of drivers.

Christiaan

---

### Post by howefield on 2016-02-23
Moved to the "*Virtualisation*" forum.

---

### Post by matt18 on 2016-02-23
ok cool. Im just trying to do some cool stuff. i do have an old p4 3.20ghrz with some ram BUT i know that probably wouldnt do the trick haha. i do have a laptop that has 12gb ram and an amd cpu. My only downfall is win 10. it seems to SUCK alot of memory. 

My main goal is to have a really awesome gns3 and vm set up at home that i can log into remotely and practice pen testing over routers and firewalls. I have done a ton of routing for my ccna and ccnp classes but i really want to apply it to pen testing. 

Im just wondering if it would be more benificail to get a second HDD for the laptop and install ubuntu on it for the mere fact that programs do seem to run faster on linux. 

thanks

Oh, i will have to try out virtual box to see if i can get the add ons working.

---

### Post by MAFoElffen on 2016-02-24
You need to check out GNS#'s minimum and recommended hardware requirements for the hypervisor host:
[https://www.gns3.com/software](https://www.gns3.com/software)

min is 2 core CPU with vt-m, 4 GB RAM and 64bit OS. Recommended is an Intel i7 4 core, with 8 GB's RAM. 

My curiosity: If you are doing Cisco CCENT, CCNP, & CCNA... then why not with Cisco's Packet Tracer? Which is what you are going to be tested with/on?

---

