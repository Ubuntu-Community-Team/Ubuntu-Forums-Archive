---
title: "[IDEA] Automatic caching of updates and discovery by other LAN machines"
date: 2007-11-09
forum: Ubuntu Brainstorm
---

### Post by CrazyGuy123 on 2007-11-09
It is easy to set up an apt-proxy repository, however most people don't.

It would be really good to have automatic cache sharing between PC's on a network.

Consider the case of a small home network with 3 PC's, connected to the internet with a fairly slow net connection, but with a fast ethernet/wireless connection between PC's.

When new Ubuntu updates are released, each PC is updated, and the updates are downloaded 3 times.

If when a package download was required the PC requiring the package sent out a broadcast packet to the LAN with info about what package it required.  Any LAN PC with those updates could respond, and a connection set up to transfer the updates.  The process would be repeated for every required package.  If no system responds, the updates will be downloaded from the internet as normal.

This does not impact security, because the packages are signed, and if a signature check failed the download could be made directly from the internet.

Any thoughts?

---

### Post by ccw on 2007-11-09
[https://launchpad.net/ubuntu/+source/apt-proxy](https://launchpad.net/ubuntu/+source/apt-proxy)

And as a network guy: I hate chatty broadcast traffic.

---

### Post by CrazyGuy123 on 2007-11-09
The point wasn't the making of a proxy/cache for the data - the idea was to have some way to auto-discover that data on a HOME network.  I can't think of many other ways to do it other than a broadcast packet.  Manually setting the address of a master cache isn't practical.  Using a master proxy/cache on a home network is limiting - what if it's powered off, yet other ubuntu machines with the packages are powered on?

Broadcast traffic shouldn't be a problem since it's in response to a user action, and probably only one broadcast packet is required.

---

### Post by ccw on 2007-11-09
> **CrazyGuy123 said:**
> The point wasn't the making of a proxy/cache for the data - the idea was to have some way to auto-discover that data on a HOME network.  I can't think of many other ways to do it other than a broadcast packet.  Manually setting the address of a master cache isn't practical.  Using a master proxy/cache on a home network is limiting - what if it's powered off, yet other ubuntu machines with the packages are powered on?

Broadcast traffic shouldn't be a problem since it's in response to a user action, and probably only one broadcast packet is required.

[http://glasnost.beeznest.org/articles/289](http://glasnost.beeznest.org/articles/289)
How hard is it to keep a linux machine up?

Can you plot out this process. I'm confused. Who sending the broadcast? The machine looking for updates or or machines advertising their cache?

---

### Post by CrazyGuy123 on 2007-11-09
> **ccw said:**
> [http://glasnost.beeznest.org/articles/289](http://glasnost.beeznest.org/articles/289)
How hard is it to keep a linux machine up?
Well your average home user doesn't.

> **ccw said:**
> Can you plot out this process. I'm confused. Who sending the broadcast? The machine looking for updates or or machines advertising their cache?
consider the simplist case:

2 computers, A and B.  Computer A is already updated.  Compuer B needs updates.  Computer B sends a broadcast UDP packet with details of what packages it needs.  Computer A receives the packet, then checks it's cache, and if it has those packages responds to computer B (wih unicast UDP).

When computer B gets the response, it now connects to computer A's apt-proxy, and retrieves the required packages.

If computer B gets no response, it downloads the packages from the net as usual.

If computer B gets 2 or more responses, it uses the first response - that gives an element of load balancing on busy networks.


Essentially his is an extension to apt-proxy(or a similar app) to make it discoverable over a network, and an extension to apt to do the discovery.

---

### Post by 23meg on 2007-11-09
[Apt-Zeroconf]("http://trac.phidev.info/trac/wiki/AptZeroconf") does exactly what you want, using Avahi.

---

### Post by CrazyGuy123 on 2007-11-09
Yep - thats exactly it.

Now what are the chances of that being enabled by default in ubuntu?  It would reduce load on Canonicals servers considerably, and considerably reduce the amount of time it takes to perform an update in he case of a home network.  It would be especially good for accelerating dist-upgrades which are normally large.

---

