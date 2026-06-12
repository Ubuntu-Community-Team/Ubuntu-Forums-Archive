---
title: "SSH Cluster Server"
date: 2012-07-28
forum: Server Platforms
---

### Post by Anvil 31 on 2012-07-28
Hello, I found the other threads to be too complex.

My question is how would I go setting up **multiple servers** on one **physical server**?

I want to setup **ten game servers** using OpenSHH and puTTY on **one physical server** to host my video game servers, do I need to use **CSSH**?

I already made one server on there, but how would i got an putting 10?
**Do I need** to give** different ports** to each individual server?

---

### Post by darkod on 2012-07-28
I have no experience with any SSH Clusters, if that's what they are called, but if you want multiple servers on one physical machine, isn't that virtualization you are talking about?

---

### Post by CharlesA on 2012-07-28
Virtualization would be the way to go.

---

### Post by BkkBonanza on 2012-07-28
Yes, you could look at [OpenVZ]("http://wiki.openvz.org/Main_Page") as it has low overhead and is easy to setup and have large numbers of virtual servers on one machine. There also some web based control panels for it too.

Once setup you can make an install script and then run it in each of the servers from the host command line using a for loop to count thru each server.

Is there some advantage to having lots of little game servers on a machine vs. one main game server?

---

### Post by CharlesA on 2012-07-28
> **BkkBonanza said:**
> 
Is there some advantage to having lots of little game servers on a machine vs. one main game server?

Outside of separation of services, I do not believe there is any benefit.

---

### Post by Anvil 31 on 2012-07-29
Is there any other ways? and what are the pros and cons?

I also would love to know how to set it up :)

But, please I'm new to Ubuntu server, so is it possible if you can make it easier? please?

---

### Post by Lars Noodén on 2012-07-29
In addition to OpenVZ, there would also be [VirtualBox](http://packages.ubuntu.com/precise/virtualbox).

However, is virtualization even needed?  Most server software can be set up to run multiple instances on the same machine.  Doing so would greatly reduce the overhead.  Also, if you have ten virtual machines, that's ten more systems that need to be maintained.

---

### Post by darkod on 2012-07-29
Another option for virtualization is XenServer made by Citrix. If I'm not mistaken it's free and is a product of a very reputable company.
[http://www.citrix.com/lang/English/lp/lp_1688615.asp](http://www.citrix.com/lang/English/lp/lp_1688615.asp)

On the website there are complete instructions for installations, also information about the features, etc.

---

### Post by spynappels on 2012-07-29
+1 to Lars' suggestion, you indicated you were willing to use different ports so this would be the simplest and most elegant solution.

---

### Post by Anvil 31 on 2012-07-29
> **spynappels said:**
> +1 to Lars' suggestion, you indicated you were willing to use different ports so this would be the simplest and most elegant solution.
Wait, will XenServer do the same thing? or will it give a different ip address, if it gives a different ip address for every server, I would like that better.

---

### Post by darkod on 2012-07-29
XenServer is used for virtualization, which means all virtual machines will be independent, like having different physical machines next to each other. So yes, all of them can have different IP. In fact you will NEED to have different IP, since it's considered as different machines and you can't have the same IP twice in a network.

---

### Post by CharlesA on 2012-07-29
> **spynappels said:**
> +1 to Lars' suggestion, you indicated you were willing to use different ports so this would be the simplest and most elegant solution.
+1 (2?) too.

Running another server on a different port would be a good idea too.

I use that when running different source games on my server.

---

### Post by Anvil 31 on 2012-07-29
> **darkod said:**
> XenServer is used for virtualization, which means all virtual machines will be independent, like having different physical machines next to each other. So yes, all of them can have different IP. In fact you will NEED to have different IP, since it's considered as different machines and you can't have the same IP twice in a network.

Well, that seems pretty good for me and it seems like a good use of hardware.

Besides I get confused with ports, i don't' even know how they work, plus they are not physical ports at all...

Anyways, do i install this on ubuntu server or is this just alone by itself on a cd.

---

### Post by darkod on 2012-07-29
> **Anvil 31 said:**
> Well, that seems pretty good for me and it seems like a good use of hardware.

Besides I get confused with ports, i don't' even know how they work, plus they are not physical ports at all...

Anyways, do i install this on ubuntu server or is this just alone by itself on a cd.

XenServer is a stand-alone bootable cd. You boot the server with it and install it. It becomes sort of a "base" of the server, and then you start adding VMs and installing what ever OS you want on them.

But before continuing, consider what other posters are saying too, especially to think about what exactly do you need, and whether you can do it in a simpler and easier way. Many VMs will also mean you need to maintain all of them, but on the other hand if sometimes you make an error in one of them, the others will keep running because they are independent.

Using different ports is not a big deal, but if you are not comfortable with it...

The solutions are there, go with what ever suits you best.

---

### Post by Anvil 31 on 2012-07-29
> **darkod said:**
> XenServer is a stand-alone bootable cd. You boot the server with it and install it. It becomes sort of a "base" of the server, and then you start adding VMs and installing what ever OS you want on them.

But before continuing, consider what other posters are saying too, especially to think about what exactly do you need, and whether you can do it in a simpler and easier way. Many VMs will also mean you need to maintain all of them, but on the other hand if sometimes you make an error in one of them, the others will keep running because they are independent.

Using different ports is not a big deal, but if you are not comfortable with it...

The solutions are there, go with what ever suits you best.

[SIZE=3]Thanks guys, you really helped me a lot I'm going with xenserver :) it seems to suit my needs.[/SIZE]

---

### Post by LHammonds on 2012-07-29
> **Anvil 31 said:**
> [SIZE=3]Thanks guys, you really helped me a lot I'm going with xenserver :) it seems to suit my needs.[/SIZE]
Be careful what you go with.  If you intend on the community to host their own servers, this would limit most of them to being able to host only a single server.

If you do not understand ports very well, you probably should read up on them.

Web servers for example, can be run on any port but the default is port 80.  A single server can host many web sites using the same port but do so by using a different IP.  A single server can be configured to have multiple IP addresses, each with their own domain or sub-domain which then handle traffic based on IP address.  Game servers can work in a similar manner making use of the same port number of your choosing and simply use different IP addresses to keep traffic separated.

LHammonds

---

### Post by Anvil 31 on 2012-07-30
> **LHammonds said:**
> Be careful what you go with.  If you intend on the community to host their own servers, this would limit most of them to being able to host only a single server.

If you do not understand ports very well, you probably should read up on them.

Web servers for example, can be run on any port but the default is port 80.  A single server can host many web sites using the same port but do so by using a different IP.  A single server can be configured to have multiple IP addresses, each with their own domain or sub-domain which then handle traffic based on IP address.  Game servers can work in a similar manner making use of the same port number of your choosing and simply use different IP addresses to keep traffic separated.

LHammonds

I want to go with dedicated, I played hosted games and the performance was horrible.

---

