---
title: "How to run two instances of apt-cacher-ng"
date: 2014-07-05
forum: Server Platforms
---

### Post by gamer82987 on 2014-07-05
I'm currently migrating installations to Ubuntu/ Xubuntu 14.04.

Newer machines are going to be imaged with the 64bit version of Ubuntu, while the older machines will run 32bit version of Xubuntu. 

Currently the network is configured to go through the apt-cacher-ng to save bandwidth but it was all running the same base installation. With the move to 14.04, i will need to run 2 instances of apt-cacher-ng, one for the 32bit, and the other instance for the 64bit version.

The question is, how can I run two instances of apt-cacher-ng on the same machine?

---

### Post by TheFu on 2014-07-05
Why do you need 2 versions?  I've been mixing/matching with a single cacher for years.

---

### Post by papibe on 2014-07-05
Hi gamer82987.

You don't need two instances. The same service can serve both 32bit clients and 64bits clients.

Also, the service can run be run on any architecture, i.e., the server can be either 32bits or 64bits.

'apt-cacher-ng' is dependent on the 'apt' protocol, not the arch, or even the release.

I have a cacher running on 10.04-32b serving a diverse list of client including, 10.04 32b, 12.04 32b, 12.04 64b, 14.04 64bit.

When you introduce a new client, apt-cacher-ng, just like any other caching proxy, would see if there's a cache for the arch and release. If it is the case, it would serve the cache. If not, it would create a new set of directories, download the new sources/packages and then serve the new created cache.

Does that help? Let us know how it goes.
Regards.

---

### Post by gamer82987 on 2014-07-06
Sweet. Thank you for the replies.

I assumed that I would need to run different instances depending on the specific distribution that is using it.

I read on another apt cacher that multiple instances needed to be ran. I assumed that the same is necessary for apt-cacher-ng
[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

> Warning: Using Apt-Cacher with more than one distribution
Because Debian and Ubuntu have identically named (but different) .deb packages in their repositories, it is unwise to setup a single apt-cacher to be a caching package server for both Debian and Ubuntu clients at the same time. A workaround for advanced users is to run two separate instances of apt-cacher on two separate ports with two separate caches.

---

### Post by TheFu on 2014-07-06
> **gamer82987 said:**
> Sweet. Thank you for the replies.

I assumed that I would need to run different instances depending on the specific distribution that is using it.

I read on another apt cacher that multiple instances needed to be ran. I assumed that the same is necessary for apt-cacher-ng
[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

I don't think so.  /var/cache/apt-cacher-ng is where my repo caching happens (probably the default) and there are separate directory structures for different distros, separate repos and for different architectures under there. It is a hierarchy.

---

