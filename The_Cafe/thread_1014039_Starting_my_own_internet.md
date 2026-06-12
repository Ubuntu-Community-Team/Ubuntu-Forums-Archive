---
title: "Starting my own internet"
date: 2008-12-17
forum: The Cafe
---

### Post by meg23 on 2008-12-17
In my area of town, I would like to start a "separate internet" that is not dependent on the services provided by comcast and the like. It is particularly for an ethnic community with hundreds of families. I would like to start a distributed network using tweaked wireless routers to spread coverage to everyone and direct users to a few central file servers where people can have access to information published by the community, for instance blogs and freely available texts. Is this possible or far fetched?

---

### Post by billgoldberg on 2008-12-17
> **meg23 said:**
> In my area of town, I would like to start a "separate internet" that is not dependent on the services provided by comcast and the like. It is particularly for an ethnic community with hundreds of families. I would like to start a distributed network using tweaked wireless routers to spread coverage to everyone and direct users to a few central file servers where people can have access to information published by the community, for instance blogs and freely available texts. Is this possible or far fetched?

It's possible.

But won't be easy or cheap to set up.

--

Just think of it like setting up a home network, but a thousand time bigger.

--

Wired would be better, but that's most likely not an option.

It should be possible wireless, but you'll need some serious hardware for that.

---

### Post by mips on 2008-12-17
Sounds like you want a Wireless LAN. Not to hard to do depending on your specific scenario. For internet access you will still require an ISP though.

---

### Post by meg23 on 2008-12-17
I figure that most people have wireless routers anyway so it should be easy. However, the distances are too great to run any type of ethernet lines, do I want to set up like a bridge connection scenario, is that even what it is called?

---

### Post by pp. on 2008-12-17
Perhaps you might want to look into a powerline LAN?

---

### Post by jcsteele on 2008-12-17
you can build point-to-point antennas rather cheaply, but you will have to build them yourself: [http://www.oreillynet.com/cs/weblog/view/wlg/448](http://www.oreillynet.com/cs/weblog/view/wlg/448) is a rather broad overview but its the basic idea.  You don't have to use a pringles can (thats silly if you placing it outside)...old satelite dishes work great (the directtv kind) and PVC pipe works well for outdoor use....use google for finding various setups, etc. many are published on the net.

We had a similar project a few years back, which required several radio towers to create a sort of mesh between several "hubs" of the network, the biggest problem was line-of-sight..if you couldn't see a tower, you couldn't get access in between the hubs.  We also had to get permission to either install a new tower, or use an existing tower (lots of rules with this problem like land ownership, etc.).  In between the hubs a person can setup their own router that gives open access to the network as well.  

On a side note, "sharing" a comcast connection to the outside internet to other people freely using your mesh wireless net is a legality problem you will have to check with comcast about - they most likely will object to someone purchasing one high speed internet connection and sharing it will multiple households or hundreds of users.

---

### Post by mips on 2008-12-17
> **meg23 said:**
> However, the distances are too great to run any type of ethernet lines, do I want to set up like a bridge connection scenario, is that even what it is called?

You can use bridges to link large distances by using directional high gain antennas. Instead of bridges I would rather use routers to minimise traffic on the long distance links. you dont need to see see all the layer two traffic in the whole network and it will cause congestion.

---

### Post by meg23 on 2008-12-17
Well, this set up will not have access to the outside internet so the comcast thing is not a big deal.

---

### Post by DonnaMalone on 2008-12-17
Looks like an expensive project, How wide do you think the area of your network will cover?

---

### Post by phen on 2008-12-17
hi!

there's a seperate, free network over berlin. it is called freifunk (means something like free-radio)

[http://global.freifunk.net/](http://global.freifunk.net/)

this is the homepage of the global freifunk network.

you should find lots of information about it there. you can use all the software for your network.

there are lots of movies explaining the setup and stuff, but they are mainly german. maybe you find help in the chat or forums.

---

### Post by meg23 on 2008-12-17
Probably about a 5 mile radius.

---

### Post by pp. on 2008-12-17
The OLPC has implemented some wirelesss mesh which might be applicable to that problem.

---

### Post by koenn on 2008-12-17
> **meg23 said:**
> In my area of town, I would like to start a "separate internet" that is not dependent on the services provided by comcast and the like. It is particularly for an ethnic community with hundreds of families. I would like to start a distributed network using tweaked wireless routers to spread coverage to everyone and direct users to a few central file servers where people can have access to information published by the community, for instance blogs and freely available texts. Is this possible or far fetched?

There are lots of initiatives like this, in cities mostly.
It can often be done with standard WiFi equipment. You may have to look into antennas, like othere have pointed out. If you split the LAN (or MAN) into subnets, you'll have to do some routing, but that can be done with free implementations of routing protocols on Linux or *BSD.

For longer distances, look up Wi-Max as an alternative to WiFi

---

### Post by mips on 2008-12-18
> **meg23 said:**
> Probably about a 5 mile radius.

Thats doable. Next question is how much money do you have at your disposal?

---

### Post by Tomatz on 2008-12-18
Why not just set up a community website? Run it from home.

It would be alot cheaper ;)

---

### Post by Thelasko on 2008-12-18
If I was going to do this, I would use [Open-Mesh.]("http://www.open-mesh.com/store/")  [Here's a article]("http://en.wikipedia.org/wiki/Wireless_mesh_network") about how it works.

---

### Post by barbedsaber on 2008-12-18
I dub thee,
Mini net
(I love being original

seriously, good luck, your gonna need it.

---

