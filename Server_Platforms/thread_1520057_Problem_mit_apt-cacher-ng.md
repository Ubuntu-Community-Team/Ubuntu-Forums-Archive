---
title: "Problem mit apt-cacher-ng"
date: 2010-06-29
forum: Server Platforms
---

### Post by Mandarine on 2010-06-29
Hi,

I got a Sheevaplug since a couple of days, running Debian Squeeze (6.0) on it. Yesterday I installed apt-cacher-ng. 
The Service ist running and I configured the Clients (Ubuntu 10.04) with a proxy for apt

**/etc/apt/apt.conf.d/01proxy**
```
Acquire::http { Proxy "http://sheeva:3142"; };
```

Right now I'm facing the following Problem: The repositories for *de.archive.ubuntu.com* are not found (http 404 error). All other repos (e. g. *archive.canonical.com, packages.medibuntu.org, security.ubuntu.com*) work.

Any suggestions?

Sascha

---

### Post by Mandarine on 2010-07-01
***

can't anybody help?

---

### Post by Plam on 2010-09-23
Same thing here (apt-cacher-ng on Squeeze and clients in Lucid Lynx). 

If anyone can help us, it will be great :D

---

### Post by paulisdead on 2010-09-23
I had to get a very specific deb to get it to work on my debian 5 box, I had a similar problem with a different repo.  The version was 0.4-1.  I've still got the deb, but it's for amd64, so I don't think it would be much good to you, but here it is [http://happyangry.com/debs/apt-cacher-ng_0.4-1_amd64.deb](http://happyangry.com/debs/apt-cacher-ng_0.4-1_amd64.deb)

*sorry if that link was dead earlier today.  I got bit by that qwest backbone in the seattle area going down.  Grab it ASAP since I'm moving tomorrow and my server will be down for awhile after.

---

