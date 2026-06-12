---
title: "Multiple NICs for Virtualbox 3 nics, one for host and 2 for vm guests"
date: 2014-11-08
forum: Virtualisation
---

### Post by cmp828 on 2014-11-08
Hello,

I am new to this forum group. I have tried to read the Virtualbox and general Googlesearchs on this question with little luck.
Running Ubuntu 14.04LTR 64 bit. I have three network interfaces installed in the computer. I want to assign two of the adapters to the Virtualbox guests. All three network cards would be on the same network.
Is there a way to assign just the one card for just the Host computer, and then a way to set up eth2 and 3 so that only traffic from the VMS and Virtualbox runs across them? Else to provide load balance or combine bandwidth so I have a 3 meg eth connection. Ideally I want eth1 to be used only by the host machine, and then assig the eth2 and 3 nics for just the VMs traffic.

I have seen some things about bonding the three interfaces, well bonding, and some things about routing tables and touting on different subnets. I even saw one note to say to disable the tcp/ip on say the ipv4 section of the interfaces for the virtualbox use, but does not appear to be working.

Trying to find the best place to ask this question and best method to do this.
My main Linux computer runs several VMs all the time, and besides using seperate drives for each VM, I want to try to use multiple interfaces as well to help keep VM traffic from killing the network connection of the main host linux machine.

Chad

---

